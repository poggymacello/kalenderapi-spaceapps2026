# JURI_90 — Skor KalenderApi (NASA Space Apps 2026, Local Event Bandung)
Dinilai 23–24 Okt 2026 dengan protokol `03-MEGA-PROMPT-JURI-90.md`. **Yang dinilai adalah rencana** (01–11). Kode, data olahan, slide, dan video dibuat 14–15 Nov. Pernyataan tantangan lengkap baru terbit 28 Okt, jadi rencana dibuat supaya bisa beradaptasi (`04` §7).

## 0. Pembaruan Rabu 28 Okt 2026 malam (statement resmi terbit)
**Temuan utama:** tantangan **"Harmonization of MODIS and VIIRS Hot Spots" ada** di daftar 14 tantangan 2026, dengan statement lengkap; tidak perlu pemetaan ulang. Statement meminta persis inti rencana kita (harmonisasi lalu web app kalender), plus empat hal yang belum ada di MVP: **pilih wilayah + rentang tanggal**, **unduh analitik/CSV**, **bulan berjalan vs median historis**, dan **color ramp aksesibel**. Kredit foto statement = **CONAE (Argentina)** → penulis kemungkinan CONAE [inf], bukan AEB/INPE. Tab Resources baru terbit 13 Nov. Slug resmi `/2026/challenges/modis-and-viirs-hot-spots/` (slug di `11` lama salah). FAQ dicek ulang: larangan mulai lebih awal tidak berubah.

**Yang dikerjakan (tanpa kode):** `12` (statement vs rencana, matriks S1–S10 diputuskan, MVP baru, kosakata resmi, batas persiapan) · `13` (paket rekrut: keputusan awal, garis waktu, profil per peran, 3 pesan siap kirim, saringan tanpa mengerjakan tantangan, kesepakatan tim) · `14` (skrip wawancara 30 menit BPBD/Manggala Agni + pesan permintaan + templat ringkasan) · `15` (checklist hari-H satu halaman) · `04` §7 terisi · `08`, `01`, `09`, `11`, `CARA_KIRIM` diperbarui.

| Kriteria (bobot) | J1 | J2 | J3 | J4 | Rata-rata 24 Okt → 28 Okt |
|---|---|---|---|---|---|
| Impact (20) | 8 | 8 → 9 | 9 | 7 | 8,00 → 8,25 |
| Creativity (20) | 8 | 7 | 8 | 7 | 7,50 → 7,50 |
| Validity (20) | 9 | 8 | 8 | 8 | 8,25 → 8,25 |
| Relevance (20) | 9 | 9 | 9 → 10 | 8 → 9 | 8,75 → 9,25 |
| Presentation (20) | 9 | 8 → 9 | 9 | 8 | 8,50 → 8,75 |
| **Skor berbobot** | | | | | **82 → 84** |

- **Relevance +0,5:** setiap permintaan eksplisit statement kini punya tempat di MVP (`12` §2, §4). J4: risiko "statement meminta hal lain" (dulu ditutup dengan matriks) kini hilang karena statement sudah dibaca.
- **Impact +0,25:** J2 melihat kartu "Oct 2026 vs typical October" sebagai cara petugas memang menilai musim. Tetap tanpa suara pengguna nyata, jadi J4 tetap 7.
- **Presentation +0,25:** kosakata resmi + satu kalimat demo yang dipahami dalam 5 detik.
- **Creativity tetap:** pembeda kuat (wilayah Argentina, poligon, gambut, normalisasi observasi) masih stretch.
- **Validity tetap:** penjelasan cell-day vs jumlah hotspot menambah, tetapi validasi turun dari 3 ke 2 provinsi (aturan matriks). Netral.
- **Fatal flaw baru?** Tidak ada. Satu risiko dicatat: wawancara praktisi sebelum acara adalah area abu-abu; dimitigasi di `14` §0 (tanpa gambar, diungkap di halaman Project, tanya Local Lead).

## 1. Aturan (dibaca langsung 23 Okt malam)
| Sumber | Isi | Dampak |
|---|---|---|
| FAQ peserta 2026 | Statement terbit 28 Okt; *"Teams are not allowed to begin working on the challenges prior to the hackathon."*; tim lokal 1–6 orang, satu tantangan; panduan Submission + Judging terbit 13 Nov | Tidak ada kode, notebook, data olahan, desain UI, atau slide final sebelum 14 Nov 09.00 |
| FAQ 2026, bagian SI | Istilah resmi **"Super Intelligence (SI)"**; alat SI boleh dipakai; submission **wajib** menjelaskan penggunaannya | `08`, `09`, `10`, `01` diperbarui |
| T&C 2026 (diperbarui 7 Agu 2026) | Data/kode non-NASA wajib bebas atau berlisensi OSI dan **lisensinya didokumentasikan**; **semua** sumber disitasi (nominasi bisa dicabut); tidak boleh ada PII; video wajib karya sendiri tanpa pelanggaran hak cipta | `docs/data_licenses.md` + `docs/numbers.md` wajib (`08`); validasi cadangan NASA MCD64A1 (`04` §10); video tanpa musik berhak cipta (`09` §2) |
| Pre-download data | **Tidak dibahas eksplisit** di FAQ maupun T&C | Keputusan konservatif: tidak diunduh sebelum 14 Nov 09.00 kecuali Local Lead mengizinkan secara tertulis (email `11` §2 pertanyaan 6). Manfaatnya kecil: set MVP ±396 MB |
| Batas demo | ≤30 detik video atau ≤7 slide (panduan 2025; cek 13 Nov) | Storyboard v2 ≤65 kata, target 29,0 detik (`09` §2) |

**Bobot rubrik:** Impact · Creativity · Validity · Relevance · Presentation, masing-masing skala 1–5 (panduan 2025) → **asumsi bobot sama, 20 masing-masing**.

## 2. Panel
J1 = ilmuwan NASA FIRMS / penginderaan jauh · J2 = petugas operasi BPBD / Manggala Agni · J3 = juri global Space Apps (dampak, cerita) · J4 = skeptis (veto 80).

## 3. Skor awal → akhir (0–10)
| Kriteria (bobot) | J1 | J2 | J3 | J4 | Rata-rata |
|---|---|---|---|---|---|
| Impact (20) | 7 → 8 | 7 → 8 | 8 → 9 | 6 → 7 | 7,00 → 8,00 |
| Creativity (20) | 7 → 8 | 6 → 7 | 6 → 8 | 5 → 7 | 6,00 → 7,50 |
| Validity (20) | 8 → 9 | 7 → 8 | 7 → 8 | 6 → 8 | 7,00 → 8,25 |
| Relevance (20) | 7 → 9 | 7 → 9 | 8 → 9 | 6 → 8 | 7,00 → 8,75 |
| Presentation (20) | 7 → 9 | 6 → 8 | 7 → 9 | 6 → 8 | 6,50 → 8,50 |
| **Skor berbobot** | | | | | **67 → 82** |

Alasan singkat (akhir) dan "apa yang membuat 10/10":
- **Impact.** J2 menghargai tiga kalimat keputusan per wilayah (`04` §8) dan dekadal VIIRS untuk onset. *10/10 kalau* ada kutipan praktisi BPBD/Manggala Agni yang mengatakan kalender ini akan dipakai untuk penetapan siaga. Itu hanya bisa didapat lewat wawancara (aksi manusia).
- **Creativity.** 14+ repo publik menyasar tantangan yang sama, dan "standar minimum" (`03` §3) sudah dimiliki semua orang. Pembeda yang ada di MVP (jendela fit bebas drift, ketidakpastian di sel kalender, kalimat keputusan) baru setingkat "perbaikan yang cerdas". *10/10 kalau* normalisasi kesempatan observasi (Tier 3 GEE) atau strata gambut benar-benar selesai, dan itu bergantung pada ukuran tim.
- **Validity.** J1: metodologi kuat (LOYO tahunan, baseline naif, cakupan interval, sensitivitas onset, burned area NASA sebagai cek cadangan). *10/10 kalau* spatial-block dan holdout tahun ekstrem juga selesai.
- **Relevance.** Matriks adaptasi S1–S8 menutup risiko terbesar: statement yang meminta hal lain.
- **Presentation.** Video satu pesan per shot dengan angka hanya dari buku besar; deck dengan judul-pesan. *10/10 kalau* diuji pada orang luar ("uji 5 detik") dan durasinya terbukti ≤30,0 detik.

## 4. Fatal flaw (J4) dan penutupnya
| # | Fatal flaw | Status | Cara menutup |
|---|---|---|---|
| F1 | Angka "20.928 vs 666" (belum diverifikasi) menjadi pembuka video; selisihnya juga akibat filter kepercayaan, bukan sensor | **Ditutup** | Dikeluarkan dari video; di pitch hanya kalau terverifikasi dan dijelaskan sebagai efek filter (`09` §2, §6) |
| F2 | Tidak ada dokumentasi lisensi data non-NASA, padahal T&C 2026 mewajibkannya | **Ditutup** (rencana) | `docs/data_licenses.md` wajib di MVP; validasi cadangan MCD64A1 (`08`, `04` §10) |
| F3 | Deklarasi penggunaan alat memakai istilah lama; FAQ 2026 mewajibkan deskripsi penggunaan SI | **Ditutup** | Istilah SI di `01`, `08`, `09`, `10` |
| F4 | Banyak angka dirujuk ke folder `riset/` yang **tidak ada** di folder ini | **Sebagian** | Aturan buku besar angka (`09` §7): angka tanpa URL tidak boleh tampil. Sumber angka konteks di `02` tetap perlu dilacak ulang (aksi manusia) |
| F5 | Rencana tidak bisa beradaptasi kalau statement meminta satuan/resolusi/AOI lain | **Ditutup** | Matriks adaptasi `04` §7 + tugas 28 Okt di `11` |

F4 sebagian terbuka, tetapi tidak fatal untuk produk, karena angka yang tidak terlacak tidak akan tampil. Veto J4 tidak berlaku.

## 5. Verifikasi data (header HTTP saja, 23 Okt malam)
- **FIRMS berkas negara Indonesia:** 48/48 berkas 200 (MODIS 2000–2025: 119,5 MB · S-NPP 2012–2025: 277,9 MB · NOAA-20 2018–2025: 106,1 MB; total ±503 MB). NOAA-21 2025 dan semua berkas 2026: 404 (memang belum ada, 2026 lewat API). Manifest: `firms_manifest_23okt2026.tsv`.
- **Pendukung:** geoBoundaries API IDN ADM1/ADM2 200 · NOAA CPC RONI.ascii.txt & oni.ascii.txt 200 (RONI JAS 2026 = 1,69) · GFW data portal 200 · FIRMS `data_availability` & `missing_data` 200 · Earthdata alert S-NPP 200 · halaman tantangan Space Apps 200 (isi masih judul).
- **Gagal dari koneksi agen:** SiPongi (kedua domain) timeout, aqua.nasa.gov timeout, Smithsonian GVP 403. Manusia perlu membukanya dari browser.
- **DOI:** 7 DOI produk resolve ke katalog Earthdata; **MCD14ML → halaman 404** (kutip juga MCD14DL NRT + Giglio 2016).

## 6. Daftar perubahan (23 Okt malam)
- `04`: §7 matriks adaptasi S1–S8; §8 tiga kalimat keputusan per wilayah dengan definisi onset + uji sensitivitas; §9 aha satu kalimat; §10 validasi tanpa risiko lisensi (MCD64A1).
- `07`: ukuran terukur (manifest); cek DOI; sumber yang tidak terjangkau; §7 runbook akuisisi Jam 0 dengan keputusan aturan.
- `08`: kickoff memakai matriks adaptasi + runbook; rencana 2 orang; MCD64A1 sebagai cadangan validasi; `data_licenses.md` + `numbers.md`; istilah SI; urutan produksi video dengan cek durasi.
- `09`: keputusan demo = video; storyboard v2 enam shot (≤65 kata); deck 7 slide dengan judul-pesan dan peta kriteria; hook cadangan; buku besar angka; perbaikan rujukan `riset/`.
- `10`: Q24 istilah SI; Q26–Q36 baru.
- `11`: ringkasan aturan resmi; rekrut tim jadi tugas paling mendesak (24 Okt); matriks diisi 28 Okt; cek S-NPP 3 Nov; email pertanyaan 6–7; baris verifikasi #9–#12.
- `01`: catatan istilah SI.

## 7. Sisa gap dan siapa yang menutup
| Gap | Dampak | Pemilik | Kapan |
|---|---|---|---|
| **Tim belum direkrut** (per 28 Okt masih 0 orang; pesan belum terkirim) | Semua kriteria; tanpa orang statistik, M2 turun ke M0 | Poggy | Kirim Kam 29 Okt, kunci Sel 3 Nov, daftar ≤ Kam 5 Nov (`13`) |
| Bentrok EAGxBerlin (keputusan ≤ 6 Nov) dengan 14–15 Nov | Kalau Poggy absen, tim tanpa ketua | Poggy | Putuskan sebelum mengirim pesan rekrut |
| Wawancara praktisi BPBD/Manggala Agni | Impact J2/J3 +1, J4 +1 | Poggy / D | Pesan Kam 29 Okt; wawancara 3–5 atau 9–11 Nov (`14`) |
| ~~Isi statement 28 Okt + keputusan matriks~~ | Relevance | ✅ Agen 28 Okt (`12`) | Poggy menyetujui |
| Tab Resources + panduan Submission/Judging | Relevance, risiko aturan | Poggy + D | Jum 13 Nov |
| Balasan Local Lead (format pitch, pre-download, Wi-Fi) | Risiko aturan | Local Lead | Sebelum 10 Nov |
| Angka konteks yang dulu bersumber di `riset/` | Validity J4 | Poggy + D | 9–11 Nov |
| S-NPP benar-benar berhenti 2 Nov? Status Aqua/Terra? | Hook pitch | Poggy | 3 Nov, 12 Nov |
| Pembeda stretch tier 1: wilayah Argentina (penulis kemungkinan CONAE) atau poligon; tier 3 normalisasi observasi | Creativity +1 | A, C (butuh tim ≥4) | Hari-H, setelah MVP hijau |

## 8. Plafon
- **Plafon sekarang (rencana, tanpa aksi manusia): 84** (28 Okt; sebelumnya 82). Yang membatasi: tim belum ada, belum ada suara pengguna, dan pembeda kreatif yang kuat masih berstatus stretch.
- **Plafon setelah aksi manusia** (tim ≥4 dengan orang statistik, satu wawancara praktisi yang boleh dikutip, balasan Local Lead, tab Resources dibaca 13 Nov): **±90**. Statement sudah dibaca dan diterapkan (bukan lagi aksi manusia). Melewati 90 dengan pasti butuh satu pembeda stretch tier 1 yang benar-benar selesai di hari-H (wilayah Argentina atau poligon). Tanpa kode, 84 adalah batas jujur.

## 9. Bukti verifikasi
- Semua edit dilakukan dengan skrip yang memeriksa setiap anchor cocok tepat satu kali (`assert`); salinan sebelum edit ada di scratchpad agen.
- Kutipan aturan diambil dari halaman FAQ dan Legal spaceappschallenge.org yang diunduh 23 Okt (teks HTML), bukan dari ringkasan pihak ketiga.

---

## 10. Fase 2 anti-generik (Kam 29 Okt 2026)
Sumber: `FORMULIR/00_BANK_CERITA_DAN_DATA_POGGY.md` §5 (karhutla) + `INDIVIDU/OCEANS2027-StudentPoster/01_ABSTRAK.md` (pekerjaan Poggy sendiri). Arsip: `_arsip_29okt\`. Tanpa kode.

| Bagian | Sebelum | Sesudah |
|---|---|---|
| Hook pitch lokal (`09` §6) | "Indonesia's fire record just lost a satellite…" (bergantung cek 3 Nov) | Cerita Poggy: 4,45 juta pasangan piksel MODIS–VIIRS klorofil laut Indonesia; sambungan mentah ±menggandakan tren penurunan di paparan. Hook lama jadi cadangan |
| Problem halaman Project (`09` §4.2) | kerangka + catatan "tulis ulang dari 02 §8" | 117 kata siap tempel: 1.161.193 ha (2023), 376.805 (2024), 359.619 (2025), 107.465 ha Jan–Jun 2026, dua URL |
| Team halaman Project (`09` §4.8b, baru) | tidak ada | 102 kata: Medan, tim olimpiade astronomi SMA Unggul Del (IAAC 2021), dua pelajaran dari OCEANS (drift VIIRS R2018 setelah 2016; "alerts live in the tails"), pernyataan tidak ada kode yang dipakai ulang |
| Paket rekrut (`13` §3.1–3.3) | pesan umum "cari teman tim" | data SiPongi + pengalaman sensor yang sama; 179 / 95 / 114 kata |
| Konteks (`02` §8) | 202.004 ha s.d. Juli (Kompas) | ditambah angka bank + catatan periode berbeda; larangan angka titik panas tahunan tanpa URL |

| Juri | Sebelum | Sesudah | Catatan |
|---|---|---|---|
| J1 NASA/ilmuwan | 84 | 85 | tim menunjukkan pengalaman nyata dengan pasangan sensor yang sama dan drift |
| J2 BPBD | 84 | 84,5 | problem kini berangka resmi per tahun |
| J3 | 84 | 84 | tim tetap belum ada |
| J4 skeptis | 84 | 84,5 | angka bersumber; batas: dua URL sekunder |
| **Rata-rata J1–J4** | **84** | **±84,5** | plafon tanpa kode tetap |
| **J5 mentor** | **±20** | **±83** | hook, problem, tim, rekrut kini milik Poggy. Belum 85: belum ada momen karhutla pribadi (asap di Medan?) dan anggota tim belum ada |
| **Rata-rata J1–J5** | — | **±84** | |

### Pertanyaan untuk Poggy (menaikkan skor)
1. **Asap:** pernah mengalami asap karhutla saat di Medan atau di asrama SMA Unggul Del (tahun berapa, apa yang terjadi: sekolah libur, masker)? → satu kalimat pembuka di Team dan hook pitch; J5 ±83 → ±88.
2. **OCEANS:** angka 4,45 juta matchup dan tren −18,5 vs −8,5 %/dekade boleh diucapkan sebelum abstraknya dikirim? Kapan persisnya dikerjakan (Okt 2026)? → kalimat hook dan Team.
3. **Tim olimpiade astronomi:** satu momen pengamatan teleskop yang kamu ingat → mengganti kalimat IAAC di Team menjadi cerita.
4. **Ari ikut atau tidak?** → paragraf Team dan peran E di `13`.
5. **EAGxBerlin vs Space Apps** sudah diputuskan? → kalimat "hadir penuh" di pesan rekrut.
