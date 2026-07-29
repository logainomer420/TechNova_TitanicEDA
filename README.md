# TechNova_TitanicEDA

Exploratory Data Analysis (EDA) on the Titanic passenger dataset — a classic dataset for practicing 
data cleaning and visualization, with real missing values and natural outliers.

## Overview

This project loads the public Titanic dataset (891 passengers, 15 columns) and performs a full 
exploratory analysis: descriptive statistics, missing value treatment, outlier detection, and 
visualizations of key distributions and relationships.

## Contents

| File | Description |
|---|---|
| `eda.ipynb` | Full Colab notebook — code, output, and charts |
| `eda.py` | Plain Python script version of the analysis |
| `EDA_Report.pdf` | Summary report with stats tables and charts |
| `titanic_raw.csv` | Original, unmodified dataset |
| `titanic_cleaned.csv` | Dataset after cleaning (missing values filled, outliers capped) |

## What the analysis covers

**1. Descriptive statistics**
Mean, median, and standard deviation computed for all numeric columns (`age`, `fare`, `pclass`, `sibsp`, `parch`, `survived`).

**2. Missing value handling**
- `age` (~20% missing) → filled with median
- `embarked` / `embark_town` (~0.2% missing) → filled with mode
- `deck` (~77% missing) → dropped (too sparse to impute reliably)

**3. Outlier detection**
Used the IQR method (1.5× interquartile range) on `fare` and `age`. Outliers were **capped** 
(winsorized) rather than removed, to reduce their influence while preserving sample size.

**4. Visualizations**
- Age and fare distributions (histograms + boxplots, before/after cleaning)
- Survival counts by sex and passenger class
- Correlation heatmap across numeric features

**5. Summary report**
All of the above compiled into a shareable PDF report.

## Tools used

- Python (Google Colab)
- pandas, numpy
- matplotlib, seaborn

## How to run

1. Open `eda.ipynb` in [Google Colab](https://colab.research.google.com) or Jupyter.
2. Run all cells top to bottom — no installs needed if using Colab.
3. `EDA_Report.pdf` will be generated in the working directory.

## Key takeaways

- Overall survival rate was ~38%, but varied sharply by sex and passenger class.
- Fare was heavily right-skewed, with a small number of high-fare outliers (mostly 1st-class passengers).
- `pclass` and `fare` showed the strongest correlation with `survived` among numeric features.
