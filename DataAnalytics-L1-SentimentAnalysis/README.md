# 🛒 Amazon Fine Food Reviews - Sentiment Analysis

A Machine Learning and Natural Language Processing (NLP) project built to classify customer sentiment (*Positive*, *Neutral*, or *Negative*) from Amazon fine food reviews using custom text preprocessing, TF-IDF feature extraction, and classification models (**Logistic Regression** vs. **Multinomial Naive Bayes**).

---

## 📌 Project Overview

Customer reviews are vital for understanding public opinion and product performance. This project aims to automatically analyze large-scale textual feedback, clean and process unstructured natural language data, and build predictive models to classify customer sentiment accurately.

* **Developer:** Shivani Sharma
* **Program / Internship:** Oasis Infobyte (Level 1, Task 4)
* **Dataset:** Amazon Fine Food Reviews (~568k reviews)
* **Sampled Size:** 50,000 representative records

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python 3.x
* **Environment:** Jupyter Notebook
* **Data Handling:** `pandas`, `numpy`
* **NLP & Text Preprocessing:** `nltk` (Stopwords, WordNetLemmatizer), `re` (Regular Expressions)
* **Feature Extraction & Modeling:** `scikit-learn` (`TfidfVectorizer`, `train_test_split`, `MultinomialNB`, `LogisticRegression`)
* **Visualization:** `matplotlib`, `seaborn`, `wordcloud`

---

## 📊 Dataset Summary & Preprocessing

The original dataset contains **568,454 rows** and **10 columns**.

### Target Label Mapping
The numerical rating (`Score` from 1 to 5) was mapped into 3 sentiment classes:
* **Score 1 & 2** ➔ `Negative`
* **Score 3** ➔ `Neutral`
* **Score 4 & 5** ➔ `Positive`

### Class Distribution (50,000 Sampled Dataset)
* **Positive:** 39,105 (78.21%)
* **Negative:** 7,104 (14.21%)
* **Neutral:** 3,791 (7.58%)

> **Note on Imbalance:** The dataset exhibits high class imbalance heavily weighted toward positive reviews, requiring detailed evaluation metrics (Precision, Recall, F1-Score) beyond simple accuracy.

---

## 🧹 NLP & Text Cleaning Pipeline

1. **Missing Value Imputation:** Handled nulls in `ProfileName` and `Summary` with `'Unknown'`.
2. **Text Normalization:** Lowercasing review text.
3. **Noise Removal:** Removed HTML tags (`<.*?>`), web links/URLs, special characters, and digits using RegEx.
4. **Stopword Removal & Lemmatization:** Tokenized text, removed English stopwords, and reduced words to their base lemma using `WordNetLemmatizer`.
5. **Feature Extraction:** Converted clean text into numerical sparse matrices using `TfidfVectorizer(max_features=5000)`.

---

## 📈 Model Performance & Comparison

The dataset was split using **80% Training / 20% Testing** with stratified sampling (`stratify=y`).

| Metric / Model | Multinomial Naive Bayes | Logistic Regression |
| :--- | :--- | :--- |
| **Overall Accuracy** | 80.43% | **84.74%** |
| **Positive Class F1-Score** | 0.8899 | **0.9206** |
| **Negative Class F1-Score** | 0.2957 | **0.6317** |
| **Neutral Class F1-Score** | 0.0000 | **0.1470** |
| **Weighted F1-Score** | 0.7380 | **0.8209** |

### Key Findings
* **Logistic Regression** outperformed Naive Bayes across all metrics, achieving higher accuracy (**84.74%**) and significantly better minority class detection (Negative F1-Score of **0.6317** vs **0.2957**).
* **Naive Bayes** suffered severely from class imbalance, completely failing to identify neutral sentiments (`F1-Score: 0.00`).

---

## 🚀 Business Applications & Impact

1. **Real-time Brand Monitoring:** Automatically aggregate customer sentiment to track overall product performance.
2. **Early Defect Detection:** Quality assurance teams can immediately flag negative reviews mentioning packaging damage, bad taste, or manufacturing faults.
3. **Customer Support Routing:** Automatically route dissatisfied/negative reviews to high-priority customer support queues for immediate resolution.
4. **Competitor & Market Intelligence:** Extract positive and neutral trends to discover key features that customers appreciate most.

---

