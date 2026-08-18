# TASK 3: Comprehensive Data Cleaning & Quality Audit on Housing Dataset

**Domain:** Data Analytics  
**Level:** Level 1  
**Author:** Shivani Sharma  
**Tech Stack:** Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook  

---

## 📌 Executive Summary
This project demonstrates end-to-end **Data Cleaning and Quality Assurance** on a complex, high-dimensional **Housing Dataset** containing **2,930 observations across 82 feature columns**. The primary objective is to transform raw, noisy, and incomplete real estate data into a structurally sound, feature-engineered dataset optimized for downstream exploratory analysis and predictive statistical modeling.

---

## 🎯 Project Objectives
1. **Data Ingestion & Initial Audit:** Perform structural inspection (`info()`, `shape`, data types) and produce an initial Data Quality Report.
2. **Duplication & Integrity Verification:** Detect and verify complete duplicate row instances.
3. **Data Type Correction:** Convert identifier variables and categorical code attributes from continuous numerical types (`int64`) to string identifiers (`object`).
4. **Range Anomaly Detection:** Audit feature upper and lower bounds to identify unfeasible outliers and data entry errors (e.g., temporal domain errors).
5. **Systematic Missing Data Strategy:** Apply domain-specific business logic to handle structural missingness versus true missing observations across numerical and categorical features.
6. **Data Quality Documentation:** Synthesize transformations into a rigorous "Before vs. After" Data Quality Summary Table.

---

## 🛠️ Data Cleaning Pipeline & Key Actions Taken

### 1. Identifier & Data Type Standardization
* **ID Variables Casted:** `Order` and `PID` were re-casted from numerical (`int64`) to string identifiers (`object`) to prevent mathematical operations or incorrect feature weighting in linear models.
* **Building Class Codes:** `MS SubClass` (numeric code representing dwelling types) was converted to string categorical representations.
* **Target Feature:** `SalePrice` was converted to `float64` for standard continuous monetary calculations.

### 2. Value Range Anomaly Correction
* **Temporal Domain Anomaly Identified:** Extreme value inspection revealed `Garage Yr Blt` with a maximum value of **2207**, which exceeded the maximum transaction sale year (`Yr Sold`: **2010**).
* **Root Cause & Fix:** Evaluated as a data entry typo for the actual year **2007**. Replaced `2207` $\rightarrow$ `2007`, successfully capping `Garage Yr Blt` at the logical maximum of **2010**.

### 3. Missing Value Imputation Strategy
Features were categorized by structural missingness versus standard missing values:
* **Structural Absence (No Feature Present):** Columns like `Alley`, `Bsmt Qual`, `Bsmt Cond`, `Fireplace Qu`, `Garage Type`, `Garage Finish`, `Pool QC`, `Fence`, and `Misc Feature` contained missing values (`NaN`) representing the *absence* of that facility (e.g., No Pool, No Garage, No Basement). Imputed with explicit labels such as `"None"`.
* **Numerical Physical Attributes:** Missing values in `Lot Frontage`, `Mas Vnr Area`, `Garage Area`, and `BsmtFin SF 1/2` were imputed with `0.0` or median figures corresponding to property sub-types.

---

## 📊 Before vs. After Data Quality Summary

| Quality Metric / Dimension | Before Cleaning (Initial State) | After Cleaning (Final State) | Summary of Actions & Justification |
| :--- | :---: | :---: | :--- |
| **Total Row Count** | `2,930` | `2,930` | No rows deleted; preserved full sample size across analysis. |
| **Total Feature Columns** | `82` | `82` | Maintained original feature space integrity. |
| **Duplicate Rows** | `0` | `0` | Verified complete row uniqueness across all features. |
| **ID Column Types** | `int64` (`Order`, `PID`) | `object` (String) | Converted to prevent improper numeric treatment. |
| **Categorical Code Types** | `int64` (`MS SubClass`) | `object` (String) | Re-casted as categorical codes. |
| **Temporal Anomalies** | `1` (`Garage Yr Blt` = 2207) | `0` (Max: 2010) | Fixed data entry typo (2207 $\rightarrow$ 2007). |
| **Structural `NaN` Records** | High count across 19+ features | `0` unresolved `NaN`s | Replaced missing categories with explicit labels ("None" / `0`). |

---

## 💡 Strategic Insights & Modeling Readiness
1. **Zero Information Loss:** Retained 100% of the property records (`2,930` rows), ensuring statistical power is preserved for downstream predictive regression models.
2. **Model Safety:** Categorical strings and explicit "None" imputations prevent silent failures or matrix degradation during One-Hot Encoding (`pd.get_dummies`) or Linear Regression fitting.
3. **Auditability:** Documented every transformation step to ensure complete reproducible pipeline logic.

---
