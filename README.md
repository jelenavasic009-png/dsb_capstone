# 🚢 Vignette Sales and Vessel Revenue Analysis (`dsb_capstone`)

> **Data Science Capstone Project** | Exploratory Data Analysis, Feature Engineering & Revenue Trends

[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Library-Pandas-orange.svg)](https://pandas.pydata.org/)
[![Status](https://img.shields.io/badge/Status-Completed%20%2F%20Active-success.svg)]()

---

## 📌 Project Overview
The primary objective of this project is to answer a core business question: **How do monthly revenues and the volume of sold vignettes trend over the years, and in what ways do vessel characteristics (such as length) impact financial outcomes?**

By leveraging historical transactional logs (`Baza podataka 5 godina.xlsx`), this project conducts a thorough **Exploratory Data Analysis (EDA)** alongside robust **Feature Engineering** to transform raw operational data into structured, actionable insights for future predictive forecasting models[cite: 2].

---

## 📂 Data Source & Structure
* **Source Dataset:** Internal Excel logs tracking issued vessel vignettes over a 5-year period[cite: 2].
* **Initial Dimensions:** 26,764 rows and 12 initial columns[cite: 2].
* **Key Attributes:** Unique vignette serial numbers, vessel names, registration IDs, physical attributes (vessel length), validity periods, regional branch offices issuing documents, and financial metrics (with and without tax)[cite: 2].

---

## ⚠️ Data Quality & Challenges
Initial data auditing revealed several structural obstacles that required systematic cleaning:
* **Missing Data:** Certain rows lacked critical details, such as vessel names or registration marks (~79 missing vessel IDs), requiring careful imputation[cite: 2].
* **Manual Entry Flaws:** Empty rows at the bottom of spreadsheets and automatically generated summary rows introduced noise that needed removal[cite: 2].
* **Date Formatting:** Raw date entries started as plain text strings (`object` data type) and were converted into proper `pandas datetime` objects for accurate chronological tracking[cite: 2].

---

## 🔄 Step-by-Step EDA & Feature Engineering Pipeline
The analysis is structured sequentially within the Jupyter/Colab notebook (`JelenaVasic_capstone.ipynb`)[cite: 1, 2]:

1. **Data Sourcing & Initial Loading:** Imported raw Excel files into a Pandas DataFrame and verified structural dimensions (`26,764 rows`, `12 columns`)[cite: 2].
2. **Structural Audit & Descriptive Statistics:** Evaluated column types via `info()` and calculated baseline descriptive statistics (mean, min, max, percentiles) using `describe()`[cite: 2].
3. **Data Cleansing:** Identified null values via `isnull().sum()` and filtered out unusable rows lacking critical identifiers to safeguard data integrity[cite: 2].
4. **Categorical Grouping & Business Insights:** Analyzed transaction volumes and gross revenue generation across regional branch offices (such as Tivat, Zelenika, and Bar) using `value_counts()` and `groupby()`[cite: 2].
5. **Datetime Normalization & Temporal Decomposition:** Converted textual dates into formal `datetime64` objects to extract dedicated `Year` and `Month` features for year-over-year and seasonal trend analysis[cite: 2].
6. **Data Visualization:** Generated visual analytical reports using Matplotlib and Seaborn, including office distribution counts, vessel length histograms, and seasonal revenue trend line charts[cite: 1, 2].
7. **Advanced Feature Engineering:** 
   * *Data Imputation:* Filled missing vessel names with 'Unknown Vessel' and missing lengths with the median value[cite: 2].
   * *Categorization:* Classified vignettes into distinct price tiers (`Low Price`, `Medium Price`, `High Price`)[cite: 2].
   * *Time Series Metrics:* Calculated time gaps (`diff`) between consecutive transactions to capture temporal momentum[cite: 2].
   * *Dimensionality Reduction:* Applied `StandardScaler` and Principal Component Analysis (`PCA`) to project numerical vessel and pricing attributes into principal components (`PCA1`, `PCA2`)[cite: 2].
8. **Predictive Modeling (Introductory Preview):** Implemented a foundational Linear Regression model grouped by year and office location to establish a baseline for future inventory demand forecasting[cite: 2].

---

## 🛠️ Technologies & Libraries Used
The project is built within a **Python 3** environment using the following core packages[cite: 2]:

| Library | Primary Purpose |
| :--- | :--- |
| **Pandas & NumPy** | Data loading, cleaning, feature engineering, and aggregation[cite: 2]. |
| **Matplotlib & Seaborn** | Visual exploratory analysis, discovering seasonal trends, and tracking data distributions[cite: 1, 2]. |
| **Scikit-learn** | Preprocessing (`StandardScaler`), feature transformation (`PCA`), and introductory predictive modeling (`Linear Regression`)[cite: 2]. |

---
*For a detailed walkthrough of the code and implementation details, please refer to the [JelenaVasic_capstone.ipynb](https://github.com/jelenavasic009-png/DSB-Unit-02/tree/main) notebook.*
