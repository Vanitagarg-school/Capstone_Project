# Capstone Project: Socioeconomic Predictors of 8th Grade Math Performance

## Overview

This project explores the relationship between socioeconomic and demographic factors and student performance in Grade 8 mathematics across U.S. urban school districts. The analysis uses data from the NAEP Trial Urban District Assessment (TUDA) merged with community-level indicators from the NCES EDGE dataset. These indicators include variables such as parental education levels, poverty rates, unemployment, and racial/ethnic breakdowns.

The primary goal of this phase (Module 20) is to perform exploratory data analysis (EDA), identify patterns in the data, clean and prepare features, and develop a baseline machine learning model to serve as a reference in the final phase (Module 24).

## Research Question

How do various socioeconomic indicators—such as poverty levels, parental education, and racial/ethnic composition—impact student achievement in 8th-grade mathematics? Which factors are most predictive of performance?

## Dataset Description

Data Sources:
  - [NAEP TUDA District-Level Results](https://www.nationsreportcard.gov/ndecore/xplore/NDE)
  - [NCES EDGE Socioeconomic Data](https://nces.ed.gov/programs/edge/)
    Merged TUDA and EDGE datasets using district name and year.

Dataset: EDGE_Studentperf_socioeconomic_features.csv(https://github.com/Vanitagarg-school/Capstone_Project/blob/main/EDGE_Studentperf_socioeconomic_features.csv)

Total Observations: 305 school districts

Key Features:
  - Economic Disadvantage (% Eligible for NSLP, % Econ Disadvantaged)
  - Parental Education (HS or College completion)
  - Race/Ethnicity composition
  - Average Math Scores and Score Percentiles (10th to 90th)
    
## Jupyter Notebook 
https://github.com/Vanitagarg-school/Capstone_Project/blob/main/CapstoneProject_SocioeconomicFactor_StudentPerformance.ipynb
    
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

## Module 24

## Modeling Approach

We tested four different regression models to predict average student math scores using community-level data.

| Model                   | R² Score | RMSE   | MAE   | Training Time |
|------------------------|----------|--------|-------|----------------|
| Linear Regression       | 0.6520   | 6.20   | 4.97  | 0.0050 seconds |
| Ridge Regression        | 0.6518   | 6.20   | 4.97  | 0.0023 seconds |
| Decision Tree Regressor| 0.3836   | 8.25   | 5.81  | 0.0028 seconds |
| Random Forest Regressor| 0.6442   | 6.27   | 4.49  | 0.1889 seconds |

### What the Results Mean
- Linear and Ridge Regression performed best, offering strong predictive power and simplicity.
- Random Forest had slightly lower accuracy (R²) but delivered the lowest MAE — meaning its predictions were closer on average.
- Decision Tree underperformed overall and had higher errors, likely due to limited depth and over-simplification.

## Key Takeaways
#### Economic Disadvantage: Districts with higher percentages of students eligible for free or reduced lunch tend to have lower math scores.
#### Parental Education: Higher levels of parental education correlate with better student performance.

## Visual Summary
  - Actual vs. Predicted Plot: Demonstrated that predicted values closely align with actual scores.
  - Residual Plot: Showed that errors are randomly distributed, indicating a good model fit.
  - Distribution of Residuals: Confirmed that residuals follow a normal distribution, suggesting consistent model performance.
  - Feature Importance (Random Forest): Identified key factors such as economic disadvantage and parental education as significant predictors.

## Next Steps
  - Explore causal relationships using longitudinal data.
  - Expand the dataset to include rural and suburban districts.
  - Develop interactive dashboards for district-level decision-makers.
