# Dark Triad and trait aggression

Replication package for **“Sex differences in the relationship between the Dark Triad and trait aggression: A variance-weighted interpretation of the bifactor model.”**

## Requirements

R 4.5.3; lavaan 0.6-21; semTools 0.5-8; lessSEM 1.5.7. Additional packages:

```r
install.packages(c("tidyverse", "pbmcapply", "see", "kableExtra", "gt", "knitr", "webshot2"))
```

Quarto is needed to render the analysis document. PNG table exports require Chrome/Chromium.

## Run the analyses

1. Place the analysis document in `Scripts/`, and the dataset (`replicationData.rds`), saved intercept diagnostics, and bootstrap results in `Data/`.
2. Create `Tables/` and `Plots/` alongside those folders.
3. Open `Scripts/replicationScript.qmd` and execute the R chunks in order, with the working directory set to `Scripts/`.

The script defaults to using saved bootstrap results (`runBootstraps <- FALSE`) and intercept diagnostics (`runDiagnostics <- FALSE`). Adjust `availableCores` to your computer, or set `parallelSupported <- FALSE` for sequential execution.

Analyses use 500 plausible-value draws; bootstrap analyses target 9,999 successful resamples with 20 draws per resample. The master seed is 779.

To rerun the bootstrap from scratch, set both `runBootstraps` and `restartBootstraps` to `TRUE`. This is computationally intensive and overwrites the saved bootstrap files.

Tables and figures are exported to `Tables/` and `Plots/`.

## Contact

Nicolás González-Raposo — nicgonzalezr@udd.cl
