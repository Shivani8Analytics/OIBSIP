# Predicting House Prices with Linear Regression
# 🏡 Ames Housing Price Prediction - Linear & Regularized Regression

An end-to-end Machine Learning project to analyze the Ames Housing dataset and predict house prices using **Linear Regression**, **Ridge Regression**, and **Lasso Regression**. The project covers data cleaning, median imputation, one-hot encoding, feature correlation analysis, and regularized model evaluation.

---

## 📌 Project Overview

Accurately predicting house prices is essential for real estate buyers, sellers, and automated valuation platforms. This project builds a linear regression pipeline to estimate property values based on key physical dimensions, quality ratings, structural age, and neighborhood locations.

* **Developer:** Shivani Sharma
* **Program / Internship:** Oasis Infobyte (Level 2, Task 1)
* **Dataset:** Ames Housing Dataset (2,930 rows, 82 columns)
* **Target Variable:** `SalePrice`

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python 3.x
* **Environment:** Jupyter Notebook
* **Data Processing & Analysis:** `pandas`, `numpy`
* **Machine Learning & Metrics:** `scikit-learn` (`LinearRegression`, `Ridge`, `Lasso`, `train_test_split`, `mean_squared_error`, `r2_score`)
* **Data Visualization:** `matplotlib`, `seaborn`

---

## 📊 Feature Selection & Data Preprocessing

From the original 82 columns, a domain-relevant subset of **10 key features** was selected to focus on impactful price drivers and eliminate sparse variables:

### Key Features Selected
* **Physical Area:** `Gr Liv Area` (Above grade living area), `Total Bsmt SF` (Basement area), `Garage Area`
* **Quality & Condition:** `Overall Qual` (1–10 rating), `Year Built`
* **Capacity & Amenities:** `Full Bath`, `Bedroom AbvGr`, `Central Air`
* **Location:** `Neighborhood`
* **Target:** `SalePrice`

### Preprocessing Pipeline
1. **Missing Value Imputation:** Imputed missing values in `Total Bsmt SF` and `Garage Area` using column **medians** to preserve dataset size without bias.
2. **Categorical Encoding:** Applied One-Hot Encoding (`pd.get_dummies` with `drop_first=True`) to `Neighborhood` and `Central Air`, expanding the feature set to **35 numerical columns**.
3. **Data Splitting:** Applied an **80% Train / 20% Test** split (`train_test_split`, `random_state=42`), resulting in 2,344 training samples and 586 test samples.

---

## 📈 Model Performance & Evaluation

The models were evaluated using **Root Mean Squared Error (RMSE)** and the **Coefficient of Determination ($R^2$ Score)**:

| Model | Train RMSE ($) | Test RMSE ($) | Test $R^2$ Score |
| :--- | :--- | :--- | :--- |
| **Linear Regression** | ~$32,150 | ~$36,210 | **0.8351** |
| **Ridge Regression** | ~$32,200 | **~$35,800** | **0.8388** |
| **Lasso Regression** | ~$32,160 | ~$36,150 | **0.8356** |

### Key Findings
* **Ridge Regression** achieved the best overall generalization performance on unseen test data with the lowest test error (**~$35,800**) and the highest variance explanation (**$R^2 = 83.88\%$**).
* **Top Price Drivers:** `Overall Qual` ($r = 0.80$), `Gr Liv Area` ($r = 0.71$), `Garage Area` ($r = 0.64$), and prime locations (e.g., `NridgHt`, `NoRidge`) showed the strongest positive linear correlation with `SalePrice`.

---

## 💡 Business Insights & Applications

1. **Automated Valuation Models (AVM):** The Ridge Regression model can serve as a baseline valuation engine for real estate platforms with an average error margin around $35.8k.
2. **Property Renovation Strategy:** Homeowners looking to maximize ROI should prioritize expanding living area (`Gr Liv Area`), upgrading build quality, and adding garage capacity over simply increasing bedroom count.
3. **Targeted Pricing:** Real estate agents can leverage location-based dummy coefficients to adjust listing prices according to neighborhood demand.

---

