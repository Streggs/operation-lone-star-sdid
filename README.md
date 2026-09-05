# Operation Lone Star: Quantitative Policy Impact Analysis
Quantitative policy impact analysis of Operation Lone Star using BLS QCEW data and Synthetic Difference-in-Differences.

## Overview

This project evaluates whether implementation of Operation Lone Star (OLS)
was associated with changes in employment, wages, and establishment activity
across selected industries in Texas border counties.

## Research Question

Did Operation Lone Star affect local labor-market outcomes and business
activity in Texas border counties relative to comparable border counties
outside Texas?

## Data

- U.S. Bureau of Labor Statistics Quarterly Census of Employment and Wages (QCEW)
- 2018–2025
- County × industry × quarter panel
- Industries: NAICS 11, 23, 42, 48–49, 56, and 72

## Methodology

Synthetic Difference-in-Differences (SDiD), following Arkhangelsky et al. (2021).

**Treatment counties:** 

All 32 Texas border counties as defined by the Texas
Department of State Health Services (DSHS). Of these, 9 counties were
excluded from the final analytical panel due to data suppression in the
BLS QCEW source data. This was caused by insufficient establishment counts to meet BLS
disclosure thresholds for one or more industry/quarter combinations.This left 23 counties in the final treatment group, as described below.

**Full list of 32 DSHS-defined border counties (FIPS)** 

48043, 48047, 48061, 48105, 48109, 48127, 48131, 48137, 48141, 48163,
48215, 48229, 48243, 48247, 48261, 48271, 48283, 48311, 48323, 48371,
48377, 48385, 48389, 48427, 48435, 48443, 48463, 48465, 48479, 48489,
48505, 48507

**9 counties excluded due to data suppression (FIPS)** 

48137, 48243, 48247, 48261, 48311, 48385, 48443, 48505, 48507

**Final treatment group (23 counties):**

48043, 48047, 48061, 48105, 48109, 48127, 48131, 48141, 48163, 48215,
48229, 48271, 48283, 48323, 48371, 48377, 48389, 48427, 48435, 48463,
48465, 48479, 48489

**Donor pool:** 

102 border counties in Arizona, California, and New Mexico.

## Key Findings

- Construction experienced the most severe downturn among all examined industries, showing significant declines across all three key metrics: total establishments, average weekly wages, and total employment.
- In the tested border counties, a drop in total establishments occurred across most studied industries, with the exception of administration & support (NAICS 56) and wholesale trade (NAICS 42), neither of which reached statistical significance.
- Beyond these findings, the remaining industries showed no statistically significant declines in either wages or employment.

## Repository Structure

- [`/report/`](./report/) — Full research report (includes Technical Appendix and Results Tables)
- [`/python/`](./python/) — Data acquisition, cleaning, and panel construction
- [`/R/`](./R/) — SDiD estimation and robustness analyses

## Research Report

[Read the full research report](report/Operation_Lone_Star_Quantitative_Policy_Impact_Analysis.pdf)

## Reproducibility

Raw QCEW files are not included in this repository. The Python pipeline
documents the data acquisition and cleaning process used to construct the
analytical panel.

### Running the pipeline

Both notebooks use relative paths and assume they are launched from the
project root (this repo's root folder, where the `sdid_exports_*` output
folders will be created).

1. Open `OLS_Data_Cleaning_and_Panel_Construction.ipynb` from the project
   root and run all cells — this creates the `sdid_exports_employment/`,
   `sdid_exports_estabs/`, and `sdid_exports_wages/` folders alongside it.
2. Open `OLS_SDID_Analysis_All_Outcomes.ipynb` **from the same project
   root** (not a different working directory) and run all cells.

If you see an error like `cannot open file 'sdid_exports_employment/
sdid_config.csv'`, your R kernel's working directory doesn't match where
Python wrote its output — check with `getwd()` in R and `os.getcwd()` in
Python; they should print the same path.

### Environment / versions used

- Python 3.13.3, pandas 2.2.3, numpy 2.2.6, requests 2.32.3
- R 4.6.1, synthdid 0.0.9

## Tools

Python | R | pandas | synthdid | BLS QCEW
