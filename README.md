# Airbnb Pricing Analysis in Hawaii

This repository contains a cleaned portfolio version of an Airbnb pricing analysis project using public Airbnb listing data from Hawaii. The goal of the project is to understand which listing, host, review, and location characteristics are associated with Airbnb nightly prices.

The main modelling approach is multiple linear regression, with an emphasis on interpretability. Supplementary machine learning models are also used as prediction benchmarks to compare whether more flexible methods can improve predictive performance.

## Project Overview

Airbnb prices can vary substantially depending on property size, room type, location, review quality, host reputation, and booking restrictions. This project studies how these factors are associated with nightly listing prices in Hawaii.

The response variable is log nightly price. Log transformation is used to reduce the strong right skew in raw Airbnb prices and to make regression coefficients easier to interpret approximately as percentage changes.

The analysis includes:

- Data cleaning and preprocessing
- Exploratory data analysis
- Variable transformation
- Multiple linear regression
- Interaction terms
- BIC-based model selection
- Partial F-tests
- Residual diagnostics
- 10-fold cross-validation
- Machine learning prediction benchmarks
- Interpretation of Airbnb pricing factors

## Research Question

Which Airbnb listing characteristics are associated with higher nightly prices in Hawaii?

In particular, the project examines whether larger listings and entire-home room types are associated with higher prices, while also accounting for review quality, host characteristics, neighbourhood, and booking restrictions.

## Repository Structure

```text
.
├── README.md
├── airbnb_hawaii_pricing_analysis.Rmd
├── data/
│   └── README.md
└── .gitignore
```

## Data Source

The original raw Airbnb data was obtained from Inside Airbnb:

> Inside Airbnb. (2024). *Get the Data*. https://insideairbnb.com/get-the-data/

The raw dataset is not included in this repository because the file is too large for direct upload to GitHub.

To reproduce the analysis, download the Hawaii raw listings dataset from Inside Airbnb, place it inside the `data/` folder, and rename it as:

```text
original_data.csv
```

The R Markdown file expects the data file to be located at:

```text
data/original_data.csv
```

## Methods

The main model is a multiple linear regression model for log nightly Airbnb price. The analysis includes listing size variables, room type, review-related variables, host-related variables, neighbourhood effects, and an interaction between accommodation capacity and room type.

Machine learning models are used as supplementary prediction benchmarks. These models help compare predictive performance and assess whether more flexible methods can capture nonlinear structure in the data.

The purpose of the project is not only to predict Airbnb prices, but also to understand which factors are associated with price differences.

## Main Findings

The analysis suggests that larger listings tend to have higher nightly prices. Accommodation capacity, number of bedrooms, and number of bathrooms are positively associated with price.

Room type also matters, especially through its interaction with accommodation capacity. This suggests that the relationship between listing size and price differs across room types.

Review quality, location-related variables, and host reputation also help explain variation in Airbnb prices. Machine learning benchmarks achieved stronger predictive performance than the linear regression model, suggesting that nonlinear relationships may exist in the data. However, the linear regression model remains useful because it provides clearer interpretation of the relationship between predictors and price.

## Reproducibility

To reproduce the analysis:

1. Download the Hawaii listings dataset from Inside Airbnb.
2. Place the raw CSV file inside the `data/` folder.
3. Rename the file as `original_data.csv`.
4. Open `airbnb_hawaii_pricing_analysis.Rmd` in RStudio.
5. Knit the R Markdown file.

The analysis may require the following R packages:

```r
install.packages(c(
  "tidyverse",
  "ggplot2",
  "dplyr",
  "readr",
  "knitr",
  "rmarkdown",
  "broom",
  "car",
  "FNN",
  "ranger",
  "xgboost"
))
```

Some machine learning benchmark sections are optional. If packages such as `FNN`, `ranger`, or `xgboost` are not installed, the corresponding benchmark method will be skipped.

## Notes

This repository is a cleaned portfolio version of an academic data analysis project. It removes course-specific submission details and focuses on the statistical modelling workflow, reproducibility, and interpretation of results.

The original raw Airbnb dataset is not stored in this repository. Users who want to reproduce the analysis should download the raw data directly from Inside Airbnb.
