# 05 — Metodologi Harmonisasi (detail langkah 3–7 di 06)
Sumber: `riset/A-sensor-harmonization.md` §1–5 dan §7. Label: **[V]** dibaca di sumber primer · **[S]** abstrak/ringkasan · **[I]** inferensi/hitungan · **[U]** belum pasti.
Ini spesifikasi metode. **Kodenya ditulis saat hackathon.**

> ## 🔒 Keputusan terkunci (23 Okt 2026), berlaku untuk semua file 04–10
> 1. **Arah kalibrasi: MODIS → setara-VIIRS.** Satuan acuan adalah **fire cell-day VIIRS S-NPP**. Nilai era MODIS dipetakan ke satuan VIIRS (bukan sebaliknya). Alasannya: rekaman masa kini dan masa depan hanya VIIRS (S-NPP → NOAA-20/21), jadi kalender hari ini tetap "teramati", dan MODIS hanya memperpanjang rekaman ke belakang. Semua frasa "VIIRS → setara-MODIS" di versi lama sudah dikoreksi.
> 2. **Jendela fit Aqua → S-NPP: Feb 2012 – Des 2022.** Alasan satu baris: Feb 2012 adalah bulan penuh pertama S-NPP (data mulai 20 Jan 2012), dan Des 2022 menutup tahun kalender terakhir sebelum Aqua melewati batas jam lintas 13.45 (Feb 2023), sehingga LOYO tetap 11 tahun utuh (2012–2022) tanpa bulan yang tercemar drift.
> 3. **Scope MVP** mengikuti `08-rencana-39-jam.md` (versi 23 Okt): toggle mentah ↔ harmonisasi, kalender 3 provinsi (Riau, Kalteng, Sumsel), **M2 vs M1** dengan LOYO, satu cek independen vs SiPongi, pita ketidakpastian. Bagian lain di file ini yang tidak termasuk daftar itu = **stretch**.


## 1. Fakta sensor yang menentukan desain
| Hal | MODIS (Terra/Aqua, C6.1) | VIIRS 375 m (S-NPP, NOAA-20, NOAA-21, C2) |
|---|---|---|
| Mulai rekaman | Terra Nov 2000, Aqua Jul 2002 | S-NPP 20 Jan 2012; NOAA-20 Apr 2018; NOAA-21 Jan 2024 |
| Piksel nadir → tepi | 1 km → ±4,8 × 2,0 km di tepi swath | 375 m → ±795 × 784 m (pertumbuhan piksel dibatasi agregasi on-board) |
| Kepercayaan | Angka 0–100 (rendah <30, nominal 30–79, tinggi ≥80) | Kategori `l`/`n`/`h`; **tinggi = piksel jenuh** |
| Jam lintas | Terra ±10.30 (bergeser ke ±09.06), Aqua ±13.30 (bergeser ke ±15.30) | Semua JPSS di slot 13.30, swath berbeda → sampel independen |

**Kenapa satu faktor global tidak bisa dibela:**
- Rasio VIIRS/MODIS di Indonesia ±5,2× (Vadrevu 2019) [V].
- Di Amerika Selatan rasionya 2,84–11,25× antar-kabupaten (White 2023) [V].
- Rasio lebih tinggi di malam hari (375 m vs 750 m: 17–25×), off-nadir, untuk api kecil/intensitas rendah, dan di tropis karena celah orbit MODIS [V/S].

## 2. Prinsip desain (sebutkan di slide metode)
1. **Satuan VIIRS adalah acuan.** Nilai era MODIS = estimasi "setara VIIRS" + pita. Jangan klaim menemukan api yang tidak terlihat MODIS.
2. **Kalibrasi hanya like-for-like dan bebas drift:** Aqua vs S-NPP (sama-sama 13.30); fit **Feb 2012 – Des 2022**, sebelum Aqua melewati batas sains 13.45 pada Feb 2023 [V]. (Versi lama menulis "sampai Jan 2023"; dikoreksi agar sama dengan 04, 10, dan §5.)
3. **Hitung okupansi, bukan piksel:** *fire cell-day* di grid 0,1°. Ini menghapus sebagian besar efek ukuran piksel, bow-tie, dan duplikat.
4. **Langkah waktu harmonisasi = bulanan.** Panduan MODIS memperingatkan bias untuk interval <±8 hari [V]. Tampilan harian/dasarian hanya VIIRS mentah.
5. **Semua angka dilaporkan dengan skill out-of-sample dan pita ketidakpastian.**

## 3. Pembersihan data (urutan)
1. **Parse:** `acq_date`+`acq_time` (UTC) → **waktu matahari lokal** = UTC + bujur/15. Ini menjaga lintasan malam 01.30 di tanggal yang benar. Simpan `satellite` sebagai ID aliran: Terra, Aqua, N, N20, N21.
2. **Kepercayaan:** MODIS ≥30; VIIRS `n` + `h`. Uji sensitivitas dengan MODIS ≥0/≥80 dan VIIRS termasuk `l`.
3. **Sumber panas statis (jangan hanya mengandalkan `type`):**
   - Buang `type ≠ 0` bila ada (hanya data standar; data NRT tidak punya `type`).
   - **Masker persisten buatan sendiri** dari semua tahun VIIRS malam: sel ±0,01° dengan ≥5 deteksi di ≥3 tahun berbeda, atau terdeteksi ≥16 hari dalam setahun. Terapkan ke **kedua sensor dan semua tahun** supaya tidak berubah terhadap waktu.
   - Buffer gunung api aktif 5 km (daftar Smithsonian GVP).
   - Buang deteksi di atas air.
   - Alasannya: ±13% deteksi VIIRS Indonesia bukan biomassa (43% industri/tambang, 14% gas flare; Sofan 2022) [V]. Panas industri yang tumbuh setelah 2015 akan menciptakan **tren naik palsu**.
   - Jebakan versi: di berkas FIRMS per negara, piksel pabrik yang sama bertipe **0** pada berkas 2001/2015 tetapi **2** pada 2022/2024 [V, teramati]. Bug `type` VIIRS baru diperbaiki Mei 2025.
4. **Outage:** tandai hari sensor yang hilang via endpoint `missing_data` FIRMS. Outage yang jatuh di musim api: Aqua 16 Agu–2 Sep 2020; S-NPP 26 Jul–10/20 Agu 2022; S-NPP 9–13 Mar 2026. Keluarkan bulan-bulan ini dari fitting; isi celah dengan sensor sekeluarga + pita lebih lebar.

## 4. Binning dan agregasi
- **Grid 0,1°** (±11 km): lebih besar dari piksel tepi MODIS (≤4,8 km), cukup halus untuk kubah gambut.
- **Fire cell-day:** bernilai 1 jika ≥1 deteksi aliran *k* jatuh di sel *c* pada hari matahari *d*. Simpan juga hitungan piksel mentah dan jumlah FRP (untuk tampilan dan uji sensitivitas).
- **Fraksi gambut** *p_c* per sel (GFW Global Peatlands / Miettinen 2016, CC BY 4.0): gambut ≥0,5; non-gambut <0,1; sel campuran dipisah atau dibuang dari fitting.
- **Agregasi bulanan**, siang (D) dan malam (N) terpisah; total per strata.

## 5. Era dan penanganan drift
| Era | Bulan | Sumber "setara VIIRS" |
|---|---|---|
| E0 *(stretch)* | Nov 2000 – Jun 2002 (Terra saja) | Terra→Aqua (fit 2003–2019) lalu Aqua→VIIRS; ditandai keyakinan rendah. **MVP mulai Jul 2002** |
| E1 | Jul 2002 – Jan 2012 | Aqua→VIIRS; Terra hanya mengisi celah Aqua |
| E2 | 20 Jan 2012 – 2 Nov 2026 | S-NPP teramati. *(Stretch)* NOAA-20 dikalibrasi ke satuan S-NPP (overlap Apr 2018–Nov 2026) untuk mengisi celah; di MVP bulan outage S-NPP cukup ditandai |
| E3 *(stretch)* | sejak 2 Nov 2026 | NOAA-20 (dan NOAA-21 setelah dikalibrasi di overlap 2024–2026) dipetakan ke satuan S-NPP. Di MVP, Nov 2026 ditandai "belum lengkap" |

- **Jendela fit:**
  - Aqua→S-NPP: **Feb 2012 – Des 2022**
  - Terra→Aqua: **2003–2019** (sebelum manuver inklinasi terakhir Terra, Feb 2020)
- **Sejak 2023:** pakai **VIIRS teramati** sebagai rekaman. Estimasi dari MODIS hanya diagnostik, sehingga kalender masa kini bebas drift.
- **Slide diagnosa drift:**
  - Residual bulanan log(VIIRS teramati / prediksi dari Aqua) 2012–2026 vs jam lintas Aqua.
  - Rasio Terra/Aqua sepanjang waktu.
  - Residual sistematis setelah 2022 = besaran drift. Ini poin bagus untuk juri.

## 6. Stratifikasi
> **MVP:** strata = pulau (Sumatra, Kalimantan, sisanya digabung) × siang/malam, disusutkan ke fit nasional. **Stretch:** gambut/non-gambut dan strata lengkap ±28 di bawah.

- **Pulau** (±7: Sumatra, Kalimantan, Sulawesi, Jawa–Bali, Nusa Tenggara, Maluku, Papua) × **gambut/non-gambut** × **siang/malam** → ±28 strata; gabungkan yang jarang.
- **Aturan data minimum:** ≥50 fire cell-day Aqua di jendela fit; kalau kurang, pakai induknya (pulau → nasional).
- Opsional: kovariat musim kering (Jun–Okt) vs basah. Cek jendela Feb–Mar Riau secara empiris.

## 7. Model transfer
> **MVP: hanya M2 (inti) vs M1 (baseline naif).** M0, M3, M4, ensemble, dan VIIRS↔VIIRS = stretch. Rencana lama "fit semua, pilih lewat validasi silang, ensemble 2 terbaik" ditunda sampai MVP selesai.

| Model | Bentuk | Peran |
|---|---|---|
| **M0** rasio per strata (ala INPE/QFED) | Ŷ_V = k_s · Y_A | Baseline |
| **M1** rasio nasional | satu *k* | Baseline naif yang harus dikalahkan |
| **M2** power law, **inti** | GLM binomial negatif per strata: log E[Y_V] = α_s + β_s · log(Y_A + 1) [+ γ_s · musim kering]; α, β disusutkan (ridge) ke fit nasional | β_s < 1 menangkap rasio tinggi di bulan sepi (api kecil) dan lebih rendah di bulan ekstrem |
| **M3** quantile mapping per strata & musim | F_V⁻¹(F_A(Y_A)); ekstrapolasi linear di ruang log di atas maksimum latih; bulan-bulan itu ditandai | Menangkap non-linearitas |
| **M4** ruang anomali (ala GWIS/INPE) | Persentil tiap sensor terhadap baseline-nya sendiri | Ditampilkan berdampingan; kesepakatan kategori M2/M3 vs M4 diukur dengan Cohen's κ (2012–2022) |
| VIIRS↔VIIRS | Bentuk M2 untuk NOAA-20→S-NPP (harapannya β≈1, α≈0) | Rantai kontinuitas pasca S-NPP |

- **Alokasi spasial (konsisten massa):** Ŷ_V(c,t) = Y_A(c,t) · [Ŷ_V(s,t) / Y_A(s,t)].
- Sel yang tidak terlihat MODIS tetap 0. Nyatakan terus terang bahwa ini **batas bawah deteksi**.

## 8. Protokol validasi (out-of-sample)
> **MVP: butir 1 (LOYO 11 fold) + butir 7 poin pertama (Spearman vs SiPongi).** Metrik MVP: MAE, persen bias, R² pada log1p, Kendall τ anomali, cakupan interval 90%. Butir 2–5, κ, dan cek El Niño/curah hujan = stretch.

1. **Leave-one-year-out** 2012–2022 (11 fold).
2. **Holdout tahun ekstrem:** latih tanpa **2015 dan 2019**, lalu prediksi keduanya. 2023 hanya sebagai uji karena masuk periode drift.
3. **Uji maju terblok:** latih 2012–2017, uji 2018–2022 (stasioneritas).
4. **Uji drift:** terapkan model 2012–2022 ke Aqua 2023–2025, laporkan tren bias.
5. **Spatial-block:** leave-one-province-out, untuk mencegah akurasi yang menggelembung (Ploton 2020).
6. **Metrik** per strata dan gabungan:
   - R² pada log1p(cell-day) + Nash–Sutcliffe
   - persen bias tahunan dan musim kering
   - MAE dan MAE/rata-rata
   - **Kendall τ** pada anomali bulanan
   - **Cohen's κ** untuk kelas kalender (<P10, P10–P50, P50–P90, >P90)
   - galat waktu puncak
   - **cakupan interval prediksi 90%** (target ±0,90)
   - penurunan MAE vs M0/M1
7. **Cek independen (bukan satelit vs satelit):**
   - Spearman ρ jumlah tahunan harmonisasi nasional vs **luas terbakar SiPongi 2015–2024** (10 titik, indikatif).
   - Bulan di atas normal vs tahun El Niño/IOD+ (2002, 2004, 2006, 2009, 2015, 2019, 2023) dan curah hujan <±4 mm/hari (Field 2016).
   - Opsional: MCD64A1/VNP64A1.

## 9. Ketidakpastian
> **MVP:** derau prediktif binomial negatif M2 + bootstrap blok-tahun (B ≈ 200 untuk menghemat waktu) → pita 5–95% di grafik seri; sel kalender diarsir bila interval 90% melintasi lebih dari satu kelas kalender. **Stretch:** probabilitas kelas penuh, inflasi era E0, dan Tier 3 GEE.

- **Parameter:** bootstrap blok-tahun (B ≈ 500), fit ulang M2/M3.
- **Noise sampling:** derau prediktif binomial negatif → pita 5–95% untuk nilai bulanan dan persentil turunan.
- **Keyakinan kategori:** pita → probabilitas tiap kelas kalender; **arsir sel** bila probabilitas kelas teratas <0,7.
- **Inflasi era:** pita diperlebar untuk E0, bulan yang celahnya diisi, dan ekstrapolasi M3.
- **Tier 3 (kalau sempat, ±4–6 jam di GEE):** hitung observasi daratan cerah per sel per bulan dari FireMask MYD14A1/VNP14A1 (kelas 5, 7, 8, 9). Lalu modelkan fire cell-day **per observasi cerah**. Ini menjawab langsung kelemahan "titik api tidak membawa info awan".

## 10. Keluaran kalender dan peringatan dini
- **Heatmap kalender:** baris = tahun 2001–kini, kolom = bulan; nilai = cell-day setara VIIRS atau persentil vs baseline (2003–2022, atau 2012–2022 VIIRS saja); lencana era, sensor, dan arsiran ketidakpastian.
- **Periode kritis:** bulan dengan median porsi aktivitas tahunan >2 × (1/12), plus onset dan dasarian puncak (VIIRS mentah sejak 2012).
- **Kondisi tak biasa:** bulan >P90 atau <P10, dengan probabilitas kategori.
- **Peringatan dini:** cell-day NRT NOAA-20/21 bulan berjalan vs persentil klimatologi dasarian VIIRS sejak 2012 (murni VIIRS, tanpa MODIS). Opsional digabung dengan ambang curah hujan.
- **Panel provenance:** versi produk, filter, daftar outage, skill model untuk strata tersebut.

## 11. Enam grafik untuk kriteria Validity (MVP = 1, 2, 3, 6 + grafik SiPongi; 4 dan 5 = stretch)
1. **[MVP]** Aqua vs S-NPP cell-day bulanan per strata (log-log), Feb 2012 – Des 2022, + garis fit M2 dan M1.
2. **[MVP]** Prediksi LOYO vs teramati, diwarnai per tahun; 2015 & 2019 disorot.
3. **[MVP]** Tabel skill M2 vs M1 (MAE, bias, τ, cakupan interval). *(Stretch: tambah M0, M3, κ.)*
4. *(stretch)* Residual drift vs jam lintas Aqua 2012–2026 + rasio Terra/Aqua.
5. *(stretch)* Peta masker sumber statis (gunung api, flare, smelter) + porsi deteksi yang dibuang per tahun.
6. **[MVP]** Kalender Riau, Kalteng, dan Sumsel Jul 2002–2026 (satuan setara-VIIRS) dengan arsiran ketidakpastian dan label tahun El Niño. Ditambah grafik **[MVP]** Spearman ρ vs luas terbakar SiPongi (mentah MODIS vs mentah VIIRS vs harmonisasi).

## 12. Bahasa yang disiplin
- Katakan **"aktivitas titik panas" / "deteksi api"**, jangan "jumlah kebakaran" atau "luas terbakar".
- Tidak ada prakiraan ML kecuali sudah dikontrol kebocorannya dan divalidasi spasial. Kalau tidak sempat, **tinggalkan**.
- Setiap angka bisa dilacak ke nama pendek produk + DOI.
