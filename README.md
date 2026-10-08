# Dark Triad and trait aggression

Replication package for **“Sex differences in the relationship between the Dark Triad and trait aggression: A variance-weighted interpretation of the bifactor model.”**

## Replication files

| File | Description |
| --- | --- |
| `Scripts/replicationScript.qmd` | Analysis code, including table and figure generation. |
| `Data/replicationData.rds` | Questionnaire responses, sex, and age for the study sample. |
| `Data/interceptsBPAQ.rds` | Saved BPAQ intercept diagnostics used to select partial invariance constraints. |
| `Data/interceptsSD3.rds` | Saved SD3 intercept diagnostics used to select partial invariance constraints. |
| `Data/baselineBoot.rds` | Bootstrap results for the confirmatory baseline model. |
| `Data/moderatedBoot.rds` | Bootstrap results for the confirmatory model with sex interactions. |
| `Data/saturatedBoot.rds` | Bootstrap results for the exploratory model with all trait-by-sex interactions. |
| `Data/parsimoniousBoot.rds` | Bootstrap results for the exploratory parsimonious model and Machiavellianism-reference sensitivity analysis. |
| `Data/correlatedFactorsBoot.rds` | Bootstrap results for the correlated three-factor SD3 model. |
| `Data/psychopathyReferenceBoot.rds` | Bootstrap results for the bifactor S−1 model with psychopathy as the reference facet. |
| `Data/narcissismReferenceBoot.rds` | Bootstrap results for the bifactor S−1 model with narcissism as the reference facet. |

## Requirements

R 4.5.3; lavaan 0.6-21; semTools 0.5-8; lessSEM 1.5.7. Additional packages:

```r
install.packages(c("tidyverse", "pbmcapply", "see", "kableExtra", "gt", "knitr", "webshot2"))
```

Quarto is needed to render the analysis document. PNG table exports require Chrome/Chromium.

## Run the analyses

1. Create a project or set working directory at the parent folder.
3. Open `Scripts/replicationScript.qmd` and execute the R chunks in order.

The script defaults to using saved bootstrap results (`runBootstraps <- FALSE`). Adjust `availableCores` to your computer, or set `parallelSupported <- FALSE` for sequential execution.

To rerun the bootstrap from scratch, set both `runBootstraps` and `restartBootstraps` to `TRUE`. This is computationally intensive and overwrites the saved bootstrap files.

Tables and figures are exported to `Tables/` and `Plots/`.

## Contact

Nicolás González-Raposo — nicgonzalezr@udd.cl
