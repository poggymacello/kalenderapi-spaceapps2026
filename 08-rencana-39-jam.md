# 08 — Rencana Eksekusi ±39 Jam (Sab 14 Nov 09.00 → Min 15 Nov 23.59)

> **Direvisi 23 Okt 2026: scope dipotong.** Versi lama mencoba 9 fitur MVP untuk 34–38 provinsi. Versi ini mengunci **satu cerita yang bisa dibuktikan**: patahan 2012 hilang setelah harmonisasi, untuk 3 provinsi gambut, dengan satu model inti yang mengalahkan baseline naif secara out-of-sample, satu cek independen, dan pita ketidakpastian. Semua yang lain adalah stretch, dikerjakan **hanya** setelah checkpoint MVP hijau.
>
> Keputusan ilmiah yang dikunci (lihat kotak di atas `05`): **MODIS → setara-VIIRS**, fit **Feb 2012 – Des 2022**.
>
> Jadwal penjurian lokal Bandung belum diumumkan. Bisa saja pitch lokal Minggu siang/sore. **Asumsikan feature freeze Minggu 12.00 dan submit paling lambat Minggu 20.00.** Format ditanyakan ke spaceappsbandung@gmail.com (draf di `11`).

> **Tambahan 23 Okt malam (JURI_90):** kickoff menjalankan matriks adaptasi `04` §7 · Jam 0 mengikuti runbook `07` §7 (±396 MB terverifikasi) · validasi cadangan MCD64A1 (NASA) · deklarasi penggunaan alat AI memakai istilah resmi 2026 **"Super Intelligence (SI)"** · `docs/data_licenses.md` dan `docs/numbers.md` (buku besar angka) wajib · produksi video dengan cek durasi ≤30,0 detik · rencana 2–3 orang karena tim **belum direkrut** per 23 Okt.

## Peran (tim ideal 4–5 orang)
| Kode | Peran | Tanggung jawab MVP | Profil |
|---|---|---|---|
| **A** | Lead data & harmonisasi (statistik) | Fire cell-day, M1 + M2, LOYO, pita ketidakpastian | Kuat statistik/Python (Informatika/Statistika/Geodesi) |
| **B** | Lead pipeline & infrastruktur (**kamu**) | Unduh, ingest DuckDB, pembersihan, produk JSON 3 provinsi, deploy, keandalan | Infra/cloud |
| **C** | Frontend & visualisasi | Pemilih 3 provinsi, heatmap kalender, seri + pita, toggle mentah ↔ harmonisasi | Web dev |
| **D** | Sains & validasi + cerita | Tabel SiPongi, cek independen, keterbatasan, slide, naskah pitch, halaman Project | Geodesi/Kehutanan/Lingkungan/GIS |
| **E** (opsional) | Desain & video | UI polish, video 30 detik, visual slide | Desain/DKV |

Kalau hanya 4 orang: E digabung ke C + D. Kalau hanya 3: D digabung ke B + kamu, dan stretch tier 2 dicoret seluruhnya.

**Kalau hanya 2 orang (Poggy + satu orang statistik), atau tidak ada yang bisa statistik:**
- Frontend diganti **satu notebook → HTML statis** (Observable Framework atau halaman yang dirender dari notebook). Tidak ada SPA.
- MVP turun ke: toggle mentah ↔ harmonisasi + kalender **Riau saja** + M2 vs M1 LOYO + pita. Validasi SiPongi nasional (10 titik) saja.
- Kalau tidak ada orang yang nyaman dengan GLM: M2 diganti **rasio per strata dengan shrinkage** (M0) vs M1, tetap dengan LOYO. Lebih sederhana tapi tetap jujur, dan namanya di slide diganti.
- Keputusan ini diambil **Sel 27 Okt** saat tim dikunci (`11` §1), bukan di hari-H.

## Scope
### MVP (wajib selesai sebelum checkpoint #3, Sab 22.00)
1. **Toggle mentah ↔ harmonisasi:** grafik bulanan MODIS mentah vs VIIRS mentah (patahan 2012 terlihat) ↔ seri harmonisasi satuan setara-VIIRS (patahan hilang) + pita.
2. **Kalender Api untuk 3 provinsi:** Riau, Kalimantan Tengah, Sumatera Selatan. Heatmap tahun × bulan, Jul 2002–2026, warna = persentil terhadap baseline, sel diarsir kalau tidak pasti. Onset, puncak, dan periode kritis per provinsi. Label statis tahun El Niño.
3. **Satu model inti vs baseline naif:** **M2** (GLM binomial negatif per strata pulau × siang/malam, disusutkan ke fit nasional) vs **M1** (satu rasio nasional). Fit Feb 2012 – Des 2022, **leave-one-year-out 11 fold**. Tabel skill: MAE, persen bias, R² log1p, Kendall τ, cakupan interval 90%.
4. **Satu cek independen:** Spearman ρ indeks tahunan per provinsi (3 provinsi × 2015–2024 = 30 titik, plus nasional 10 titik) vs **luas terbakar SiPongi**, untuk mentah MODIS, mentah VIIRS, dan harmonisasi. **Cadangan (naik ke MVP kalau SiPongi per provinsi tidak bisa diambil sampai Sab 13.00):** MCD64A1 C6.1 lewat GEE, dijumlah per provinsi per bulan 2002–2024 (data NASA, tanpa masalah lisensi). Dengan MCD64A1, cek bisa dilakukan bulanan, bukan hanya tahunan.
5. **Pita ketidakpastian:** derau prediktif M2 + bootstrap blok-tahun (B ≈ 200).
6. **Halaman Metode & Validasi** (EN) + `methods.md`, `limitations.md`, `ai_use.md` (judul di halaman Project mengikuti istilah resmi 2026, *"Super Intelligence (SI) tools"*; FAQ mewajibkan deskripsi cara alat SI dipakai), **`data_licenses.md`** (lisensi setiap dataset non-NASA: geoBoundaries CC BY 4.0, GFW peat CC BY 4.0, SiPongi = status lisensi + URL + tanggal akses; T&C menolak solusi tanpa dokumentasi lisensi), dan **`numbers.md`** (setiap angka di video, slide, dan halaman Project → sel notebook atau URL sumber).
7. Pembersihan minimum: filter kepercayaan (MODIS ≥30, VIIRS n+h), `type == 0` bila ada, masker sumber persisten sederhana (satu query VIIRS malam), buang deteksi di atas air.

### Stretch (urutan prioritas; mulai hanya kalau checkpoint #3 hijau)
| Tier | Fitur | Perkiraan |
|---|---|---|
| 1 | Grafik diagnosa drift (residual log VIIRS/prediksi-Aqua 2012–2026) | ±1 jam (model sudah ada) |
| 1 | Ekspor CSV per provinsi | ±30 menit |
| 1 | Strata gambut vs non-gambut (GFW peat) | ±2 jam |
| 2 | Holdout tahun ekstrem (2015, 2019) + leave-one-province-out | ±2 jam |
| 2 | Label/i18n Bahasa Indonesia | ±1–2 jam |
| 2 | Rantai NOAA-20 → S-NPP untuk celah outage dan Nov 2026 | ±2 jam |
| 2 | Tracker kumulatif 2026 vs amplop P10–P90 | ±2 jam |
| 3 | Lebih banyak provinsi / kabupaten | ±2–3 jam |
| 3 | M3 (quantile mapping), M4 (ruang anomali), ensemble | ±3–4 jam |
| 3 | Kustom poligon di browser | ±3 jam |
| 3 | Komposit fase ENSO (RONI) | ±2 jam |
| 3 | Bulletin PDF ID/EN | ±2 jam |
| 3 | Tier 3 GEE (normalisasi observasi cerah) | ±4–6 jam |
| 3 | Negara pembanding, validasi MCD64A1, ringkasan LLM | masing-masing ±2 jam |

**Aturan stretch:** satu stretch selesai (termasuk tampil di web dan disebut di `methods.md`) sebelum mulai yang berikutnya. Stretch yang setengah jadi **tidak** ditampilkan dan tidak disebut di pitch.

## Timeline per blok
| Waktu | Target (definisi "selesai") | Pemilik |
|---|---|---|
| **Sab 09.00–09.45** | Kickoff: baca ulang statement (kalau ada perubahan sejak 28 Okt), **terapkan baris matriks `04` §7 yang sudah diputuskan 28 Okt**, kunci MVP, buat repo, bagi tugas. **Menit pertama: mulai unduh sesuai runbook `07` §7** (S-NPP 2012–2025 → MODIS 2002–2025 → API 2026 → geoBoundaries ADM1 → RONI; NOAA-20 hanya kalau baris S7 aktif). B memeriksa ukuran berkas terhadap `JURI_90/firms_manifest_23okt2026.tsv` | Semua |
| 09.45–13.00 | Ingest → Parquet; pembersihan minimum (MVP 7); fire cell-day 0,1° bulanan per aliran sensor; **grafik patahan mentah MODIS vs VIIRS** untuk Indonesia + 3 provinsi (artefak demo pertama) | B, A |
| 09.45–13.00 | Kerangka web dengan data mock: pemilih 3 provinsi, heatmap kalender, seri + pita, toggle | C |
| 09.45–13.00 | Tabel SiPongi luas terbakar Riau/Kalteng/Sumsel + nasional 2015–2024 ke CSV (sumber dicatat); draf masalah & keterbatasan | D |
| **13.00 checkpoint #1** | Patahan 2012 terlihat jelas di grafik 3 provinsi; kerangka web jalan | — |
| 13.00–18.00 | M1 + M2 di jendela Feb 2012 – Des 2022; LOYO 11 fold; tabel skill | A |
| 13.00–18.00 | Produk JSON 3 provinsi (seri mentah, seri harmonisasi, klimatologi, persentil, onset/puncak, periode kritis) dari keluaran sementara A | B |
| 13.00–18.00 | Komponen kalender dan toggle dengan skema JSON asli | C |
| 13.00–18.00 | Skrip cek Spearman vs SiPongi (siap menerima seri dari A) | D |
| **18.00 checkpoint #2** | Seri harmonisasi 3 provinsi keluar + tabel M2 vs M1. Kalau M2 **tidak** mengalahkan M1, laporkan apa adanya dan cari tahu kenapa (jangan disembunyikan) | — |
| 18.00–22.00 | Pita ketidakpastian (NB + bootstrap B ≈ 200); arsiran sel | A |
| 18.00–22.00 | Integrasi data asli ke web; deploy pertama ke Cloudflare Pages + cermin GitHub Pages | C, B |
| 18.00–22.00 | Cek SiPongi: ρ mentah MODIS vs mentah VIIRS vs harmonisasi; halaman Metode & Validasi | D, A |
| **22.00 checkpoint #3 = MVP selesai** | Versi online end-to-end: toggle, kalender 3 provinsi, tabel skill, cek SiPongi, pita. Dicek dari jendela incognito di HP | — |
| 22.00–02.00 | **Stretch tier 1 saja** (drift, CSV, gambut) kalau #3 hijau. Kalau #3 belum hijau, semua orang memperbaiki MVP | A, B, C |
| 02.00–07.00 | Tidur bergiliran (min. 3 jam per orang). Satu orang jaga build & data | — |
| **Min 07.00–12.00** | Perbaiki bug; uji perangkat (HP & laptop, Chrome & Firefox); `methods.md` + `limitations.md`; stretch tier 2 **hanya** kalau semua MVP hijau | C, D, B, A |
| **12.00 FEATURE FREEZE** | Tidak ada fitur baru setelah ini | — |
| 12.00–16.00 | 7 slide + video 30 detik (narasi EN, subtitle) + teks halaman Project + deklarasi SI. **Urutan video:** 12.00–13.00 rekam 6 shot layar sesuai storyboard `09` §2; 13.00–14.00 rekam narasi (≤65 kata) + subtitle; 14.00 cek durasi `ffprobe` **≤30,0 detik** (target 29,0 supaya aman setelah encode YouTube); 14.30 unggah publik + buka dari incognito. Setiap angka di layar dicocokkan ke `numbers.md` | D, E, kamu |
| 16.00–18.00 | Latihan pitch 3×, waktu ketat; Q&A drill (`10-QnA-juri.md`) | Semua |
| 18.00–20.00 | **Submit di halaman Project**; cek semua link via incognito; screenshot bukti submit | B, D |
| 20.00–23.59 | Buffer darurat | — |

## Rencana cadangan (kalau macet)
| Masalah | Cadangan |
|---|---|
| Agregasi cell-day lambat | DuckDB `GROUP BY floor(lat*10), floor(lon*10), solar_date, stream` langsung dari Parquet; batasi ke bounding box Sumatra + Kalimantan dulu |
| Model per-strata tidak stabil (data sedikit) | Turunkan ke strata pulau saja (tanpa siang/malam), dengan shrinkage ke nasional |
| M2 tidak mengalahkan M1 | Tetap tampilkan tabelnya. Ini temuan jujur. Kalender tetap dibuat dari model yang lebih baik di LOYO |
| Frontend terlambat | Streamlit/Observable Framework untuk demo, web statis menyusul |
| Hosting gagal | GitHub Pages; terakhir pakai video demo |
| SiPongi per provinsi tidak bisa diambil | Pakai angka tahunan nasional resmi (10 titik) dan sebut sebagai indikatif |
| API FIRMS 2026 lambat/kena batas | Kalender cukup sampai Okt 2026 dari NRT yang sudah terunduh; tandai "2026 belum lengkap" |
| Anggota sakit/absen | Scope turun ke MVP 1, 2 (Riau saja), 3, 6 |

## Aturan main tim
- Satu sumber kebenaran: repo Git. Semua angka di slide diambil dari output notebook, **tidak diketik manual**.
- Setiap klaim di pitch punya angka + sumber. Kalau belum tervalidasi, sebut "eksperimental".
- Fitur stretch yang tidak selesai tidak disebut di pitch, slide, atau halaman Project.
- Catat semua penggunaan AI/SI (alat, untuk apa, bagian mana) di `docs/ai_use.md`. Panduan submission 2026 (terbit 13 Nov) kemungkinan memakai label **"Super Intelligence (SI)"**, mengikuti FAQ 2026; ikuti label persis di formulir.
- Gambar/video buatan alat SI diberi watermark yang terlihat (aturan 2025, dicek ulang 13 Nov). Grafik dari notebook kita sendiri bukan buatan SI.
