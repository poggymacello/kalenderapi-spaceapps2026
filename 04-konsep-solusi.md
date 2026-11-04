# 04 — Konsep Solusi: KalenderApi
Dokumen ini berisi **ide dan keputusan produk**. Implementasinya dibuat saat hackathon (lihat 06 dan 08).

> **Diperbarui 23 Okt 2026:** arah kalibrasi dan jendela fit dikunci di kotak paling atas `05`: **MODIS → setara-VIIRS, fit Feb 2012 – Des 2022**. Fitur ditandai **[MVP]** atau **[stretch]** sesuai `08` versi 23 Okt.
>
> **Tambahan 23 Okt malam (JURI_90):** §7 matriks adaptasi terhadap pernyataan tantangan yang terbit 28 Okt · §8 keluaran yang bisa langsung dipakai untuk keputusan BPBD · §9 "aha" satu kalimat · validasi independen cadangan memakai data NASA (MCD64A1) untuk menghindari risiko lisensi data non-NASA (T&C 2026).

## 1. Satu kalimat
**KalenderApi** menyambung rekaman titik panas MODIS (2000–) dan VIIRS (2012–) menjadi **satu seri yang konsisten, lengkap dengan ketidakpastiannya**, lalu menyajikannya sebagai **kalender aktivitas pembakaran untuk wilayah mana pun**. Hasilnya, BPBD dan pengambil keputusan bisa menjadwalkan status siaga, patroli, dan modifikasi cuaca **sebelum musim api lokal dimulai**.

Tagline (EN): *"One fire record, every satellite, any place: know when your area burns before it does."*

## 2. Siapa penggunanya dan keputusan apa yang dibantu
| Pengguna | Keputusan | Tampilan yang menjawab |
|---|---|---|
| **BPBD / kepala daerah** | Kapan menetapkan *siaga darurat* (membuka bantuan BNPB) | Onset & puncak musim per kabupaten; "biasanya mulai minggu ke-…" |
| **BNPB / satgas** | Rotasi helikopter, jadwal OMC sebelum puncak | Puncak antarprovinsi yang berbeda-beda; jendela "masih basah" terakhir |
| **Kemenhut / Manggala Agni** | Patroli di lokasi terbakar berulang | Kalender per KHG/kecamatan; anomali musim berjalan |
| **BMKG** | Mandat "tren dan siklus musim" (Inpres 3/2020) | Klimatologi aktivitas pembakaran yang tahan pergantian sensor |
| **Jurnalis / kebijakan** | Klaim "naik/turun" antartahun | Seri harmonisasi + pita ketidakpastian, bukan angka mentah campuran |
| **Operator ala INPE / ilmuwan NASA** | Kontinuitas rekaman | Seri referensi setara-Aqua + indeks harmonisasi multi-sensor, metode terbuka |

> Hipotesis pengguna di atas diambil dari dokumen resmi dan liputan. **Lebih kuat lagi kalau tim bisa mewawancarai satu praktisi** (BPBD/Manggala Agni) sebelum 14 Nov. Wawancara itu riset, bukan "membangun".

## 3. Fitur (selaras dengan MVP di 08)
1. **Pilih area:** **[MVP]** 3 provinsi: Riau, Kalimantan Tengah, Sumatera Selatan. **[stretch]** kabupaten, gambar poligon, negara lain (bukti generalisasi).
2. **[MVP] Kalender Api:** heatmap tahun × bulan, Jul 2002–2026 (2000–2002 Terra-only = stretch). Warna menunjukkan persentil terhadap baseline. Sel berketidakpastian tinggi diarsir.
3. **[MVP] "Kenapa harus diharmonisasi?":** toggle mentah MODIS vs VIIRS (patahan 2012) ↔ seri harmonisasi + pita. **Ini momen demo utama.**
4. **[MVP] Periode kritis:** bulan dengan porsi aktivitas >2× rata-rata, plus onset dan puncak.
5. **[MVP, ringan] Bulan anomali + label tahun El Niño** (2015, 2019, 2023, 2026) sebagai label statis. Komposit per fase ENSO = stretch (butir 7).
6. **Tracker 2026:** kumulatif tahun berjalan vs amplop historis P10–P90 *(stretch)*.
7. **Kalender per fase ENSO (RONI):** "kalau El Niño, area ini biasanya…" *(stretch)*.
8. **Bulletin 1 halaman ID/EN** untuk BPBD *(stretch)*.
9. **[MVP] Halaman metode & validasi:** metrik M2 vs M1 (LOYO), cek SiPongi, keterbatasan, sitasi data, repo.
10. **[stretch] Mode kepercayaan eksplisit:** "SiPongi-compatible" (tinggi saja), "NASA-recommended" (nominal + tinggi), "All". Pengali antar-mode ikut ditampilkan, supaya kekacauan 20–30× di §3 dokumen 02 terlihat dan terjelaskan.

## 4. Keputusan ilmiah yang diambil sejak awal (ringkasan 05)
- **Satuan VIIRS sebagai acuan.** MODIS-era menjadi "setara VIIRS" **dengan pita ketidakpastian**; tidak pernah mengklaim menemukan api kecil yang tidak terlihat MODIS.
- **Hitung okupansi, bukan piksel:** *fire cell-day* di grid 0,1°.
- **Harmonisasi bulanan**, karena MODIS bias untuk interval <8 hari. Tampilan harian/dasarian hanya VIIRS mentah.
- **Kalibrasi hanya like-for-like dan bebas drift:** Aqua (13.30) vs S-NPP (13.30), jendela fit **Feb 2012 – Des 2022**.
- **Setiap angka punya sumber produk (nama pendek + DOI) dan ketidakpastian.**

## 5. Kenapa konsep ini menjawab kedua kemungkinan penulis tantangan
| Jika penulisnya… | Yang mereka cari | Yang kita tunjukkan |
|---|---|---|
| **NASA (FIRMS / tim sains api)** | Produk standar, ketidakpastian, validasi independen, kosakata "harmonized, uncertainties, independent reference" | **MVP:** M2 vs M1 dengan LOYO + cek vs luas terbakar SiPongi + pita. *Stretch:* M3, spatial-block, MCD64A1, slide diagnosa drift |
| **AEB/INPE (Brasil)** *(28 Okt: kredit foto statement = CONAE Argentina, jadi baris ini kurang mungkin; lihat `12` §1)* | Seri referensi yang bertahan melewati pergantian satelit | **MVP:** argumen bahwa satuan acuan VIIRS bertahan setelah MODIS pensiun. *Stretch:* mode seri referensi setara-Aqua, rantai NOAA-20/21 setelah S-NPP berhenti (2 Nov 2026), contoh Pará (Brasil) |

## 6. Peta kriteria juri → bukti di produk
| Kriteria | Bukti |
|---|---|
| Impact | Keputusan *siaga darurat* yang membuka bantuan BNPB; El Niño berlanjut ke Feb–Mar 2027 |
| Creativity | **MVP:** jendela fit bebas drift + pita ketidakpastian di kalender + pengguna BPBD yang konkret. *Stretch:* normalisasi observasi, strata gambut, rantai NOAA-21 |
| Validity | **MVP:** tabel skill M2 vs M1 (LOYO), validasi vs SiPongi, cakupan interval prediksi. *Stretch:* spatial-block, MCD64A1 |
| Relevance | Data NASA (FIRMS MODIS C6.1, VIIRS C2) adalah inti; 3 provinsi gambut prioritas (area bebas & bilingual = stretch) |
| Presentation | Demo 30 detik dengan toggle patahan 2012; halaman proyek seperti mini-paper (09) |

## 7. Matriks adaptasi: kalau pernyataan tantangan (28 Okt) berbeda dari asumsi
Inti yang **tidak berubah** apa pun isi statement: grid 0,1° × fire cell-day × aliran sensor, fit pada periode overlap dengan validasi out-of-sample, pita ketidakpastian, toggle mentah ↔ harmonisasi. Yang berubah hanya **arah, satuan waktu, wilayah, dan keluaran**. Isi kolom "keputusan" pada 28 Okt, lalu catat di `11` §5.

| # | Kalau statement… | Yang naik ke MVP | Yang turun ke stretch | Biaya tambahan | Keputusan 28 Okt |
|---|---|---|---|---|---|
| S1 | Meminta satuan acuan **setara-MODIS** atau "MODIS-like continuity" | Arah dibalik: VIIRS → setara-Aqua dengan bentuk M2 yang sama (fit di jendela yang sama). Kalender tetap ditampilkan juga dalam satuan VIIRS sebagai opsi | Tidak ada | ±1 jam (simetris dengan M2) | **Tidak aktif** (statement tidak menentukan satuan) |
| S2 | Meminta kalender **mingguan/harian** | Klimatologi dasarian **VIIRS-saja** untuk 2012+ (tidak boleh dari MODIS, lihat `05` §2.4); kalender bulanan harmonisasi untuk 2002+ | Bulletin, ENSO | ±2 jam | **Tidak aktif** (statement memakai bulan) |
| S3 | Mewajibkan **AOI bebas** (gambar poligon / unggah) | Kustom poligon (Turf.js di atas grid sparse) | Kalender per kabupaten, ekspor CSV | ±3 jam | **Aktif sebagian:** MVP = preset + input lintang/bujur + radius (±1,5 jam); poligon = stretch tier 1. Ekspor CSV **tidak** turun (diminta statement, lihat S9 di `12`) |
| S4 | Menekankan **global / negara lain** | Satu wilayah non-Indonesia sebagai bukti generalisasi (berkas negara FIRMS ada untuk semua negara; kandidat: Brasil/Pará kalau penulisnya AEB/INPE) | Provinsi ke-3 | ±2 jam | **Tidak untuk MVP.** Stretch tier 1: satu wilayah Argentina (penulis kemungkinan CONAE [inf]) |
| S5 | Meminta **intensitas** (FRP) atau luas, bukan jumlah | Varian "FRP-weighted cell-day" memakai field `frp` yang sudah ada di CSV | M3/M4 | ±1–2 jam | **Tidak aktif** (statement meminta jumlah hotspot) |
| S6 | Meminta **peringatan dini / anomali musim berjalan** | Tracker 2026 vs amplop P10–P90 (VIIRS NRT, tanpa ML) | Komposit ENSO | ±2 jam | **Aktif:** MVP = kartu "bulan lengkap terakhir (Okt 2026) vs median 2002–2025 + P25–P75" (±1 jam); tracker kumulatif tetap stretch |
| S7 | Menyebut **NOAA-20/21 wajib** (pasca S-NPP) | Rantai NOAA-20 → satuan S-NPP (overlap Apr 2018 – Nov 2026) | Gambut | ±2 jam | **Tidak aktif** (tidak disebut); tetap stretch tier 2 untuk Nov 2026 |
| S8 | Menyebut dataset wajib lain (mis. MCD64A1, VNP14A1) | Dataset itu masuk validasi atau normalisasi observasi | Butir stretch dengan biaya setara | tergantung | **Tunggu tab Resources 13 Nov** (FIRMS disebut sebagai saran) |

> **Diputuskan Rab 28 Okt 2026 malam** setelah membaca statement resmi (rincian dan dua baris baru S9 rentang tanggal + unduh, S10 palet aksesibel: `12` §2–§3). Tiga baris aktif berbiaya (S3, S6, S9) → aturan di bawah dijalankan: **provinsi preset turun ke 2 (Riau + Kalteng)**; Sumsel lewat input lintang/bujur dan kembali kalau checkpoint #2 hijau.

**Aturan:** setiap baris yang naik harus menurunkan sesuatu dengan biaya setara. Batas 39 jam tidak berubah. Kalau ≥3 baris aktif sekaligus, kurangi provinsi menjadi 2 (Riau + Kalteng).

## 8. Keluaran yang bisa dipakai untuk keputusan (bukan hanya heatmap)
Pengguna BPBD tidak membaca persentil. Untuk setiap wilayah, kalender menghasilkan **tiga kalimat yang bisa dicek**, masing-masing dengan pita ketidakpastian dan definisi tertulis di halaman Metode:
1. **"Season usually starts in [bulan]"**: onset = bulan pertama ketika porsi aktivitas tahunan median melewati 2 × (1/12), dihitung dari seri harmonisasi. Uji sensitivitas ambang 1,5× dan 2,5× dilaporkan.
2. **"Peak is usually [bulan] (range [a–b])"**: bulan dengan median tertinggi, rentang = P25–P75 bulan puncak antar-tahun.
3. **"In El Niño years, activity in [bulan] was [x]× the median"**: dari label tahun El Niño (MVP, deskriptif saja; tidak ada prakiraan).

Kalimat ini yang ditaruh di slide 6 dan detik 20–26 video. Kalau definisi onset tidak stabil (sensitivitas mengubah bulan), tulis "onset uncertain" di sel itu. Jangan dipaksakan.

## 9. Aha satu kalimat (judul dan hook)
*"Indonesia's fire record looks like fires jumped five-fold in 2012. They didn't: a sharper satellite arrived. KalenderApi removes the satellite from the story, so a district can see when its own fire season starts."*
(Angka "five-fold" hanya dipakai kalau rasio dari data kita sendiri memang ±5; kalau tidak, ganti dengan angka yang diukur.)

## 10. Validasi independen tanpa risiko lisensi
T&C 2026 mewajibkan data non-NASA "freely and publicly available" atau berlisensi open source, dengan lisensi didokumentasikan, dan **semua** sumber disitasi. Lisensi data SiPongi tidak tercantum di sumber yang kita punya. Karena itu:
- **Cek utama tetap SiPongi** (luas terbakar resmi, dikutip sebagai angka publikasi pemerintah dengan URL dan tanggal akses), dengan catatan status lisensinya di `docs/data_licenses.md`.
- **Cek cadangan dari NASA:** **MCD64A1 C6.1** (burned area bulanan) lewat Google Earth Engine, dijumlahkan per provinsi per bulan. Ini data NASA, jadi bebas masalah lisensi, dan juri ilmuwan FIRMS mengenalnya. Naik ke MVP kalau SiPongi per provinsi tidak bisa diambil pada Jam 0, atau kalau statement menyebut burned area.
