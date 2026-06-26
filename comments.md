# Poster Review Comments — `poster_updated.tex`

Each comment below is paired with how it was resolved. See `CHANGES.md` for the exact before/after LaTeX.

---

1. **"alpaka portability framework" → "alpaka portability library"**
   - ✅ Done. Changed to "alpaka portability library".

2. **HLT is not defined.**
   - ✅ Done. Acronym spelled out at first use in the title banner: "...CMS High-Level Trigger (HLT) in Run 3".

3. **"HLT local reconstruction" → "pixel local reconstruction at HLT"**
   - ✅ Done.

4. **"heavy-ion safeguards, a two-buffer race condition fix, and structural warning resolutions." — do you really need this bullet?**
   - ✅ Simplified. Bullet reduced to "Merged into the CMS software framework (CMSSW)." (dropped the technical list; expanded the CMSSW acronym).

5. **"from Fill ..." — do you really need the LHC fill number? Couldn't you just say "at the end of 2025"?**
   - ✅ Done. Fill numbers removed in favour of dates everywhere **except** the deployment bullet, which keeps **Fill 11200** once as the canonical "went live" marker.

6. **"14 October 2025, LHC Fill 11190" — do you need it?**
   - ✅ Done. Fill number removed; date kept (covered by the same Fill-number policy as comment 5).

7. **"Single-muon gun, no pile-up, pT > 10 GeV, 2 < |η| < 3, BPIX L1; truth taken as the closest SimHit." — rephrase (super jargon).**
   - ✅ Rephrased in plainer language: simulated single muons, no extra collisions (no pile-up), pT > 10 GeV, crossing the forward part of the inner barrel layer; reconstructed hit compared to the true simulated position; the local-y residual is bimodal because broken/shortened clusters pull the hit in opposite directions depending on incidence angle.

8. **"tt, ⟨PU⟩ ≃ 63, 13.6 TeV, 100k events." — jargon.**
   - ✅ Rephrased to "Simulated t-tbar events at √s = 13.6 TeV with realistic Run-3 pile-up." (dropped the explicit ⟨PU⟩ = 63 number and event count; kept a Run-3 pile-up mention).

9. **"the central region is unaffected." — but morphing was not applied in the barrel, so rephrase.**
   - ✅ Rephrased to "...the central region lies outside the morphed rings and is unchanged by construction."

10. **"October 2025 data: before vs after enabling morphing at Fill 11200" — rephrase.**
    - ✅ Rephrased to "...comparing data before and after morphing was enabled at the HLT on 17 October 2025." (removed Fill number and the duplicated date).

11. **"Improved forward physics" — reading "forward physics" did not suggest η slightly above 2; can we improve this text box?**
    - ✅ Summary flowchart node changed to "Recovered physics performance at high |η| (J/ψ yield)".

12. **Make all references clickable (for the PDF version).**
    - ✅ Done. Added `hyperref` with CMS-navy `colorlinks`. The TWiki URL [5] and the DOI in [1] are now clickable.

---

# Round 2 — Henriette Aarup Petersen

## General

- **Last name spelled incorrectly — should be Petersen.**
  - ✅ Done. "Henriette Peterson" → "Henriette Petersen".
- **Update all figures to PDF so print resolution is good enough (will send the two local-reco ones).**
  - ✅ Mostly done. All data plots now use vector PDFs from `newfigs/`: algorithm (`cand_E_final_T`), cluster recovery (`fig3_303042568`), local-x/y residuals (`recHitXResLayer1`/`recHitYResLayer1`), efficiency/fake (`effic`/`fakeduprate_vs_eta`), dz/pT resolution (`dzres_vs_eta_Sigma`/`ptres_vs_eta_Sigma`), size-x (`hlt_sizex_inner/outer_0`), size-y η-split (`hlt_sizey_vs_eta_inner/outer_0`). J/ψ yield + mass kept as PNG (`jpsi_n_sig_vs_eta`, `fit_eta_11`) — fine for scouting per request.
  - ⚠️ Four figures have no PDF source (custom diagrams / annotated published figure): sensor cross-sections and the config grid + Phase-1 detector map. These were **upscaled 3× (Lanczos, 300 DPI)** as an interim measure — see note to Henriette below.
- **Make sure you have all the very latest figures from the note.**
  - ⏳ Pending — to be specified which figures are out of date.
- **Don't hyphen "digi morphing" — keep it consistent with the note (no hyphen).**
  - ✅ Done. "The digi-morphing algorithm" → "The digi morphing algorithm" (and source comment). Code flag `DoDigiMorphing` left literal.
- **Add the digi morphing DP note as a reference (for now use the twiki).**
  - ✅ Already added — the CMS DigiMorphing TWiki is reference [5] and is clickable; serves as the note citation for now.

## Overview

- **"...is the innermost tracker." → "...innermost tracker sub-system."**
  - ✅ Done.
- **"...radiation damage to its innermost regions." → "...to the barrel pixel layer closest to the beam (BPIX L1)".**
  - ✅ Done.
- **Don't hyphen "charge-collection efficiency" (everywhere).**
  - ✅ Done in Overview and Motivation.
- **Reword "where shallow track angles — combined with the per-pixel charge threshold — produce truncated or broken clusters..." → "...— due to the per-pixel charge threshold — can lead to truncated or broken clusters...".**
  - ✅ Done.

## Motivation: broken & shortened clusters

- **Repeats info already said above; shorten to "Radiation damage lowers the charge collection efficiency, so charge deposits can fall below the per-pixel threshold."**
  - ✅ Done.
- **Also mention that digi morphing can't fix shortened clusters.**
  - ✅ Done — added that morphing recovers broken clusters but cannot recover shortened ones.

## Implementation & deployment

- **Put [1] after "alpaka"; order references by first appearance.**
  - ✅ Done. `[2]` now follows "alpaka", and references are renumbered by first appearance: [1] Chiochia, [2] Bocci (alpaka), [3] Vami, [4] CMS HLT, [5] TWiki.
- **Change config bullet to "Morphed regions are fully configurable via configuration flags".**
  - ✅ Done.
- **"Merged into CMSSW, featuring several subsequent optimizations" and drop the rest.**
  - ✅ Done.

## Impact on clusters in data

- **The over/under-merging sentence isn't fully correct: we WANT to merge fragments from the same track angle; over-merging (different tracks) and under-merging (gap too large) are the limitations.**
  - ✅ Reworded: morphing merges fragments consistent with the same incidence angle; limitations are over-merging (fragments from different tracks) and under-merging (gap too large for the kernel).

## Application: targeted regions

- **Change title to "Application: targeted regions".**
  - ✅ Done (single colon).

## HLT local hit resolution

- **pT > 10 GeV → pT ≈ 10 GeV.**
  - ✅ Done.
- **"Local-x essentially unchanged ... since damage mainly lengthens local-y clusters." → "...since radiation damage resulting in broken clusters mainly affects the local y-coordinate".**
  - ✅ Done.

## HLT tracking: impact parameter & pT

- **Remove the dxy bullet (not shown) and remove the punctuation after the bullet.**
  - ✅ Done — dxy bullet removed; trailing period dropped from the final bullet.

## Cluster-size trends in data

- **Swap to where one can see local y split in pseudorapidity.**
  - ✅ Done — size-y figure swapped to the η-split version (`hlt_sizey_vs_eta_inner/outer_0.pdf`); caption updated.

---

## Note to Henriette — figures still needed in vector/PDF form

The following figures have no vector source available and were **upscaled from PNG (3×, Lanczos, 300 DPI)** as an interim measure for printing. For true print quality they should be regenerated as PDF/vector:

- `config_grid` — the "Digi Morphing Configuration" table (custom diagram; needs regenerating as vector).
- `detector_regions` — the 3D BPIX module-rings drawing, annotated from Vami PoS(LHCP2019)010 [3]. The published source figure is itself a raster (~147 ppi), so a clean version would need re-rendering of the base drawing.
- `sensor_broken` / `sensor_short` — sensor cross-section diagrams (small source images; ideally redrawn as vector).

---

## Note to Henriette — QR code added

A **QR code** was added at the bottom of column 3 (next to the alpaka logo, labelled "Scan for details"). It links to the CMS DigiMorphing TWiki:
`https://twiki.cern.ch/twiki/bin/view/CMSPublic/DigiMorphing2025`

Because the QR now provides that link, the TWiki was **removed from the reference list** (it was the former reference [5] and was not cited inline anywhere). References are now [1]–[4]. If you'd prefer the TWiki to remain a written reference as well, it can easily be added back.
