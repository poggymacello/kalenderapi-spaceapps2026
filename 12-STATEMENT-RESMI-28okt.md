# 12 · Statement resmi 28 Okt vs rencana KalenderApi
Dibaca langsung Rabu 28 Okt 2026 malam (WIB) dari halaman resmi spaceappschallenge.org lewat browser. Isi statement **diparafrasakan**, tidak disalin, supaya file ini tidak menjadi salinan teks resmi. Buka sumbernya sendiri sebelum mengambil keputusan.

## 1. Hasil cek: tantangan kita ADA di daftar 2026
| Hal | Hasil 28 Okt | Sumber |
|---|---|---|
| Jumlah tantangan 2026 | **14** | [Daftar 2026 Challenges](https://www.spaceappschallenge.org/2026/challenges/) |
| Tantangan kita | **"Harmonization of MODIS and VIIRS Hot Spots"**, ada, dengan statement lengkap (Background, Objectives, Potential Considerations) | [Halaman tantangan](https://www.spaceappschallenge.org/2026/challenges/modis-and-viirs-hot-spots/) |
| Slug yang benar | `/2026/challenges/modis-and-viirs-hot-spots/` (bukan `harmonization-of-modis-and-viirs-hot-spots/` seperti tertulis di `11`) | idem |
| Tingkat & subjek | Advanced + Intermediate · Earth Science, Software | idem |
| Tab Resources | Kosong. Tertulis: resources tersedia **Jumat 13 Nov** | idem, tab Resources |
| Penulis (dugaan) | Kredit foto statement: **CONAE (badan antariksa Argentina)**. Dugaan kuat penulisnya CONAE **[inf]**, bukan AEB/INPE Brasil seperti tebakan lama di `01` §1 dan `04` §5 | idem |

**Kesimpulan: tidak perlu pemetaan ulang ke tantangan lain.** Tantangan lain yang menyentuh api atau bencana, untuk catatan saja: "Dancing with the SARs" (NISAR radar, perubahan permukaan termasuk kebakaran hutan) dan "Flame in Freefall" (pembakaran di gravitasi mikro, bukan karhutla). Keduanya jauh lebih jauh dari rencana kita.

## 2. Apa yang diminta statement vs rencana kita
| Yang diminta / disarankan statement (parafrase) | Status di rencana 23 Okt | Keputusan 28 Okt |
|---|---|---|
| **Web application** yang memakai data hotspot hasil harmonisasi | Ada (web statis, `06`, `08`) | Tetap. Rencana 2 orang (notebook → HTML statis) masih sah karena tetap halaman web |
| Dua tahap: harmonisasi dulu sampai **sensor asal tidak lagi penting**, lalu aplikasi | Ada (M2 → kalender) | Tetap. Kalimat "sensor of origin no longer matters" dipakai di pitch |
| **Burning activity calendar** berbasis jumlah hotspot, **awal 2000-an sampai sekarang** | Ada (Jul 2002–2026, Terra-only 2000–2002 = stretch) | Tetap. "Early 2000s" sudah terpenuhi dari Jul 2002 |
| Pengguna **memilih wilayah** dan **rentang tanggal**, lalu **mengunduh analitik dan visualisasi** | Wilayah = 3 provinsi preset. Rentang tanggal dan unduhan belum ada di MVP | **Naik ke MVP:** filter rentang tanggal + unduh CSV tabel bulanan + unduh PNG kalender (S9 di §3) |
| **Bandingkan bulan berjalan dengan median historis** wilayah itu; anomali terhadap rata-rata multi-tahun | Tracker 2026 = stretch tier 2 | **Naik ke MVP (versi ringan):** kartu "bulan lengkap terakhir vs median 2002–2025 seri harmonisasi + rentang P25–P75" (S6) |
| Bulan dan tahun dengan aktivitas tertinggi; periode kritis | Ada (onset, puncak, periode kritis, `04` §8) | Tetap |
| **Color ramp yang aksesibel** | Tidak disebut | **MVP, biaya hampir nol:** palet ramah buta warna (S10) |
| Pengguna: early warning dan emergency responders, ilmuwan, land managers, **firefighters** | BPBD, BNPB, Manggala Agni, BMKG, ilmuwan (`04` §2) | Cocok. Manggala Agni = "firefighters" versi Indonesia; sebut begitu di pitch |
| Disarankan: gambar AOI di peta **atau** masukkan lintang/bujur | Poligon = stretch tier 3 | **MVP ringan:** input lintang/bujur + radius km di atas grid 0,1°. Gambar poligon naik ke stretch tier 1 (S3) |
| Disarankan: **CSV hotspot** hasil pencarian | Ekspor CSV per provinsi = stretch tier 1 | MVP = CSV **tabel bulanan** (mentah MODIS, mentah VIIRS, harmonisasi, pita). CSV **baris hotspot mentah** per provinsi × tahun = stretch tier 1, kalau ukuran berkas statis masuk akal (cek di Jam 2) |
| Data yang disarankan: FIRMS (MODIS + VIIRS) | Ada (`07`) | Tetap. Tunggu tab Resources 13 Nov untuk dataset tambahan (S8) |

**Satu ketegangan yang harus dijawab di halaman Metode:** statement berbicara tentang **jumlah hotspot**, sedangkan satuan harmonisasi kita adalah **fire cell-day** (okupansi grid 0,1°). Keputusan: kalender diberi label *"harmonized hotspot activity (VIIRS-equivalent fire cell-days)"*, tooltip dan CSV menampilkan juga **jumlah hotspot mentah per sensor**, dan halaman Metode menjelaskan dalam dua kalimat kenapa jumlah piksel mentah tidak bisa dibandingkan (piksel VIIRS 375 m vs MODIS 1 km: satu api yang sama menghasilkan lebih banyak deteksi VIIRS). Ini juga jawaban Q baru di §5.

## 3. Matriks adaptasi `04` §7: keputusan 28 Okt
| # | Pemicu | Aktif? | Keputusan |
|---|---|---|---|
| S1 | Satuan setara-MODIS | **Tidak** | Statement tidak menentukan satuan. Tetap setara-VIIRS (`05`) |
| S2 | Kalender mingguan/harian | **Tidak** | Statement memakai bulan ("bulan berjalan", "bulan dan tahun tertinggi"). Tetap bulanan |
| S3 | AOI bebas | **Sebagian** | MVP: preset provinsi + input lintang/bujur + radius. Poligon = stretch tier 1 |
| S4 | Global / negara lain | **Tidak untuk MVP** | Stretch tier 1: satu wilayah Argentina sebagai bukti generalisasi (penulis kemungkinan CONAE **[inf]**). Pilih provinsinya di hari-H dari data, bukan dari ingatan |
| S5 | Intensitas (FRP) / luas | **Tidak** | Statement meminta jumlah hotspot |
| S6 | Peringatan dini / anomali | **Ya** | MVP: kartu "bulan lengkap terakhir vs median". Bulan acuan = **Okt 2026** (masih S-NPP), sehingga MVP tidak bergantung pada rantai NOAA-20 |
| S7 | NOAA-20/21 wajib | **Tidak** | Tidak disebut. Rantai NOAA-20 tetap stretch tier 2, dipakai kalau ingin menampilkan Nov 2026 (S-NPP berhenti 2 Nov) |
| S8 | Dataset wajib lain | **Tunggu 13 Nov** | Tab Resources baru terbit 13 Nov. Baca saat itu; kalau ada dataset yang disebut, masuk validasi atau diabaikan dengan alasan tertulis |
| S9 (baru) | Rentang tanggal + unduh | **Ya** | MVP: filter rentang tanggal, CSV tabel bulanan, PNG kalender |
| S10 (baru) | Color ramp aksesibel | **Ya** | MVP: palet sekuensial ramah buta warna + legenda angka |

**Aturan `04` §7 dijalankan:** ada 3 baris aktif berbiaya (S3, S6, S9; S10 hampir gratis), jadi **provinsi preset turun dari 3 ke 2: Riau + Kalimantan Tengah**. Sumatera Selatan tetap bisa dicapai lewat input lintang/bujur, dan menjadi hal pertama yang kembali kalau checkpoint #2 (Sab 18.00) hijau.

Perkiraan biaya tambahan: S3 ringan ±1,5 jam (C) · S6 ±1 jam (A + C) · S9 ±1 jam (B + C) · S10 ±10 menit. Yang turun: provinsi ke-3 di validasi (cek SiPongi menjadi 2 provinsi × 10 tahun + nasional 10 titik = 30 titik) dan seluruh kerja preset Sumsel (±2 jam).

## 4. Perubahan MVP di `08` (berlaku mulai 28 Okt)
1. Kalender Api: **2 provinsi preset** (Riau, Kalteng) + **input lintang/bujur + radius**.
2. **Filter rentang tanggal** pada kalender dan seri.
3. **Kartu "Oct 2026 vs typical October"**: nilai harmonisasi vs median 2002–2025 (seri harmonisasi, inilah gunanya harmonisasi) dan rentang P25–P75, dengan kalimat yang bisa dicek (format `04` §8).
4. **Unduh:** CSV tabel bulanan (kolom: wilayah, bulan, hotspot mentah MODIS, hotspot mentah VIIRS, harmonisasi, P5, P95, flag ketidakpastian) + PNG kalender.
5. **Palet aksesibel** + legenda angka.
6. Validasi: Spearman ρ vs SiPongi untuk 2 provinsi + nasional.
Sisanya di MVP `08` tidak berubah.

## 5. Kosakata resmi dari statement (pakai persis di halaman Project, video, deck)
*burning activity calendar* · *active fire hotspots* · *harmonize / harmonized hotspots* · *area of interest* · *critical periods* · *unusual conditions* · *historical median* · *anomalies against multi-year averages* · *early warning and emergency responders* · *land managers* · *firefighters* · *accessible color ramps* · *sensor of origin*.

Pertanyaan juri baru yang muncul dari statement (jawaban EN, angka diisi hari-H):
- **"The challenge asks for hotspot counts. Why cell-days?"** → Raw hotspot counts aren't comparable: one fire gives more VIIRS detections than MODIS detections, because VIIRS pixels are smaller. Counting burning grid cells per day removes most of that pixel-size effect before we calibrate. The CSV still gives raw hotspot counts per sensor, so nothing is hidden.
- **"How does this month compare?"** → Show the card: October 2026 vs the 2002–2025 harmonized median for the same area, with the P25–P75 range. Say "above the usual range" only if it is outside P75.

## 6. Aturan persiapan dicek ulang 28 Okt (FAQ peserta 2026)
FAQ masih menulis: *"Teams are not allowed to begin working on the challenges prior to the hackathon."* Tidak ada aturan baru tentang apa yang boleh disiapkan. Hal lain yang dicek ulang di FAQ hari ini: tim lokal 1–6 orang, semua di Local Event yang sama, satu tantangan; Space Apps Connect buka **3 Nov**; panduan Project Submission dan Judging & Awards terbit **13 Nov**; alat SI boleh dipakai dan setiap submission wajib menjelaskan cara pakainya.

| Boleh sebelum 14 Nov 09.00 | Tidak boleh |
|---|---|
| Membaca statement, literatur, dan dokumentasi FIRMS | Kode, notebook, skrip, atau repo KalenderApi |
| Merekrut tim, membagi peran, mendaftar, membuat akun (Earthdata, FIRMS MAP_KEY, GEE, GitHub) | Mengunduh lalu mengolah data Indonesia (keputusan konservatif `11`: unduh mentah pun ditunda sampai 14 Nov kecuali Local Lead mengizinkan tertulis) |
| **Wawancara praktisi** tentang cara kerja mereka, tanpa menunjukkan desain atau prototipe (`14`). Diungkap di halaman Project | Desain UI, wireframe, mockup, palet final, slide final, storyboard yang sudah berisi angka |
| Latihan alat di proyek mainan dengan data lain (`11` §6) | Membawa kode latihan ke repo hari-H |
| Menulis rencana seperti file ini | Menulis teks halaman Project final |

Catatan jujur: wawancara praktisi adalah area abu-abu yang paling dekat dengan "mulai mengerjakan". Cara aman: pertanyaan tentang **pekerjaan mereka**, bukan tentang fitur aplikasi kita; tidak menunjukkan gambar; minta konfirmasi Local Lead (email `11` §2, pertanyaan 3); dan tulis di halaman Project bahwa percakapan terjadi sebelum acara.

## 7. Dampak ke pitch
- Statement sendiri menyebut MODIS di Terra dan Aqua **mendekati akhir masa operasi** dan digantikan VIIRS. Hook "S-NPP berhenti 2 Nov" tetap menunggu cek 3 Nov (`11` §3 #1), tetapi kalimat "MODIS is retiring" sekarang punya sumber resmi: statement itu sendiri.
- Kalimat demo baru (detik 20–26 video, atau slide 6): *"October 2026 in Riau: [x] versus a typical October of [m] (range [a]–[b])."* Hanya kalau angkanya ada di `numbers.md`.
- Kalau penulisnya memang CONAE, juri global kemungkinan termasuk ilmuwan api Argentina. Contoh satu wilayah Argentina (stretch tier 1) menjadi pembeda yang murah, tetapi hanya ditampilkan kalau selesai.
