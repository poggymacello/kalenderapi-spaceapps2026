# CARA_KIRIM — KalenderApi (NASA Space Apps 2026, Local Event Bandung)
Agen tidak mendaftar, login, push, atau mengirim apa pun. Semua langkah dilakukan tim sendiri. Format pasti mengikuti **Project Submission Guide yang terbit 13 Nov**; tabel di bawah memakai format 2025 dan harus dicek ulang hari itu.

## 1. Mekanisme
| Hal | Isi |
|---|---|
| Tempat submit | **Halaman Project tim** di spaceappschallenge.org (FAQ 2026: wajib untuk penjurian global) |
| Tenggat | Min 15 Nov 2026 23.59 waktu lokal (WIB). Target internal: **submit 20.00** (`08`). Tanyakan ke Local Lead apakah penjurian lokal punya tenggat lebih awal (`11` §2 pertanyaan 5) |
| Syarat tim | 1–6 orang, semua terdaftar di **Local Event Bandung yang sama**, satu tantangan: "Harmonization of MODIS and VIIRS Hot Spots" |
| Bahasa | Semua teks bahasa Inggris; video dengan subtitle Inggris |
| Demo | **Video ≤30 detik** (rencana kita), host publik tanpa login (YouTube publik/unlisted atau GitHub). Nama berkas: `kalenderapi-demo-30s.mp4` |
| Proyek final | Repo GitHub publik `kalender-api` (lisensi Apache-2.0 atau MIT; tanpa pilihan, NASA memakai Apache 2.0) + situs statis (Cloudflare Pages + cermin GitHub Pages) |
| Field wajib (format 2025) | Nama proyek · high-level summary · link demo · link proyek final · deskripsi detail · **penggunaan alat SI** · data NASA/mitra yang dipakai · referensi (semua sumber) · centang T&C + orisinalitas |
| Lampiran dari repo | `docs/methods.md`, `limitations.md`, `ai_use.md` (SI), `data_licenses.md`, `numbers.md`, `data/MANIFEST.sha256` |

## 2. Checklist H-1 (Jumat 13 Nov)
*Versi lengkap satu halaman (termasuk tas dan jam per jam Sab–Min): `15-CHECKLIST-HARI-H.md`.*
- [ ] Baca tab **Resources** di halaman tantangan (`/2026/challenges/modis-and-viirs-hot-spots/`, terbit 13 Nov) dan putuskan baris S8 (`12` §3)
- [ ] Baca **Project Submission Guide** dan **Judging & Awards Guide** 2026. Ubah `01`, `09`, dan file ini kalau batas demo, label SI, atau field berbeda
- [ ] Semua anggota sudah terdaftar dan ada di tim yang sama di **Local Event Bandung** (screenshot halaman tim)
- [ ] Tantangan di halaman tim = "Harmonization of MODIS and VIIRS Hot Spots"
- [ ] Earthdata Login dan **FIRMS MAP_KEY** berfungsi (uji satu panggilan `data_availability` di luar repo); MAP_KEY disimpan di pengelola sandi, bukan di grup
- [ ] Akun GitHub + Cloudflare Pages siap; akun GEE aktif (untuk cadangan MCD64A1)
- [ ] Laptop: Python 3.12 + DuckDB + pandas + geopandas + statsmodels; Node + Vite; Git; ffmpeg/ffprobe (untuk cek durasi video)
- [ ] Matriks adaptasi `04` §7 sudah terisi (✅ 28 Okt, `12` §3); balasan Local Lead sudah dibaca
- [ ] **Tidak ada** kode, notebook, data Indonesia yang terunduh/terolah, atau slide KalenderApi di laptop sebelum 14 Nov 09.00
- [ ] Hotspot HP berkuota ≥2 GB (unduhan Jam 0 ±396–503 MB)

## 3. Checklist submit (Min 15 Nov 18.00–20.00)
- [ ] Video: `ffprobe` durasi **≤30,0 detik**; subtitle Inggris; tanpa logo NASA; tanpa musik berhak cipta; watermark kalau ada visual buatan SI; orang yang tampil sudah memberi izin tertulis
- [ ] Semua angka di video, slide, dan halaman Project ada di `numbers.md` dengan asal yang jelas
- [ ] Bagian **SI** diisi dari `ai_use.md` (alat, untuk apa, bagian mana)
- [ ] **Referensi lengkap**: FIRMS acknowledgement (`07` §4), DOI produk, geoBoundaries, GFW peat, RONI, SiPongi (URL + tanggal akses), makalah algoritma. T&C: tanpa sitasi, nominasi bisa dicabut
- [ ] `data_licenses.md` mencantumkan lisensi setiap dataset non-NASA
- [ ] Repo publik; README punya satu perintah reproduksi; tidak ada MAP_KEY atau rahasia di riwayat git; tidak ada data pribadi
- [ ] Semua link (demo, repo, situs, cermin) dibuka dari **jendela incognito** di HP dan laptop
- [ ] Fitur yang diminta statement tampil: pilih wilayah (preset + lintang/bujur), rentang tanggal, kartu bulan vs median, unduh CSV + PNG, palet aksesibel (`12` §4)
- [ ] Tekan submit; **screenshot halaman konfirmasi**; catat jamnya
- [ ] Kalau ada pitch lokal: deck 7 slide (judul dihitung) dan video cadangan ada di 2 laptop + HP
