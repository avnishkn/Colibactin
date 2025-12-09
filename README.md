# Early-Onset Colorectal Cancer: Colibactin Signature Analysis

## Overview

This project analyzes genetic mutational signatures in early-onset colorectal cancer from the Cancer Genome Atlas (TCGA) data, with a focus on the colibactin-associated signature (SBS88).

The hypothesis being interrogated is that early-onset colorectal tumours show stronger evidence of the colibactin mutational signature compared to late-onset tumours.

## Background

**Colibactin** is a genotoxic metabolite produced by certain strains of *E. coli* that can cause DNA double-strand breaks. The colibactin mutational signature (SBS88) is characterized by specific patterns of single nucleotide variants (SNVs) and has been associated with colorectal cancer.

**Early-onset colorectal cancer** (diagnosis ≤40 years) is increasingly common and may have distinct mutational patterns compared to late-onset disease (diagnosis ≥70 years).

## Data Sources

TCGA COAD/READ via GDC API; COSMIC SBS96 v3.4 signatures (SBS88).

## Project Structure

```
Colibactin/
├── early_coad_read.ipynb          # Main analysis notebook
├── data/
│   └── maf/                       # Mutation Annotation Format (MAF) files
│       ├── downloads/            # Raw downloads from GDC
│       ├── raw/                  # Extracted MAF files
│       └── unzipped/             # Processed MAF files
└── cosmic_sbs_v3.4/              # COSMIC mutational signatures (SBS96)
```

## Analysis

1. Download MAF files and patient ages from GDC API
2. Stratify patients: early-onset (≤40 years) vs late-onset (≥70 years)
3. Compute 96-trinucleotide context frequencies and cosine similarity to SBS88
4. Compare SBS88 signal between groups (Mann-Whitney U test)

## Dependencies

- Python 3.7+
- pandas, numpy, scipy
- matplotlib, seaborn
- requests
- tqdm
- jupyter notebook

## Usage

Run `early_coad_read.ipynb` cells sequentially. Note: The notebook extracts COSMIC signatures from `COSMIC_catalogue-signatures_SBS96_v3.4.zip` which can be downloaded from [COSMIC](https://cancer.sanger.ac.uk/signatures/) and placed in the project root. The extracted `cosmic_sbs_v3.4/` folder contains the required signature files.

## References

- TCGA: https://portal.gdc.cancer.gov/
- COSMIC (Catalogue of Somatic Mutations in Cancer): https://cancer.sanger.ac.uk/signatures/
- Pleguezuelos-Manzano et al., Nature, 2020: https://www.nature.com/articles/s41586-020-2080-8

