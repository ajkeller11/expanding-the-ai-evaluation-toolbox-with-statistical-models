# NIST AI 800-3 Code Supplement

This repository contains data and code to reproduce results from _[Expanding the AI Evaluation Toolbox with Statistical Models]()_. See the paper for more details on methods and motivation. Existing packages available to execute similar analyses include [`HiBayes`](https://ukgovernmentbeis.github.io/hibayes/) and [`vitals`](https://vitals.tidyverse.org).

Paper figures and tables can be reproduced by running:

```sh
make all
```

Or run individual analysis groups:

```sh
make gpqa
make bbh
make mmlu
make simulations
```

Outputs are written to: [`figures/`](figures) and [`tables/`](tables).
The standard analysis runs also generate the appendix diagnostic figures, including GPQA Figure C.4 and BBH/MMLU Figure C.5 outputs.

## Data files
- [`benchmark_results/`](benchmark_results): Extracted scores for GPQA Diamond, BIG-Bench Hard, and Global-MMLU Lite benchmark runs
- [`simulations/simulation_results/`](simulations/simulation_results/): CSVs containing simulation results reported in paper

[`simulations/run_simulations.R`](simulations/run_simulations.R) contains functions to reproduce the simulation results data.

## Analysis scripts
- [`analysis_scripts/gpqa_analysis.R`](analysis_scripts/gpqa_analysis.R): Generates GPQA Diamond outputs from benchmark results (Figure 1, Figure 4, Figure C.2, Figure C.4, Table C.9)
- [`analysis_scripts/bbh_analysis.R`](analysis_scripts/bbh_analysis.R): Generates BIG-Bench Hard outputs from benchmark results (Figure 5, Figure C.5a)
- [`analysis_scripts/mmlu_analysis.R`](analysis_scripts/mmlu_analysis.R): Generates Global-MMLU Lite outputs from benchmark results (Figure C.3, Figure C.5b)
- [`analysis_scripts/simulation_analysis.R`](analysis_scripts/simulation_analysis.R): Generates "toy experiment" outputs from simulation results (Figure 2, Figure C.1, Table C.5, Table C.6)
- [`src/`](src): Helper functions; GLMMs are fit and estimated in [`src/analysis_functions.R`](src/analysis_functions.R)

Table C.5 consumes baseline simulation-result CSVs for Settings A, B, and C from [`simulations/simulation_results/`](simulations/simulation_results).

Note that depending on available computational resources, it may take several minutes to run the analysis scripts, particularly those for BIG-Bench Hard and Global-MMLU Lite.

## Requirements

Reproduction scripts are written in R. To install required packages, run `renv::restore()`. 

## Disclaimer

References and uses of existing software in this repository are not intended to imply recommendation or endorsement of any product or service by NIST, nor are they intended to imply that the software identified or used is necessarily the best available for the purpose.
