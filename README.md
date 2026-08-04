# Retail Sales Data - Exploratory Data Analysis (EDA)

## Project Overview
This project performs an Exploratory Data Analysis (EDA) on a retail sales dataset containing 1,000 transaction records across 9 attributes. The objective is to identify purchasing patterns, analyze customer demographics, evaluate category performance, and derive actionable business insights.

---

## Tech Stack
* Python 3.x
* pandas
* matplotlib & seaborn
* Jupyter Notebook

---

## Dataset Overview
* Records: 1,000 transactions
* Total Attributes: 9 columns
* Features: Transaction ID, Date, Customer ID, Gender, Age, Product Category, Quantity, Price per Unit, Total Amount

---

## Key Analysis Steps

1. Initial Inspection: Checked dataset shape (1000, 9) and confirmed 0 null values.
2. Data Preprocessing: Cast Date column to Pandas datetime64 format for time series analysis.
3. Descriptive Statistics: Calculated mean, median, mode, and standard deviation for numerical variables.
4. Time Series Analysis: Resampled monthly and quarterly sales to detect performance trends and identified a data logging boundary drop in early 2024.
5. Customer Demographics: Analyzed age distribution (bimodal peaks at 20, 40, and 60 years) and gender breakdown (nearly 50-50 split).
6. Product Category Analysis: Compared unit sales volume vs revenue across Beauty, Clothing, and Electronics categories.
7. Correlation Analysis: Evaluated feature relationships, discovering a strong correlation (r = 0.85) between Price per Unit and Total Amount.
8. Deep-Dive Visualizations: Analyzed spending patterns by segmenting category revenue across gender and age groups.

---

## Key Business Insights

* Revenue Driver: Total revenue is heavily driven by Price per Unit (r = 0.85) rather than purchase quantity (r = 0.37).
* Higher Female Spending: Although total headcount is split equally (~50% Male / ~50% Female), female shoppers generate higher total revenue across all three product categories.
* Core Buying Cluster: The 36 to 65 age bracket represents the largest purchasing group, with Clothing and Electronics being their top preferences.

---

## Actionable Business Recommendations

1. Target Female Customer Segments: Tailor marketing campaigns and loyalty perks specifically toward female shoppers, who yield higher average transaction revenue across all categories.
2. Implement Product Bundling: Since low-cost items dominate order counts, create bundled packages (e.g., pairing low-cost accessories with electronics) to raise average order values.
3. Focus Advertising on Core Demographics: Prioritize promotional budgets on the 36 to 65 age group while creating introductory incentives for younger shoppers (18 to 25).
4. Audit Data Pipelines: Collaborate with the data engineering team to resolve the transaction recording cutoff in early 2024 to ensure continuous data tracking.

---

## How to Run

1. Clone the repository:
   git clone https://github.com/your-username/retail-sales-eda.git

2. Navigate to the project directory:
   cd retail-sales-eda

3. Install requirements:
   pip install pandas matplotlib seaborn notebook

4. Launch the notebook:
   jupyter notebook ShivaniSharma_Task1.ipynb

