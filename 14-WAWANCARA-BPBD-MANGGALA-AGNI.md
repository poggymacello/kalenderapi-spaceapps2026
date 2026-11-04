# 14 · Skrip wawancara BPBD / Manggala Agni (30 menit)
Disusun Rabu 28 Okt 2026. Menggantikan panduan singkat di `11` §4.2–4.3 dan diselaraskan dengan statement resmi (`12`). Tujuannya satu: mendapat **satu kutipan praktisi yang boleh dipakai** dan **satu keputusan nyata** yang dibantu kalender. Ini satu-satunya jalan menaikkan Impact J2/J3 ke 9–10 (`JURI_90/SKOR.md`).

## 0. Batas aturan (baca sebelum menghubungi siapa pun)
- FAQ 2026 melarang tim mulai mengerjakan tantangan sebelum 14 Nov. Wawancara ini diperlakukan sebagai **belajar tentang pekerjaan pengguna**, bukan menguji produk.
- **Jangan menunjukkan** sketsa, wireframe, mockup, grafik, atau angka hasil olahan. Semua pertanyaan diucapkan.
- Catatan wawancara adalah catatan mentah, bukan spesifikasi fitur.
- Di halaman Project nanti, tulis terbuka: *"Before the event, we spoke with one fire-management practitioner about how alert levels are decided. No designs or code were shown."*
- Kalau Local Lead menjawab bahwa wawancara tidak boleh, batalkan dan ganti dengan membaca dokumen publik saja.

## 1. Siapa yang dihubungi (urut peluang)
| Prioritas | Target | Kenapa | Jalur resmi |
|---|---|---|---|
| 1 | **BPBD Provinsi Riau** atau **BPBD Kalimantan Tengah** (bidang kedaruratan / pencegahan) | Dua provinsi preset MVP (`12` §3); mereka yang mengusulkan status siaga | Situs resmi atau akun media sosial resmi BPBD provinsi; email dinas yang tercantum di sana |
| 2 | **Daops Manggala Agni** di Riau atau Kalteng | "Firefighters" dalam bahasa statement; memakai data hotspot untuk patroli | Kanal resmi Kementerian Kehutanan / Daops setempat |
| 3 | Stasiun klimatologi **BMKG** di provinsi tersebut | Menerbitkan peringatan kemudahan terbakar; paham musim | Kanal resmi BMKG provinsi |
| 4 (cadangan) | Dosen kehutanan, geodesi, atau meteorologi yang pernah bekerja dengan BPBD | Lebih mudah dijangkau; kutipannya menguatkan J1, bukan J2 | Lewat dosen wali atau kenalan di ITB |

Jangan memakai nomor pribadi yang didapat dari sumber tidak jelas. Kalau kontak datang lewat kenalan, minta kenalan itu yang memperkenalkan dulu.

## 2. Pesan permintaan
### 2.1 Email / pesan resmi (Bahasa Indonesia, 116 kata)
```text
Yth. Bapak/Ibu,

Saya Poggy Macello Gultom, mahasiswa Teknik Elektro ITB. Bersama tim, saya akan mengikuti NASA Space Apps Challenge 2026 pada 14–15 November dengan tantangan resmi tentang kalender aktivitas kebakaran dari data titik panas satelit NASA (MODIS dan VIIRS).

Sebelum acara, kami ingin belajar langsung dari praktisi: bagaimana BPBD/Manggala Agni memutuskan kapan mulai siaga, dan data titik panas apa yang dipakai sehari-hari. Apakah Bapak/Ibu berkenan berbincang sekitar 30 menit lewat telepon atau video call, antara Selasa 3 sampai Kamis 5 November atau Senin 9 sampai Rabu 11 November?

Kami tidak akan mengutip nama atau jabatan tanpa izin dan tidak merekam tanpa persetujuan. Ini kegiatan mahasiswa nonkomersial.

Hormat saya,
Poggy Macello Gultom
Teknik Elektro, Institut Teknologi Bandung
```

### 2.2 Versi pendek (DM resmi media sosial, 54 kata)
```text
Selamat siang. Saya Poggy, mahasiswa Teknik Elektro ITB. Tim kami ikut NASA Space Apps 2026 (14–15 Nov) dengan tantangan kalender kebakaran dari data titik panas satelit NASA. Boleh kami minta waktu 30 menit untuk belajar dari petugas tentang cara menentukan masa siaga karhutla? Ke alamat email mana sebaiknya kami kirim permohonan resminya? Terima kasih.
```

### 2.3 Tindak lanjut (kalau 3 hari tidak ada balasan, 28 kata)
```text
Selamat siang, Bapak/Ibu. Menindaklanjuti permohonan kami beberapa hari lalu: kalau 30 menit terlalu panjang, 15 menit lewat telepon sudah sangat membantu. Kami menyesuaikan dengan waktu Bapak/Ibu. Terima kasih.
```

**Jadwal kirim:** Kam 29 Okt (bersamaan dengan pesan rekrut) ke 3 target prioritas 1–2. Tindak lanjut Min 1 Nov. Kalau sampai Rab 4 Nov belum ada jadwal, hubungi target prioritas 4.

## 3. Skrip wawancara (30 menit)
Pewawancara: Poggy (atau D). Pencatat: anggota kedua kalau ada. Bahasa Indonesia.

### Pembuka (2 menit, ucapkan apa adanya)
> Terima kasih atas waktunya, Bapak/Ibu. Kami tim mahasiswa ITB yang akan ikut NASA Space Apps. Kami ingin memahami cara kerja Bapak/Ibu, bukan menjual atau menguji apa pun. Boleh saya mencatat? Kalau ada yang ingin kami kutip, kami akan bertanya dulu: boleh dengan nama dan jabatan, jabatan saja, atau anonim. Wawancara ini tidak direkam kecuali Bapak/Ibu mengizinkan.

Catat jawabannya: izin mencatat (ya/tidak), izin rekam (ya/tidak), bentuk kutipan (nama+jabatan / jabatan / anonim / tidak boleh).

### Blok A · Keputusan siaga (9 menit)
1. Musim 2026 ini, kapan status siaga darurat karhutla ditetapkan di wilayah Bapak/Ibu? Siapa yang mengusulkan dan siapa yang memutuskan?
2. Apa yang paling menentukan waktu penetapannya? *(Biarkan menjawab dulu. Baru kalau perlu, sebut: jumlah titik panas, hari tanpa hujan, peringatan BMKG, El Niño, kejadian di lapangan.)*
3. Pernahkah status ditetapkan **terlalu lambat** atau **terlalu cepat**? Apa akibatnya?
4. Kalau Bapak/Ibu bisa tahu "biasanya musim api di kabupaten ini mulai bulan X", keputusan apa yang akan berubah? *(Dengarkan: anggaran, patroli, posko, helikopter, modifikasi cuaca.)*

### Blok B · Data dan kepercayaan (8 menit)
5. Data titik panas dari mana yang dipakai sehari-hari? *(SiPongi, BMKG, BRIN, FIRMS, aplikasi lain.)*
6. Pernah menemui angka titik panas yang berbeda jauh antarsumber? Ceritakan satu kejadiannya. Bagaimana menjelaskannya ke pimpinan?
7. Tingkat kepercayaan (confidence) apa yang dipakai: semua, nominal, atau tinggi saja?
8. Apa yang membuat Bapak/Ibu **tidak percaya** pada sebuah angka atau peta?

### Blok C · Cara melihat sejarah api (7 menit; semua lisan, tanpa gambar)
9. Saat menilai musim tahun ini, apakah Bapak/Ibu membandingkannya dengan tahun-tahun sebelumnya? Dengan cara apa sekarang?
10. Kalau ada angka "bulan ini dibandingkan bulan yang sama di tahun-tahun biasa", apakah itu dipakai, dan oleh siapa?
11. Wilayah apa yang paling sering dipakai untuk melihat data: provinsi, kabupaten, kecamatan, KHG, atau titik koordinat posko?
12. Kalau data bisa diunduh, dalam bentuk apa: tabel Excel/CSV, gambar untuk laporan, atau ringkasan satu halaman? Untuk laporan ke siapa?

### Blok D · Kalimat yang bisa dikutip (3 menit)
13. Dalam satu kalimat: apa yang paling sulit dari memakai data titik panas untuk menentukan masa siaga?
14. Kalau ada rekaman kebakaran 20 tahun yang konsisten antarsatelit, apa satu hal yang akan Bapak/Ibu lakukan dengannya?

Setelah jawaban 13 atau 14, tanyakan: *"Boleh kalimat itu kami kutip? Dengan nama dan jabatan, jabatan saja, atau anonim?"*

### Penutup (1 menit)
> Terima kasih. Setelah acara 15 November, bolehkah kami mengirimkan hasilnya untuk mendapat masukan?

## 4. Aturan selama wawancara
- Jangan mengarahkan jawaban ("Pasti butuh kalender, kan?"). Tanyakan kejadian nyata, bukan pendapat tentang ide kita.
- Jangan menjanjikan bahwa aplikasi akan dipakai atau dirawat setelah lomba.
- Jangan menulis nomor HP, email pribadi, atau alamat narasumber di folder ini.
- Kalau narasumber menyebut angka, catat sumbernya. Angka tanpa sumber tidak masuk `numbers.md`.

## 5. Templat ringkasan (tulis ≤24 jam setelah wawancara, maksimal 1 halaman)
Simpan sebagai `wawancara-1.md` di folder ini (catatan riset, bukan bagian repo).
| Bagian | Isi |
|---|---|
| Tanggal, durasi, kanal | |
| Narasumber | Jabatan dan instansi saja; nama hanya kalau izin "nama+jabatan" |
| Izin | Catat · rekam · bentuk kutipan |
| Keputusan nyata yang dibantu kalender | Satu kalimat (dari jawaban 4 atau 14) |
| Kapan siaga 2026 ditetapkan, dan apakah terlambat | |
| Sumber data yang dipakai + masalah antarsumber | |
| Yang membuat tidak percaya | |
| Wilayah dan format unduhan yang diminta | (jawaban 11–12; masukan untuk keputusan S3 dan S9 di `12`) |
| Kutipan yang boleh dipakai | Kata per kata, dalam bahasa aslinya + terjemahan Inggris |
| Yang mengubah rencana kita | Maksimal 3 butir; tulis juga yang **tidak** diubah |

**Dipakai di:** `04` §2 (pengguna), `10` Q19 (jawaban "who will use this"), slide 2 deck lokal, dan satu kalimat di halaman Project. Kutipan berbahasa Indonesia diterjemahkan ke Inggris dengan catatan "translated by the team".
