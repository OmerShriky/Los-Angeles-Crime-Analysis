# Los Angeles Crime Analysis & Demographic Vulnerability (2020-2024)

## Overview
This repository contains the complete data analysis, statistical testing, and visualization code for an in-depth study of crime patterns in the City of Los Angeles. 

The project aims to identify underlying macro-level crime trends over time and evaluate demographic disparities in violent crime victimization. We utilize advanced statistical modeling to explore how vulnerability to violent crime shifts fundamentally across different life stages and genders, and how these dynamics evolved during the significant crime drop observed in 2024.

## Dataset
The analysis is based on the official Crime Data from 2020 to Present, published by the City of Los Angeles on its open data platform. 
* **Source:** [Los Angeles Open Data Portal](https://catalog.data.gov/dataset/crime-data-from-2020-to-present)
* **Data Access:** The notebook fetches the data directly via API, ensuring reproducibility without the need to download heavy CSV files manually.

## Key Methodologies
1. **Normality Assessment:** Utilization of **Q-Q Plots (Quantile-Quantile Plots)** to visually evaluate the distribution of crime data and test for normality assumptions prior to non-parametric testing.
2. **Non-Parametric Temporal Comparisons:** Application of the **Wilcoxon Signed-Rank Test** to assess the statistical significance of differences in crime rates across matched temporal intervals.
3. **Macro-Level Trend Analysis:** Implementation of **Negative Binomial Regression** to model crime counts and evaluate the statistical significance of temporal shifts (specifically the decline in 2024).
4. **Micro-Level Demographic Analysis:** Execution of **Chi-Square Tests of Independence** to examine the relationship between victim gender and crime severity (Violent vs. Non-Violent). This includes age stratification into specific cohorts (`<18`, `18-25`, `26-35`, `36-50`, `51-64`, `65+`) and temporal comparisons (Pre-2024 vs. 2024).
5. **Multiple Testing Corrections:** Strict control of Type I errors across multiple comparisons using **False Discovery Rate (FDR) / Benjamini-Hochberg** and the highly conservative **Bonferroni** corrections.

## Key Findings
* **The 2024 Crime Drop:** A statistically significant, citywide decline in overall crime rates occurred in the year 2024 compared to previous years.
* **Impact on Minority Demographics:** The reduction in crime was not uniform; Black and Hispanic populations experienced a highly significant shift, demonstrating a substantial decrease in crime victimization during the 2024 period.
* **The Demographic Pivot:** A persistent structural shift exists in violent victimization based on age and gender. Females under the age of 50 face a significantly higher relative probability of a crime being violent. From age 51 onwards, the dynamic inverts, and males become disproportionately more likely to experience violence.

## Prerequisites & Libraries
The analysis is written in Python 3 and designed to run in Google Colab. The following libraries and modules are utilized across the project:
* `requests`, `urllib.request` & `io` - Handling API calls, URL requests, and data streams to fetch the raw dataset.
* `pdfplumber` - Parsing and text extraction from PDF documents (requires explicit installation: `!pip install pdfplumber -q`).
* `pandas` - Data manipulation, cleaning, and aggregation.
* `numpy` - Numerical operations and array handling.
* `statsmodels` - Formulating regression models (`formula.api`) and applying multiple testing corrections like Bonferroni and FDR (`multipletests`).
* `scipy` - Conducting statistical hypothesis testing (`scipy.stats` for Chi-Square and Wilcoxon tests).
* `patsy` - Creating design matrices and defining contrast coding (`Sum` contrasts) for the regression models.
* `scikit-learn` (`sklearn`) - Evaluating regression model performance using metrics such as Mean Squared Error (MSE) and Mean Absolute Error (MAE).
* `matplotlib.pyplot` & `seaborn` - Generating statistical graphics, bar plots, and demographic visualizations.

## How to Run and Reproduce the Analysis
This project is built to run seamlessly in **Google Colab**. Follow these steps to reproduce the exact findings of our study:

1. **Open the Notebook:** 
   * Download the `LA_Crime_Analysis.ipynb` file from this repository.
   * Go to [Google Colab](https://colab.research.google.com/) and upload the notebook (`File` -> `Upload notebook`).
2. **Run the Environment:**
   * No local data download is required. The first cell in the notebook contains the script to fetch the latest dataset directly from the LA City API via `requests` and `io`.
   * Go to the top menu and select `Runtime` -> `Run all`.
3. **Execution Time:** 
   * Note that downloading the raw CSV via the API (over 1 Million rows) takes appriximatly 4-5 minutes depending on your internet connection and Colab's allocated instance.
4. **Outputs:** 
   * The notebook will automatically clean the data, print the statistical summaries, output the corrected p-value tables, and generate the comparative bar charts.

## Project Structure
* `LA_Crime_Analysis.ipynb`: The main Jupyter Notebook containing all code, comments, and visualizations.
* `README.md`: Project documentation.

## Authors
* Omer Shriky
* Ronen Agayev

---
*Note: This project was conducted as part of an academic research assignment.*
