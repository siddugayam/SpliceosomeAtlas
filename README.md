# SpliceosomeAtlas

**Pan-cancer alteration landscape of the core spliceosome machinery**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Data: TCGA](https://img.shields.io/badge/Data-TCGA%20PanCancer%20Atlas-green)](https://www.cbioportal.org)
[![R version](https://img.shields.io/badge/R-%3E%3D4.2-blue)](https://www.r-project.org)

---

## Overview

**SpliceosomeAtlas** is a reproducible data resource quantifying copy number alteration (CNA) and somatic mutation frequencies for **15 core spliceosome / splicing-factor genes** across **32 TCGA PanCancer Atlas tumour types** (n = 10,195 samples). Recurrent splicing-factor mutations (notably SF3B1, U2AF1, SRSF2, ZRSR2) are established drivers in myeloid neoplasms and recur across solid tumours.

This repository accompanies the manuscript:

> Gayam PKR, Earny VA, Aranjani JM, Fayaz SM. *Pan-cancer alteration landscape of the core spliceosome machinery.* [Journal name, 2026]

---

## Key findings

- **PRPF8** is the most frequently altered gene across cancers (mean **45.9%** any-alteration), and **SF3B1** is the most frequently *mutated* (mean **2.7%**)
- **Copy number alteration dominates** over somatic mutation across all 15 genes
- **OV** shows the highest pan-pathway alteration burden (**69.6%**); **THCA** the lowest (**5.0%**)
- In breast cancer (BRCA, n=1,052), **PRPF8** is the most altered gene (**65.4%**)

---

## Repository structure

```
SpliceosomeAtlas/
├── data/                          # All CSV data files
├── notebooks/notebook.ipynb       # Python data retrieval pipeline (cBioPortal API)
├── figures/                       # Generated TIFF figures (300 DPI)
├── spliceosome_figures.R
├── DATA_DICTIONARY.md
├── CITATION.cff
├── requirements.txt
├── README.md
├── LICENSE                        # MIT (code)
└── LICENSE-data.md                # CC BY 4.0 (data)
```

---

## Genes analysed

| Category | Genes |
|---|---|
| U2 snRNP / 3′SS | SF3B1, SF3A1, U2AF1, U2AF2, ZRSR2, PHF5A, SUGP1 |
| U5 / core | PRPF8, LUC7L2 |
| SR proteins | SRSF2, RBM39 |
| Regulators / hnRNP | RBM10, HNRNPK, FUBP1, DDX3X |

---

## Reproducing the figures

### Requirements
- R ≥ 4.2
- Packages: `tidyverse`, `pheatmap`, `RColorBrewer`, `ggpubr`, `scales`, `cowplot`, `viridis`, `ggtext`, `patchwork`

### Steps
```r
source("spliceosome_figures.R")   # Output: 5 TIFF files in figures/
```
All packages are automatically installed if not already present.

---

## Reproducing the data retrieval

The Python notebook (`notebooks/notebook.ipynb`) retrieves data directly from the **cBioPortal public API** and is fully reproducible.

```bash
pip install -r requirements.txt
cd notebooks && jupyter notebook notebook.ipynb
```
> No login or API key required. cBioPortal data is publicly available. Retrieved June 2026 (cBioPortal v7.0.0).

---

## Data description

| File | Description | Rows | Columns |
|---|---|---|---|
| `*_alteration_freqs_long.csv` | Master long-format table | 480 | 23 (see `DATA_DICTIONARY.md`) |
| `*_any_alter_freq_matrix.csv` | Gene × tumour matrix (any alteration) | 15 | 32 |
| `*_any_cna_freq_matrix.csv` | Gene × tumour matrix (CNA only) | 15 | 32 |
| `*_mut_freq_matrix.csv` | Gene × tumour matrix (mutation only) | 15 | 32 |
| `spliceosome_gene_rank_summary.csv` | Gene ranking across 32 studies | 15 | 9 |
| `spliceosome_top5_tumours_per_gene.csv` | Top 5 tumours per gene | 75 | 9 |
| `spliceosome_tumour_burden_ranking.csv` | Tumour burden ranking (15 genes) | 32 | 7 |
| `brca_spliceosome_*.csv` | BRCA deep-dive (n=1,052) | 15 | 15 |
| `tcga_pancan_atlas_sample_set_summary.csv` | Study metadata and sample counts | 32 | 7 |

---

## Tumour type abbreviations

| Code | Cancer type | N |
|---|---|---|
| BRCA | Breast Invasive Carcinoma | 1,052 |
| COADREAD | Colorectal Adenocarcinoma | 532 |
| LGG | Brain Lower Grade Glioma | 511 |
| LUAD | Lung Adenocarcinoma | 511 |
| OV | Ovarian Serous Cystadenocarcinoma | 511 |
| UCEC | Uterine Corpus Endometrial Carcinoma | 511 |
| HNSC | Head and Neck Squamous Cell Carcinoma | 509 |
| PRAD | Prostate Adenocarcinoma | 489 |
| THCA | Thyroid Carcinoma | 487 |
| LUSC | Lung Squamous Cell Carcinoma | 484 |
| *...and 22 more* | | |

Full list in `data/tcga_pancan_atlas_sample_set_summary.csv`

---

## Citation

```bibtex
@article{gayam2026spliceosome,
  title   = {Pan-cancer alteration landscape of the core spliceosome machinery},
  author  = {Gayam, Prasanna Kumar Reddy and Earny, Venkat Abhiram and Aranjani, Jesil Mathew and SM, Fayaz},
  journal = {[Journal name]},
  year    = {2026}
}
```
Please also cite the cBioPortal:
> Cerami E, et al. The cBio Cancer Genomics Portal. *Cancer Discov.* 2012;2(5):401–404.

---

## Data availability

All underlying data were obtained from publicly available TCGA PanCancer Atlas studies via the cBioPortal API. No individual patient data are included.

---

## License

Code is licensed under the **MIT License** ([LICENSE](LICENSE)); data files are licensed under **CC BY 4.0** ([LICENSE-data](LICENSE-data.md)). Every column is documented in [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md).

---

## Contact

**Gayam Prasanna Kumar Reddy**
Manipal Academy of Higher Education, India
siddugayam1994@gmail.com

*Issues and pull requests welcome.*
