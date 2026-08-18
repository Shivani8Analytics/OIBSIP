# TASK 1: Exploratory Data Analysis (EDA) on Retail Sales Data

**Domain:** Data Analytics  
**Level:** Level 1  
**Author:** Shivani Sharma  
**Tech Stack:** Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook  

---

## 📌 Executive Summary
This project delivers a comprehensive **Exploratory Data Analysis (EDA)** on a retail sales dataset containing **1,000 transaction records**. The primary goal is to uncover purchasing patterns, evaluate customer demographics, assess category performance, and translate raw data into actionable revenue-driving strategies.

---

## 🎯 Project Objectives
1. **Data Hygiene & Preprocessing:** Audit missing values, verify data integrity, and convert date features for time-series modeling.
2. **Statistical Analysis:** Calculate central tendencies (mean, median, mode) and dispersion measures (std dev) to understand variable distribution and skewness.
3. **Time Series Modeling:** Aggregate monthly and quarterly revenue streams to track seasonal velocity and detect data anomalies.
4. **Demographic Segmentation:** Analyze customer distribution across age cohorts and gender.
5. **Product & Revenue Performance:** Evaluate sales volume versus total revenue generated per product category.
6. **Correlation Analysis:** Discover relationships between transaction variables using statistical correlation matrices.

---

## 📊 Key Findings & Analytical Insights

### 1. Descriptive Statistics & Data Distribution
* **Age Distribution:** Symmetrical (Mean: `41.39`, Median: `42.0`). Displays a **bimodal pattern** with prominent peaks at ages **20, 40, and 60**, indicating multi-generational customer cohorts.
* **Basket Size:** Average transaction quantity is `2.51` units (Median: `3.0`), with `4` units being the most frequent purchase size.
* **Pricing & Revenue Skewness:**
  * **Price Per Unit:** Mean (`$179.89`) > Median (`$50.00`), indicating significant **right-skewness**. Budget-tier items ($50) dominate transaction volume.
  * **Total Amount:** Strongly right-skewed (Mean: `$456.00`, Median: `$135.00`, Std Dev: `$560.00`), proving that high-ticket purchases heavily drive overall revenue variance.

### 2. Time-Series Trends & Anomaly Detection
* **Monthly Velocity:** Steady sales flow between **$24K and $47K** per month. Peak performance occurred in **May 2023 (~$53K)** and **November 2023 (~$47K)**.
* **Quarterly Velocity:** Q1 2024 generated peak quarterly revenue (~**$126K**).
* **Data Logging Anomaly:** A sharp, abrupt drop in sales occurred in February 2024 (~$1.5K). Because quarterly data smooths normal fluctuations, this isolated crash indicates an **incomplete transaction logging/ingestion issue** rather than a true drop in business demand.

### 3. Demographic & Category Insights
* **Gender Parity:** Customer breakdown is balanced (51% Female / 49% Male). However, **female customers generate higher total revenue across all three categories** (Beauty, Clothing, Electronics).
* **Volume vs. Value Paradox:**
  * **Clothing** leads in total unit transaction volume (**351 purchases**).
  * **Electronics** leads in total revenue generated (~**$155K**), driven by higher unit pricing.
  * **Beauty** generates competitive revenue (~**$142K**) despite lower transaction volume, indicating strong profit margins.

### 4. Correlation Dynamics
* **Price per Unit vs. Total Amount ($r = 0.85$):** Very strong positive correlation. Unit pricing is the primary driver of order value.
* **Quantity vs. Total Amount ($r = 0.37$):** Moderate correlation. Quantity purchased plays a secondary role in overall revenue.
* **Price vs. Quantity ($r = 0.018$):** Near-zero correlation. Price sensitivity does not directly reduce basket volume.

---

## 💡 Strategic Business Recommendations

1. **Target Multi-Generational Clusters:**
   * Design marketing campaigns tailored specifically to the three primary age cohorts (**20s, 40s, and 60s**).
   * Run targeted campaigns for female shoppers, as they demonstrate higher spend velocity across all categories.

2. **Capitalize on Product Bundling:**
   * Create cross-category product bundles (e.g., pairing high-margin *Beauty* products or mid-tier *Electronics* with high-volume *Clothing* items) to increase overall average transaction value ($ATV$).

3. **Data Pipeline Optimization:**
   * Direct the data engineering team to audit the transaction logging pipeline for early 2024 to rectify missing ingestion logs and restore metric accuracy.

---
