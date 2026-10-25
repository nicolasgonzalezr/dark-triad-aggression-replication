# Dark Triad and trait aggression

Replication package for **“Sex differences in the relationship between the Dark Triad and trait aggression: A variance-weighted interpretation of the bifactor model.”**

This project examines how sex differences and overlapping Dark Triad traits relate to trait aggression. The R/Quarto analysis combines measurement models, plausible values, structural models, bootstrap inference, and sensitivity analyses of factor parametrization.

## Start here

- **Read the analysis:** [`Scripts/replicationScript.qmd`](Scripts/replicationScript.qmd).
- **Inspect outputs:** [`Tables/`](Tables/) and [`Plots/`](Plots/).
- **Reproduce using saved bootstrap results:** use the default `runBootstraps <- FALSE` setting.
- **Regenerate bootstrap results:** follow the configuration notes below; this is computationally intensive and can overwrite stored results.

## Repository map

| Path | Purpose |
| --- | --- |
| `Scripts/replicationScript.qmd` | Analysis code, including table and figure generation. |
| `Data/` | Replication data, saved intercept diagnostics, and bootstrap results. |
| `Tables/` | Exported analysis tables. |
| `Plots/` | Exported figures. |

## Requirements

The existing replication documentation reports R 4.5.3, lavaan 0.6-21, semTools 0.5-8, and lessSEM 1.5.7. These are reference versions; the repository does not currently provide an environment lockfile.

Additional R packages used by the script include:

```r
install.packages(c(
  "tidyverse", "pbmcapply", "see", "kableExtra",
  "gt", "knitr", "webshot2"
))
```

The script also checks for missing required packages and attempts to install them from CRAN. Installing current CRAN releases does not recreate the reference package versions.

Quarto is needed to render the analysis document. PNG table exports require Chrome/Chromium.

## Run the analyses

The script uses paths such as `../Data/replicationData.rds`, `../Tables/`, and `../Plots/`. **When executing R chunks interactively, the working directory must be `Scripts/`.**

For interactive execution:

1. Clone or download the complete repository.
2. Start R in the repository root and run `setwd("Scripts")`.
3. Open `replicationScript.qmd` and execute the R chunks in order.

To render from a terminal, starting in the repository root:

```bash
cd Scripts
quarto render replicationScript.qmd
```

Keep the `Data/`, `Scripts/`, `Tables/`, and `Plots/` directories together. Rendering is an analytical computation, not just conversion of an existing report: model fitting and plausible-value draws still run when stored bootstrap results are used.

## Computation settings

| Setting | Default in the script | Purpose |
| --- | --- | --- |
| `runBootstraps` | `FALSE` | Use stored bootstrap results unless explicitly enabled. |
| `restartBootstraps` | `FALSE` | Regenerate bootstrap matrices when enabled with bootstrap execution. |
| `runRegularization` | `FALSE` | Use saved intercept diagnostics unless regularized CFA is enabled. |
| `parallelSupported` | `TRUE` | Use parallel computation for the relevant procedures. |
| `availableCores` | `15` | Number of parallel workers; reduce to suit your computer. |
| `B` | `9999` | Bootstrap resamples. |
| `M` | `500` | Full-sample plausible-value draws. |
| `MB` | `20` | Plausible-value draws inside each bootstrap resample. |
| `export` | `TRUE` | Export tables and figures. |

Set `parallelSupported <- FALSE` for sequential execution if needed. To rerun the bootstrap from scratch, set both `runBootstraps` and `restartBootstraps` to `TRUE`. Preserve a separate copy of stored results before regenerating them.

The script sets `RNGkind("L'Ecuyer-CMRG")` and `masterSeed <- 779`. Numerical output can still depend on the software environment and execution configuration.

## Replication objects

| File in `Data/` | Description |
| --- | --- |
| `replicationData.rds` | Questionnaire responses, sex, and age for the study sample. |
| `interceptsBPAQ.rds` | Saved BPAQ intercept diagnostics used to select partial invariance constraints. |
| `interceptsSD3.rds` | Saved SD3 intercept diagnostics used to select partial invariance constraints. |
| `baselineBoot.rds` | Bootstrap results for the confirmatory baseline model. |
| `moderatedBoot.rds` | Bootstrap results for the confirmatory model with sex interactions. |
| `saturatedBoot.rds` | Bootstrap results for the exploratory model with all trait-by-sex interactions. |
| `parsimoniousBoot.rds` | Bootstrap results for the exploratory parsimonious model and Machiavellianism-reference sensitivity analysis. |
| `correlatedFactorsBoot.rds` | Bootstrap results for the correlated three-factor SD3 model. |
| `psychopathyReferenceBoot.rds` | Bootstrap results for the bifactor S−1 model with psychopathy as the reference facet. |
| `narcissismReferenceBoot.rds` | Bootstrap results for the bifactor S−1 model with narcissism as the reference facet. |

## Contact

Nicolás González-Raposo — [nicgonzalezr@udd.cl](mailto:nicgonzalezr@udd.cl)
