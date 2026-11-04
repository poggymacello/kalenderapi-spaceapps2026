# 13 · Paket rekrut tim KalenderApi (NASA Space Apps 2026, Bandung)
Disusun Rabu 28 Okt 2026 malam. Menggantikan pesan rekrut di `11` §4.1 (tenggat lama 26–27 Okt sudah lewat dan tim belum ada). Semua pesan **dikirim sendiri oleh Poggy**; agen tidak mengirim apa pun.

## 0. Putuskan dulu sebelum mengirim (5 menit)
1. **Apakah kamu pasti di Bandung Sab 14 – Min 15 Nov?** Master v14 mencatat EAGxBerlin (keputusan ≤ Jum 6 Nov) bentrok dengan tanggal ini. Orang yang kamu ajak akan mengosongkan akhir pekannya. Kalau jawabannya "tergantung EAGxBerlin", tulis itu di pesan atau tunda rekrut. Rekomendasi: Space Apps diprioritaskan, karena tim lokal sudah bergantung padamu.
2. **Ari ikut atau tidak?** Profil (`FORMULIR\00_PROFIL_POGGY_ARI.md` §2) mencatat Ari belum tercantum di Space Apps. Ari kuat sebagai pembicara dan operator demo (juru bicara SIGAP). Tanyakan langsung; kalau ikut, Ari mengisi peran **E (cerita + pitch lokal)**, bukan menggantikan A atau D.
3. **Ukuran target:** 4 orang (kamu + A + D + C). Minimum yang masih layak: 3 (kamu + A + D). Maksimum aturan: 6.

## 1. Garis waktu rekrut (realistis untuk minggu ini)
| Kapan (WIB) | Langkah | Selesai kalau… |
|---|---|---|
| **Kam 29 Okt pagi** (10 menit, sebelum mengurus IRENA) | Kirim pesan §3.1 ke ≥3 grup + pesan personal §3.2 ke 3–5 orang yang kamu kenal | Pesan terkirim |
| Kam 29 – Min 1 Nov | Jawab DM yang masuk dengan 3 pertanyaan saring (§4) | Ada ≥2 kandidat per peran A dan D |
| **Sen 2 Nov** | Telepon/video 10 menit per kandidat (§4) | Pilihan per peran |
| **Sel 3 Nov** | **Kunci tim.** Kirim kesepakatan §5 di grup; tiap orang membalas "setuju" | Grup tim + 3–4 jawaban "setuju" |
| Sel 3 Nov | Space Apps Connect buka. Kalau peran A atau D masih kosong, pasang pesan §3.3 di Space Apps Connect / Find a Team | Pesan terpasang |
| **Kam 5 Nov** | Semua anggota mendaftar di spaceappschallenge.org, memilih **Local Event Bandung**; ketua membuat tim dan mengundang | Screenshot halaman tim |
| Jum 6 – Min 8 Nov | Kamu di Jakarta (Codex Hackathon). Tidak ada tugas rekrut | Tidak ada |
| Sel 10 Nov | Rapat online 45 menit (`08`, `12` §4, `15`) | Semua tahu perannya |
| Kalau **Sel 3 Nov** belum ada orang statistik | Jalankan rencana 2 orang di `08` (notebook → HTML statis, model M0) dan cari peran D saja | Keputusan tertulis di grup |

## 2. Peran dan profil yang dicari
| Kode | Peran | Wajib bisa | Sinyal bagus | Jurusan yang biasanya cocok | Prioritas |
|---|---|---|---|---|---|
| **A** | Statistik & harmonisasi | Python + pandas; regresi (GLM atau minimal regresi linear dengan diagnosa); paham validasi silang | Pernah mengerjakan proyek regresi/kalibrasi dengan data nyata; tahu bedanya error in-sample vs out-of-sample | Statistika, Matematika, Aktuaria, Informatika, Geodesi | **1 (tanpa A, MVP turun)** |
| **D** | GIS, validasi, dan cerita | Membaca peta dan batas wilayah (QGIS atau geopandas); bisa mencari dan merapikan data resmi pemerintah | Paham karhutla/gambut, kenal SiPongi atau BMKG; bisa menulis paragraf "limitations" yang jujur | Geodesi & Geomatika, Rekayasa Kehutanan, Teknik Lingkungan, PWK, Meteorologi, Oseanografi | **2** |
| **C** | Web & visualisasi | JavaScript/TypeScript; satu library grafik (ECharts, D3, Plotly); pernah deploy situs statis | Pernah membuat heatmap atau peta interaktif; peduli aksesibilitas warna | Informatika, STI, atau siapa pun yang punya portofolio web | 3 |
| **E** | Cerita, video, pitch lokal (opsional) | Bicara bahasa Inggris dengan jelas; bisa memotong video pendek | Pengalaman pitch/lomba presentasi | DKV, atau Ari kalau ikut | 4 |
| **B** | Pipeline & infrastruktur | (Poggy) | Sudah terisi | Teknik Elektro | Terisi |

**Yang tidak perlu:** pengalaman satelit atau penginderaan jauh. Rencana, data, dan metode sudah tertulis (`04`–`08`); yang dibutuhkan adalah tangan yang terampil dan bisa hadir penuh.

## 3. Pesan siap kirim
### 3.1 Grup (WhatsApp/LINE angkatan, himpunan, unit; Bahasa Indonesia, ±180 kata; diperbarui 29 Okt dengan data SiPongi dan pengalaman nyata Poggy)
```text
Cari 2–3 teman tim NASA Space Apps Challenge 2026, Local Event Bandung, Sab 14 – Min 15 Nov.

Tantangan resmi yang kami ambil: "Harmonization of MODIS and VIIRS Hot Spots". Isinya: menyambung 20+ tahun data titik api satelit NASA (MODIS dan VIIRS) jadi satu kalender aktivitas kebakaran yang konsisten, dalam bentuk web app untuk petugas kebencanaan dan pemadam. Fokus kami provinsi gambut seperti Riau dan Kalimantan Tengah. Karhutla 2023 menghanguskan 1,16 juta ha, dan 2026 sampai Juni sudah 107 ribu ha (SiPongi/Kemenhut).

Bulan ini aku baru menyambung dua sensor yang sama untuk klorofil laut Indonesia (4,45 juta pasangan piksel). Pelajarannya: sambungan mentah bisa menggandakan tren palsu. Masalah titik api ini sama persis.

Dicari:
1. Statistik/data: Python, pandas, regresi, validasi silang (paling penting)
2. GIS/lingkungan: peta, batas wilayah, isu karhutla
3. Web: JavaScript, grafik, deploy situs statis

Syarat: hadir penuh 14–15 Nov dan bersedia daftar di situs Space Apps sebelum 5 Nov. Tidak perlu pengalaman satelit. Rencana dan bahan bacaan sudah siap.

DM aku sebelum Minggu 1 Nov: nama, jurusan + angkatan, dan satu proyek data/peta/web yang pernah kamu kerjakan.
```

### 3.2 Pesan personal (ke orang yang kamu kenal, ±95 kata; 29 Okt)
```text
Halo, aku Poggy (EL 2022). Aku lagi bikin tim untuk NASA Space Apps 2026 di Bandung, 14–15 Nov. Tantangannya menyambung data titik api satelit NASA dari dua sensor jadi satu kalender kebakaran yang konsisten, buat petugas kebencanaan. Bulan ini aku baru mengerjakan hal serupa untuk klorofil laut Indonesia (MODIS ke VIIRS, 4,45 juta pasangan piksel), jadi aku tahu jebakannya.

Aku butuh satu orang yang nyaman dengan regresi dan validasi silang di Python, dan aku kepikiran kamu. Rencana dan bahan sudah aku siapkan; kodenya baru boleh dibuat saat acara. Mau ngobrol 10 menit Senin 2 Nov?
```
Ganti kalimat kedua paragraf kedua sesuai peran: "…yang biasa pakai QGIS atau geopandas dan paham isu karhutla" (D) atau "…yang biasa bikin grafik interaktif dan deploy situs statis" (C).

### 3.3 Space Apps Connect / Find a Team (English, mulai 3 Nov, ±110 kata; 29 Okt)
```text
Team KalenderApi (Local Event: Bandung, Indonesia) is looking for 1–2 teammates for "Harmonization of MODIS and VIIRS Hot Spots".

We will harmonize MODIS and VIIRS active fire hotspots into one burning activity calendar, with uncertainty, for fire-prone peat provinces in Indonesia, and serve it as a web app for disaster agencies and firefighters.

Looking for:
- Statistics/data: Python, regression, cross-validation
- GIS: maps, boundaries, Indonesian fire context

You must be registered for the Bandung Local Event and able to attend both days, 14–15 November. No satellite experience needed. Message Poggy (ITB Electrical Engineering). In October he bridged MODIS and VIIRS chlorophyll over Indonesian seas (4.45 million matchups), so the method traps are already mapped.
```

### 3.4 Tambahan untuk email Local Lead (`11` §2), kalau email itu belum terkirim
Tambahkan satu pertanyaan sebelum penutup:
> 8. **Team matching:** do you help individual participants at the Bandung event find a team? We are looking for one teammate with a statistics background.

## 4. Saring kandidat (tanpa mengerjakan tantangan)
Penyaringan **tidak boleh** berupa tugas yang menyentuh data atau desain KalenderApi (aturan FAQ). Pakai pertanyaan umum.

**Tiga pertanyaan lewat DM (semua peran):**
1. Proyek data/peta/web apa yang pernah kamu kerjakan sendiri? Satu kalimat: datanya apa, kamu mengerjakan bagian apa, hasilnya apa.
2. Bisa hadir penuh Sab 14 Nov pagi sampai Min 15 Nov malam? Ada acara lain di tanggal itu?
3. Sudah pernah ikut tim lain di Space Apps 2026? (Aturan: satu orang hanya boleh di satu tim.)

**Telepon 10 menit (satu pertanyaan konsep per peran, bukan soal karhutla):**
| Peran | Pertanyaan | Jawaban yang baik menyebut… |
|---|---|---|
| A | "Dua termometer membaca ruangan yang sama dan selalu berbeda. Bagaimana kamu menyamakan bacaannya, dan bagaimana kamu tahu caramu benar?" | Data saat keduanya membaca bersamaan; model sederhana dulu; uji di data yang tidak dipakai untuk fit; melaporkan ketidakpastian |
| D | "Kamu punya ribuan titik koordinat dan batas kabupaten. Bagaimana menghitung jumlah titik per kabupaten, dan apa yang bisa salah?" | Spatial join; sistem koordinat; titik di laut atau di garis batas; versi batas wilayah yang berbeda |
| C | "Kamu harus menampilkan 25 tahun × 12 bulan data di HP. Apa yang kamu pilih, dan bagaimana memastikan pembaca buta warna tetap bisa membacanya?" | Heatmap atau grid; palet sekuensial ramah buta warna; legenda angka; data kecil (JSON) supaya cepat |

Pilih orang yang menjawab dengan **langkah dan cara mengecek**, bukan yang paling banyak menyebut istilah.

## 5. Kesepakatan tim (kirim di grup saat mengunci, Sel 3 Nov)
```text
Kesepakatan Tim KalenderApi, NASA Space Apps 2026 Bandung
1. Hadir penuh Sab 14 Nov 09.00 sampai submit Min 15 Nov (target 20.00). Kalau ada halangan, kabari sebelum Sel 10 Nov.
2. Daftar di spaceappschallenge.org, pilih Local Event Bandung, dan terima undangan tim paling lambat Kam 5 Nov.
3. Sebelum 14 Nov 09.00 kita TIDAK membuat kode, notebook, desain UI, atau slide untuk proyek ini (aturan resmi). Yang boleh: membaca file rencana, membuat akun, latihan alat di data lain.
4. Satu orang hanya di satu tim Space Apps 2026.
5. Peran: A statistik & harmonisasi · B pipeline & infrastruktur (Poggy) · C web & visualisasi · D GIS, validasi & cerita · E pitch & video (opsional). Nama per peran ditulis di deskripsi grup dan tidak diubah tanpa persetujuan semua.
6. Semua anggota dicantumkan di halaman Project. Penggunaan alat SI dicatat di docs/ai_use.md dan dijelaskan di submission (aturan resmi).
7. Kunci API (FIRMS MAP_KEY, dll.) disimpan masing-masing, tidak ditempel di grup.
Balas "setuju" kalau oke.
```
Teks ini sudah final; nama per peran cukup ditulis di deskripsi grup.

## 6. Bahan baca untuk anggota baru (urut, ±60 menit)
1. `12` (statement resmi vs rencana) · 2. `04` (konsep) · 3. `08` (rencana 39 jam, bagian peran dan MVP) · 4. bagian per peran: A → `05`; D → `02` dan `14`; C → `06`; E → `09`.
Bagikan sebagai berkas baca saja. Jangan membuat repo proyek sebelum 14 Nov.
