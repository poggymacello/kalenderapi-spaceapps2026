# 01 — Tantangan, Penjurian, dan Aturan Submit
Sumber utama: `riset/C-judging-competitors.md` §1–2. Label: **[V]** dibaca langsung di sumber resmi · **[I]** indeks pencarian · **[inf]** inferensi.

## 1. Tantangannya
- **Judul:** "Harmonization of MODIS and VIIRS Hot Spots". Satu repo peserta menyebutnya "Challenge #9".
- **Isi lengkap belum terbit sampai 28 Okt 2026.** Halaman resminya baru menampilkan judul.
- **Inti yang tersirat** dari judul dan frasa yang beredar:
  - menyambung seri titik panas MODIS (2000–) dengan VIIRS (2012–) menjadi satu rekaman yang konsisten;
  - menghasilkan **kalender aktivitas pembakaran** untuk area yang dipilih pengguna.
- **Siapa penulisnya [inf]:** semua tantangan 2026 ditulis SME NASA atau Space Agency Partner (17 badan, termasuk **Badan Antariksa Brasil** dan **CONAE** Argentina) [V].
  - **Kandidat Brasil (AEB/INPE).** INPE memakai "satélite de referência" Aqua MODIS yang akan berakhir. FAQ INPE menyebut penggantinya S-NPP VIIRS, yang justru berhenti 2 Nov 2026.
  - **Kandidat NASA.** Kontinuitas MODIS→VIIRS adalah prioritas NASA. Ilmuwan api NASA (Boschetti/Roy/Giglio) mengusulkan seri harmonisasi MODIS/VIIRS 25 tahun "with uncertainties".
  - **Strategi:** bangun solusi yang memuaskan **kedua** pembaca. Untuk ilmuwan NASA: produk standar FIRMS + ketidakpastian + validasi. Untuk operator ala INPE: seri referensi yang bertahan melewati pergantian satelit.

## 2. Kriteria juri (pakai rubrik 2025, cek ulang 13 Nov)
Lima kriteria, **masing-masing diberi skor 1–5 di setiap level penjurian** [I, panduan 2025]:

| Kriteria | Pertanyaan juri | Deskriptor skor 5 (2025) |
|---|---|---|
| **Impact** | Seberapa besar masalahnya, berapa banyak yang terbantu | Masalah signifikan, jangkauan luas |
| **Creativity** | Baru, atau perbaikan inkremental | "groundbreaking approach that has never been attempted before" |
| **Validity** | Sahih secara ilmiah? Bekerja di dunia nyata? | Sahih secara ilmiah & layak teknis, "fully developed and ready for real-world implementation" |
| **Relevance** | Menjawab tantangan? Lengkap? Mudah dipakai? | "NASA data is integral to the project's success" |
| **Presentation** | Seberapa baik cerita tim | Dihitung dari demo **dan** keseluruhan halaman proyek |

- Nama resminya **Impact**, bukan "Influence"; "Influence" hanya muncul di ringkasan pihak ketiga.
- Panduan 2021 meminta tim memberi **perhatian yang sama** untuk presentasi seperti untuk empat kriteria lain [V].

## 3. Alur penjurian
1. **Lokal (Bandung):** panel juri lokal memilih **1–3 proyek** sebagai *Global Nominee* (tergantung jumlah submit). Hadiah lokal terpisah [V, 2021]. Format lokal Indonesia tidak terdokumentasi publik; **tanyakan ke Local Lead**.
2. **Global:** SME NASA dan mitra menilai semua nominee lalu memilih *Global Finalists* dan *Honorable Mentions* [V]. Kemungkinan penulis tantangan ini ikut menilai [inf].
3. **Eksekutif:** pimpinan NASA/mitra memilih **10 Global Winners**, satu per kategori penghargaan, dari semua tantangan [V].

**Corong peserta [V]:**
| Tahun | Submit | Global Nominee | Finalist | Honorable Mention | Winner |
|---|---|---|---|---|---|
| 2025 | 11.500+ | 1.290+ (±11%) | 45 (±3,5% nominee) | 23 | 10 |
| 2024 | 9.996 | 940+ | 40 | 19 | 10 |

**Kategori yang paling cocok [inf]:** *Best Use of Science*, *Best Use of Data*, *Local Impact* (2024 dimenangkan alat GIS kebakaran G.R.O.W., Brasil), *Galactic Impact*.

**Pola historis [inf]:** proyek kebakaran cukup sering jadi nominee/finalist tetapi jarang menang. Kalau menang, alasannya **pengguna lokal yang jelas dan aksesibilitas**, bukan algoritma deteksi.

**Rekam jejak ITB:** tim STEI ITB "AIM-X" (2025) meraih Global Nominee & Local Winner + **Best Pitch**. Artinya juri lokal menghargai penyampaian.

## 4. Syarat submit (cek ulang di panduan 13 Nov)
- **Halaman Project adalah yang dinilai juri.** Mayoritas penilaian berasal dari submission [V 2022; I 2025].
- **Demo:** video **≤30 detik** atau **≤7 slide termasuk judul** [I 2025]. Pada 2022 juri berhenti menilai di batas itu [V]. Pada 2024 demo yang melebihi batas dilaporkan **tidak eligible untuk penjurian global** [I].
- Bahasa Inggris di halaman proyek dan materi yang ditautkan; video berbahasa lain wajib subtitle Inggris [V].
- Wajib memakai sebagian data terbuka NASA atau Space Agency Partner [V].
- Menjawab tantangan resmi; "Create Your Own Challenge" tidak ikut penjurian global [V].
- Tim 1–6 orang, **semua terdaftar di Local Event yang sama** [V].
- Tautan publik ke proyek final (repo, demo).

## 5. Aturan AI (2025, akan dicek ulang)
- **Update 23 Okt (FAQ 2026, dibaca langsung):** istilah resmi 2026 adalah **"Super Intelligence (SI)"**. Alat SI boleh dipakai, dan setiap submission **wajib** menjelaskan cara alat SI dipakai. Lihat juga ringkasan T&C 2026 di `11` (lisensi data non-NASA, sitasi semua sumber).
- Gambar/video buatan AI wajib **watermark** yang terlihat.
- Kode dan data buatan AI wajib **diakui** di teks deskripsi dan metadata.
- Juri menimbang "originality, intent, and execution" dalam pekerjaan berbantuan AI.
- Praktik tim: catat semua penggunaan AI di `docs/ai_use.md` (lihat 08).

## 6. Saran resmi tentang yang dinilai
- Struktur "30 Seconds of Glory" (2022):
  1. kenalkan tim
  2. sebut tantangannya
  3. judul + tagline solusi
  4. cara kerja dan bagaimana data badan antariksa memungkinkannya
  5. dampak ke depan
- Demo "sering menjadi bagian pertama yang dilihat juri" [V].
- Wawasan yang menarik + cerita yang kuat naik ke atas; jaga halaman proyek dan kode open-source tetap mutakhir [V 2016].
