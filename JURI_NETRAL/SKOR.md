# SKOR juri netral (buta): KalenderApi, NASA Space Apps 2026 Bandung
Dinilai Jum 6 Nov 2026.

> **Batas bacaan.** Juri ini **hanya** membaca: `PAKET_PENILAI_SpaceApps.md` (scratchpad), lalu `12-STATEMENT-RESMI-28okt.md`, `04-konsep-solusi.md`, `05-metodologi-harmonisasi.md`, `06-arsitektur-teknis.md`, `08-rencana-39-jam.md`, `09-pitch-dan-halaman-proyek.md`, `03-pesaing-dan-celah.md`, `02-konteks-indonesia-karhutla.md`, `14-WAWANCARA-BPBD-MANGGALA-AGNI.md`. Tidak ada file lain yang dibuka: tidak ada `JURI_90`, `_arsip_29okt`, `MEGA_PROMPT.md`, atau `10-QnA-juri.md`. Web hanya dipakai untuk cek fakta teknis (§7). Tidak ada file proyek lain yang diubah.

Yang dinilai adalah **RENCANA**. Batas dari paket berlaku: Validity (bagian implementasi) dan Presentation (demo) maks **14,4**; Influence maks **16** (belum ada suara pengguna nyata); klaim "akan diukur" bernilai nol.

---

## 1. Skor per persona (/20 per kriteria)

### N1 · Ilmuwan api / remote sensing (NASA, CONAE, INPE)
| Kriteria | Skor | Bukti |
|---|---|---|
| Influence | 13 | Pengguna dan keputusan konkret: "Kapan menetapkan *siaga darurat* (membuka bantuan BNPB)" (`04` §2). Batas 16 berlaku karena `14` baru berupa skrip. N1 menilai dampak ilmiah lebih penting dari dampak lokal, jadi angka ini wajar |
| Creativity | 13 | Pembeda yang ada di MVP hanya "jendela fit bebas drift + pita ketidakpastian di kalender + pengguna BPBD yang konkret" (`04` §6). Pembeda kuat lainnya (normalisasi observasi, gambut, rantai NOAA-21) berlabel *stretch*. Inti cell-day 0,1°, shrinkage, dan LOYO sudah diklaim FireCal (`03` §2) |
| Validity | 13 | Metode rapi dan jujur: "Kalibrasi hanya like-for-like dan bebas drift: Aqua (13.30) vs S-NPP (13.30)" (`04` §4); "Sel yang tidak terlihat MODIS tetap 0 … batas bawah deteksi" (`05` §7). **Cacat yang akan ditemukan N1:** cek SiPongi 2015–2024 (`08` MVP butir 4) seluruhnya jatuh di era VIIRS teramati, padahal `06` langkah 6 menulis "Feb 2012 – kini = VIIRS S-NPP teramati". Artinya "harmonisasi" dan "mentah VIIRS" adalah seri yang sama di jendela uji itu, sehingga uji ini tidak bisa membuktikan harmonisasi. Batas 14,4 |
| Relevance | 17 | Langsung menjawab statement: "sensor of origin no longer matters" dipakai di pitch, kalender dari "awal 2000-an", anomali vs median (`12` §2). Data inti NASA FIRMS |
| Presentation | 11 | Kosakata NASA disiplin (`09` §5). Demo belum ada (batas 14,4). Untuk ilmuwan, toggle patahan 2012 adalah visual yang tepat |
| **Total** | **67** | |

### N2 · Juri lokal Bandung (dosen/praktisi data)
| Kriteria | Skor | Bukti |
|---|---|---|
| Influence | 14 | Masalah lokal yang berat dan bersumber: "2015 merugikan US$16,1 miliar (1,9% PDB)" (`02` §1); "bantuan helikopter dan dana baru turun setelah daerah menetapkan siaga" (`02` §7). Batas 16 |
| Creativity | 12 | Kalimat keputusan "Season usually starts in [bulan]" (`04` §8) lebih dari sekadar heatmap. Tetapi untuk juri lokal, kalender tetap terlihat seperti heatmap dan grafik garis |
| Validity | 11 | Kelayakan 39 jam meragukan. MVP setelah 28 Okt menumpuk GLM NB per strata, LOYO 11 fold, bootstrap B≈200, input lintang/bujur + radius, filter tanggal, kartu anomali, CSV, PNG, SPA Vite + MapLibre + ECharts, dan video (`08` §Scope, `12` §4), padahal "Tim belum terbukti terkunci" (paket). `08` menulis "Keputusan ini diambil Sel 27 Okt saat tim dikunci", dan tidak ada bukti keputusan itu sudah diambil |
| Relevance | 16 | Indonesia, gambut, El Niño 2026–2027: "El Niño berlanjut ke Jan–Mar 2027, tepat di jendela Feb–Mar Riau" (`02` §7) |
| Presentation | 12 | Storyboard per shot dengan batas kata dan cek `ffprobe` ≤30,0 detik (`09` §2); uji 5 detik per slide (`09` §3). Rencana presentasi terbaik dari kelima kriteria, tetapi tetap dibatasi 14,4 |
| **Total** | **65** | |

### N3 · Tim juara Space Apps sebelumnya
| Kriteria | Skor | Bukti |
|---|---|---|
| Influence | 13 | Sejalan dengan pola "Data Bumi untuk masalah lokal nyata" (paket, pola juara; G.R.O.W. 2024). Tanpa kutipan pengguna, tetap di bawah batas |
| Creativity | 12 | Momen demo = "toggle mentah MODIS vs VIIRS (patahan 2012) ↔ seri harmonisasi + pita" (`04` §3 butir 3). Momen ini jelas tetapi tidak spektakuler dibanding simulasi asteroid AIM-X 2025. Icarus juga mengklaim "Toggle mentah vs harmonisasi" (`03` §2) |
| Validity | 13 | "Kalau M2 tidak mengalahkan M1 … laporkan apa adanya" (`08` checkpoint #2), sebuah kejujuran yang jarang ditemukan di tim juara. Batas 14,4 |
| Relevance | 16 | Kosakata resmi dipetakan satu per satu (`12` §5) |
| Presentation | 11 | Hook pribadi "four and a half million pairs of MODIS and VIIRS pixels over Indonesian seas" (`09` §6) kuat dan autentik, tetapi butuh 20 detik untuk menjelaskan bahwa itu data laut, bukan api. Batas 14,4 |
| **Total** | **65** | |

### N4 · Tim pesaing terkuat di Bandung
| Kriteria | Skor | Bukti |
|---|---|---|
| Influence | 12 | Celah yang bisa diserang: "Hipotesis pengguna di atas diambil dari dokumen resmi dan liputan" (`04` §2), jadi belum ada pengguna sungguhan |
| Creativity | 11 | Pesaing bisa menunjuk FireCal: "cell-day 0,1° harian; rasio MODIS→VIIRS … disusutkan ke prior global … validasi leave-one-year-out; flag 2σ" (`03` §2). Ini hampir sama dengan inti MVP KalenderApi |
| Validity | 12 | Serangan: n=10 titik nasional (`05` §8 butir 7, "indikatif") dan cek SiPongi yang tidak menguji era MODIS (lihat N1) |
| Relevance | 16 | Sulit diserang, karena tantangan dan datanya tepat |
| Presentation | 10 | Pesaing dengan peta interaktif yang mulus akan terlihat lebih "jadi" daripada grafik garis + heatmap |
| **Total** | **61** | |

### N5 · Skeptis dengan veto
| Kriteria | Skor | Bukti |
|---|---|---|
| Influence | 11 | Belum ada wawancara (paket, status). Angka "+80% vs 2023 … padahal angkanya sendiri menghasilkan +117%" (`02` §2) menunjukkan bahwa data sekunder pun belum stabil |
| Creativity | 12 | Kalimat pembeda di `03` §4 menjual 5 hal yang sebagian besar *stretch* (lihat §2) |
| Validity | 11 | Ada klaim "akan diukur" yang bernilai nol: "[x]% lower error on unseen years" (`09` §2 S4), "[r]× more hotspots" (S2). Kontinjensinya ada ("Jangan mengarang keunggulan", `09` §2), dan itu yang mencegah skor lebih rendah |
| Relevance | 15 | Tepat sasaran, tetapi "any place" (tagline, `04` §1) tidak didukung MVP yang terdiri dari 2 provinsi + lintang/bujur |
| Presentation | 10 | Judul slide 5 "It beats a naive conversion factor on years it never saw" (`09` §3) ditulis sebelum hasilnya ada |
| **Total** | **59** | |

### Konsensus
| Persona | N1 | N2 | N3 | N4 | N5 |
|---|---|---|---|---|---|
| Total | 67 | 65 | 65 | 61 | 59 |

**Median = 65/100**, rentang ketidakpastian **60–69**. Menurut jangkar paket, rencana ini ada di antara "ide bagus, eksekusi belum terbukti" (60) dan "kandidat Local Winner kredibel" (70). Belum mencapai 70 karena tim belum terkunci dan belum ada suara pengguna.

---

## 2. Veto N5: **AKTIF** (status hari ini, bisa dicabut)
Total sudah di bawah 70, jadi veto belum memotong skor sekarang. Tetapi veto ini **mengunci batas 70 pada plafon (b)** sampai diperbaiki. Dua dasarnya:

1. **Klaim melebihi bukti.** `03` §4 menyuruh tim mengucapkan keras-keras: *"Observation-normalized, drift-aware, uncertainty-propagated harmonization that survives the S-NPP and MODIS shutdowns, validated against independent burned area, with an Indonesian peat case study and an INPE-compatible reference series."* Dari tujuh klaim itu, hanya *drift-aware* dan *uncertainty-propagated* yang ada di MVP. Normalisasi observasi = stretch tier 3 (`08`), gambut = tier 1, rantai NOAA-20 untuk "survives S-NPP" = tier 2, seri INPE = stretch (`04` §5), dan "validated against independent burned area" cacat (§1 N1). Tagline "every satellite, any place" (`04` §1) punya masalah yang sama.
2. **Ketidakkonsistenan dengan aturan pre-build buatan tim sendiri.** `12` §6 menaruh "Menulis teks halaman Project final" di kolom **Tidak boleh**. Tetapi `09` §4 butir 2 dan 8b sudah berisi "Teks siap tempel (EN, 29 Okt, 118 kata)" untuk bagian Problem dan Team. Ini area abu-abu (tidak ada kode, tidak ada data olahan), tetapi juri skeptis akan menandainya.

**Cara mencabut veto:** (a) kalimat pembeda dan tagline ditulis ulang agar hanya berisi isi MVP, dan sisanya diberi label "if completed"; (b) teks di `09` §4 diberi label "draf riset, ditulis ulang dari nol pada 14 Nov", lalu benar-benar ditulis ulang di hari-H dan diungkapkan di halaman Project.

---

## 3. Head-to-head (KalenderApi sesuai rencana sekarang vs 5 pesaing yang dieksekusi dengan baik)
Pesaing:
- **P1:** tim lain di tantangan api yang sama, dengan dashboard FIRMS standar (rasio global, peta, CSV)
- **P2:** tim pertanian + data NASA (SMAP/IMERG) dengan petani sungguhan
- **P3:** chatbot AI di atas data NASA
- **P4:** simulasi asteroid/antariksa ala AIM-X 2025
- **P5:** tim visualisasi data kuat di tantangan lain

| Juri | vs P1 | vs P2 | vs P3 | vs P4 | vs P5 | Menang |
|---|---|---|---|---|---|---|
| N1 | **KA** (rigor ilmiah jauh di atas) | P2 (pengguna nyata + validasi lapangan) | **KA** | **KA** (relevansi Bumi) | **KA** | 4/5 |
| N2 | **KA** (relevansi Indonesia) | P2 (demo pengguna nyata) | **KA** (chatbot biasanya dangkal) | P4 (preseden 2025 + pitch) | P5 (demo lebih jelas dalam 30 detik) | 2/5 |
| N3 | **KA** | P2 (pola 4 Global Award pertanian) | **KA** | P4 (momen wow) | P5 | 2/5 |

**Total: 8/15 menang.** KalenderApi selalu mengalahkan pesaing di tantangan yang sama dan chatbot. Ia kalah ketika lawannya punya pengguna nyata (P2) atau momen visual (P4, P5). Kedua kekalahan itu persis mencerminkan dua lubang terbesar di §6.

---

## 4. Tiga plafon
| Skenario | Skor | Rentang | Alasan |
|---|---|---|---|
| **(a) Rencana sekarang** | **65** | 60–69 | Konsensus §1 |
| **(b) Semua isi 39 jam dieksekusi baik + tim terkunci dengan orang statistik + 1 wawancara praktisi nyata** | **77** | 73–81 | Batas Influence naik (≈17), batas build hilang (Validity ≈16–17, Presentation ≈15–16). Menjadi "Local Winner jelas" hanya **jika veto §2 dicabut** (kalau tidak, maks 70). Tidak sampai 90 karena juri NASA tetap bisa berkata "FireCal sudah melakukan cell-day + LOYO" dan momen demonya bisa disamai (Icarus punya toggle) |
| **(c) MVP saja** (dibangun, tanpa stretch, tanpa wawancara) | **70** | 66–73 | Validity/Presentation naik, Influence tetap ≤16, Creativity tertahan karena pembeda kuat semuanya stretch |

---

## 5. 90 membutuhkan:
**90 TIDAK dilaporkan.** Saat ini tidak ada satu pun syarat paket yang terpenuhi. Checklist:
- [ ] **Momen menang ≤30 detik yang tidak bisa disamai.** Toggle mentah↔harmonisasi sudah diklaim Icarus (`03` §2). Perlu satu hal yang hanya KalenderApi punya, misalnya grafik diagnosa drift Aqua (residual setelah 2022) **ditambah** satu kalimat keputusan BPBD yang dikutip dari praktisi sungguhan
- [ ] **Bukti sudah dibuat:** situs online, tabel skill M2 vs M1 dengan angka nyata di `numbers.md`, video ≤30,0 detik
- [ ] **Juri NASA tidak bisa bilang "sudah ada":** minimal satu dari normalisasi observasi (Tier 3), rantai NOAA-20/21 pasca S-NPP, atau validasi independen era MODIS (2002–2011) **selesai dan tampil**
- [ ] **Validasi yang benar-benar menguji harmonisasi** di era sebelum 2012 (lihat lubang #2)
- [ ] **Suara pengguna nyata:** ≥1 kutipan praktisi BPBD/Manggala Agni yang boleh dipakai, sesuai templat `14` §5
- [ ] **Tim terkunci** dengan peran A (statistik) yang terbukti mampu menjalankan GLM NB + bootstrap
- [ ] **Veto dicabut** (§2 a dan b)
- [ ] Semua angka di video/slide berstatus "terukur" atau "dikutip" di `numbers.md`

---

## 6. Lima lubang teratas dan perbaikannya (tanpa kode, sesuai larangan pre-build)

1. **Tim belum terkunci; seluruh MVP bergantung pada peran A (statistik).** Hari ini, 8 hari sebelum acara, `08` masih berasumsi 4–5 orang. *Perbaikan:* tetapkan tenggat penguncian tim (paling lambat Selasa 10 Nov) dan putuskan **sekarang**, secara tertulis, versi MVP mana yang berlaku untuk 2, 3, atau 5 orang. Untuk versi 2 orang, terapkan tanpa ragu: Riau saja, M0 vs M1, HTML dari notebook (`08` "Kalau hanya 2 orang"). Hapus kartu anomali dan input lintang/bujur dari MVP versi kecil.

2. **Cek independen tidak menguji harmonisasi.** SiPongi 2015–2024 seluruhnya berada di era VIIRS teramati, sehingga "harmonisasi" = "mentah VIIRS" di jendela itu (`06` langkah 6). Uji itu hanya membuktikan bahwa VIIRS lebih baik dari MODIS, bukan bahwa sambungannya benar. *Perbaikan (di tingkat rencana):* ubah cek independen agar mencakup era MODIS. Contohnya MCD64A1 bulanan per provinsi 2002–2024, dengan uji apakah hubungan "indeks titik panas vs luas terbakar" **stabil melewati 2012** untuk seri harmonisasi tetapi patah untuk seri mentah. Catat sebagai keterbatasan bahwa MCD64A1 sebagian bergantung pada MODIS. Hapus baris "mentah VIIRS vs harmonisasi" dari grafik SiPongi atau jelaskan kenapa keduanya identik.

3. **Belum ada suara pengguna, jadi Influence terkunci di ≤16.** *Perbaikan:* kirim hari ini ke prioritas 4 di `14` §1 (dosen kehutanan/geodesi yang pernah bekerja dengan BPBD), sambil terus menindaklanjuti BPBD Riau/Kalteng. Tetapkan target 1 wawancara 15 menit sebelum Rabu 11 Nov. Satu kutipan tentang *kapan siaga ditetapkan* sudah cukup untuk mengubah 2 dari 3 kekalahan head-to-head.

4. **Klaim melebihi isi MVP (pemicu veto).** Contohnya kalimat pembeda `03` §4, tagline "every satellite, any place", dan judul slide 5 yang ditulis sebelum hasil ada. *Perbaikan:* siapkan dua versi kalimat. Versi MVP: "drift-aware, uncertainty-banded, out-of-sample tested". Versi "jika selesai" untuk setiap stretch. Judul slide 5 dibuat bersyarat, mengikuti aturan `09` §2 untuk S4.

5. **Pembeda kuat semuanya stretch, sedangkan inti MVP ≈ FireCal.** *Perbaikan:* jalankan aturan `04` §7 ("setiap baris yang naik harus menurunkan sesuatu"). **Naikkan grafik diagnosa drift** (tier 1, ±1 jam, `08`) ke MVP dan **turunkan** input lintang/bujur + radius ke stretch, karena statement hanya *menyarankannya* (`12` §2). Grafik drift adalah satu-satunya pembeda murah yang dikenali juri NASA ("under active investigation", `03` §4 #2) dan tidak ada di daftar klaim pesaing.

Catatan tambahan (di luar 5 besar): bagian Problem `09` §4 memakai dua periode luas terbakar 2026 yang berbeda (107.465 ha Jan–Jun vs 202.004 ha Jan–Jul, `02` §8). Pilih satu, seperti yang sudah disarankan `02` sendiri.

---

## 7. Cek fakta teknis (web, 6 Nov 2026)
- **S-NPP berhenti:** blog Earthdata FIRMS menyebut produksi data S-NPP berhenti **13.00 UTC 2 Nov 2026**, dan NOAA-20/21 disarankan sebagai pengganti. Klaim `02` §4 terkonfirmasi (satu halaman katalog menulis 1 Nov, jadi sebut "2 Nov per FIRMS"). Hook cadangan "lost a satellite" sah dipakai. Sumber: [Earthdata: Transitioning from Suomi NPP](https://www.earthdata.nasa.gov/news/blog/transitioning-from-suomi-npp-viirs-omps-what-firms-users-need-know)
- **Aqua MODIS:** NSIDC menulis bahwa Aqua mulai bergeser Juli 2021 dan bahwa misi berakhir sekitar **Agustus 2026** (MLT ±15.50). `02` §4 masih menulis "belum ada konfirmasi resmi", jadi perlu dicek ulang. Ini tidak mengubah metode (fit hanya 2012–2022), tetapi memperkuat cerita "record is breaking". Tanggal persis batas 13.45 MLT (Feb 2023, `05` §2) tidak bisa dipastikan dari sumber yang ditemukan, karena sumber-sumbernya saling bertentangan. Perlakukan sebagai **[U]** sampai dicek dari dokumen MODAPS. Sumber: [NSIDC Data Announcement](https://nsidc.org/ru/node/51980), [Aqua MODIS Acquisition Plan Through August 2026](https://ladsweb.modaps.eosdis.nasa.gov/alerts-and-issues/171807), [Giglio, LANCE UWG Orbit Drift 2025](https://landweb.modaps.eosdis.nasa.gov/data/filePost/LANCE_UWG_Orbit_Drift_Giglio_202505.pdf)
- **Resolusi:** MODIS 1 km di nadir dan VIIRS I-band 375 m, sesuai `05` §1.
