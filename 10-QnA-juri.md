# 10 — Bank Pertanyaan Juri (SME NASA & juri lokal)
> **Tambahan 23 Okt malam (JURI_90):** Q26–Q36 (statement berubah, pesaing FireCal, lisensi data, istilah SI, resolusi waktu, definisi onset, burned area, wawancara praktisi, kelemahan terbesar). Q24 memakai istilah SI.
>
> **Diperbarui 23 Okt 2026:** jawaban disesuaikan dengan MVP di `08`. Bagian dalam *{kurung kurawal}* hanya diucapkan kalau stretch-nya benar-benar selesai; kalau tidak, pakai kalimat "that's our next step".

Jawaban singkat dalam bahasa Inggris. Angka dalam [kurung] diisi dari hasil hari-H, jangan dikarang. Sumber: `riset/A` §7, `riset/C` §5–6, `riset/B` §5–6.

## A. Validitas ilmiah
1. **"You just multiplied MODIS by five."**
   → No. Published VIIRS/MODIS ratios range from about 2.8 to 11 within a single country, and they differ by day/night and scan angle. We fit a stratified, non-linear transfer (β < 1), and it beats constant ratios out of sample: MAE [x] vs [y], κ [x].
2. **"Pre-2012 'VIIRS-equivalent' fires are invented."**
   → They are statistical estimates of what VIIRS would have counted, with uncertainty bands. Spatial detail stays capped by what MODIS saw (mass-consistent allocation). *{The anomaly-space calendar (M4) does not depend on absolute scaling.}*
3. **"Your calibration is contaminated by orbit drift."**
   → The Aqua-to-S-NPP fit window is February 2012 to December 2022. Aqua passed its 13:45 limit in February 2023, so no drifted month enters the fit. *{Our drift-test slide quantifies the residual after 2022.}* From 2012 the record is VIIRS-observed anyway; MODIS only extends it backward.
4. **"Volcanoes and industry inflate counts."**
   → About 13% of Indonesian VIIRS detections are non-biomass. We apply a time-invariant persistent-source mask plus volcano buffers to both sensors, and report the share removed each year.
5. **"FIRMS already has a `type` field."**
   → Typing differs by product version: the same pixels are type 0 in 2015 files and type 2 in 2022/2024. There was a VIIRS type bug until May 2025, and NRT data have no type. So `type` is only a first pass.
6. **"Fewer hotspots in the worst peat months means fewer fires?"**
   → No. Smoke and haze hide fires, and smouldering peat burns underground. We label the metric "detected burning activity", show night VIIRS (better for peat), and optionally normalize by clear observations.
7. **"Hotspots aren't fires."**
   → Agreed. The calendar shows occupancy (fire cell-days) and percentiles, never "number of fires" or burned area.
8. **"Clouds: a quiet week could just be a cloudy week."**
   → Yes. That's why we [normalize by clear-land observations from the MYD14A1/VNP14A1 fire masks] / [flag low-information cells with hatching]. FIRMS points alone carry no cloud information.
9. **"MODIS daily data are biased."**
   → The MODIS user guide warns against intervals shorter than about 8 days. We harmonize monthly only; daily and dekadal views are raw VIIRS.
10. **"Outages create fake dips."**
    → Outage-aware fitting (Aqua Aug–Sep 2020, S-NPP Jul–Aug 2022, S-NPP Mar 2026), gap-filling from a same-family sensor with wider bands, and flags in the UI.

## B. Validasi & overfitting
11. **"How do you know it works?"**
    → Leave-one-year-out over 2012–2022 (11 folds), and the core model has to beat a naive single national ratio out of sample. Metrics: MAE, % bias, R² on log counts, Kendall τ on anomalies, and 90% interval coverage [x]. Plus an independent check against official burned area. *{Also an extreme-year holdout (2015, 2019) and leave-one-province-out.}*
12. **"Only ~11 years of overlap: overfitting?"**
    → Two or three parameters per stratum, partial pooling toward the national fit, and blocked tests. Interval coverage is reported, not assumed.
13. **"Random cross-validation inflates skill."**
    → That's why we hold out whole years, never random months. *{We also ran leave-one-province-out.}* Otherwise: spatial-block validation is our next step.
14. **"Any independent check, not satellite vs satellite?"**
    → Spearman ρ against official SiPongi burned area 2015–2024 ([x], indicative with 10 points), plus agreement with El Niño/positive-IOD years and low-rainfall months. MCD64A1/VNP64A1 is optional.
15. **"Is your trend real or an artefact?"**
    → Static-source masking is time-invariant and trends are shown with uncertainty. We don't claim attribution (oil palm, restoration, fire bans).

## C. Kontinuitas & masa depan
16. **"S-NPP is gone. Does your reference disappear?"**
    → No. Our reference unit is VIIRS, and NOAA-20 and NOAA-21 carry the same instrument. Mapping them to S-NPP units on the 2018–2026 and 2024–2026 overlaps is a short, like-for-like step *{and we've done it for NOAA-20}*. Re-anchoring to NOAA-20 is also what NASA's QFED is doing.
17. **"What happens when MODIS dies in 2027?"**
    → Nothing breaks. The present-day calendar is VIIRS-native; MODIS only extends the record backward.
18. **"Why not keep each sensor separate, like GWIS?"**
    → Separate series can't give one long baseline across 2012, which is exactly where Indonesia's official numbers disagree (95% vs 82%). *{We also show the per-sensor anomaly view (M4) and its agreement with ours (κ).}*

## D. Relevansi & dampak
19. **"Who will actually use this?"**
    → District and provincial disaster agencies (BPBD) deciding when to declare *siaga darurat*, which unlocks BNPB helicopters and funds. Fire seasons are local: Riau peaks in February and June, South Sumatra in September. [Name the practitioner we interviewed, if any.]
20. **"How is this different from SiPongi, BRIN, GFW or FireWatch?"**
    → None of them offers one cross-calibrated MODIS+VIIRS record with uncertainty for any area. SiPongi headlines swing 20–30× by filter; BRIN dropped MODIS; GFW keeps the sensors separate.
21. **"Does it work outside Indonesia?"**
    → The method is area-agnostic: everything is a 0.1° grid, so any area is a sum of cells. We validated three Indonesian peat provinces for this weekend. *{Here's [country].}*
22. **"There are already a dozen repos for this challenge."**
    → Ours uses a drift-free fit window, carries uncertainty into the calendar cells, beats a naive ratio out of sample, is checked against independent official burned area, and is built around a concrete Indonesian decision (*siaga darurat*). *{Plus: peat-stratified, observation-normalized, NOAA-20/21 chain.}* Say only what we actually built.

## E. Teknis & etika
23. **"Will the demo still work during judging?"**
    → Static site, no backend, no API key in the client; Cloudflare Pages plus a GitHub Pages mirror; a backup video.
24. **"Did you use AI?"**
    → Yes, and it's disclosed in our "Super Intelligence (SI) tools" section, as the 2026 FAQ asks: [tools, for what]. Every number comes from our notebooks; any SI-generated imagery is watermarked.
25. **"Did you build this before the hackathon?"**
    → No. Before 14 November we only read the literature, set up accounts, and planned roles. The Git history starts on 14 November.

## F. Tambahan (uji persona J1–J4, 23 Okt malam)
26. **"The challenge statement asks for [X], not what you built."** *(J1, J4)*
    → We read the statement on 28 October and adapted on day one: [baris `04` §7 yang aktif]. The core (a shared 0.1° occupancy grid, an out-of-sample-validated transfer and uncertainty bands) is the same in every variant; only the direction, time step or area changes.
27. **"FireCal and others already do LOYO, shrinkage and 2σ flags. What's new?"** *(J1, J4)*
    → Those are the baseline, and we have them too. What we add: a fit window that ends before Aqua's orbit drift (Dec 2022), uncertainty carried into the calendar cells, an independent burned-area check rather than satellite-vs-satellite only, and outputs phrased as the decision a BPBD has to make. *{Plus peat strata / NOAA-20 chain if finished.}* Their README claims aren't something we can verify, so we compare on method, not on their numbers.
28. **"Which licenses cover your data? Is SiPongi open?"** *(J4)*
    → NASA FIRMS and MCD64A1 are NASA open data. geoBoundaries and the GFW peat layer are CC BY 4.0. SiPongi is a public government portal; we cite the figures with URL and access date and state its licence status in `data_licenses.md`. *{Our main independent check used MCD64A1, so the result doesn't depend on SiPongi.}*
29. **"BPBD decides week by week. A monthly calendar is too coarse."** *(J2)*
    → Agreed for operations. The harmonized record is monthly because MODIS is biased below about eight days. For 2012 onward we also show dekadal (10-day) climatology from VIIRS alone, which is what an onset date should come from.
30. **"Your onset definition looks arbitrary."** *(J1, J2)*
    → It's written down (first month above twice the uniform share) and we report how it moves at 1.5× and 2.5×. Where it moves, the cell says "onset uncertain".
31. **"Why not just use burned area?"** *(J1)*
    → Burned area arrives late and misses small and peat fires; active fire is what's available in near real time. We use burned area as an independent check, not as the product.
32. **"Did you talk to anyone who would use this?"** *(J2, J3)*
    → [Kalau wawancara terjadi: role + one sentence, with permission.] / [Kalau tidak:] Not yet. Our user model comes from published regulations (Permen LHK P.9/2018, Inpres 3/2020) and BNPB statements; a practitioner interview is our first next step.
33. **"Night detections matter for peat. Do you use them?"** *(J1)*
    → Day and night are separate strata, because the VIIRS/MODIS ratio differs most at night. *{Night-only peat view if finished.}*
34. **"What happens to your calendar now that S-NPP is gone?"** *(J2)*
    → The reference unit is VIIRS; NOAA-20 and NOAA-21 carry the same instrument. For November 2026 we flag the month as incomplete *{or: we already map NOAA-20 onto S-NPP units}*.
35. **"What's your biggest weakness?"** *(J4)*
    → Eleven years of overlap and three provinces. Skill is reported with intervals, and the method is the contribution; more provinces is a data-download away, not a redesign.
36. **"Why should Space Apps judges care beyond Indonesia?"** *(J3)*
    → Every agency that built a fire baseline on MODIS faces the same cliff as MODIS retires. Our grid works for any area FIRMS covers; Indonesia is the hardest test case because of peat, clouds and haze.
