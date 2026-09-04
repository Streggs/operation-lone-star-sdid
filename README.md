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

**Treatment counties:** 23 Texas' Border Counties, with the following Federal Information Processing Standards (FIPS): 
  ```text
  48127, 48163, 48271, 48283, 48323, 48463, 48465, 48043, 48105, 48109, 
  48141, 48229, 48371, 48377, 48389, 48435, 48047, 48061, 48131, 48215, 
  48427, 48479, 48489
  ```
**Donor pool:** 102 Border counties in Arizona, California, and New Mexico.

## Key Findings

- Construction experienced the most severe downturn among all examined industries, showing significant declines across all three key metrics: total establishments, average weekly wages, and total employment.
- In the tested border counties, a drop in total establishments occurred across all studied industries, with the sole exception of administration and support (NAICS 56).
- Beyond these findings, the remaining industries showed no statistically significant declines in either wages or employment.

## Repository Structure

- `/report/` — Full research report
- `/python/` — Data acquisition, cleaning, and panel construction
- `/R/` — SDiD estimation and robustness analyses
- `/documentation/` — Technical appendix
- `/outputs/` — Figures and results tables

## Research Report

[Read the full research report](report/Operation_Lone_Star_Quantitative_Policy_Impact_Analysis.pdf)

## Reproducibility

Raw QCEW files are not included in this repository. The Python pipeline
documents the data acquisition and cleaning process used to construct the
analytical panel.

## Tools

Python | R | pandas | synthdid | BLS QCEW
