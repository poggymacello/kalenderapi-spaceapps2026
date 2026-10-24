# JURI_90 — Skor KalenderApi (NASA Space Apps 2026, Local Event Bandung)
Dinilai 23–24 Okt 2026 dengan protokol `03-MEGA-PROMPT-JURI-90.md`. **Yang dinilai adalah rencana** (01–11). Kode, data olahan, slide, dan video dibuat 14–15 Nov. Pernyataan tantangan lengkap baru terbit 28 Okt, jadi rencana dibuat supaya bisa beradaptasi (`04` §7).

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
| **Tim belum direkrut** (skor mengandaikan 4–5 orang, termasuk satu orang statistik) | Semua kriteria; tanpa orang statistik, M2 turun ke M0 | Poggy | 24–27 Okt |
| Wawancara praktisi BPBD/Manggala Agni | Impact J2/J3 +1 | D atau Poggy | 2–5 Nov |
| Isi statement 28 Okt + keputusan matriks | Relevance | Poggy + A | 28 Okt |
| Balasan Local Lead (format pitch, pre-download, Wi-Fi) | Risiko aturan | Local Lead | Sebelum 10 Nov |
| Angka konteks yang dulu bersumber di `riset/` | Validity J4 | Poggy + D | 9–11 Nov |
| S-NPP benar-benar berhenti 2 Nov? Status Aqua/Terra? | Hook pitch | Poggy | 3 Nov, 12 Nov |
| Pembeda Tier 3 (normalisasi observasi) atau strata gambut | Creativity +1 | A (butuh tim ≥4) | Hari-H, setelah MVP hijau |

## 8. Plafon
- **Plafon sekarang (rencana, tanpa aksi manusia): 82.** Yang membatasi: tim belum ada, belum ada suara pengguna, dan pembeda kreatif yang kuat masih berstatus stretch.
- **Plafon setelah aksi manusia** (tim 4–5 dengan orang statistik, satu wawancara praktisi yang boleh dikutip, statement dibaca dan matriks diterapkan, balasan Local Lead): **±89**. Melewati 90 butuh setidaknya satu pembeda stretch tier 1–3 (strata gambut atau normalisasi observasi) yang benar-benar selesai di hari-H.

## 9. Bukti verifikasi
- Semua edit dilakukan dengan skrip yang memeriksa setiap anchor cocok tepat satu kali (`assert`); salinan sebelum edit ada di scratchpad agen.
- Kutipan aturan diambil dari halaman FAQ dan Legal spaceappschallenge.org yang diunduh 23 Okt (teks HTML), bukan dari ringkasan pihak ketiga.
