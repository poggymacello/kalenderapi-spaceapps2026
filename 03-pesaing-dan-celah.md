# 03 — Pesaing dan Celah yang Belum Diisi
Sumber: `riset/C-judging-competitors.md` §4 dan `riset/A-sensor-harmonization.md` §4. Klaim repo pesaing adalah **klaim mereka sendiri** dari README; kodenya tidak diaudit.

## 1. Alat yang sudah ada vs kebutuhan tantangan
Kebutuhan: (a) **satu seri panjang MODIS+VIIRS yang dikalibrasi silang**, (b) **kalender/musim**, (c) **deteksi anomali terhadap baseline**, (d) **untuk area apa pun yang dipilih pengguna**.

| Alat | (a) Seri harmonisasi | (b) Kalender | (c) Anomali | (d) AOI bebas | Catatan |
|---|---|---|---|---|---|
| **NASA FIRMS** | ✗ (tiap sensor terpisah) | ✗ | ✗ | ✓ unduh/API | Titik FIRMS tidak membawa info awan/data hilang |
| **Global Forest Watch / Global Nature Watch** | ✗ (dataset terpisah) | sebagian (mingguan) | ✓ (±σ, ">+2σ") | ✓ gambar/unggah | **Paling dekat untuk anomali**, tapi baseline-nya tidak sadar sensor |
| **GWIS (JRC)** | ✗ | ✓ (profil negara) | ✓ (vs rata-rata 10 tahun) | ✗ | Unit nasional/regional saja |
| **INPE BDQueimadas (Brasil)** | ✗ (disambung tanpa kalibrasi) | sebagian | ✓ (vs rata-rata) | ✗ | **Paling dekat untuk kontinuitas** ("satélite de referência") |
| **SiPongi+ (Kemenhut)** | ✗ (sensor dicampur) | tidak ditemukan | tidak ditemukan | sebagian (filter provinsi) | Angka headline berubah 20–30× antarfilter |
| **ASMC** | ✗ (S-NPP→NOAA-20 tanpa catatan kalibrasi) | sebagian | kualitatif | ✗ | Hanya subregion, baseline ±5 tahun |
| **Nusantara Atlas FireWatch** | tidak terdokumentasi | ✓ kurva musim | ✓ vs tahun sebelumnya | sebagian | **Pesaing terkuat untuk cerita peringatan dini di Indonesia** (hotspot + bekas bakar Sentinel-2) |
| **BRIN hotspot** | tidak ditemukan | ✗ | ✗ | provinsi/kab/kec | Sudah meninggalkan MODIS; seri patah |

**Kesimpulan:** celah yang dibidik tantangan ini nyata. Belum ada yang menawarkan (a) + (d) **beserta ketidakpastian**. GFW membuktikan pengguna menghargai tampilan anomali musiman untuk area kustom; INPE membuktikan operator menghargai satu seri yang sebanding.

## 2. Pesaing langsung: 14+ repo publik untuk tantangan yang sama
Sebagian besar dari tim Bangladesh. **Tidak ada yang membidik Indonesia atau gambut.**

| Repo | Klaim utama |
|---|---|
| **FireCal** (paling lengkap) | Filter api vegetasi; cell-day 0,1° harian; rasio MODIS→VIIRS per area per bulan dari overlap 2012+, disusutkan ke prior global k = 2,653; 3 era sensor; substitusi saat outage; validasi leave-one-year-out; flag 2σ; peringatan dini 6 hari NRT; negara/kotak/koordinat apa pun; aplikasi offline + API |
| **IGNIS** | Rekaman 26 tahun untuk 9 wilayah, clustering api, "ML family", jalan di GIBS |
| **Icarus** | Toggle mentah vs harmonisasi, panel provenance, pipeline deterministik + test (sebagian besar masih kerangka) |
| **Kiln Watch** | Bangladesh; memisahkan tungku bata dari pembakaran lahan; rantai Aqua→S-NPP→NOAA-20→NOAA-21 dengan rentang galat; UI Bangla; README-nya sendiri menyebut aturan larangan membangun lebih awal |
| **NPC FireCalendar** | Dedup ±1 km harian; faktor MODIS→VIIRS ±0,41–0,49 |
| Lainnya | Burning Activity Calendar (prakiraan 30 hari), Cauchy's Comet (rencana quantile mapping + validasi MCD64A1), Ignis-Atlassia, FIREMAP-X, TerraFlux, Florida Fire Project, EarthFire, BD_FireOps, itssouradip34 |

> Beberapa repo mengklaim aplikasi yang sudah jadi. Itu bisa jadi masalah aturan bagi mereka (tidak boleh membangun sebelum 14 Nov), tetapi itu urusan panitia. Bagi kita, mereka tetap pesaing.

## 3. Standar minimum (semua orang akan punya)
Grid bersama · kalibrasi rasio/kuantil di periode overlap · uji leave-one-year-out · flag 2σ · gambar AOI · toggle mentah/harmonisasi · ekspor CSV.

**Kalau KalenderApi hanya punya ini, tidak akan menonjol.**

## 4. Celah yang belum terlihat di teks publik pesaing (pembeda kita)
| # | Pembeda | Kenapa juri SME peduli |
|---|---|---|
| 1 | **Normalisasi kesempatan observasi** (awan/no-data dari produk L3 MOD14A1/MYD14A1/VNP14A1) | FIRMS sendiri menyebut titik api tidak membawa info awan; minggu "sepi" bisa berarti tidak terlihat |
| 2 | **Sadar drift orbit Aqua/Terra**: jendela fit sebelum drift (Aqua ≤ Des 2022, Terra ≤ 2019) + slide diagnosa residual | Aqua melewati batas sains 13.45 MLT pada Feb 2023; NASA menyebut dampaknya pada produk api "under active investigation" |
| 3 | **Stratifikasi gambut vs non-gambut × siang/malam × pulau** | VIIRS malam paling informatif untuk gambut yang membara; rasio sensor sangat heterogen (2,8–11× dalam satu negara) |
| 4 | **Masker sumber panas statis buatan sendiri** (gunung api, flare, smelter seperti Weda Bay) yang konsisten sepanjang waktu | ±13% deteksi VIIRS Indonesia bukan biomassa; field `type` FIRMS berubah antarversi (piksel yang sama bertipe 0 di 2015, 2 di 2022) |
| 5 | **Rantai kalibrasi S-NPP → NOAA-20 → NOAA-21** sebelum S-NPP berhenti | Langsung relevan dengan tantangan: rekaman harus bertahan setelah 2 Nov 2026 dan setelah MODIS pensiun |
| 6 | **Validasi independen**: luas terbakar SiPongi (Landsat), MCD64A1/VNP64A1, tahun ekstrem (2015, 2019, 2023) | Pesaing memvalidasi satelit terhadap satelit; hanya satu repo konsep yang merencanakan burned area |
| 7 | **Validasi spatial-block** (leave-one-province-out) + interval prediksi yang diuji cakupannya | Validasi acak menggelembungkan akurasi (Ploton 2020); juri SME mencari kebocoran data |
| 8 | **Mode "seri referensi" ala INPE** (seri setara-Aqua) di samping indeks harmonisasi multi-sensor | Melindungi kita jika penulis tantangan ternyata AEB/INPE |
| 9 | **Pengguna Indonesia yang konkret + keputusan *siaga darurat*** | Penghargaan *Local Impact* historis jatuh ke aksesibilitas untuk pengguna lokal |

**Kalimat pembeda (ucapkan keras-keras):**
> *"Observation-normalized, drift-aware, uncertainty-propagated harmonization that survives the S-NPP and MODIS shutdowns, validated against independent burned area, with an Indonesian peat case study and an INPE-compatible reference series."*

## 5. Kesalahan yang dihukum juri SME (hindari)
- Menyebut titik panas sebagai "jumlah kebakaran" atau "luas terbakar".
- Mengabaikan awan dan observasi yang hilang.
- Satu faktor konversi global ("dikali 5").
- Klaim ML tanpa validasi, atau validasi yang bocor lintas ruang/waktu.
- Baseline anomali yang melintasi pergantian sensor tanpa harmonisasi.
