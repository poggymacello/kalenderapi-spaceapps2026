# 15 · Checklist hari-H KalenderApi (Jum 13 – Min 15 Nov 2026)
Disusun Rabu 28 Okt 2026. Satu halaman untuk dicetak atau disimpan di HP setiap anggota. Rencana per blok tetap di `08`; perubahan MVP 28 Okt di `12` §4; submit di `JURI_90/CARA_KIRIM.md`. Jam = WIB.

**Yang belum diketahui (tunggu balasan Local Lead, `11` §2):** lokasi persis, jam buka/tutup venue, boleh menginap atau tidak, jadwal pitch lokal, tenggat lokal. Isi di grup begitu ada jawaban, lalu sesuaikan baris bertanda (LL).

## A. Jumat 13 Nov (H-1)
**Siang (Poggy + D)**
- [ ] Buka tab **Resources** halaman tantangan (terbit 13 Nov). Catat dataset yang disebut; putuskan baris S8 (`12` §3) dan tulis di grup
- [ ] Baca **Project Submission Guide** dan **Judging & Awards Guide** 2026. Cek: batas demo (video ≤30 detik / ≤7 slide?), label SI, field wajib. Kalau berbeda, ubah `09` §2 dan `CARA_KIRIM` malam ini
- [ ] Baca ulang statement; kalau ada perubahan sejak 28 Okt, catat di `12`

**Malam (semua)**
- [ ] Halaman tim di spaceappschallenge.org: semua anggota terdaftar, Local Event Bandung, tantangan "Harmonization of MODIS and VIIRS Hot Spots" (screenshot)
- [ ] Akun jalan: Earthdata Login, FIRMS MAP_KEY (uji satu panggilan `data_availability` di luar repo), GitHub, Cloudflare Pages, GEE (untuk cadangan MCD64A1)
- [ ] Laptop: Python 3.12 + DuckDB + pandas + geopandas + statsmodels; Node + Vite; Git; ffmpeg/ffprobe
- [ ] **Laptop bersih:** tidak ada kode, notebook, data Indonesia terunduh, atau slide KalenderApi. Folder latihan (`11` §6) dipindah jauh dari desktop
- [ ] Hotspot HP berkuota ≥2 GB (unduhan Jam 0 ±396–503 MB)
- [ ] Tidur sebelum 23.00

**Tas (masing-masing)**
- [ ] Laptop + charger · kabel roll (satu per tim) · power bank · mouse
- [ ] KTM dan KTP
- [ ] Earphone dengan mikrofon (rekam narasi video Minggu siang)
- [ ] Jaket, botol minum, obat pribadi
- [ ] (LL) Perlengkapan menginap kalau venue buka semalaman: sikat gigi, kaus ganti

## B. Sabtu 14 Nov
| Jam | Yang harus terjadi | Siapa | Lulus kalau… |
|---|---|---|---|
| 08.15 (LL) | Tiba di venue bersama; cari meja dekat stopkontak | Semua | Semua hadir |
| **09.00** | Hackathon mulai. **Menit pertama: unduhan berjalan** sesuai runbook `07` §7 (S-NPP 2012–2025 → MODIS 2002–2025 → API 2026 → geoBoundaries ADM1 → RONI). Cocokkan ukuran dengan `JURI_90/firms_manifest_23okt2026.tsv` | B | Unduhan berjalan sebelum 09.05 |
| 09.00–09.45 | Kickoff: terapkan keputusan `12` §3 (S3, S6, S9, S10 aktif; 2 provinsi preset), kunci MVP, buat repo, bagi tugas | Semua | Daftar MVP di README |
| 09.45–13.00 | Ingest + cell-day + grafik patahan 2012 (B, A) · kerangka web dengan data mock: pemilih wilayah + input lintang/bujur, kalender, filter tanggal (C) · tabel SiPongi Riau/Kalteng + nasional (D) | B, A, C, D | |
| **13.00 checkpoint #1** | Patahan 2012 terlihat di grafik 2 provinsi; kerangka web jalan | Semua | Screenshot di grup |
| 13.00–18.00 | M1 + M2, LOYO (A) · produk JSON termasuk median dan P25–P75 per bulan untuk kartu "Oct 2026" (B) · komponen kalender, kartu, unduh CSV/PNG (C) · skrip Spearman (D) | Semua | |
| **18.00 checkpoint #2** | Seri harmonisasi + tabel M2 vs M1 keluar. Hijau → Sumsel kembali sebagai preset ke-3 | A | Tabel skill ter-commit |
| **22.00 checkpoint #3 = MVP** | Versi online end-to-end dibuka dari incognito di HP: toggle, kalender 2 provinsi, input lintang/bujur, filter tanggal, kartu Oct 2026, unduh CSV + PNG, tabel skill, cek SiPongi, pita, palet aksesibel | Semua | Semua butir tampil |
| 22.00–02.00 | Stretch tier 1 saja (poligon, CSV baris hotspot, drift, wilayah Argentina, gambut), satu per satu | A, B, C | Selesai penuh atau tidak ditampilkan |
| 02.00–07.00 | Tidur bergiliran ≥3 jam per orang; satu orang jaga | Semua | |

## C. Minggu 15 Nov
| Jam | Yang harus terjadi | Siapa |
|---|---|---|
| 07.00–12.00 | Perbaiki bug; uji HP + laptop, Chrome + Firefox; `methods.md`, `limitations.md`, `ai_use.md`, `data_licenses.md` | Semua |
| **12.00** | **Feature freeze** | |
| 12.00–14.00 | Rekam 6 shot video (`09` §2) + narasi ≤65 kata + subtitle | D, E, Poggy |
| **14.00** | `ffprobe` durasi **≤30,0 detik** (target 29,0) | Poggy |
| 14.30 | Video diunggah publik; dibuka dari incognito | E |
| **16.00** | Cek `numbers.md`: setiap angka di video, deck, dan halaman Project punya asal | D |
| 16.00–18.00 | Latihan pitch lokal 3× dengan stopwatch + drill Q&A `10` dan `12` §5 | Semua |
| **18.00–20.00** | **Submit** (checklist `CARA_KIRIM` §3); screenshot konfirmasi | B, D |
| (LL) | Pitch lokal sesuai jadwal Local Lead | E / Poggy |
| 20.00–23.59 | Buffer darurat. Tenggat resmi 23.59 | |

## D. Lima hal yang tidak boleh terlewat (cek di setiap checkpoint)
1. **SI:** setiap penggunaan alat SI dicatat di `docs/ai_use.md` saat terjadi, bukan diingat-ingat di akhir.
2. **Lisensi dan sitasi:** setiap dataset non-NASA masuk `data_licenses.md` saat diunduh.
3. **Tidak ada PII dan rahasia:** MAP_KEY hanya di variabel lingkungan; cek riwayat git sebelum repo dibuat publik.
4. **Angka:** tidak ada angka yang diketik manual ke slide atau video; semua dari notebook atau URL di `numbers.md`.
5. **Stretch setengah jadi tidak ditampilkan** dan tidak disebut.

## E. Kalau tim hanya 2 orang
Ikuti `08` "Kalau hanya 2 orang": notebook → HTML statis, kalender **Riau saja** + input lintang/bujur kalau sempat, M2 (atau M0) vs M1 LOYO, pita, kartu Oct 2026, unduh CSV. Checkpoint #3 digeser ke Min 02.00; feature freeze tetap Min 12.00.
