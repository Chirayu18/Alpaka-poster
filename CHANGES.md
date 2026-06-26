# Poster Changes — `poster_updated.tex`

Compile command (run from the poster directory):

```bash
pdflatex "poster_updated.tex"
```

---

## Change 1 — alpaka "framework" → "library", define HLT, rephrase insertion point

**alpaka wording** (Implementation & deployment block):

```latex
% Before
Written in the \textbf{alpaka} portability framework

% After
Written in the \textbf{alpaka} portability library
```

**Define HLT acronym** (title banner):

```latex
% Before
Radiation-damage mitigation at the CMS High-Level Trigger in Run~3

% After
Radiation-damage mitigation at the CMS High-Level Trigger (HLT) in Run~3
```

**Where morphing is inserted** (Implementation & deployment block):

```latex
% Before
inserted before the pixel clusterizer in HLT local reconstruction.

% After
inserted before the pixel clusterizer in pixel local reconstruction at HLT.
```

---

## Change 2 — Simplify the "Merged into CMSSW" bullet

**Goal:** Drop the in-the-weeds technical list; keep only the upstreaming fact, and expand CMSSW.

```latex
% Before
\item Merged into \textbf{CMSSW}, featuring subsequent optimizations like heavy-ion safeguards, a two-buffer race condition fix, and structural warning resolutions.

% After
\item Merged into the \textbf{CMS software framework} (CMSSW).
```

---

## Change 3 — LHC Fill numbers: keep only the deployment Fill

**Goal:** Fill numbers are jargon for a poster audience. Keep **Fill 11200** once, at the deployment bullet (the canonical "went live" marker), and replace all other Fill references with plain dates.

| Location | Before | After |
|---|---|---|
| Fig 1 caption | `25~July~2024, LHC Fill~9931` | `25~July~2024` |
| Deployment bullet | `LHC Fill~11200 (17~October~2025)` | **kept** |
| Fig 2 caption | `14~October~2025, LHC Fill~11190` | `14~October~2025` |
| Fig 7 caption | `Dashed line: Fill~11200, 17~October~2025` | `Dashed line: 17~October~2025` |
| J/ψ block | `enabling morphing at Fill~11200` | `enabling morphing (17~October~2025)` |

---

## Change 4 — De-jargon the "HLT local hit resolution" intro

**Goal:** The simulation-setup sentence was dense detector jargon. Rephrase in plainer language.

```latex
% Before
Single-muon gun, \textbf{no pile-up}, $p_{T}>10$~GeV, $2<|\eta|<3$, BPIX~L1;
truth taken as the closest SimHit. A pronounced bimodal residual in local~$y$
arises from oppositely-biased shortened / broken clusters (tracks of opposite
incidence angle).

% After
\textbf{Simulated single muons} with no additional collisions (no pile-up), each
with $p_{T}>10$~GeV and crossing the forward part of the inner barrel layer
($2<|\eta|<3$, BPIX~L1). The reconstructed hit is compared to the true simulated
position. The residual in local~$y$ is \textbf{bimodal}: broken or shortened
clusters pull the hit in opposite directions depending on the track's incidence
angle.
```

---

## Change 5 — De-jargon the "HLT tracking: efficiency & purity" intro

**Goal:** Replace the shorthand sample description with plainer language; drop pile-up number and event count.

```latex
% Before
$\mathrm{t\bar{t}}$, $\langle\mathrm{PU}\rangle\simeq63$, 13.6~TeV, 100k events.

% After
\textbf{Simulated $\mathrm{t\bar{t}}$ events} at $\sqrt{s}=13.6$~TeV with realistic
Run-3 pile-up.
```

---

## Change 6 — Fix "the central region is unaffected" (efficiency block)

**Goal:** "Unaffected" wrongly implied morphing was applied centrally with no effect. Morphing is simply not applied there (confined to forward BPIX rings).

```latex
% Before
...forward region, where broken clusters are most frequent --- the central region is
unaffected.

% After
...forward region, where broken clusters are most frequent --- the central region lies
outside the morphed rings and is unchanged by construction.
```

---

## Change 7 — Rephrase J/ψ scouting data-comparison sentence

**Goal:** Avoid duplicating the date ("October 2025 data" and "17 October 2025") and read more clearly.

```latex
% Before
constraint (NoVtx), October~2025 data: \textbf{before} vs \textbf{after} enabling
morphing (17~October~2025).

% After
constraint (NoVtx), comparing data \textbf{before} and \textbf{after} morphing was
enabled at the HLT on 17~October~2025.
```

---

## Change 8 — Clarify the final Summary flowchart node

**Goal:** "Improved forward physics" reads like a different subfield rather than the forward tracker region ($|\eta|\gtrsim2$). Make the region explicit.

```latex
% Before
{Improved forward physics (J/$\psi$ yield)};

% After
{Recovered physics performance at high $|\eta|$ (J/$\psi$ yield)};
```

---

## Change 9 — Clickable references (URLs and DOIs)

**Goal:** Make URLs and DOIs in the References block clickable in the PDF, styled in CMS navy.

Added `hyperref` **after** the colour definitions (so `cmsnavy` is available to the link colours):

```latex
\definecolor{softgray}{HTML}{EEF1F6}

% ---- clickable links (load after colours are defined) ------------------
\usepackage[colorlinks=true,urlcolor=cmsnavy,linkcolor=cmsnavy,citecolor=cmsnavy]{hyperref}
```

Wrapped the DOI in reference [1] with `\href`:

```latex
% Before
doi:10.3389/fdata.2020.601728.

% After
\href{https://doi.org/10.3389/fdata.2020.601728}{doi:10.3389/fdata.2020.601728}.
```

The TWiki URL in [5] (already inside `\url{}`) becomes clickable automatically once `hyperref` is loaded.

---

# Answers to Henriette

- **Add the digi morphing DP note as a reference (for now use the twiki):** Already added — the CMS DigiMorphing TWiki is reference [5] (`\url{https://twiki.cern.ch/twiki/bin/view/CMSPublic/DigiMorphing2025}`) and is now clickable. It serves as the digi morphing DP note citation until the note itself is public.
- **Update all figures to PDF for print resolution:** Pending — Chirayu to send the two local-reco figures (and others) as PDF/vector files. Converting the existing PNGs to PDF would not improve resolution, so this is deferred until the source files arrive.
- **Use the very latest figures from the note:** Pending — to be specified; figures will be swapped once the correct/latest files are provided.
- **Cluster-size trends: swap to local-y split in pseudorapidity:** Pending — the `csize_eta_inner/outer` files currently in `posterfigs/` are not the correct ones; awaiting the right figures.

---

## Change 10 — Shorten the "Motivation" block and note morphing can't fix shortened clusters

**Goal:** The block repeated information already in the Overview. Shorten it, and add that digi morphing cannot recover shortened clusters.

```latex
% Before
Radiation damage lowers the charge-collection efficiency, so charge deposits fall
below threshold. During Run~3, the LHC has delivered more than 350~fb$^{-1}$ of
integrated luminosity, resulting in significant radiation damage in the innermost
regions of the pixel detector. For \textbf{shallow-angle} tracks at high $|\eta|$ --- which
cross many pixels and give long local-$y$ clusters --- this leaves:
\begin{itemize}
  \item \textbf{broken clusters}: internal gaps split one cluster into fragments;
  \item \textbf{shortened clusters}: the reconstructed extent is truncated.
\end{itemize}
Both bias the hit position and degrade tracking \emph{exactly where the detector
is most irradiated}.

% After
Radiation damage lowers the charge collection efficiency, so charge deposits can fall
below the per-pixel threshold. For \textbf{shallow-angle} tracks at high $|\eta|$ this
leaves:
\begin{itemize}
  \item \textbf{broken clusters}: internal gaps split one cluster into fragments;
  \item \textbf{shortened clusters}: the reconstructed extent is truncated.
\end{itemize}
Digi morphing recovers \textbf{broken} clusters by bridging internal gaps, but
\textbf{cannot recover shortened clusters}, where charge is lost at the cluster ends.
```

---

## Change 11 — One-page layout: figure swap to PDF + spacing / balance

**Goal:** After swapping figures to the latest vector PDFs, the poster overflowed to 2 pages and the columns became uneven (column 3 much taller). Restore a single A0 page with three balanced columns, all plots visible, no empty bottoms — **without resizing any figures**.

### What changed (layout only — no figure sizes touched)

1. **Removed the alpaka logo** (and its `\vspace{25mm}`) from the bottom of column 3. This was decorative and not referenced by any review comment; removing it frees space in the tallest column.
   ```latex
   % Removed:
   \bsep
   \vspace{25mm}
   \begin{center}
     \includegraphics[width=0.55\linewidth]{alpaka.png}
   \end{center}
   ```

2. **Page margins** (`geometry`): reduced top and bottom margins to recover vertical space.
   ```latex
   % Before
   \usepackage[a0paper,landscape=false,margin=17mm]{geometry}
   % After
   \usepackage[a0paper,landscape=false,hmargin=17mm,top=12mm,bottom=10mm]{geometry}
   ```

3. **Gap between banner and columns** tightened:
   ```latex
   % Before
   \vspace{2mm}{\color{cmsred}\rule{\textwidth}{3pt}}\par
   \vspace{6mm}
   % After
   \vspace{1mm}{\color{cmsred}\rule{\textwidth}{3pt}}\par
   \vspace{-2mm}
   ```

4. **Tight, uniform block spacing.** Default `\bsep` reduced 3mm→2mm for all columns. Blocks are packed tightly with a consistent small gap between them (no large gaps between blocks, per request). The naturally shorter columns (1 and 3) leave their leftover whitespace at the bottom rather than distributing it between blocks.

### Result

Single A0 page, blocks tightly packed. Column content bottoms sit at ~91% / ~99% / ~89% of the page height (columns 1/2/3); nothing clipped, no gaps between blocks.

### Figures swapped to latest vector PDFs (sizes unchanged)

algorithm `cand_E_final_T.pdf`, cluster recovery `fig3_303042568.pdf`, local-x/y residuals `recHitXResLayer1.pdf` / `recHitYResLayer1.pdf`, efficiency/fake `effic.pdf` / `fakeduprate_vs_eta.pdf`, dz/pT resolution `dzres_vs_eta_Sigma.pdf` / `ptres_vs_eta_Sigma.pdf`, size-x `hlt_sizex_inner_0.pdf` / `hlt_sizex_outer_0.pdf`, size-y split in pseudorapidity `hlt_sizey_vs_eta_inner_0.pdf` / `hlt_sizey_vs_eta_outer_0.pdf`. J/psi yield + mass kept as PNG (`jpsi_n_sig_vs_eta.png`, `fit_eta_11.png`). Four diagram/annotated figures without a vector source were upscaled 3x (Lanczos, 300 DPI) as `*_hr.png`: `config_grid`, `detector_regions`, `sensor_broken`, `sensor_short`.

### Figures enlarged to fill the shorter columns

To fill the leftover bottom whitespace in the shorter columns (1 and 3) without adding gaps between blocks, a few figures were enlarged (width fraction only; aspect ratios unchanged):

| Figure | Column | Width fraction (before → after) |
|---|---|---|
| Fig 1 — algorithm (`cand_E_final_T`) | 1 | 0.80 → 0.92 |
| Fig 2 — cluster recovery (`fig3_303042568`) | 1 | 0.82 → 0.94 |
| Sensor cross-sections (stack) | 1 | 0.72 → 0.88 |
| Fig 6 — size-x pair | 3 | 0.49 → 0.498 |
| Fig 7 — size-y (η-split) pair | 3 | 0.49 → 0.498 |
| Figs 8–9 — J/ψ pair | 3 | 0.45 → 0.495 |

### alpaka logo restored to fill column 3

Column 3's remaining bottom whitespace (its figure pairs are at the column-width limit) is filled by placing the **alpaka logo** at the bottom of column 3, below the References block. Columns now bottom out at ~96% / ~99% / ~95% (cols 1/2/3) — balanced, one page, no gaps between blocks.

### References made clickable (verified links only)

In addition to [2] (DOI) and [5] (TWiki) which were already clickable:
- **[1]** Chiochia, IEEE TNS — added DOI `\href{https://doi.org/10.1109/TNS.2005.852748}{...}` (DOI resolves).
- **[3]** Vami, PoS(LHCP2019)010 — linked to `https://pos.sissa.it/350/010` (verified earlier this session).
- **[4]** CMS-DP-2022-014 — **left as plain text**: could not verify a stable CDS record URL (CDS search blocks fetching), so no link added per the "only verifiable links" instruction.

**Note:** No review-comment text was removed. The alpaka logo (originally removed during layout work) was restored to column 3.

### QR code added; TWiki removed from references

- Added a **QR code** (navy, generated for `https://twiki.cern.ch/twiki/bin/view/CMSPublic/DigiMorphing2025`, saved as `posterfigs/qr_twiki.png`) at the bottom of column 3, alongside a smaller alpaka logo, with a "Scan for details" label.
- Since the QR provides the TWiki link, the **TWiki reference [5] was removed** from the reference list (it was not cited inline). References are now [1]–[4]. Logged in `comments.md` under "Note to Henriette — QR code added".
- Column bottoms after this: ~96% / ~99% / ~97% (cols 1/2/3), one page.

### Column 1 decorative touch — cartoon alpacas

A **full-width "alpaca morphing" cartoon** was added at the bottom of column 1 as a decorative, on-theme touch — a visual pun on both "alpaka" and "digi *morphing*". It is drawn in **TikZ** (pure vector — scales cleanly for A0 print, no external image file):
- `\alpaca{scale}{wool colour}{scarf colour}` — a single cartoon alpaca.
- `\alpacafrag{scale}{wool}` — a "broken" alpaca split into a front + rear fragment with a gap.
- `\alpacamorph{width}` — the full-width scene: a broken alpaca → (arrow) → two merging alpacas with a faint translucent "helper" → (arrow) → one recovered alpaca, plus two bystanders, all on a soft green ground line. Mirrors the dilation → (helper digis) → erosion algorithm. Invoked with the column width (`\linewidth`, scaled to 99.5%). Text labels were intentionally omitted — the pun reads visually through the shapes and arrows.

(Earlier iterations — a navy–gold–navy accent rule, three separate alpacas, then a plain five-alpaca herd, then a labelled morphing sequence — were replaced by this label-free morphing cartoon.)

Final column bottoms: ~99% / ~99% / ~97% (cols 1/2/3), one A0 page.
