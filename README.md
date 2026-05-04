# PrismEval

This repository contains the R code for the PrismEval paper.

---

## Overview

We propose a Gaussian Variational EM (GVEM) algorithm for fitting the PrismEval 
model with model- and task-level random effects, applied to evaluate the 
prompt sensitivity of LLM on benchmark.

---

## Repository Structure

```
.
├── README.md                  # this file
├── requirements.R             # installs all required R packages
│
├── R/
│   ├── main.R                 # core GVEM functions (sourced by all scripts)
│   ├── real_data_clean.R      # step 1: clean and preprocess raw data
│   ├── real_data_run.R        # step 2: fit GVEM model to real data
│   └── simulation.R           # step 3: simulation study
│
├── data/
│   ├── main_alpha_results.csv  # estimated prompt effects from real data (included)
│   └── README_data.md         # instructions for downloading the raw data
│
└── results/
    ├── real_data/             # outputs from real_data_run.R
    └── simulation/            # outputs from simulation.R
```

---

## Execution Order

### To reproduce the simulation study only (recommended for reviewers)

```
R/simulation.R      (uses data/main_alpha_results.csv directly)
```

### To reproduce the full pipeline from scratch

```
[Public Website]
      ↓  download output.csv  (see data/README_data.md)
R/real_data_clean.R
      ↓  arc_resp.RData, dummy_matrix.RData
R/real_data_run.R
      ↓  main_alpha_results.csv  (same file already provided in data/)
R/simulation.R
```

> **Note:** `main_alpha_results.csv` provided in `data/` is the direct output
> of `R/real_data_run.R`. It is included so that the simulation study can be
> run and verified without requiring access to the raw data.

All scripts source `R/main.R` automatically — do not run `main.R` directly.

---

## Requirements

R version 4.0 or higher is required. Install all dependencies by running:

```r
source("requirements.R")
```

Required packages: `mirt`, `dplyr`, `tidyr`, `parallel`, `ggplot2`.

---

## Data

The raw data is publicly available and must be downloaded before running the
real data analysis. See [`data/README_data.md`](data/README_data.md) for
download instructions.

`main_alpha_results.csv` is already provided in `data/` and is sufficient to
reproduce the simulation study without downloading the raw data.

---

## Reproducing the Results

### Step 1: Install packages
```r
source("requirements.R")
```

### Step 2 (optional): Download and clean real data
Follow the instructions in `data/README_data.md`, then run:
```r
source("R/real_data_clean.R")
```

### Step 3 (optional): Fit model to real data
```r
source("R/real_data_run.R")
```

### Step 4: Run simulation study
```r
source("R/simulation.R")
```

---

## Note on Index Notation

The indices `i` and `j` in the code are used in the **reverse order** compared
to the paper. Specifically, `i` indexes groups in the code (items in the paper),
and `j` indexes items in the code (groups in the paper).

---

## Session Info

```
R version 4.5.2
```