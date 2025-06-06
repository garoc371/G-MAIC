This repository includes code to reproduce the simulation and analysis for the manuscript "Regression augmented weighting adjustment for indirect comparisons in health decision modelling"

## Scripts Overview:
`sim_pop_norm.R`: Simulates population data with normally distributed covariates.
`sim_pop_nonnorm.R`: Simulates population data with non-normally distributed (mixed) covariates.
`cpp_gcomp_norm.R`: Runs various analysis methods (Bucher, MAIC, Bayesian G-computation, G-MAIC) on the simulated normal data.
`cpp_gcomp_nonnorm.R`: Runs the same analysis methods on the simulated non-normal data.
`analysis_norm.R`: Processes and visualizes results from the normal data analysis.
`analysis_nonnorm.R`: Processes and visualizes results from the non-normal data analysis.


## Reproducing the Main Analysis (2000 Monte Carlo Replications):
## Data Simulation:

  - Run `sim_pop_norm.R` (outputs to `pop_data/normal/`).
  - Run `sim_pop_nonnorm.R` (outputs to `pop_data/non_norm/`). (Ensure these output directories exist or are created by the script).

## Run Analyses:

  - Run cpp_gcomp_norm.R (saves results, e.g., to `results/normal2/` or `results/normal3/` as per script paths).
  - Run cpp_gcomp_nonnorm.R (saves results, e.g., to `results/non_norm2/` or `results/non_norm3/`). (Ensure these output directories exist or are created by the script. Adjust paths inside these scripts if needed).


## Generate Summaries & Plots:

  - Run `analysis_norm.R` and `analysis_nonnorm.R` to process results and generate plots.
  - Note on Saving Plots: To save the generated plots as image files, you must uncomment the `ggsave()` lines within the `analysis_norm.R` and `analysis_nonnorm.R` scripts. Ensure the output directories (e.g., `plots/normal/` and `plots/non_norm/`) exist before running.


### Scripts are set up for N_sim = 2000 for the main analysis.

### Optional: Running with 5000 Monte Carlo Replications:
If you wish to run the analysis for 5000 Monte Carlo replications:

 1. Modify `N_sim`: In all four simulation (`sim_pop_*.R`) and computation (`cpp_gcomp_*.R`) scripts, change the N_sim variable from 2000 to 5000.
 2. Run Simulation & Computation: Execute these modified scripts as per step 1 and 2 in "Reproducing the Main Analysis".
 3. Adjust Analysis Scripts:
      In `analysis_norm.R` and `analysis_nonnorm.R`, when results are combined (e.g., in the `bind_rows(...)` call), you will need to change the object name `mis_bayes.results` to `mis_bayes_gcomp.results`. This is because naming differences in the past simulations.
 4. Run Analysis Scripts: Run `analysis_norm.R` and `analysis_nonnorm.R`.
