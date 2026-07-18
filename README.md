# Obesity Multi-omics Analysis

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![R](https://img.shields.io/badge/R-%3E%3D4.3-blue)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey)

## Overview

This repository contains the complete and reproducible R workflow used for the longitudinal multi-omics analyses performed in a randomized obesity intervention study.

The analysis integrates lipidomics, metabolomics, PFAS measurements, and clinical phenotypes to investigate molecular changes during weight loss and weight regain.

The repository generates all primary statistical analyses, publication-quality figures, and supplementary tables reported in the manuscript.

---

## Repository Structure

```
obesity-multiomics-analysis
│
├── Scripts_manuscript.Rmd        Complete analysis workflow
├── Scripts_manuscript.html       Rendered analysis report
├── Figures/                      Publication figures
├── Tables/                       Supplementary tables
├── README.md
├── LICENSE
└── CITATION.cff
```

---

## Analysis Workflow
```text
                                      STUDY DESIGN
┌──────────────────────────────────────────────────────────────────────────────┐
│ Randomized Obesity Intervention Trial                                        │
│                                                                              │
│ Participants → Baseline (BL) → 6 Months → 12 Months                          │
│                      │              │            │                            │
│                      └──────── Longitudinal Clinical Follow-up ──────────────┘
└──────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                           DATA ACQUISITION                                   │
├──────────────────────────────────────────────────────────────────────────────┤
│ • Clinical metadata                                                          │
│ • Lipidomics                                                                 │
│ • Metabolomics                                                               │
│ • PFAS measurements                                                          │
└──────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                           PREPROCESSING                                      │
├──────────────────────────────────────────────────────────────────────────────┤
│ • Sample filtering                                                           │
│ • Feature filtering (missingness threshold)                                  │
│ • Half-minimum imputation                                                    │
│ • Log2 transformation                                                        │
│ • Autoscaling                                                                │
│ • Metadata harmonization                                                     │
└──────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
        ┌─────────────────────────────────────────────────────────────┐
        │                                                             │
        ▼                                                             ▼
┌──────────────────────────────┐                     ┌──────────────────────────┐
│ Longitudinal Statistics      │                     │ Network Analysis         │
├──────────────────────────────┤                     ├──────────────────────────┤
│ • Linear mixed models        │                     │ • WGCNA                  │
│ • Estimated marginal means   │                     │ • Soft thresholding      │
│ • Pairwise contrasts         │                     │ • Module detection       │
│ • Phase comparisons          │                     │ • Eigengene calculation  │
│ • Group × Time interaction   │                     │ • Module–trait analysis  │
│ • Group × Phase interaction  │                     │ • Hub feature detection  │
│ • FDR correction             │                     │                          │
└──────────────────────────────┘                     └──────────────────────────┘
        │                                                             │
        └──────────────────────────────┬──────────────────────────────┘
                                       ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                           VISUALIZATION                                      │
├──────────────────────────────────────────────────────────────────────────────┤
│ • Longitudinal trajectories                                                  │
│ • Forest plots                                                               │
│ • Heatmaps                                                                   │
│ • Module–trait correlation heatmaps                                          │
│ • Network summaries                                                          │
└──────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                              OUTPUTS                                         │
├──────────────────────────────────────────────────────────────────────────────┤
│ ✓ Statistical result tables                                                  │
│ ✓ Estimated marginal means                                                   │
│ ✓ WGCNA module assignments                                                   │
│ ✓ Publication figures (PDF/PNG)                                              │
│ ✓ Supplementary Excel tables                                                 │
│ ✓ Reproducible manuscript report (HTML)                                      │
└──────────────────────────────────────────────────────────────────────────────┘

```

---

## Features

- Longitudinal mixed-effects modelling
- Estimated marginal means (EMMs)
- Pairwise temporal contrasts
- Randomisation × time interaction analyses
- Randomisation × phase interaction analyses
- Multiple testing correction (Benjamini–Hochberg FDR)
- Weighted Gene Co-expression Network Analysis (WGCNA)
- PFAS longitudinal analyses
- Publication-ready figures
- Supplementary tables

---

## Statistical Methods

The pipeline includes

- Linear mixed-effects models (`lme4`)
- Estimated marginal means (`emmeans`)
- Spearman correlation
- Benjamini–Hochberg FDR correction
- WGCNA
- Principal component visualization
- Heatmaps
- Longitudinal trajectory analyses

---

## Software Requirements

- R ≥ 4.3
- RStudio (recommended)

### Main R packages

- tidyverse
- lme4
- lmerTest
- emmeans
- WGCNA
- pheatmap
- ComplexHeatmap
- ggplot2
- broom.mixed
- openxlsx
- patchwork
- cowplot
- janitor
- readxl

---

## Running the Analysis

Clone the repository

```bash
git clone https://github.com/shashank-KU/obesity-multiomics-analysis.git
```

Open

```
Scripts_manuscript.Rmd
```

Update the file paths in the parameter section if necessary.

Render the workflow

```r
rmarkdown::render("Scripts_manuscript.Rmd")
```

---

## Outputs

The workflow generates

- Publication figures (PDF/PNG)
- Supplementary Excel tables
- WGCNA module assignments
- Estimated marginal means
- Statistical summary tables

---

## Data Availability

Raw participant-level omics and clinical data are not included in this repository because they contain sensitive human research data.

Researchers interested in accessing the data should contact the corresponding authors and comply with institutional and ethical approval requirements.

---

## Citation

If you use this workflow, please cite the associated publication once available.

Citation information is also provided in `CITATION.cff`.

---

## License

This project is distributed under the MIT License.

See the LICENSE file for details.

---

## Contact

**Shashank Gupta**

School of Medical Sciences

Örebro University

Sweden

GitHub:
https://github.com/shashank-KU
