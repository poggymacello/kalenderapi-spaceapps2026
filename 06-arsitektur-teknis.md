# 06 — Arsitektur Teknis (rencana; kode ditulis saat hackathon)

> **Diperbarui 23 Okt 2026:** langkah 3, 5, dan 6 dikoreksi agar arah kalibrasi sama dengan 04/05 (**MODIS → setara-VIIRS**, fit Feb 2012 – Des 2022). Tampilan dan sumber data ditandai [MVP]/[stretch] sesuai `08`.

> Status: **rencana**. Sesuai aturan Space Apps, kode, aplikasi, dan slide baru dibuat mulai **Sabtu 14 Nov 2026 09.00**. Dokumen ini menjadi cetak biru supaya ±39 jam itu habis untuk membangun, bukan berdebat.

## 1. Prinsip desain (kenapa begini)
| Prinsip | Alasan dari sudut pandang juri |
|---|---|
| **Semua dihitung di depan (offline), web cuma menyajikan file statis** | Link demo harus bisa dibuka juri kapan saja tanpa login. Tanpa backend, tidak ada server yang bisa mati saat penjurian. Hosting gratis (Cloudflare Pages / GitHub Pages) |
| **Grid-first: semua hotspot diringkas ke grid 0,1° × bulan × sensor** | AOI apa pun (provinsi, kabupaten, poligon gambar sendiri, negara lain) = jumlah sel grid, sehingga instan di browser. Ini memenuhi "within a selected area of interest" di challenge |
| **Pemisahan tegas data mentah vs harmonisasi** | Juri SME ingin melihat masalahnya ("patahan" 2012) dan solusinya berdampingan. Toggle mentah ↔ harmonisasi adalah momen demo utama |
| **Setiap angka punya ketidakpastian** | Pita interval prediksi dan skor kesepakatan sensor menjawab kriteria *Validity* |
| **Reproducible & open-source** | Notebook + `methods.md` + sitasi data di repo publik. SME NASA menghargai ini, dan disyaratkan di halaman submission (referensi) |

## 2. Sumber data (semua publik)
| Data | Isi | Pakai untuk |
|---|---|---|
| NASA FIRMS — MODIS C6.1 (Terra & Aqua), arsip + NRT | lat, lon, acq_date, acq_time, satellite, confidence (0–100), frp, daynight, **type** | Seri 2000/2002–sekarang |
| NASA FIRMS — VIIRS 375 m S-NPP (2012–), NOAA-20 (2018–), NOAA-21 (2023–) | idem; confidence l/n/h; **type** | Seri 2012–sekarang + overlap untuk kalibrasi |
| geoBoundaries IDN ADM1/ADM2 (CC BY 4.0, cek metadata) | Batas provinsi & kabupaten | AOI siap pilih |
| Global Peatlands (GFW; Miettinen et al. 2016 untuk Indonesia; CC BY 4.0) | Sebaran gambut | *(stretch)* Stratifikasi gambut vs non-gambut |
| NOAA CPC **RONI** (indeks ENSO resmi sejak 1 Feb 2026) + ONI | Fase El Niño/La Niña | *(stretch)* Kalender komposit per fase ENSO. MVP cukup label statis tahun El Niño |
| KLHK/Kemenhut SiPongi — luas karhutla per provinsi per tahun | Data resmi | **Validasi eksternal** indeks harmonisasi |
| (Stretch) NASA MCD64A1 burned area; GPM IMERG curah hujan | — | Validasi tambahan; outlook |

> Pengunduhan data dilakukan di awal hackathon (Jam 0). Sebelum hari-H cukup memastikan link dan format.

## 3. Pipeline data (Python: DuckDB + pandas + geopandas + statsmodels)
```
[1 ingest]   CSV FIRMS → Parquet (per sensor, per tahun)
[2 bersihkan] type==0 (vegetasi), buang vulkanik/industri/offshore; filter confidence;
              pisah day/night; dedup; potong ke daratan Indonesia (+ negara pembanding)
[3 samakan skala] fire cell-day per aliran sensor di grid 0,1° (okupansi, bukan piksel):
              sel bernilai 1 bila ≥1 deteksi pada hari matahari itu. Ini menyamakan skala
              MODIS dan VIIRS tanpa me-resample VIIRS ke ~1 km. Simpan juga hitungan mentah
[4 agregasi]  grid 0,1° × bulan × sensor × day/night × strata (gambut/non-gambut)
[5 kalibrasi] overlap Aqua vs S-NPP, Feb 2012 – Des 2022 → model transfer
              MODIS(Aqua) → setara-VIIRS per strata (M2 vs baseline M1)
              + validasi leave-one-year-out (11 fold) → metrik (MAE, bias, R², τ, cakupan)
[6 harmonisasi] seri gabungan dalam satuan VIIRS: Jul 2002 – Jan 2012 = estimasi dari Aqua
              (+ pita); Feb 2012 – kini = VIIRS S-NPP teramati. Terra-only 2000–2002 = stretch
[7 produk AOI] [MVP] Riau, Kalteng, Sumsel → JSON: seri bulanan mentah & harmonisasi,
              klimatologi (median/P75/P90), persentil anomali, onset/puncak, periode kritis
              [stretch] kabupaten, tracker kumulatif tahun berjalan, komposit fase ENSO
[8 ekspor]    aset statis (JSON/Parquet kecil) + laporan metode (notebook → HTML)
```
Detail matematika langkah 3–7 ada di `05-metodologi-harmonisasi.md`.

## 4. Frontend (SPA statis)
- **Stack:** Vite + TypeScript, MapLibre GL (peta; gambar poligon = stretch), Apache ECharts (heatmap kalender, seri dengan pita). MVP berbahasa Inggris; i18n ID, ekspor PDF, dan CSV = stretch.
- **Halaman/tampilan:**
  1. **[MVP] Peta & AOI:** tombol Riau, Kalimantan Tengah, Sumatera Selatan. *(Stretch: kabupaten, gambar poligon, 1 lokasi luar negeri.)*
  2. **[MVP] Kalender Api:** heatmap tahun × bulan (warna = persentil vs baseline), strip "periode kritis", label tahun El Niño.
  3. **[MVP] "Kenapa harus diharmonisasi?":** grafik mentah MODIS vs VIIRS (patahan 2012) ↔ seri harmonisasi + pita ketidakpastian.
  4. **[stretch] Tracker musim berjalan:** kumulatif 2026 vs amplop historis (P10–P90).
  5. **[stretch] Kalender per fase ENSO:** "Kalau El Niño, kalender AOI ini biasanya seperti apa".
  6. **[stretch] Bulletin 1 halaman:** ringkasan untuk BPBD/pemadam (ID/EN), unduh PDF.
  7. **[MVP] Metode & validasi:** metrik, keterbatasan, sitasi data, link repo.
- **[stretch] Kustom AOI di browser:** muat tabel grid sparse (Parquet ±beberapa MB) lalu jumlahkan sel di dalam poligon (Turf.js); hitung persentil di klien.

## 5. Struktur repo (dibuat saat hackathon)
```
kalender-api/
├─ data/            (tidak di-commit; skrip unduh saja)
├─ pipeline/        ingest.py · clean.py · celldays.py · aggregate.py · harmonize.py · products.py
├─ notebooks/       01_eda_break.ipynb · 02_harmonization_cv.ipynb · 03_validation_klhk.ipynb
├─ web/             src/ (map, calendar, tracker, enso, bulletin, i18n) · public/data/*.json
├─ docs/            methods.md · data_sources.md · limitations.md · ai_use.md
└─ README.md        cara reproduksi + sitasi + lisensi (MIT/Apache-2.0)
```

## 6. Keandalan saat penjurian
- Hosting utama Cloudflare Pages + cermin GitHub Pages. Semua aset statis, tanpa API key di klien.
- **Video demo 30 detik** tetap tersedia kalau internet venue bermasalah.
- Uji di HP & laptop, Chrome & Firefox. Target muat < 3 detik di 4G.
- Semua link (repo, demo, video, slide) dicek dari jendela incognito sebelum submit.

## 7. Anggaran performa (perkiraan kasar)
- Grid 0,1° Indonesia ±170 × 460 sel. Yang pernah ada api jauh lebih sedikit; data sparse.
- Per AOI JSON: 25 tahun × 12 bulan × beberapa metrik, hitungannya beberapa puluh KB.
- Data deteksi mentah Indonesia (MODIS + VIIRS) diproses lokal dengan DuckDB; tidak dikirim ke browser.
