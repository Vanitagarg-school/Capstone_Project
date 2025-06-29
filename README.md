# Capstone Project: Socioeconomic Predictors of 8th Grade Math Performance

## Overview

This project explores the relationship between socioeconomic and demographic factors and student performance in Grade 8 mathematics across U.S. urban school districts. The analysis uses data from the NAEP Trial Urban District Assessment (TUDA) merged with community-level indicators from the NCES EDGE dataset. These indicators include variables such as parental education levels, poverty rates, unemployment, and racial/ethnic breakdowns.

The primary goal of this phase (Module 20) is to perform exploratory data analysis (EDA), identify patterns in the data, clean and prepare features, and develop a baseline machine learning model to serve as a reference in the final phase (Module 24).

## Research Question

How do socioeconomic and demographic factors impact Grade 8 math achievement in urban school districts?

## Dataset Description

Data Sources:
  - [NAEP TUDA District-Level Results](https://www.nationsreportcard.gov/ndecore/xplore/NDE)
  - [NCES EDGE Socioeconomic Data](https://nces.ed.gov/programs/edge/)
Dataset: EDGE_Studentperf_socioeconomic_features.csv(https://github.com/Vanitagarg-school/Capstone_Project/blob/main/EDGE_Studentperf_socioeconomic_features.csv)
Total Observations: 305 school districts
Key Features:
  - Economic Disadvantage (% Eligible for NSLP, % Econ Disadvantaged)
  - Parental Education (HS or College completion)
  - Race/Ethnicity composition
  - Average Math Scores and Score Percentiles (10th to 90th)

## Data Cleaning Summary

Removed non-data rows containing metadata (e.g. "Percentage").
Replaced masked or suppressed values (‡, #, —) with NaN.
Converted all appropriate columns to numeric types.
Dropped fully missing columns (e.g. 'Pctl_0').

## Exploratory Data Analysis (EDA)

Summary statistics and .info() inspection conducted to understand feature distributions.
A correlation matrix revealed:
  - Positive correlation between higher parental education and student performance.
  - Negative correlation between economic disadvantage (NSLP eligibility) and math scores.
Scatterplot analysis supported the hypothesis that poverty levels inversely relate to academic performance.

## Key Observations

Districts with higher rates of poverty and lower parental education consistently showed lower math performance.
Percentile math scores (Pctl_25, Pctl_50, Pctl_75) were strongly correlated with average scores, confirming consistency in performance measurement.
Some features, like American Indian representation, had limited reporting and were not included in modeling due to high missingness.

## Baseline Model

Model Used: Linear Regression
Features Selected: 7 socioeconomic indicators
Target: Average Math Score (Avg_Score)
Evaluation Metrics:
  R-squared: 0.6520134305921936
  RMSE: 6.198129456779874
