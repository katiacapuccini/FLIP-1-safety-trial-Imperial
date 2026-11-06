# FLIP-1 Safety Trial: Data Analysis

R Markdown notebooks, data and outputs for the FLIP-1 analysis of LACTIN-V: vaginal microbiome transitions, host immune mediator responses and DESI-MS metabolomics. 


## Running the analysis

Open the repository root as the working directory (for example as an RStudio project) and knit each notebook. Every notebook calls `here::i_am()`, so all paths resolve relative to the repository root.


## Requirements

R (≥ 4.x) with the following packages:

- **CRAN:** here, tidyverse (readr, dplyr, tidyr, purrr, tibble, ggplot2), janitor, expss, reshape2, cluster, ggpubr, rstatix, patchwork, paletteer, circlize, networkD3, ggalluvial, svglite, caret, randomForest, ranger, doParallel, pROC, plotROC, precrec
- **Bioconductor:** BiocParallel, ComplexHeatmap
- **Palettes:** impressionist.colors (used through `paletteer`)
