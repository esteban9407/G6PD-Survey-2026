# G6PD Survey 2026 — Code Repository
**Grupo Malaria, Universidad de Antioquia**

---

## Study overview

This repository contains the analytical code underlying the findings reported in:

> *Prevalence of glucose-6-phosphate dehydrogenase (G6PD) deficiency in a malaria endemic malaria region of Colombia: implications for radical cure of Plasmodium vivax* — submitted to PLOS Global Public Health, 2026.

The primary objective of this study was to estimate the prevalence of G6PDd phenotypes in Quibdó, a highly malaria endemic region of Colombia, across three different populations: the largely Afro-Colombian general population, indigenous communities, and outpatients with suspected malaria. A secondary objective was to explore the relationship between G6PDd and the risk of Plasmodium infection..

**This repository contains CODE ONLY.** Per PLOS Global Public Health's distinct policies for [data availability](https://journals.plos.org/globalpublichealth/s/data-availability) and [materials/software/code sharing](https://journals.plos.org/globalpublichealth/s/materials-software-and-code-sharing), the dataset and its data dictionary/codebook are deposited separately in Zenodo (see **Data access** below), each governed by its own repository and DOI.

---

## Repository contents

```
├── README.md                              # This file
├── LICENSE                                # MIT license
├── code/
│   ├── pipeline_tables_G6PDSurvey.R      # Table 1, Table 2, Table 3, S1-S4 Tables — all tables in one script
│   └── pipeline_Fig_G6PDSurvey.R    # Fig 1, Fig 3, Fig 4, Fig S2, Fig S_BA — all figures in one script
```

---

## Data access

The anonymized dataset and its data dictionary/codebook (`codebook_G6PD_survey_2026_EN.xlsx`) are deposited separately in Zenodo, per PLOS's data availability policy:

> **DOI:** [to be added upon deposit]

Access to the dataset requires agreeing to the terms of the data use agreement, given that the study involves human participants from vulnerable populations. Requests for access can be directed to the corresponding author.

This code repository itself is registered separately with Zenodo (via a GitHub Release) to obtain its own, distinct DOI for the code, per PLOS's code-sharing policy.

---

## Data dictionary (reference only)

The codebook deposited alongside the data in Zenodo contains four sheets:

| Sheet | Contents |
|---|---|
| Description | Column-level description of the codebook structure |
| FI-Inclusion | Full variable list with codes, categories, types, and conditional logic |
| G6PD-Variants | Named G6PD variant reference matrix |
| PCR | PCR module variables and processing moments |

Sentinel codes applied globally: `-999` = Missing (non-response or data entry error) / `-9999` = Not applicable (skip logic).

---

## How to run the code

### Requirements

- R ≥ 4.2.0
- Packages: `ggplot2`, `dplyr`, `tidyr`, `cowplot`, `survey`, `openxlsx`, `stringr`, `geeasy`, `readxl`
- `MASS` must be installed (not necessarily attached) — required for profile-likelihood confidence intervals in Table 3 / S4 Table

Install all dependencies:

```r
install.packages(c("ggplot2", "dplyr", "tidyr", "cowplot",
                   "survey", "openxlsx", "stringr", "geeasy",
                   "readxl", "MASS"))
```

### Setup

1. **Load the dataset into R first, as an object named `bd_G6PDSurvey_2026`, before running either script.** Neither script reads the raw data file directly by default — both expect `bd_G6PDSurvey_2026` to already exist in the R environment. (`pipeline_tables_G6PDSurvey.R` includes a fallback block that loads it from `bd_G6PDSurvey_2026.xlsx` via `readxl::read_excel()` only if the object is not already present.)
2. Set your working directory to the folder where output files should be saved.
3. Run each script independently — both are self-contained and include their own data preparation blocks.

### Output files

All figures export as TIFF (300 dpi, LZW compression) and all tables as `.xlsx`, compliant with PLOS Global Public Health submission requirements.

**Figures** (`pipeline_Fig_G6PDSurvey.R`): `Fig1.tif`, `Fig4A.tif`, `Fig4B.tif`, `Fig4.tif`, `Fig3.tif`, `FigS2.tif`, `FigS_BA.tif`

**Tables** (`pipeline_tables_G6PDSurvey.R`): `Table1_G6PD_2026.xlsx`, `Table2_G6PD_2026.xlsx`, `Table3_G6PD_2026.xlsx`, `TableS1_G6PD_2026.xlsx`, `TableS2_G6PD_2026.xlsx`, `TableS3_G6PD_2026.xlsx`, `TableS4_G6PD_2026.xlsx`

---

## Study design note

Group 1 (General population, Quibdó) was recruited through a complex survey design with stratification by neighborhood (PSU), household selection probabilities, and individual selection weights. All prevalence estimates, medians, and adjusted models for Group 1 incorporate sampling weights (via the `survey` package for descriptive statistics, and via GEE with clustering/weighting for Table 3 and the S4 Table). Groups 2 (Indigenous) and 3 (Outpatients) were recruited through exhaustive or convenience sampling and are analyzed without weights.

---

## Participant exclusion

Eight participants (specific IDs, see `pipeline_tables_G6PDSurvey.R` Section 1) are excluded from all analyses in this repository -- both tables and figures -- **with one exception**: the Bland-Altman agreement plots (`Fig S_BA`, Section 7 of `pipeline_Fig_G6PDSurvey.R`) intentionally use the full, non-excluded dataset.

---

## Ethical statement

The study was approved by the Ethics Committee of the Universidad de Antioquia (Act No. [to be added]). All participants provided written informed consent. Data have been de-identified prior to deposit. No direct identifiers (names, document numbers, dates of birth) are included in the deposited dataset.

---

## License

- **This repository (code):** MIT License — free to use, modify, and distribute with attribution
- **Data and documentation (deposited separately in Zenodo):** Creative Commons Attribution 4.0 International (CC BY 4.0)

---

## Citation

If you use this code or the associated dataset, please cite:

> [Full citation to be added upon publication]

---

## Contact
Juan Esteban Martínez López — Grupo Malaria
---
Daniel Camilo Aguirre Acevedo — Instituto de Investigaciones Médicas
---
**Universidad de Antioquia, Medellín, Colombia**
