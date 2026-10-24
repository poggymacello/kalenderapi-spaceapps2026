# 07 — Akses Data dan Persiapan yang Boleh Dilakukan Sebelum 14 Nov
Sumber: `riset/A-sensor-harmonization.md` §6. Pola URL sudah dicek 9 Okt dengan berkas kecil Luksemburg; data Indonesia **belum** diunduh. Pengunduhan dan pemrosesan baru dilakukan di Jam 0 hackathon (lihat 06, 08).

## 1. Sumber data dan cara mengambilnya
**A. Berkas tahunan per negara FIRMS (cara termudah)**
- MODIS: `https://firms.modaps.eosdis.nasa.gov/data/country/modis/{YYYY}/modis_{YYYY}_{Country}.csv`. Terverifikasi untuk 2001, 2015, 2022, 2024. **Cek ulang 23 Okt (hanya header HTTP, tidak diunduh): `modis_2025_Indonesia.csv` sekarang tersedia (HTTP 200, ±1,4 MB).**
- VIIRS S-NPP: `…/data/country/viirs-snpp/{YYYY}/viirs-snpp_{YYYY}_{Country}.csv`. Terverifikasi 2022, 2024. **23 Okt: `viirs-snpp_2025_Indonesia.csv` tersedia (HTTP 200, ±7,6 MB).**
- NOAA-20: `…/data/country/viirs-jpss1/{YYYY}/viirs-jpss1_{YYYY}_{Country}.csv`. Terverifikasi 2018, 2022. **23 Okt: 2025 tersedia (HTTP 200, ±7,6 MB).**
- NOAA-21: `viirs-jpss2/2024` masih 404; **23 Okt: `viirs-jpss2/2025` juga 404** [U]. NOAA-21 lewat API NRT saja (stretch).
- Token negara **`Indonesia`** [V, dicek 23 Okt lewat header HTTP berkas 2024/2025].

**B. FIRMS API (untuk 2026; 2025 sudah ada di berkas negara)**
- Endpoint area: `/api/area/csv/[MAP_KEY]/[SOURCE]/[west,south,east,north]/[DAY_RANGE 1–5]/[YYYY-MM-DD]`.
  - Bounding box Indonesia: `95,-11,141,6`.
- Sumber: `MODIS_SP`, `MODIS_NRT`, `VIIRS_SNPP_SP/NRT`, `VIIRS_NOAA20_SP/NRT`, `VIIRS_NOAA21_NRT`.
  - Setelah 2 Nov 2026 pakai NOAA-20/21 NRT.
  - **Tidak ada NOAA-21 SP**; arsip NOAA-21 masih terbatas.
- Batas: **5.000 transaksi per 10 menit**. Permintaan besar dihitung beberapa transaksi. MAP_KEY gratis lewat email.
  - Anggaran panggilan: karena 2025 sudah tersedia sebagai berkas negara, API cukup untuk 1 Jan–15 Nov 2026 ≈ 319 hari ≈ **64 panggilan per sumber** (rentang 5 hari). Muat kalau diberi jeda.
- Endpoint pendukung:
  - `data_availability` untuk mengetahui rentang SP/NRT
  - `missing_data` untuk outage
  - Endpoint negara saat ini "not available"; pakai bounding box.

**C. Archive Download Tool FIRMS:** SHP/CSV/JSON untuk data >7 hari, login Earthdata atau kode email, hasil dikirim via email. NRT diganti data standar dengan jeda ±5 bulan.

**D. Google Earth Engine (untuk normalisasi observasi, Tier 3)**
- `MODIS/061/MYD14A1`, `MODIS/061/MOD14A1`, `NASA/VIIRS/002/VNP14A1` (sejak 2012-01-19).
- FireMask di produk ini punya kelas **awan dan no-data**, kunci untuk "cell-day per observasi cerah".

**E. Data pendukung**
- **Batas wilayah:** geoBoundaries IDN ADM1/ADM2 (CC BY 4.0).
- **Gambut:** GFW Global Peatlands (Miettinen 2016, CC BY 4.0).
- **ENSO:** NOAA CPC RONI/ONI.
- **Validasi:** SiPongi luas terbakar per provinsi per tahun.
- **Gunung api:** Smithsonian GVP.
- Opsional: MCD64A1/VNP64A1, CHIRPS/GPM IMERG.

## 2. Ukuran
> **Terukur 23 Okt malam (header HTTP saja, tanpa mengunduh isi; manifest lengkap di `JURI_90/firms_manifest_23okt2026.tsv`):** semua 48 berkas negara Indonesia menjawab HTTP 200: MODIS 2000–2025 (26 berkas) **119,5 MB**; VIIRS S-NPP 2012–2025 (14) **277,9 MB**; NOAA-20 2018–2025 (8) **106,1 MB**. Total **±503 MB**; set MVP (MODIS 2002–2025 + S-NPP 2012–2025) **±396 MB**. Tahun terbesar: S-NPP 2015 (69,3 MB), 2014 (43,8 MB), 2019 (34,6 MB). NOAA-21 (`viirs-jpss2`) 2025 dan semua berkas 2026 masih 404, jadi 2026 tetap lewat API. Perkiraan lama di bawah ("0,5–1 GB") ternyata batas bawahnya yang benar.

Perkiraan lama (9 Okt):
- VIIRS S-NPP Indonesia ±412 ribu deteksi/tahun (2012–2016) ≈ **30–40 MB CSV/tahun**; tahun ekstrem 2–3× lebih besar.
- MODIS ±79 ribu/tahun ≈ 6–8 MB/tahun.
- Total 2001–2024 ≈ **0,5–1 GB CSV**. Simpan sebagai Parquet; olah dengan DuckDB.
- Catatan 23 Okt: berkas 2025 jauh lebih kecil dari perkiraan per tahun (MODIS ±1,4 MB, S-NPP ±7,6 MB), wajar untuk tahun La Niña/netral dengan api rendah. Ukuran tahun ekstrem tetap diasumsikan 2–3× rata-rata.

## 3. Jebakan data yang harus diingat
| Jebakan | Penanganan |
|---|---|
| Kolom `version` MODIS di berkas negara berganti-ganti (6.2 → 6.03 → 61.03) dan typing `type` berubah antarversi | Jangan percaya `type` lintas tahun; pakai masker buatan sendiri (05 §3) |
| Data NRT **tidak punya `type`** | Masker sendiri wajib untuk data terbaru |
| NRT vs standar beda geolokasi (offset ratusan meter) | Jangan dicampur untuk periode yang sama; utamakan SP |
| Kepercayaan MODIS (angka) ≠ VIIRS (kategori); BRIN mengode VIIRS sebagai 7/8/9 | Petakan eksplisit; mode kepercayaan ditampilkan di UI |
| S-NPP berhenti 2 Nov 2026; status Aqua/Terra tidak pasti | Rantai NOAA-20/21; cek halaman LAADS dan Earthdata alerts sebelum hari-H |

## 4. Sitasi wajib
> **Cek DOI 23 Okt (resolusi doi.org):** `10.5067/FIRMS/VIIRS/VNP14IMGT_NRT.002`, `10.5067/FIRMS/VIIRS/VJ114IMGT_NRT.002`, `10.5067/VIIRS/VNP14A1.002`, `10.5067/MODIS/MCD64A1.061`, `10.5067/VIIRS/VNP14IMG.002`, `10.5067/VIIRS/VJ114IMG.002`, `10.5067/FIRMS/MODIS/MCD14DL.NRT.0061` → halaman katalog Earthdata (200). **`10.5067/FIRMS/MODIS/MCD14ML` diarahkan ke halaman yang 404**: DOI-nya tetap boleh dikutip, tapi tambahkan juga MCD14DL NRT DOI di atas dan makalah Giglio et al. 2016, lalu cek ulang 13 Nov.

- Pengakuan FIRMS: *"We acknowledge the use of imagery from the NASA LANCE FIRMS (https://earthdata.nasa.gov/firms), part of the NASA Earth Science Data and Information System (ESDIS)."*
- DOI dataset (verifikasi dulu di doi.org): MCD14ML `10.5067/FIRMS/MODIS/MCD14ML`; VNP14IMGT NRT `10.5067/FIRMS/VIIRS/VNP14IMGT_NRT.002`; VJ114IMGT NRT `10.5067/FIRMS/VIIRS/VJ114IMGT_NRT.002`; VNP14A1 `10.5067/VIIRS/VNP14A1.002`.
- Makalah algoritma: Giglio et al. 2016; Schroeder et al. 2014. Lapisan gambut: WRI/GFW + Miettinen et al. 2016.

## 5. Checklist persiapan yang BOLEH sebelum 14 Nov
> Versi bertanggal (dengan draf email, pesan rekrut, dan panduan wawancara) ada di `11-CHECKLIST-PRA-HARI-H.md`.
| Siapa | Kegiatan | Status aturan |
|---|---|---|
| Semua | Baca 01–05 dan 10; hafalkan pembeda dan bahasa yang disiplin | ✅ belajar |
| Semua | Buat **akun Earthdata Login**; minta **FIRMS MAP_KEY**; akun Google Earth Engine | ✅ akses alat |
| B (kamu) | Pastikan Python 3.12 + DuckDB + geopandas + statsmodels, Node + Vite terpasang; akun Cloudflare Pages / GitHub Pages | ✅ alat |
| C | Latihan MapLibre + ECharts di proyek **lain** (jangan dibawa ke repo hari-H) | ✅ latihan |
| D | Kumpulkan **tautan** sumber SiPongi per provinsi per tahun (tanpa mengolah datanya); siapkan daftar pertanyaan wawancara praktisi | ✅ riset |
| D | (Opsional) wawancara 1 praktisi BPBD/Manggala Agni: kapan mereka mulai siaga, data apa yang mereka pakai | ✅ riset pengguna |
| Lead | Email **spaceappsbandung@gmail.com**: format pitch lokal (durasi, live/rekaman, juri), dan persiapan apa yang boleh | ✅ |
| Semua | **28 Okt:** baca pernyataan tantangan lengkap; sesuaikan istilah dengan teks resmi | ✅ |
| Semua | **13 Nov:** baca panduan Judging & Submission 2026; cek batas demo dan aturan AI | ✅ |
| — | Menulis kode/notebook, mengunduh dan memproses data Indonesia, membuat slide final, desain UI | ❌ **tunggu 14 Nov 09.00** |

## 6. Hal yang perlu dicek ulang sebelum hari-H
> Cek 23 Okt malam: **SiPongi (sipongi.kehutanan.go.id dan sipongi.menlhk.go.id) dan aqua.nasa.gov tidak bisa dijangkau** dari koneksi agen (timeout); Smithsonian GVP menolak permintaan otomatis (403). Bisa jadi hanya pemblokiran jaringan. **Manusia perlu membuka ketiganya dari browser** sebelum 9 Nov. Kalau SiPongi memang tidak bisa diakses, validasi utama pindah ke MCD64A1 (`04` §10).

> Daftar lengkap dengan hasil cek 23 Okt + sumber ada di `11-CHECKLIST-PRA-HARI-H.md` §3.
- Apakah Aqua/Terra masih mengumpulkan data per Nov 2026 (halaman misi Aqua, LAADS transition).
- Ketersediaan berkas negara NOAA-21 di FIRMS.
- Token nama berkas `Indonesia` dan ukuran berkas sebenarnya (dicek di Jam 0).

## 7. Runbook akuisisi data (rencana; dijalankan Sab 14 Nov 09.00)
**Status aturan.** FAQ 2026: *"Teams are not allowed to begin working on the challenges prior to the hackathon."* FAQ dan T&C 2026 **tidak** menyebut secara eksplisit apakah mengunduh data publik lebih awal termasuk "working on the challenge". Keputusan kita: **tidak mengunduh sebelum 14 Nov 09.00** kecuali Local Lead mengizinkan secara tertulis (pertanyaan 6 di email `11` §2). Alasannya, manfaatnya kecil: seluruh set MVP hanya ±396 MB, sekitar 6 menit di 10 Mbps atau ±27 menit di 2 Mbps. Risikonya (dianggap mulai lebih awal) jauh lebih mahal. Yang boleh sekarang: memasang alat, membuat akun dan MAP_KEY, dan menulis daftar URL di bawah (ini perencanaan, bukan produk).

**Urutan Jam 0 (09.00–09.30, B memegang laptop paling kencang + hotspot cadangan):**
| Langkah | Isi | Ukuran / waktu | Cek selesai |
|---|---|---|---|
| 1 | Berkas negara S-NPP 2012–2025 | 277,9 MB | 14 berkas, ukuran sama dengan manifest |
| 2 | Berkas negara MODIS 2002–2025 (+2000–2001 untuk stretch E0) | 119,5 MB | 26 berkas |
| 3 | NOAA-20 2018–2025 (hanya kalau statement baris S7 aktif atau stretch rantai) | 106,1 MB | 8 berkas |
| 4 | API FIRMS 2026: `VIIRS_SNPP_NRT`/`SP`, `MODIS_NRT`/`SP`, `VIIRS_NOAA20_NRT`, `VIIRS_NOAA21_NRT`, bbox `95,-11,141,6`, rentang 5 hari | ±64 panggilan per sumber, beri jeda | Endpoint `data_availability` dicek dulu |
| 5 | `missing_data` FIRMS untuk daftar outage | kecil | Daftar outage ditulis ke `docs/data_sources.md` |
| 6 | geoBoundaries IDN ADM1 (dan ADM2 untuk stretch) | kecil | 200 di API `gbOpen/IDN/ADM1` (dicek 23 Okt) |
| 7 | NOAA CPC `RONI.ascii.txt` + `oni.ascii.txt` | kecil | 200 (dicek 23 Okt; RONI sudah sampai JAS 2026 = 1,69) |
| 8 | Tabel SiPongi per provinsi 2015–2024 (D, manual dari browser, catat URL + tanggal akses) | — | CSV + kolom sumber |
| 9 | (Cadangan validasi) MCD64A1 via GEE `MODIS/061/MCD64A1`, dijumlah per provinsi per bulan | di server GEE | Hanya kalau SiPongi gagal |

**Pola URL (diverifikasi 23 Okt, header saja):**
```
https://firms.modaps.eosdis.nasa.gov/data/country/modis/{YYYY}/modis_{YYYY}_Indonesia.csv
https://firms.modaps.eosdis.nasa.gov/data/country/viirs-snpp/{YYYY}/viirs-snpp_{YYYY}_Indonesia.csv
https://firms.modaps.eosdis.nasa.gov/data/country/viirs-jpss1/{YYYY}/viirs-jpss1_{YYYY}_Indonesia.csv
https://firms.modaps.eosdis.nasa.gov/api/area/csv/{MAP_KEY}/{SOURCE}/95,-11,141,6/{1..5}/{YYYY-MM-DD}
https://www.geoboundaries.org/api/current/gbOpen/IDN/ADM1/
https://www.cpc.ncep.noaa.gov/data/indices/RONI.ascii.txt
```
**Reproduksibilitas (dibuat di hari-H, bukan sekarang):** skrip unduh di repo membaca daftar URL, membandingkan ukuran berkas dengan manifest, lalu menulis SHA-256 setiap berkas ke `data/MANIFEST.sha256`. README menyebut tanggal akses dan versi koleksi (MODIS C6.1, VIIRS C2). MAP_KEY dibaca dari variabel lingkungan, tidak pernah di-commit.

**Kalau internet venue lambat:** pakai hotspot HP. Berkas negara tidak bisa dipotong per pulau, jadi unduh tahun overlap 2012–2022 (kedua sensor) lebih dulu, lalu sisanya. Fitting M1/M2 sudah bisa dimulai begitu tahun overlap lengkap.
