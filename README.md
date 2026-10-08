# ARS co-regulation in cancer

Do aminoacyl-tRNA synthetase (ARS) genes behave as a co-regulated module in human tumours, and is this module linked to ATF4 / integrated stress response activity and promoter chromatin accessibility?

This repository contains all code for the analysis behind a planned bioRxiv preprint. Every step uses public data (TCGA, ENCODE, DepMap/CCLE) and can be re-run in Google Colab.

## Status

| Step | Notebook | Status |
| --- | --- | --- |
| 1. Feasibility pilot (TCGA-LUAD) | `notebooks/01_feasibility_pilot.ipynb` | Done (decision: A) |
| 2. Pan-cancer co-expression | `notebooks/02_pancancer_coexpression.ipynb` | Done (decision: A) |
| 3. ATF4 / ISR association | `notebooks/03_atf4_signature.ipynb` | Planned |
| 4. Differential expression (DESeq2) and enrichment (clusterProfiler) | `notebooks/04_differential_expression.ipynb` | Planned |
| 5. Chromatin layer (TCGA ATAC-seq, ENCODE ATF4 ChIP-seq) | `notebooks/05_chromatin.ipynb` | Planned |
| 6. Independent validation | `notebooks/06_validation.ipynb` | Planned |

## Repository structure

```text
ars-coregulation-cancer/
├── README.md
├── notebooks/        # one notebook per analysis step, run in order
├── data/             # download instructions only — raw data are NOT stored in the repository
├── results/          # tables (TSV) produced by the notebooks
├── figures/          # figures produced by the notebooks
└── logs/             # software versions, input manifests, SHA-256 fingerprints
```

## Data sources

| Data | Source | Used in |
| --- | --- | --- |
| TCGA RNA-seq (STAR TPM and counts) | UCSC Xena GDC hub / GDC Data Portal | Steps 1–4 |
| TCGA ATAC-seq (Corces et al., Science 2018) | GDC ATAC-seq AWG publication page | Step 5 |
| ATF4 ChIP-seq (K562: ENCSR044UJJ, HepG2: ENCSR288ZFV) | ENCODE | Step 5 |
| Validation cohort | DepMap/CCLE or GEO (to be selected) | Step 6 |

The exact download links, file sizes and SHA-256 fingerprints of every input are written to `logs/input_manifest.tsv` and `logs/input.sha256.txt` by each notebook.

## How to run

1. Open a notebook in Google Colab (**File > Open notebook > GitHub**).
2. Save a copy in your own Drive (**File > Save a copy in Drive**).
3. Run the cells in order. Each notebook explains where to find its input links.

## Gene sets

* Cytoplasmic ARS (20 genes): AARS1, CARS1, DARS1, EPRS1, FARSA, FARSB, GARS1, HARS1, IARS1, KARS1, LARS1, MARS1, NARS1, QARS1, RARS1, SARS1, TARS1, VARS1, WARS1, YARS1
* Mitochondrial ARS (17 genes): AARS2, CARS2, DARS2, EARS2, FARS2, HARS2, IARS2, LARS2, MARS2, NARS2, PARS2, RARS2, SARS2, TARS2, VARS2, WARS2, YARS2
* Control signatures (ATF4 targets without ARS genes; proliferation markers) are defined in each notebook. Pilot lists are provisional and will be replaced by published gene sets.

## Author

Hatice Kübra Meşe — Molecular Biology and Genetics (B.Sc.), bioinformatics training at DNA Academy (BIF101–BIF301).
