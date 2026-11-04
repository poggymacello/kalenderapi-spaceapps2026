# 09 — Pitch, Demo 30 Detik, dan Halaman Proyek
> **Diperbarui 23 Okt 2026:** isi disesuaikan dengan MVP baru di `08` (3 provinsi, M2 vs M1, LOYO, cek SiPongi, pita). Butir bertanda *(stretch)* hanya ditampilkan kalau benar-benar selesai.
>
> **Tambahan 23 Okt malam (JURI_90):** storyboard video v2 per shot (≤65 kata, angka hanya dari `numbers.md`) · deck 7 slide dengan judul-pesan dan peta kriteria · hook cadangan · istilah SI dan tabel lisensi di halaman Project.

Catatan bicara dan kerangka ini adalah **rencana**. Slide, video, dan teks halaman proyek dibuat saat hackathon (blok Min 12.00–16.00 di 08). Batas demo dicek ulang di panduan 13 Nov.

## 1. Yang dinilai juri, urut pengaruhnya
1. **Halaman Project:** sumber utama penilaian global ("the majority of judges' evaluation").
2. **Demo:** video ≤30 detik **atau** ≤7 slide termasuk judul. Melebihi batas berisiko **tidak eligible**.
3. **Pitch lokal Bandung:** formatnya ditanyakan ke Local Lead. Tim ITB 2025 menang *Best Pitch*, jadi penyampaian dihargai.

## 2. Video 30 detik ("30 Seconds of Glory"): storyboard v2 (23 Okt malam)
**Keputusan:** demo yang di-submit = **video 30 detik**. Alasannya, demo sering menjadi bagian pertama yang dilihat juri, dan video tidak bergantung pada siapa yang membacanya. Deck 7 slide (§3) dipakai untuk pitch lokal Bandung. Tinjau ulang setelah panduan 13 Nov terbit.

**Aturan produksi:** satu pesan per shot · narasi **≤65 kata** (±2,2 kata/detik, cukup santai untuk penutur non-native) · subtitle Inggris dibakar ke video · setiap angka di layar harus ada di `docs/numbers.md` · tanpa logo NASA (aturan merek) · tanpa musik berhak cipta (T&C video: konten tidak boleh melanggar hak cipta; kalau pakai musik, pilih yang berlisensi bebas dan catat lisensinya) · durasi akhir dicek `ffprobe` **≤30,0 detik**, target 29,0.

| Shot | Detik | Visual | Teks di layar (≤7 kata) | Narasi EN | Kriteria |
|---|---|---|---|---|---|
| S1 | 0,0–3,5 | Peta Indonesia gelap, titik VIIRS satu musim menyala (dari data kita) + baris kecil "KalenderApi · Team [nama] · Bandung" | "Harmonization of MODIS and VIIRS Hot Spots" | "Team [name], Bandung, on MODIS–VIIRS harmonization." (7 kata) | Presentation (tim + tantangan) |
| S2 | 3,5–10,0 | Grafik bulanan mentah Riau 2002–2026: garis MODIS lalu VIIRS; lompatan 2012 disorot | "2012: [r]× more hotspots. Same fires?" | "In 2012 a sharper satellite joined, and Indonesia's hotspot counts jumped [r]-fold. The fires didn't." (15) | Relevance, Impact |
| S3 | 10,0–16,5 | Animasi toggle mentah → harmonisasi; pita 90% muncul, lompatan hilang | "MODIS → VIIRS units, with uncertainty" | "KalenderApi maps twenty-three years of NASA MODIS onto VIIRS units, with uncertainty bands." (13) | Validity, Relevance (data NASA) |
| S4 | 16,5–21,5 | Satu angka besar dari tabel skill (bukan tabelnya) | "[x]% lower error on unseen years" | "On held-out years it beats a single conversion factor by [x] percent." (12) | Validity |
| S5 | 21,5–27,0 | Heatmap kalender Riau tahun × bulan; kolom onset dan puncak disorot; kalimat onset dari `04` §8 | "Riau: season usually starts [bulan]" | "The result is a burning calendar for any area." (9) | Impact, Creativity |
| S6 | 27,0–29,5 | Kartu akhir: tagline + URL proyek + "Data: NASA FIRMS (LANCE)" | "Act before your fire season starts" | "So districts can act before their fire season starts." (9) | Impact |

Total narasi ±65 kata. **Yang sengaja dikeluarkan dari video:** "20.928 vs 666" (belum diverifikasi, dan selisihnya akibat filter kepercayaan, bukan sensor, sehingga mengaburkan pesan utama); daftar outage; nama model. Kalimat "Suomi-NPP went dark on 2 November" hanya dipakai di slide 3 dan pitch lokal, **setelah** dicek 3 Nov bahwa data benar-benar berhenti.

**Kalau angka [r] atau [x] tidak mendukung cerita** (misalnya M2 tidak mengalahkan M1): S4 diganti "Tested on years it never saw" + angka cakupan interval 90% yang terukur. Jangan mengarang keunggulan.

## 3. Tujuh slide (deck pitch lokal; slide judul dihitung)
Setiap judul slide berupa **kalimat lengkap** yang menyampaikan pesannya; badan slide ≤25 kata; satu visual per slide.

| # | Judul slide (pesan) | Visual | Bukti / angka (sumber) | Kriteria utama |
|---|---|---|---|---|
| 1 | "One fire record, every satellite, any place." | Judul, nama tim, nama tantangan, Bandung, kalender Riau kecil, QR ke halaman Project | — | Presentation, Relevance |
| 2 | "Indonesia's hotspot record has a 2012 cliff that isn't about fire." | Grafik mentah MODIS vs VIIRS (data kita) | Lompatan [r]× (notebook); contoh resmi: 2015→2016 turun 95% (Terra/Aqua) vs 82% (NOAA), KLHK SP.361/2017 | Impact, Relevance |
| 3 | "And the record is breaking right now." | Garis waktu: AVHRR NOAA-15/19 berhenti Jun 2025 · S-NPP berhenti 2 Nov 2026 · MODIS berakhir · El Niño kuat sampai Jan–Mar 2027 | Earthdata alert S-NPP, NOAA CPC; setiap tanggal dicek ulang 3 dan 12 Nov | Impact |
| 4 | "We harmonize fire occupancy, not pixels, on a drift-free window." | Pipeline 5 kotak: cell-day 0,1° → masker sumber statis → strata pulau × siang/malam → M2 MODIS→VIIRS (Feb 2012 – Des 2022) → pita bootstrap | `05` §2–7 | Creativity, Validity |
| 5 | "It beats a naive conversion factor on years it never saw." | Tabel skill M2 vs M1 (LOYO 11 fold) + titik ρ vs burned area | MAE, bias, τ, cakupan 90% (notebook); ρ vs SiPongi atau MCD64A1 | Validity |
| 6 | "Every district gets three sentences it can act on." | Kalender 3 provinsi + kalimat onset/puncak/El Niño (`04` §8) + skenario BPBD Riau, Feb 2027 | Notebook; Permen LHK P.9/2018 (parameter status) | Impact, Relevance |
| 7 | "What it can't see, and what comes next." | Tiga keterbatasan (titik panas ≠ api; awan/asap; gambut membara) · repo open source · satu baris penggunaan SI · langkah lanjut (rantai NOAA-20/21, provinsi lain) | `limitations.md`, `ai_use.md` | Validity, Presentation |

**Uji 5 detik:** tunjukkan tiap slide 5 detik ke orang di luar tim. Kalau dia tidak bisa mengulang pesannya, perbaiki judulnya, bukan isinya.

## 4. Halaman Project sebagai "mini-paper"
Urutan bagian (bahasa Inggris):
1. **Summary** (≤100 kata) + tautan demo, repo, video.
2. **Problem:** angka tidak sebanding + rekaman yang terputus + musim lokal. **Teks siap tempel (EN, 29 Okt, 118 kata; setiap angka masuk `numbers.md` dengan URL di bawah):**
   > Indonesia's forestry ministry counted 1,161,193 hectares burned in 2023, 376,805 in 2024 and 359,619 in 2025 (SiPongi, reported by ANTARA, 10 Feb 2026). Another 107,465 hectares burned from January to June 2026 (Kemenhut, reported by RCTI+, 19 Jul 2026). Agencies plan patrols, water bombing and emergency status around when the fire season starts in their own area. But the hotspot record they look at is two satellite records joined end to end: MODIS since 2000 and VIIRS since 2012, with different pixel sizes and detection limits. A hotspot count from 2010 and one from 2020 are not the same unit. KalenderApi puts both in VIIRS units, with uncertainty, so each area gets its own burning activity calendar.

   URL: https://en.antaranews.com/news/403742/homepage-v2.html · https://www.rctiplus.com/news/detail/berita-utama/5431984/kemenhut--107-465-hektare-hutan-dan-lahan-ludes-terbakar-sepanjang-2026 (keduanya sekunder yang mengutip SiPongi/Kemenhut; SiPongi sendiri gagal dibuka 29 Okt, cek lagi 13 Nov dan ganti ke URL primer kalau bisa).
3. **Data:** nama pendek produk, koleksi, rentang tanggal, DOI. FIRMS MCD14ML C6.1; VNP14IMG/VJ114IMG C2; geoBoundaries; GFW peat; RONI; SiPongi.
4. **Method:** diagram pipeline + prinsip (satuan acuan VIIRS: MODIS → setara-VIIRS; okupansi; bulanan; fit Feb 2012 – Des 2022 bebas drift).
5. **Validation:** tabel metrik M2 vs M1 (LOYO 11 fold, cakupan interval), cek independen vs SiPongi. Tambahkan extreme-year, spatial-block, drift test **hanya** kalau stretch-nya selesai.
6. **Uncertainty:** cara pita dibuat, arti arsiran.
7. **Limitations:** titik panas ≠ api ≠ luas; awan dan asap; gambut di bawah tanah; data uji kecil; batas bawah deteksi era MODIS.
8. **User scenario:** BPBD Riau, Februari 2027.
8b. **Team** (teks siap tempel, EN, 29 Okt; tambahkan satu kalimat per anggota setelah tim dikunci 3 Nov, isinya dari jawaban saring §4 di `13`):
   > Poggy Macello Gultom (Electrical Engineering, ITB, final year) runs the data pipeline. He grew up in Medan, North Sumatra, and was on the astronomy olympiad team at SMA Unggul Del on Lake Toba (Silver Honour, IAAC 2021). In October 2026 he worked on the same two sensors for the ocean: 4.45 million MODIS–VIIRS chlorophyll matchups over Indonesian seas. Two lessons carry over. VIIRS R2018 drifted after 2016, so we fit only on a drift-free window. And a bridge that is right on average can still get alerts wrong, because alerts live in the tails. No code from that project is reused here.
9. **Reproducibility:** repo publik, lingkungan, satu perintah untuk menjalankan ulang, provenance data.
10. **Use of Super Intelligence (SI) tools** (istilah FAQ 2026; ikuti label persis di formulir): alat, untuk apa, bagian mana. Diambil dari `docs/ai_use.md`.
11. **Data licenses:** tabel lisensi dataset non-NASA dari `docs/data_licenses.md` (wajib menurut T&C 2026).
12. **References & acknowledgements** (kalimat pengakuan FIRMS di 07 §4). T&C 2026: **semua** sumber wajib disitasi, termasuk yang open source; tanpa sitasi, nominasi bisa dicabut.

## 5. Kosakata yang dipakai juri NASA
- Pakai: *harmonized*, *uncertainties*, *independent reference*, *significance*, *out-of-sample skill*, *observation opportunity*, *orbit drift*, *continuity*.
- **Istilah dari statement resmi 28 Okt (wajib dipakai persis):** *burning activity calendar*, *active fire hotspots*, *area of interest*, *critical periods*, *unusual conditions*, *historical median*, *early warning and emergency responders*, *land managers*, *firefighters*, *accessible color ramps*, *sensor of origin* (`12` §5). "Number of hotspots" boleh dipakai karena statement memakainya; "number of fires" tetap dihindari.
- Hindari: "number of fires", "burned area" (kecuali untuk validasi), "AI predicts", "accuracy 99%".

## 6. Pitch lokal (versi 3–5 menit, sesuaikan dengan format yang diumumkan)
1. **Hook (20 dtk), versi utama 29 Okt (cerita nyata Poggy, 39 kata):** "In October I lined up four and a half million pairs of MODIS and VIIRS pixels over Indonesian seas. Splicing the two sensors roughly doubled the apparent decline on the shelves. Indonesia's fire record has the same splice, in 2012." *(Sumber: abstrak OCEANS 2027 Poggy, `INDIVIDU\OCEANS2027-StudentPoster\01_ABSTRAK.md`: 4,45 juta matchup; tren 2003–2016 −18,5 vs −8,5 %/dekade. Itu data klorofil, bukan api; kodenya tidak dipakai di KalenderApi.)* Hook lama jadi cadangan: "Indonesia's fire record just lost a satellite, twelve days ago." *(hanya kalau cek 3 Nov memastikan S-NPP berhenti 2 Nov)* atau "In 2012, Indonesia's hotspot count jumped [r]-fold overnight. Not one extra fire caused it." 
2. **Masalah (40 dtk):** 95% vs 82% (KLHK SP.361/2017); lompatan [r]× di 2012 dari data kita; musim Riau ≠ Sumsel. "20.928 vs 666" hanya kalau sudah diverifikasi dengan screenshot (`11` §3 #5), dan disebut sebagai efek **filter kepercayaan**, bukan sensor.
3. **Demo langsung (90 dtk):**
   - pilih Riau → toggle mentah/harmonisasi → kalender (Feb & Jun) → onset 2027
   - ganti ke Sumsel (puncak September) untuk menunjukkan musim yang berbeda
   - *(stretch)* negara lain untuk bukti generalisasi
4. **Validasi (40 dtk):** satu tabel skill + cek burned area. Grafik drift hanya kalau stretch tier 1 selesai.
5. **Dampak (30 dtk):** *siaga darurat* → helikopter & dana BNPB; BMKG "tren dan siklus musim".
6. **Penutup (10 dtk):** tagline.

**Latihan:** 3× dengan stopwatch + drill tanya-jawab dari 10 (blok Min 16.00–18.00 di 08).

## 7. Buku besar angka (`docs/numbers.md`, dibuat di hari-H)
Setiap angka yang muncul di video, slide, halaman Project, atau pitch punya satu baris: angka · kalimat tempat dipakai · asal (sel notebook + commit, atau URL + tanggal akses) · status (*terukur / dikutip / belum terverifikasi*). Angka berstatus "belum terverifikasi" tidak boleh tampil. Cek terakhir dilakukan pada Min 15 Nov 16.00, sebelum latihan pitch.

Angka pra-hari-H yang sudah punya sumber per 23 Okt (cek `11` §3): S-NPP berhenti 2 Nov 2026 (Earthdata alert) · SiPongi 202.004 ha Jan–Jul 2026, +69% (Kompas 3 Okt 2026) · RONI JAS 2026 = 1,69 (NOAA CPC, dibaca 23 Okt). Yang **belum**: 20.928 vs 666, Niño-3.4 +2,1 °C, "+80% vs 2023", status Aqua/Terra.
