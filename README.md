# PhonePe Digital Payments Project

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green?style=flat&logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Numerical-yellow?style=flat&logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-9cf?style=flat)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-red?style=flat&logo=jupyter)

A comprehensive Python-based data analysis of PhonePe transaction data, user behavior, device usage, and demographic correlations across Indian states and districts - spanning multiple years and quarters.

---

## 📖 Overview

PhonePe is one of India's leading digital payments platforms. This case study explores transaction trends, device brand usage, regional demographics, and data quality across state and district levels. The objective is to derive actionable insights for stakeholders by applying data loading, cleaning, EDA, merging, and visualization techniques in Python.

---

## 🎯 Objectives

- **Practical Python** - Apply Pandas, Matplotlib, Seaborn and NumPy on real-world fintech data.
- **Insightful Analysis** - Understand transaction trends, user behavior, and demographic correlations across India.
- **Skill Development** - Build confidence handling multi-sheet Excel datasets with state and district granularity.

---

## 📂 Datasets

Five datasets spread across sheets in an Excel file:

| Dataset | Description |
|---|---|
| `State_Txn and Users` | Transaction count, amount, ATV, registered users, and app opens at state level |
| `State_TxnSplit` | Breakdown of transaction types (e.g. Recharge, P2P) at state level |
| `State_DeviceData` | Device brand usage and registered user percentage at state level |
| `District_Txn and Users` | Transaction and user data at district level with district codes |
| `District Demographics` | Population, area, population density, and headquarters for each district |

> **Data spans:** Multiple years and quarters across Indian states and union territories

---

## 📊 Data Dictionary

### 1. State_Txn and Users
| Column | Description |
|---|---|
| State | Name of the state |
| Year | Year of the data |
| Quarter | Quarter of the year |
| Transactions | Number of transactions |
| Amount (INR) | Total transaction amount in INR |
| ATV (INR) | Average transaction value in INR |
| Registered Users | Number of registered users |
| App Opens | Number of app opens |

### 2. State_TxnSplit
| Column | Description |
|---|---|
| State | Name of the state |
| Year / Quarter | Time period |
| Transaction Type | Type (e.g. Recharge & bill payments, Peer-to-peer payments) |
| Transactions | Number of transactions |
| Amount (INR) | Total transaction amount in INR |
| ATV (INR) | Average transaction value in INR |

### 3. State_DeviceData
| Column | Description |
|---|---|
| State | Name of the state |
| Year / Quarter | Time period |
| Brand | Device brand name |
| Registered Users | Number of registered users on that brand |
| Percentage | Share of users using that brand |

### 4. District_Txn and Users
| Column | Description |
|---|---|
| State / District / Code | Location identifiers |
| Year / Quarter | Time period |
| Transactions | Number of transactions |
| Amount (INR) / ATV (INR) | Transaction metrics |
| Registered Users / App Opens | User engagement metrics |

### 5. District Demographics
| Column | Description |
|---|---|
| State / District / Code | Location identifiers |
| Headquarters | District headquarters city |
| Population | Population of the district |
| Area (sq km) | Area in square kilometers |
| Density | Population density |
| Alternate Name | Alternate district name |

---

## 📊 Analysis Covered

### Task 1 — Data Loading and Understanding
- Load all 5 datasets; display first/last/middle rows and every 10th row.
- Summary statistics, data types, and missing value analysis for each dataset.
- Total state and district counts; state with the highest number of districts.

### Task 2 — Exploratory Data Analysis (EDA)
- Total transactions and amount per state over time; top 5 and bottom 5 by volume.
- Most common transaction type per state and quarter.
- Device brand with the highest registered users per state.
- Top district per state by population with a column chart.
- Average transaction value (ATV) per state; top 5 and bottom 5.
- App opens over time by state with trend line plots.
- Transaction type distribution for the most recent quarter (bar chart).
- Unique district name ↔ district code mapping exported as CSV.

### Task 3 — Data Quality Checks
- Aggregate district-level totals (transactions, amount, registered users) per state.
- Compare with state-level figures to surface any discrepancies.

### Task 4 — Data Merging and Advanced Analysis
- Ratio of registered users to population per state (column chart).
- Correlation between population density and transaction volume (scatter plot).
- Average transaction amount per user per state; top 5 and bottom 5.
- Device brand usage ratio per state (bar chart).

### Task 5 — Data Visualization
- Line plot: total transactions and amount over time for a selected state.
- Pie chart: transaction type distribution for a selected state and quarter.
- Bar plot: population density of districts in a selected state.

### Task 6 — Insights and Conclusions
- Trends and patterns identified from transaction time-series data.
- Demographic correlations (population density vs. transaction volume).
- Summary of key findings and actionable recommendations.

---

## 🛠️ Key Techniques Used

### Data Wrangling
```python
df.isnull().sum() / len(df) * 100          # Missing value percentage
df.value_counts().idxmax()                  # State with most districts
df.drop_duplicates(subset=["District", "Code"])  # Unique district-code mapping
df.groupby("State").sum()                   # State-level aggregation
```

### Analysis
```python
df.groupby(["State", "Quarter"])["Transaction Type"].agg(lambda x: x.mode()[0])
# Most common transaction type per state and quarter

recovery_rate = registered_users / population   # Users-to-population ratio
atv = amount / transactions                     # Average transaction value

df1.merge(df2, on="State")                      # Join state-level datasets
df.corr()                                       # Correlation matrix
```

### Visualisation
- Column charts for district populations and user-to-population ratios
- Line plots for transaction trends and app opens over time
- Bar charts for transaction type distributions and device brand usage
- Scatter plots for population density vs. transaction volume
- Pie charts for transaction type share per quarter

---

## 📁 Project Structure

```
📁 phonepe-case-study/
  ├── 📓 PhonePe_Project.ipynb
  ├── 📊 phonepe_dataset.xlsx
  │     ├── State_Txn and Users
  │     ├── State_TxnSplit
  │     ├── State_DeviceData
  │     ├── District_Txn and Users
  │     └── District Demographics
  ├── 📄 district_code_mapping.csv      ← exported in Task 2.8
  └── 📄 README.md
```

---

## ▶️ How to Run

```bash
git clone https://github.com/your-username/phonepe-case-study
cd phonepe-case-study
pip install pandas matplotlib numpy openpyxl
jupyter notebook PhonePe_Project.ipynb
```
