# Identifying the optimal rapid antigen test for screening and determining the end of isolation: a modeling study

## 1. Monolix

(Step 1) Download MONOLIX software (https://monolixsuite.slp-software.com/getting-started/2024R1/download) and install it in your PC
(Step 2) To perform NLME estimation, open the file "Both.mlxtran" in MONOLIX or follow a MONOLIX guideline (https://monolixsuite.slp-software.com/monolix/2024R1/estimation-tasks).
Note that in both cases, you should put the below files in a same working directory.
- "All.csv" is data of nasal and saliva paired longitudinal viral load data for symptomatic COVID-19 patients.
- "model_both.txt" is the description for mathematical model of viral kinetics.
(Step 3) After the etimation is done, extract the following result files.
- "populationParameters_Both.txt" includes the estimated population (fixed effect) parameters 
- "estimatedIndividualParameters_Both.txt" includes the estimated individual parameters (related to random effect). 
Note that these files are used to run R simulations in the next section.


## 2. R_simulation

R codes simulate an in silico analysis for comparison between nasal RAT and saliva RAT under pre-symptomatic screening and post-symptomatic ending isolation.
CSV files incidate result files for our primary outcomes with uncertainty from R simulations.

( Generating virtual individuals )
"Generating_virtual.R" shows generating virtual individuals using the estimated viral dynamics parameters.

( Main simulations )
1) "Fig2A_Dynamics.R" shows the estimated viral load trajectories at both nasal and saliva samples using a viral dynamics model.
2) "Fig2B_Profiles.R" shows computing infectiousness profiles from the estimated viral load trajectories.
3) "Fig3_Pre.R" shows simulating the effectiveness of RATs in the pre-symptomatic screening.
4) "Fig4_Post.R" shows simulating the effectiveness of RATs in the post-symptomatic ending isolation.

( Supplementary simulations )
1) "Sensitivity_Negbio.R" shows the simulation using negative binomial offspring distribution compared with Poisson offspring ditribution.
2) "Sensitivity_SI_IP.R" shows sensitivity analyses varying screening period (serial interval; SI) and isolation period (IP).
3) "Sensitivity_R0.R" shows sensitivity analyses varying a basic reproduction number (R0).
4) "Sensitivity_Scale.R" shows sensitivity analyses varying a scaling factor (related to the assay's sensitivity).

* Text files and R (version 4.2.3) codes above should be in the same location.
* Please set your working directory in R code - "setwd("~/Desktop/XXX")".
