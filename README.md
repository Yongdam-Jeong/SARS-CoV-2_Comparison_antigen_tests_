# Identifying the optimal rapid antigen test for screening and determining the end of isolation: a modeling study

## 1. Monolix

(Step 1) Download and install Monolix
- Download the Monolix Suite from https://monolixsuite.slp-software.com/getting-started/2024R1/download
- Install it on your computer.
  
(Step 2) Run the NLME estimation
- Open the file "Both.mlxtran" in Monolix and perform NLME estimation by following the Monolix guideline:
https://monolixsuite.slp-software.com/monolix/2024R1/estimation-tasks
- Make sure the following files are in the same working directory:
* "All.csv": paired longitudinal nasal and saliva viral load data for symptomatic COVID-19 patients.
* "model_both.txt": description of the viral kinetics mathematical model.
  
(Step 3) Export the estimation results
- After the etimation is completed, export the following result files:
* "populationParameters_Both.txt": estimated population (fixed-effect) parameters.
* "estimatedIndividualParameters_Both.txt": estimated individual parameters (related to random effects).
- These files are required for running the R simulations in the next section.


## 2. R_simulation

The R scripts perform in silico analyses comparing nasal and saliva RATs for pre-symptomatic screening and post-symptomatic ending of isolation.
The CSV files are output files for the primary outcomes, including uncertainty from the simulations.

( Generating virtual individuals )
"Generating_virtual.R": generates virtual individuals using the estimated viral dynamics parameters.
"VL.csv": generated 10,000 virtual COVID-19 infected individuals with viral loads over time

( Main simulations )
1) "Fig2A_Dynamics.R": shows the estimated viral load trajectories for nasal and saliva samples using the viral dynamics model.
2) "Fig2B_Profiles.R": computes infectiousness profiles from the estimated viral load trajectories.
3) "Fig3_Pre.R": simulates the effectiveness of RATs for pre-symptomatic screening.
4) "Fig4_Post.R": simulates the effectiveness of RATs for post-symptomatic ending of isolation.

( Supplementary simulations )
1) "Sensitivity_Negbio.R": compares simulations using a negative binomial offspring distribution with those using a Poisson offspring distribution.
2) "Sensitivity_SI_IP.R": sensitivity analyses varying the screening period (serial interval, SI) and isolation period (IP).
3) "Sensitivity_R0.R": sensitivity analyses varying the basic reproduction number (R0).
4) "Sensitivity_Scale.R": sensitivity analyses varying the scaling factor related to assay sensitivity.

* All text files and R scripts (R version 4.2.3) should be stored in the same directory.
* In each R script, set your working directory, for example: "setwd("~/Desktop/XXX")".
