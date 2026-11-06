# FLIP-1 Safety Trial: Data Analysis (Imperial)

R Markdown notebooks, data and outputs for the FLIP-1 analysis of LACTIN-V: vaginal microbiome transitions, host immune mediator responses and DESI-MS metabolomics. The VMET2 cohort is used for comparison.

## Repository layout

```
.
├── Microbiome_Figures.Rmd                    # CST transitions (Sankey), sampling plots, bacterial load / LACTIN-V
├── RespondervsNonResponderClassification.Rmd # Clusters participants into LACTIN-V responders vs non-responders
├── FLIP_ImmuneProfiles.Rmd                   # Immune mediators: colonisers vs non-colonisers, CST effects, VMET2 vs FLIP
├── DESI_MS_MetabolomicAnalysis.Rmd           # DESI-MS random-forest models (CST, immune mediators), metabolite correlations
├── Data/        # Input data (clinical, microbiome parameters, immune profiles, DESI-MS, 16S tables)
│   └── 16S Data/  # 16S feature tables (BIOM/TSV), taxonomy, VALENCIA CST assignments
├── Figures/     # Generated figures (PNG/SVG/PDF)
└── Results/     # Generated tables and fitted models (CSV/RDS)
```

## Running the analysis

Open the repository root as the working directory (for example as an RStudio project) and knit each notebook. Every notebook calls `here::i_am()`, so all paths resolve relative to the repository root.

Suggested order:

1. `Microbiome_Figures.Rmd`: writes `Figures/Microbiome_VMETFLIPSankey.rds`, which `FLIP_ImmuneProfiles.Rmd` reads for panel a of the full figure.
2. `RespondervsNonResponderClassification.Rmd`
3. `FLIP_ImmuneProfiles.Rmd`
4. `DESI_MS_MetabolomicAnalysis.Rmd`: retrains the random-forest models and writes them to `Results/DESI/`. To reuse the saved models instead of retraining, follow the comments in the notebook.

## Requirements

R (≥ 4.x) with the following packages:

- **CRAN:** here, tidyverse (readr, dplyr, tidyr, purrr, tibble, ggplot2), janitor, expss, reshape2, cluster, ggpubr, rstatix, patchwork, paletteer, circlize, networkD3, ggalluvial, svglite, caret, randomForest, ranger, doParallel, pROC, plotROC, precrec
- **Bioconductor:** BiocParallel, ComplexHeatmap
- **Palettes:** impressionist.colors (used through `paletteer`)

```r
install.packages(c("here", "tidyverse", "janitor", "expss", "reshape2", "cluster",
                   "ggpubr", "rstatix", "patchwork", "paletteer", "circlize",
                   "networkD3", "ggalluvial", "svglite", "caret", "randomForest",
                   "ranger", "doParallel", "pROC", "plotROC", "precrec"))
if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")
BiocManager::install(c("BiocParallel", "ComplexHeatmap"))
```
