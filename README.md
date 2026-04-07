# Multivariate-exploration-of-a-metabolomics-dataset

# Multivariate Exploration of a Metabolomics Dataset

An R-based project for multivariate analysis of a metabolomics dataset using `SummarizedExperiment`, dimensionality reduction (PCA and MDS), and exploratory data visualization.

## Overview

This project analyzes a metabolomics dataset consisting of **120 metabolites** measured across **60 samples** (Cases and Controls), integrating clinical metadata such as age, sex, BMI, batch, and cholesterol levels. The analysis is implemented as a fully reproducible R Markdown document.

## Workflow

### 1. Data Integration & Sample Selection
Abundance data, sample metadata, and metabolite annotations are loaded and assembled into a `SummarizedExperiment` object. A balanced subset of **50 samples** (25 Cases, 25 Controls) is randomly selected for downstream analysis.

### 2. Data Preparation
- Metabolites with >20% missing values are removed
- Remaining NAs are imputed using **K-Nearest Neighbours** (KNN, k=5) via the `impute` Bioconductor package
- Abundance values are **log₂-transformed** and **z-score scaled** per metabolite

### 3. PCA Analysis
Principal Component Analysis is performed on the scaled data. Samples are visualized in PC1/PC2 space and colored by group, batch, sex, age, BMI, and cholesterol to identify sources of variance. The top metabolite contributors (loadings) to PC1 and PC2 are reported.

### 4. MDS Comparison
Classical Multidimensional Scaling (MDS) is applied on Euclidean distances and compared side-by-side with PCA to assess consistency across dimensionality reduction methods.

## Input Files

| File | Description |
|---|---|
| `assay.csv` | Metabolite abundance matrix (120 metabolites × 60 samples) |
| `sample_metadata.csv` | Clinical variables per sample (group, batch, sex, age, BMI, cholesterol) |
| `feature_metadata.csv` | Metabolite annotations (biochemical class, analytical platform) |

## Key Packages

| Package | Purpose |
|---|---|
| `SummarizedExperiment` | Integrated data container for omics data |
| `impute` | KNN-based missing value imputation |
| `ggplot2` | Data visualization |
| `gridExtra` | Multi-panel plot layouts |
| `kableExtra` | Formatted tables in R Markdown |  

## How to Run

1. Clone this repository
2. Place `assay.csv`, `sample_metadata.csv`, and `feature_metadata.csv` in the project root
3. Open `Multivariate_exploration_of_a_metabolomics_dataset.Rmd` in RStudio
4. Click **Knit** to generate the HTML report
