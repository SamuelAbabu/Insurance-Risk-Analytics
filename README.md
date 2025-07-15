# 🚗 Insurance Risk Analytics & Predictive Modeling

This repository contains an end-to-end data analytics pipeline for **AlphaCare Insurance Solutions**, focused on understanding car insurance claim risks and optimizing marketing strategies in South Africa.

## 📘 Project Overview

**Business Goal**: Identify low-risk customer segments and propose premium adjustments to attract new clients while maintaining profitability.

**Duration**: Feb 2014 – Aug 2015  
**Tasks Covered**:  
- 🧪 Exploratory Data Analysis (EDA)  
- 🔄 Data Version Control (DVC) Integration  
- 🧠 Statistical Modeling (Task-3 onward)

---

## 🎯 Objectives

- Quantify **claim risks** and **margins** across provinces, vehicle types, and customer demographics.
- Detect **outliers** and data integrity issues in historical records.
- Establish a **reproducible pipeline** using Git and DVC.
- Support compliance, auditability, and traceability in insurance analytics workflows.

---

## 📊 Task 1: Exploratory Data Analysis (EDA)

### 🔍 Key Metrics
- `LossRatio = TotalClaims / TotalPremium`
- `Margin = TotalPremium - TotalClaims`

### 🧠 EDA Highlights

- Provinces like **Gauteng** and **KwaZulu-Natal** show elevated risk.
- High variance in claims across **vehicle types**.
- Gender-based differences observed, especially in claim severity.
- Several **custom value estimates** exceed ZAR 1M — flagged as outliers.

### 📈 Visualizations

#### 🚗 Claim Severity by Vehicle Type
```python
sns.boxplot(data=df, x='VehicleType', y='TotalClaims')
🧍 Claim Distribution by Gender
python
sns.histplot(data=df, x='TotalClaims', hue='Gender', bins=50, kde=True)
🗺️ Average Loss Ratio by Province
python
df.groupby('Province')['LossRatio'].mean().sort_values().plot(kind='barh')
Visual plots available in: notebooks/eda_task1.ipynb

🔁 Task 2: Reproducible Data Pipeline with DVC
⚙️ Setup
bash
pip install dvc
dvc init
mkdir ./notebook/dvc_local_storage
dvc remote add -d localremote ./notebook/dvc_local_storage
📦 Data Tracking
bash
dvc add data/insurance_data.csv
git add data/insurance_data.csv.dvc .gitignore
git commit -m "Track data file with DVC"
🚀 Data Push
bash
dvc push
Data stored locally (excluded from Git) for compliance with GitHub’s file-size limits and reproducibility standards.

🧼 Git Hygiene
✔ Cleaned history using git filter-repo ✔ Removed oversized data files from version control ✔ .gitignore updated to exclude:

Data/
notebook/dvc_local_storage/
.dvc/cache/
🧮 Coming Soon
Task-3: Hypothesis Testing

Risk differences across provinces and zip codes

Margin and claim severity segmentation

Gender-based statistical significance

Task-4: Predictive Modeling

Claim severity prediction (RMSE, R²)

Premium optimization using feature-based pricing