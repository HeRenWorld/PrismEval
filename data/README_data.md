# Data

## Raw Data (`output.csv`)

The raw data used in this paper is the ARC (AI2 Reasoning Challenge) benchmark,
publicly available at:

> **https://huggingface.co/datasets/nlphuji/DOVE_Lite**

### Download Instructions

1. Go to the URL above
2. Download the file and rename it `output.csv`
3. Place it in this `data/` folder
4. Run `R/real_data_clean.R` to preprocess it

### Processed Data

Running `R/real_data_clean.R` will generate the following files in `data/`,
which are required by `R/real_data_run.R`:

| File | Description |
|---|---|
| `arc_resp.RData` | Item response matrix with model labels |
| `dummy_matrix.RData` | Prompt factor dummy matrix (S x P) |
| `arc_df_final_wide.RData` | Full cleaned wide-format data frame |

**Note:** These processed files are not included in the repository to avoid
redistributing third-party data. They must be generated locally by running
`R/real_data_clean.R` after downloading `output.csv`.

---

## Simulation Input (`main_alpha_results.csv`)

This file is included directly in the repository and contains the estimated
prompt effect coefficients (`alpha_main`) from the real data analysis
(`R/real_data_run.R`).

The simulation study (`R/simulation.R`) uses these real estimated parameters
to generate synthetic data, making the simulation setting grounded in the actual
prompt effects observed in the ARC benchmark.
**Reviewers can therefore run the simulation study directly without
completing the real data analysis first.**

| File | Description | Source |
|---|---|---|
| `main_alpha_results.csv` | Estimated model-specific prompt effect coefficients from real data | Output of `R/real_data_run.R` |
