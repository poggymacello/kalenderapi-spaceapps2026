# 11 — Checklist Pra-Hari-H (23 Okt – 13 Nov 2026)
### NASA Space Apps 2026 · Local Event Bandung · KalenderApi · hackathon Sab 14 Nov 09.00 – Min 15 Nov 23.59
Disusun Jumat 23 Okt 2026. Semua isi file ini boleh dilakukan sebelum 14 Nov (belajar, akun, riset pengguna, latihan di proyek lain). **Tidak boleh sebelum 14 Nov 09.00:** menulis kode/notebook KalenderApi, mengunduh dan memproses data Indonesia, desain UI, slide final.

> **Cek aturan resmi 23 Okt malam (dibaca langsung, bukan dari indeks):**
> - **FAQ 2026:** challenge statement terbit **28 Okt**; *"Teams are not allowed to begin working on the challenges prior to the hackathon."* Tim lokal minimal 1 orang, maksimal 6, satu tim satu tantangan. Panduan Project Submission dan Judging & Awards terbit **13 Nov**; panduan Space Apps Connect **3 Nov**.
> - **FAQ 2026 mengganti istilah "AI" menjadi "Super Intelligence (SI)"** dan menyatakan setiap submission **wajib** menjelaskan cara alat SI dipakai. Semua file sudah diperbarui (`08`, `09`, `10`).
> - **T&C 2026 (diperbarui 7 Agu 2026):** acara mulai 14 Nov; data/kode non-NASA wajib tersedia bebas atau berlisensi OSI dan **lisensinya didokumentasikan**; **semua sumber wajib disitasi** (nominasi bisa dicabut kalau tidak); konten asli otomatis Apache 2.0 kalau tidak memilih lisensi; tidak boleh ada data pribadi (PII); video wajib karya sendiri tanpa pelanggaran hak cipta, dan setiap orang yang tampil harus memberi izin tertulis.
> - **Mengunduh data lebih awal:** FAQ dan T&C tidak membahasnya secara eksplisit. Keputusan: **tidak diunduh sebelum 14 Nov 09.00** kecuali Local Lead mengizinkan secara tertulis (pertanyaan 6 di §2). Runbook dan manifest berkas sudah siap (`07` §7; `JURI_90/firms_manifest_23okt2026.tsv`). Memasang alat dan membuat akun tetap boleh.
> - ~~Halaman tantangan `…/2026/challenges/harmonization-of-modis-and-viirs-hot-spots/` aktif (HTTP 200), isinya masih judul saja.~~
> - **Update Rab 28 Okt malam:** statement lengkap terbit; tantangan kita **ada** di daftar 14 tantangan 2026. Slug yang benar: `/2026/challenges/modis-and-viirs-hot-spots/`. FAQ dicek ulang: aturan larangan mulai lebih awal tidak berubah. Keputusan matriks dan perubahan MVP: `12`. Paket rekrut: `13`. Skrip wawancara: `14`. Checklist hari-H: `15`.

> **Bentrok jadwal yang perlu diingat:** 28 Okt (AI Builder kirim formulir), 31 Okt (IEEEXtreme), 6–8 Nov (Codex Hackathon Jakarta), 13 Nov (laporan dana Wasit). Tugas di bawah sudah menghindari tanggal itu.

---

## 1. Checklist bertanggal
| Tanggal | Tugas | Siapa | Selesai kalau… | ✓ |
|---|---|---|---|---|
| ⚠️ **Lewat (28 Okt: belum terkirim)** → diganti **Kam 29 Okt pagi**, pakai `13` §3 | Tim belum ada per 23 Okt, padahal skor plan mengandaikan 4–5 orang. Kirim pesan rekrut §4.1 **hari ini** ke ≥3 grup. Kalau sampai Min 25 Okt belum ada orang statistik, pakai rencana 2 orang di `08` | Poggy | Pesan terkirim di ≥3 grup | ☐ |
| **Jum 23 – Min 25 Okt** | **Rekrut tim 4–5 orang** (§4.1). Wajib ada: **A = statistik/Python** (GLM, validasi silang) dan **D = GIS/geodesi/kehutanan** (SiPongi, batas wilayah, cerita). Tambahan: C = web dev, E = desain/video (opsional) | Poggy | 3–4 nama bersedia, peran tertulis | ☐ |
| ~~Sel 27 Okt~~ → **Sel 3 Nov** | **Kunci tim** dengan kesepakatan `13` §5. Satu orang = satu tim. Semua bisa hadir penuh 14–15 Nov. Kalau belum ada orang statistik: rencana 2 orang | Poggy | 3–4 balasan "setuju" di grup | ☐ |
| ~~Sel 27 – Rab 28 Okt~~ → **paling lambat Kam 5 Nov** | **Semua anggota mendaftar** di spaceappschallenge.org dan **join Local Event Bandung yang sama**. Ketua membuat tim dan mengundang anggota | Semua | Screenshot halaman tim yang menampilkan semua anggota + Bandung | ☐ |
| Sab 24 – Rab 28 Okt | **Akun alat:** Earthdata Login (semua), **FIRMS MAP_KEY** (minimal B dan A; gratis via email), **Google Earth Engine** non-komersial (A, untuk stretch Tier 3), akun Cloudflare Pages + GitHub (B, C) | Semua | Daftar akun di grup (tanpa menulis password/MAP_KEY di grup) | ☐ |
| **Sen 26 Okt** | **Email Local Lead** (§2). Kirim sendiri | Poggy | Email terkirim | ☐ |
| **Rab 28 Okt** | **Baca pernyataan tantangan lengkap** (§5). Bandingkan dengan asumsi di 01, 04, 05. **Isi kolom "keputusan" di matriks adaptasi `04` §7** (S1–S8), lalu ubah file yang terdampak. Catatan: 28 Okt juga hari kirim formulir AI Builder; sisihkan 60 menit malam hari | Semua (baca); Poggy + A (putuskan) | Matriks `04` §7 terisi + catatan "statement vs asumsi" di file ini | ✅ Agen 28 Okt (`12`). Poggy tinggal membaca `12` (10 menit) dan menyetujui |
| **Kam 29 Okt** (tindak lanjut Min 1 Nov) | **Kirim pesan permintaan wawancara** `14` §2 ke 2–3 kontak resmi BPBD Riau/Kalteng atau Daops Manggala Agni | Poggy (D kalau sudah ada) | Minimal 1 jadwal wawancara | ☐ |
| Kam 29 Okt – Kam 5 Nov | **Latihan stack di proyek mainan lain** (§6). Kode latihan **tidak dibawa** ke repo hari-H | A, B, C | Tiap orang pernah menjalankan bagiannya dari awal sampai deploy | ☐ |
| Sab 31 Okt | (IEEEXtreme) libur | — | — | — |
| Sel 3 – Kam 5 Nov **atau** Sen 9 – Rab 11 Nov | **Wawancara 1 praktisi** (30 menit, skrip `14` §3). Ringkasan 1 halaman (`14` §5) | Poggy / D | Ringkasan + izin dikutip | ☐ |
| ~~Sen 2 Nov~~ → **Sel 10 Nov** | Rapat online 45 menit: peran, MVP baru (`12` §4), checklist `15`, siapa jaga malam | Semua | — | ☐ |
| Sen 2 Nov | Telepon saring kandidat 10 menit per orang (`13` §4) | Poggy | Pilihan per peran | ☐ |
| Sel 3 Nov | Space Apps Connect buka: pasang pesan `13` §3.3 kalau peran A/D masih kosong | Poggy | Pesan terpasang | ☐ |
| Jum 6 – Min 8 Nov | (Codex Hackathon, Poggy di Jakarta) libur KalenderApi | — | — | — |
| 🆕 Sel 3 Nov | Cek apakah data S-NPP benar-benar berhenti 2 Nov (Earthdata alert + `data_availability` FIRMS dengan MAP_KEY). Hasilnya menentukan hook pitch (`09` §6) | Poggy | Baris #1 §3 diperbarui | ☐ |
| 🆕 Sel 3 Nov | Baca panduan Space Apps Connect; buka SiPongi, aqua.nasa.gov, dan volcano.si.edu dari browser (tidak terjangkau dari koneksi agen 23 Okt) | Poggy | Baris #9–#10 §3 diperbarui | ☐ |
| **Sen 9 – Rab 11 Nov** | **Cek ulang fakta** (§3), terutama yang bertanda "cek lagi" | Poggy + D | Kolom "hasil" diperbarui | ☐ |
| Sel 10 Nov | Baca balasan Local Lead; sesuaikan jam freeze dan submit di `08` kalau pitch lokal punya jadwal khusus | Poggy | `08` diperbarui | ☐ |
| Kam 12 Nov | Laptop semua anggota siap: Python 3.12 + DuckDB + pandas + geopandas + statsmodels; Node + Vite; Git. Isi daya, cek charger | Semua | Screenshot versi | ☐ |
| **Jum 13 Nov** | **Baca panduan Judging & Submission 2026** (batas demo ≤30 detik / ≤7 slide, aturan SI) **dan tab Resources tantangan** (terbit 13 Nov; putuskan S8). Ubah `01`, `09`, `12` kalau berbeda. Ikuti `15` §A | Poggy + D | — | ☐ |
| **Sab 14 Nov 09.00** | Mulai. Ikuti `08` | Semua | — | — |

---

## 2. Draf email ke Local Lead (DRAF, dikirim sendiri)
**Kepada:** spaceappsbandung@gmail.com
**Subjek:** Pertanyaan format pitch & persiapan: NASA Space Apps 2026 Bandung

> Halo Tim Local Lead NASA Space Apps Bandung,
>
> Perkenalkan, saya Poggy dari Teknik Elektro ITB. Tim kami akan ikut Space Apps 2026 di Local Event Bandung dan rencananya mengambil tantangan "Harmonization of MODIS and VIIRS Hot Spots". Ada beberapa hal yang ingin kami pastikan:
>
> 1. **Format penjurian lokal:** apakah ada pitch langsung di depan juri? Kalau ada, berapa durasinya, hari dan jam berapa (Sabtu 14 atau Minggu 15 November), dan apakah presentasi langsung, rekaman, atau cukup halaman Project + demo 30 detik?
> 2. **Bahasa:** pitch lokal boleh berbahasa Indonesia, atau wajib bahasa Inggris seperti halaman Project?
> 3. **Persiapan yang boleh dilakukan sebelum 14 November:** apakah boleh membuat akun dan API key (Earthdata, FIRMS), membaca literatur, menyiapkan daftar pertanyaan, dan mewawancarai praktisi (misalnya BPBD)? Kami memahami bahwa kode, data olahan, dan desain baru dibuat saat hackathon.
> 4. **Lokasi dan jam:** apakah acara diadakan di satu tempat secara langsung, dan apakah peserta boleh menginap/bekerja di lokasi semalaman? Jam berapa lokasi buka dan tutup?
> 5. **Tenggat submit lokal:** apakah ada tenggat lebih awal dari 15 November 23.59 untuk penjurian lokal?
> 6. **Data publik:** FAQ menyebut tim tidak boleh mulai mengerjakan tantangan sebelum hackathon. Apakah **mengunduh berkas data publik NASA FIRMS apa adanya** (tanpa diolah) sebelum 14 November termasuk yang dilarang? Kalau ragu, kami akan mengunduhnya saat acara dimulai.
> 7. **Internet dan listrik:** apakah lokasi menyediakan Wi-Fi yang cukup untuk mengunduh ±500 MB data di awal acara?
>
> Terima kasih banyak atas bantuannya.
>
> Salam,
> Poggy Macello Gultom
> Teknik Elektro ITB

---

## 3. Fakta yang harus dicek ulang
Dicek 23 Okt 2026 lewat pencarian web dan cek header HTTP (tanpa mengunduh data). "Cek lagi" = belum pasti, ulangi sebelum hari-H.

| # | Fakta di file kita | Hasil cek 23 Okt | Status | Sumber |
|---|---|---|---|---|
| 1 | **S-NPP berhenti 13.00 UTC 2 Nov 2026** (02 §4, 05, 09) | Alert Earthdata (diperbarui 14 Okt 2026): data S-NPP berhenti **13.00 UTC 2 Nov 2026 (2026/306)**, "subject to change". Pengganti yang disarankan: NOAA-21 (utama), NOAA-20 (kedua). Catatan: pemberitahuan NOAA NESDIS 3 Agu 2026 menyebut **1 Nov 2026**; selisih satu hari tidak dijelaskan | ✅ untuk 2 Nov, **cek lagi 3 Nov** apakah data benar-benar berhenti | [Earthdata alert](https://www.earthdata.nasa.gov/data/alerts-outages/suomi-npp-observations-cease-november-2-2026) · [NOAA NESDIS](https://www.nesdis.noaa.gov/news/cessation-of-suomi-national-polar-orbiting-partnership-s-npp-data-users-onafter-november-01-2026) |
| 2 | **Aqua/Terra MODIS "mulai dimatikan akhir 2026–awal 2027"** (02 §4, 07 §3) | Tidak ditemukan pengumuman resmi 2026. Laporan status Aqua (2023–2024) memproyeksikan **instrumen dimatikan 26 Agu 2026** dan passivation **4 Nov 2026**; halaman misi Aqua menyebut passivation "Fall 2026". DEA Hotspots (Australia): Terra MODIS tidak lagi tersedia lewat direct broadcast, Aqua sedang dikurangi | ⚠️ **Cek lagi** di aqua.nasa.gov dan LADS. Dampak ke MVP kecil: fit berakhir Des 2022 dan rekaman sejak 2012 sudah VIIRS teramati. Kalau Aqua mati Agu 2026, kalimat di 02 §4 perlu diubah menjadi "sudah dimatikan" | [Aqua mission](https://aqua.nasa.gov/) · [Aqua status Jul 2024](https://aqua.gsfc.nasa.gov/sites/default/files/AquaStatus_July2024.pdf) · [LADS: Terra's future](https://ladsweb.modaps.eosdis.nasa.gov/alerts-and-issues/171790) |
| 3 | **SiPongi Jan–Jul 2026: 202.004 ha (+69% yoy)** (02 §2) | Dikonfirmasi: Kompas (3 Okt 2026) mengutip SiPongi **202.004,30 ha Jan–Jul 2026, +69%** vs periode sama 2025. Sumber lain memberi 202.010,96 ha untuk Jan–Agu. Angka terbaru BNPB: **129.899,59 ha di 6 provinsi prioritas s.d. 12 Okt 2026** (bukan angka nasional SiPongi) | ✅ angka Jan–Jul; **cek lagi** apakah SiPongi sudah merilis angka s.d. Sep/Okt | [Kompas 3 Okt 2026](https://lestari.kompas.com/read/2026/10/03/093745086/luas-karhutla-2026-melonjak-perbaikan-tata-kelola-lahan-dan-gambut-jadi) · [Bisnis 13 Okt 2026](https://kabar24.bisnis.com/read/20261013/15/2012121/bnpb-karhutla-di-kalimantan-hingga-51389-hektare) |
| 4 | **Arsip FIRMS 2025 "masih 404"** (07 §1) | **Sudah tersedia.** Cek header HTTP 23 Okt: `modis_2025_Indonesia.csv` (200, ±1,4 MB), `viirs-snpp_2025_Indonesia.csv` (200, ±7,6 MB), `viirs-jpss1_2025_Indonesia.csv` (200, ±7,6 MB). `viirs-jpss2` 2025 masih 404. Token negara `Indonesia` benar. Halaman Archive Download menulis NOAA-21 tersedia sejak 17 Jan 2024 (lewat tool arsip, bukan berkas negara) | ✅ (07 sudah diperbarui) | Cek langsung URL berkas negara FIRMS · [FIRMS Archive Download](https://firms.modaps.eosdis.nasa.gov/download/) |
| 5 | Selisih 20.928 vs 666 titik (3 Okt 2026) | Belum dicek | Cek lagi (screenshot SiPongi + rilis Kemenhut) | — |
| 6 | NOAA CPC El Niño Advisory, Niño-3.4 +2,1 °C (8 Okt 2026) | Belum dicek | Cek lagi di update CPC berikutnya (biasanya Kamis kedua tiap bulan, ±12 Nov) | — |
| 7 | Batas demo ≤30 detik / ≤7 slide; aturan AI | Dari panduan 2025 | Cek di panduan 2026 pada 13 Nov | — |
| 8 | "Halaman SiPongi menulis +80% vs 2023" (02 §2) | Tidak ditemukan dalam pencarian | Cek lagi, atau hapus dari pitch | — |
| 9 | Berkas negara FIRMS Indonesia untuk semua tahun | **Dicek 23 Okt malam (header saja):** 48 berkas 200 (MODIS 2000–2025, S-NPP 2012–2025, NOAA-20 2018–2025), total ±503 MB; NOAA-21 2025 dan semua 2026 = 404 | ✅ | `JURI_90/firms_manifest_23okt2026.tsv` |
| 10 | Sumber pendukung | geoBoundaries API ADM1/ADM2 200 · NOAA CPC RONI & ONI 200 (RONI JAS 2026 = 1,69) · GFW data portal 200 · FIRMS `data_availability`/`missing_data` 200 · Earthdata alert S-NPP 200 · **SiPongi & aqua.nasa.gov timeout, GVP 403** dari koneksi agen | ⚠️ manusia membuka SiPongi/aqua/GVP dari browser | Cek 23 Okt |
| 11 | DOI produk | VNP14IMGT_NRT.002, VJ114IMGT_NRT.002, VNP14A1.002, MCD64A1.061, VNP14IMG.002, VJ114IMG.002, MCD14DL.NRT.0061 → 200. **MCD14ML → halaman 404** | ⚠️ kutip juga MCD14DL + Giglio 2016 | `07` §4 |
| 12 | Istilah dan aturan SI 2026 | FAQ: "Super Intelligence (SI)", deskripsi penggunaan wajib | ✅ | FAQ peserta 2026 |

---

## 4. Rekrut, outreach, dan wawancara
> **28 Okt:** pesan rekrut versi baru (dengan judul tantangan resmi, garis waktu baru, saringan, dan kesepakatan tim) ada di `13`. Skrip wawancara versi baru di `14`. Teks di §4.1–4.3 di bawah disimpan sebagai arsip.

### 4.1 Pesan rekrut (WhatsApp/LINE grup angkatan, himpunan, unit)
> **Cari 2–4 teman tim NASA Space Apps 2026 (Bandung), 14–15 Nov** 🛰️
> Hackathon resmi NASA, 2 hari (Sab 14 Nov 09.00 – Min 15 Nov malam), Local Event Bandung. Juara lokal bisa jadi Global Nominee.
>
> Tantangan: **"Harmonization of MODIS and VIIRS Hot Spots"**. Rencana kami: menyambung 25 tahun data titik api satelit NASA jadi satu kalender musim api yang konsisten untuk provinsi gambut (Riau, Kalteng, Sumsel), supaya BPBD bisa menetapkan siaga sebelum musim api lokal mulai.
>
> Butuh:
> 1. **Statistik/data (paling penting):** nyaman dengan Python/pandas dan regresi (GLM, validasi silang). Statistika, Matematika, Informatika, Geodesi.
> 2. **GIS/lingkungan:** paham peta, batas wilayah, atau isu karhutla/gambut. Geodesi, Kehutanan, Teknik Lingkungan, Planologi.
> 3. *(opsional)* **Web dev** (JavaScript/TypeScript, grafik) atau **desain/video**.
>
> Syarat: bisa ikut penuh 14–15 Nov, mau baca sedikit materi sebelumnya (sudah disiapkan). Tidak perlu pengalaman satelit.
> DM aku sebelum **Senin 26 Okt**: nama, jurusan + angkatan, satu hal yang pernah kamu kerjakan dengan data/peta/web.

### 4.2 Pesan permintaan wawancara (BPBD / Daops Manggala Agni)
> Selamat pagi/siang Bapak/Ibu [nama/jabatan],
>
> Saya Poggy, mahasiswa Teknik Elektro ITB. Bersama tim, kami sedang menyiapkan proyek untuk NASA Space Apps Challenge 2026 tentang **kalender musim kebakaran hutan dan lahan** berbasis data satelit NASA, untuk provinsi seperti Riau, Kalimantan Tengah, dan Sumatera Selatan.
>
> Kami ingin belajar langsung dari praktisi: bagaimana BPBD/Manggala Agni memutuskan kapan mulai siaga, dan data titik panas apa yang biasa dipakai. Apakah Bapak/Ibu berkenan berbincang **±30 menit** lewat telepon atau video call antara **2–5 November**, di waktu yang paling longgar bagi Bapak/Ibu?
>
> Kami tidak akan mengutip nama atau jabatan tanpa izin, dan tidak merekam tanpa persetujuan. Ini kegiatan mahasiswa nonkomersial.
>
> Terima kasih banyak atas waktunya.
> Salam hormat,
> Poggy Macello Gultom, Teknik Elektro ITB

Catatan: cari kontak resmi (situs/media sosial BPBD provinsi, Daops Manggala Agni, atau dosen/kenalan yang punya jalur). Jangan mengirim ke nomor pribadi yang didapat dari sumber tidak jelas.

### 4.3 Panduan wawancara (30 menit)
**Pembuka (2 menit):** perkenalan, tujuan, minta izin mencatat, tanyakan boleh dikutip atau tidak (dengan nama / jabatan saja / anonim).

**Keputusan siaga (10 menit)**
1. Bagaimana proses penetapan status *siaga darurat* karhutla di daerah Bapak/Ibu? Siapa yang mengusulkan, siapa yang memutuskan?
2. Parameter apa yang paling menentukan? (titik panas, hari tanpa hujan, FDRS, El Niño, kejadian di lapangan)
3. Kapan biasanya status ditetapkan tahun ini dan tahun-tahun sebelumnya? Pernah merasa terlambat atau terlalu dini?
4. Kalau ada kalender "biasanya musim api di kabupaten X mulai minggu ke-…", apakah itu akan dipakai? Untuk keputusan apa?

**Data yang dipakai (10 menit)**
5. Data titik panas dari mana yang dipakai sehari-hari? (SiPongi, BMKG, BRIN, FIRMS, aplikasi lain)
6. Pernah bingung karena angka titik panas berbeda antarsumber? Contoh kejadiannya?
7. Tingkat kepercayaan apa yang dipakai (semua, nominal, tinggi)?
8. Seberapa sering data perlu diperbarui supaya berguna: harian, mingguan, bulanan?

**Format dan batasan (6 menit)**
9. Bentuk apa yang paling berguna: peta, tabel, grafik, PDF satu halaman, pesan WhatsApp?
10. Apa yang membuat Bapak/Ibu **tidak percaya** pada sebuah angka atau peta?
11. Apa yang paling sering terlewat dari alat yang ada sekarang?

**Penutup (2 menit):** boleh dihubungi lagi untuk umpan balik setelah 15 Nov? Ucapkan terima kasih.

**Setelah wawancara:** tulis ringkasan 1 halaman dalam 24 jam: 3 kutipan (kalau diizinkan), keputusan nyata yang dibantu kalender, format yang diminta, hal yang membuat tidak percaya. Masukkan ke `04` §2 dan jawaban Q19 di `10`.

---

## 5. Hari statement terbit (Rab 28 Okt): yang harus dibandingkan
*Diisi agen 28 Okt malam (rincian `12`):*
- [x] Judul dan nomor tantangan sama? **Judul sama.** Nomor tidak ditampilkan di halaman resmi
- [x] Siapa penulisnya? **Tidak disebut;** kredit foto CONAE (Argentina) → kemungkinan CONAE [inf]. `04` §5 diberi catatan
- [x] Apakah statement **menentukan satuan acuan**? **Tidak.** Statement hanya meminta sensor asal "tidak lagi penting". Keputusan setara-VIIRS di `05` tetap
- [x] Definisi "burning activity calendar" dan resolusi waktu: **jumlah hotspot per bulan, awal 2000-an sampai sekarang**, plus perbandingan bulan berjalan vs median historis
- [x] Apakah area of interest wajib bebas? **Disarankan, tidak wajib** (gambar di peta atau lintang/bujur). MVP: input lintang/bujur + radius; poligon naik ke stretch tier 1; provinsi preset turun ke 2
- [x] Dataset yang disebut wajib atau disarankan: **FIRMS (MODIS + VIIRS) disarankan**; tab Resources baru 13 Nov
- [x] Contoh keluaran atau pengguna: web app, kalender, pilih wilayah + rentang tanggal, unduh analitik/visualisasi, CSV hotspot, color ramp aksesibel; pengguna = early warning & emergency responders, ilmuwan, land managers, firefighters
- [x] Istilah resmi yang dipakai: disalin ke `09` §5 dan `12` §5

---

## 6. Latihan stack di proyek mainan (bukan KalenderApi)
Tujuannya melatih tangan dengan alat yang sama, memakai **data dan topik lain**. Kode latihan disimpan di folder terpisah dan **tidak** dibawa ke repo hari-H.

| Peran | Latihan (contoh) | Alat |
|---|---|---|
| B | Katalog gempa USGS (CSV publik) → Parquet → agregasi grid 1° × bulan dengan DuckDB → JSON kecil | DuckDB, pandas |
| A | Di data latihan yang sama: GLM binomial negatif + validasi leave-one-year-out + bootstrap blok | statsmodels |
| C | Heatmap tahun × bulan + grafik seri dengan pita di ECharts; deploy halaman statis ke Cloudflare Pages | Vite, TypeScript, ECharts |
| D | Ambil satu tabel resmi (bukan SiPongi karhutla) dan rapikan ke CSV dengan catatan sumber; latihan menulis paragraf "limitations" | Spreadsheet/pandas |

---

## 7. Yang hanya bisa dilakukan manusia
- [ ] Memutuskan bentrok EAGxBerlin vs 14–15 Nov **sebelum** mengirim pesan rekrut (`13` §0)
- [ ] Merekrut dan mengunci anggota tim (`13`)
- [ ] Mendaftar di spaceappschallenge.org dan join Local Event Bandung (tiap anggota sendiri)
- [ ] Membuat akun Earthdata, FIRMS MAP_KEY, GEE (simpan kunci sendiri, jangan ditempel di grup)
- [ ] Mengirim email ke Local Lead dan pesan ke praktisi
- [ ] Melakukan wawancara
- [x] ~~Mengisi matriks adaptasi `04` §7~~ (diisi agen 28 Okt; Poggy cukup menyetujui `12` §3)
- [ ] Membuka SiPongi, aqua.nasa.gov, dan GVP dari browser (tidak terjangkau dari agen)
