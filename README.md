---
editor_options: 
  markdown: 
    wrap: 72
---

# MBAN-5560-A1

Machine Learning and Artificial Intelligence \# LOESS Cross-Validation
and Model Benchmarking

This project investigates the predictive performance of LOESS regression
under different resampling and hyperparameter tuning strategies. Using
simulated nonlinear data, the analysis compares single train–test
splits, nested k-fold cross-validation, bootstrap cross-validation with
out-of-bag (OOB) validation, and benchmark models.

The goal is to understand the **bias–variance tradeoff**,
**hyperparameter instability**, and the impact of **proper resampling
methods** on model selection and predictive accuracy.

------------------------------------------------------------------------

## Project Structure

-   `analysis.Rmd`\
    Main R Markdown file containing all code, analysis, plots, and
    written answers.

-   `analysis.pdf` / `analysis.html`\
    Rendered final report (included if required for submission).

-   `README.md`\
    Project overview and documentation.

------------------------------------------------------------------------

## Data Description

The data are simulated to have a known but complex nonlinear structure:

$$
f(x) = 50 + 15x - 0.3x^2 + 30\sin(x/3) + 10\cos(x)
$$

Random noise is added to generate realistic observations. This setup
allows direct comparison between the true function and fitted models.

------------------------------------------------------------------------

## Methods and Analysis

### Part A: Data Exploration

-   Visualization of noisy data and the true underlying function
-   Initial LOESS fits with varying span values
-   Discussion of nonlinearity and modeling challenges

### Part B: Single Train–Test Split

-   80/20 split with grid search over LOESS span
-   Demonstration of instability across different random seeds

### Part C: Nested 10-Fold Cross-Validation

-   Proper nested CV structure with correct loop ordering
-   Hyperparameter tuning for:
    -   LOESS span (degree = 1)
    -   LOESS span and degree (1 or 2)
-   Evaluation of stability and generalization performance

### Part D: Bootstrap Cross-Validation

-   Bootstrap CV with out-of-bag (OOB) validation
-   Comparison with k-fold CV in terms of variability and stability
-   Analysis of OOB sample size and randomness

### Part E: Benchmark Comparison

Benchmark models evaluated using the same outer splits: - Linear
regression - Polynomial regression (degree 4) - LOESS with default
parameters (span = 0.75)

Results are compared against the tuned LOESS model.

------------------------------------------------------------------------

## Key Findings

-   Hyperparameter tuning dramatically improves LOESS performance
    compared to default settings.
-   Nested k-fold cross-validation provides more stable and reliable
    estimates than single splits or bootstrap CV.
-   The tuned LOESS model outperforms linear, polynomial, and default
    LOESS models in both accuracy and reliability.
-   Additional tuning of polynomial degree provides only marginal
    improvement relative to tuning span alone.

------------------------------------------------------------------------

## Software and Libraries

The analysis is implemented in **R**, using:

-   `tidyverse`
-   `knitr`
-   `kableExtra`

All results are reproducible using the provided R Markdown file.

------------------------------------------------------------------------

## How to Reproduce

1.  Open the project `.Rproj` file in RStudio\
2.  Open `analysis.Rmd`\
3.  Knit the document to HTML or PDF

All figures, tables, and results will be generated automatically.

------------------------------------------------------------------------

## Notes

This project emphasizes **correct resampling methodology**,
particularly: - Proper nested cross-validation - Correct loop ordering
for hyperparameter tuning - Fair benchmark comparisons using identical
data splits

------------------------------------------------------------------------

## Author

Krishna\
Master's of Business Analytics
