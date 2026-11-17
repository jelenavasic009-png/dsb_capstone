# 🛥️ Vignette Sales and Vessel Revenue Analysis (`dsb_capstone`)

> **Data Science Capstone Project** | End-to-End Exploratory Data Analysis, Feature Engineering, Predictive Modeling & Anomaly Detection

[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Library-Pandas-orange.svg)](https://pandas.pydata.org/)
[![Scikit-Learn](https://img.shields.io/badge/ML-Scikit--Learn-F7931E.svg)](https://scikit-learn.org/)
[![Prophet](https://img.shields.io/badge/Forecasting-Prophet-008080.svg)](https://facebook.github.io/prophet/)
[![Plotly](https://img.shields.io/badge/Visualization-Plotly-3F4F75.svg)](https://plotly.com/python/)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)]()

---

## 📌 Project Overview
The primary objective of this Capstone project is to analyze five years (2021–2025) of maritime vignette issuance records (`Baza podataka 5 godina.xlsx`) to answer three core operational and financial questions:
1. **What are the primary drivers behind individual vignette pricing and total port revenue?**
2. **How do seasonal demand patterns and customer loyalty evolve across regional branch offices?**
3. **Can machine learning models accurately forecast future monthly revenue, predict vignette pricing, and isolate high-value vessel anomalies?**

By combining thorough **Exploratory Data Analysis (EDA)**, domain-driven **Feature Engineering**, **Supervised & Unsupervised Machine Learning**, and **Time-Series Forecasting**, this project transforms 26,764 raw transactional records into actionable strategic recommendations for maritime authorities.

---

## 📁 Repository Structure
```text
dsb_capstone/
├── data/
│   └── Baza podataka 5 godina.xlsx          # Raw 5-year maritime vignette dataset (26,764 records)
├── docs/                                    # Supporting project documentation and reports
├── notebooks/
│   └── 01_EDA_JelenaVasic_capstone.ipynb    # Complete end-to-end analysis, visualizations & ML pipeline
├── requirements.txt                         # Python environment dependencies
└── README.md                                # Project overview, methodology, and key findings
```

### ⚙️ Setup & Installation
To reproduce this analysis locally:
```bash
git clone [https://github.com/jelenavasic009-png/dsb_capstone.git](https://github.com/jelenavasic009-png/dsb_capstone.git)
cd dsb_capstone
pip install -r requirements.txt
```

---

## 📂 Data Source & Quality Audit
* **Source Dataset:** Historical maritime administration logs tracking issued vessel vignettes from **2021 to 2025** (`26,764 rows × 11 original columns`).
* **Key Attributes:** Vignette serial numbers, vessel names, vessel lengths (m), purpose of use (`personal` vs. `chartering`), validity timestamps (`Valid from`, `Valid until`), duration tiers (`24h`, `7d`, `1M`, `3M`, `6M`, `1y`), issuing port branches (`Tivat`, `Zelenika`, `Bar`, `Kumbor`, `Kotor`, `Budva`), and financial metrics (`Price excluding tax €`, `Tax €`, `Total price €`).
* **Data Quality & Cleansing:**
  * Audited missing entries (`6` null vessel names imputed as `'Unknown Vessel'`, `3` null durations imputed as `'Unknown Duration'`) without losing transactional records.
  * Verified zero illogical dates (`Valid until < Valid from`), zero negative/zero prices, and zero invalid vessel lengths.
  * Standardized `datetime64` fields to extract `Year`, `Month`, `Season`, `Clean_Year`, and a binary `Is_Covid_Period` indicator (covering `2021–2022` in the dataset).

---

## 🔄 End-to-End Analytical & Machine Learning Pipeline
The entire workflow is documented and reproducible inside [`notebooks/01_EDA_JelenaVasic_capstone.ipynb`](notebooks/01_EDA_JelenaVasic_capstone.ipynb):

1. **Data Sourcing, Audit & Cleansing (Steps 1–3):** Loaded raw Excel records, inspected data types (`info()`), computed baseline statistics (`describe()`), imputed missing values, and verified logical integrity.
2. **Regional Performance & Vessel Loyalty Analysis (Steps 4–4.1):** Evaluated branch-level revenue concentration and tracked repeat customers across `12,326` unique vessels (`4,225` multi-year returning vessels; `356` vessels returning every single year from 2021 to 2025).
3. **Temporal Decomposition & Visual Analytics (Steps 5–6):** Decomposed timestamps into operational seasons, computed 30-day rolling revenue averages, and built multi-year seasonal and stacked branch revenue charts.
4. **Feature Engineering & Dimensionality Reduction (Steps 7–8):** Applied `StandardScaler` and **PCA** (preserving >80% variance across vessel dimensions and pricing) and introduced `Is_Covid_Period` flags to isolate pandemic-era market shifts.
5. **Time-Series Revenue Forecasting (Steps 9–10):** Aggregated monthly branch demand using One-Hot Encoding and trained a **Facebook Prophet** model with yearly seasonality to project revenue trends for the upcoming 12 months.
6. **Price Prediction & Regularization (Steps 11, 13–15):**
   * Built a baseline single-variable **Linear Regression** model using vessel length alone ($R^2 = 0.31$).
   * Upgraded to a multi-variable **Random Forest Regressor** incorporating vessel length, validity duration, purpose of use, month, and issuing port—achieving **$R^2 = 0.9737$**.
   * Benchmarked **Ridge (L2)** and **Lasso (L1)** regularization ($R^2 = 0.7203$) and extracted **Feature Importance** rankings to interpret pricing drivers.
7. **Customer Segmentation & Anomaly Detection (Steps 12 & 16):** Combined **K-Means Clustering** (commercial vessel tiers) with **DBSCAN** density-based clustering to detect `6` core operational groups and automatically flag `93` statistical outliers (`0.35%`).

---

## 📊 Key Findings & Business Recommendations
* **Hub Dominance:** **Tivat** is the primary financial hub, generating nearly **47% (€1.73M)** of total gross revenue due to high transaction volume combined with larger average vessel lengths (~20.0m).
* **Primary Pricing Drivers:** Feature importance from the Random Forest model ($R^2 = 0.9737$) confirmed that vignette pricing is governed by **vessel length (45.14%)**, **validity duration tiers (30.03% combined)**, and **purpose of use (22.87% across chartering and personal categories)**, while issuing branch and month have minimal impact on individual ticket prices.
* **High-Value Anomaly Management:** DBSCAN isolated **93 extreme transactions (0.35%)**—predominantly superyachts (>60m) and high-ticket vignettes (€2,000–€5,000+)—highlighting the value of dedicated VIP berth and port administration workflows.

---

## 🛠️ Technologies & Libraries Used
| Library | Primary Purpose |
| :--- | :--- |
| **Pandas & NumPy** | Data ingestion, cleansing, aggregation, loyalty cross-tabulation, and feature engineering. |
| **Matplotlib & Seaborn** | Exploratory visualizations, rolling averages, seasonal line plots, and static cluster plots. |
| **Plotly** | Interactive scatter plots and exploratory visualizations. |
| **Scikit-Learn** | `StandardScaler`, `PCA`, `OneHotEncoder`, `ColumnTransformer`, `LinearRegression`, `Ridge`, `Lasso`, `RandomForestRegressor`, `KMeans`, and `DBSCAN`. |
| **Prophet** | Automated time-series decomposition and 12-month revenue forecasting. |

---
*For full code execution, charts, and detailed commentary, open [`notebooks/01_EDA_JelenaVasic_capstone.ipynb`](notebooks/01_EDA_JelenaVasic_capstone.ipynb).*
