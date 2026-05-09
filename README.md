# 💳 Credit Card Default Prediction

A machine learning project to predict credit card defaults using behavioral, demographic, and financial features. The goal is to help financial institutions assess credit risk and minimize potential losses by identifying high-risk customers in advance.

---

## 📌 Project Overview

- **Objective:** Predict whether a customer will default on their credit card payment in the next month.
- **Dataset:** Contains features such as payment history, billing amounts, credit limits, demographic info, and utilization patterns.
- **Target Variable:** Binary classification — Default (1) or No Default (0).

---

## 📊 Exploratory Data Analysis (EDA)

- **Class imbalance:** Only ~19% of customers are defaulters → handled with SMOTETomek.
- **Gender insights:** More female clients, but males had a slightly higher default rate (~21% vs ~18%).
- **Education level:** University students had the most credit cards; high school students had the highest default rate.
- **Marital status:** Singles owned more cards; married users had the highest default risk.
- **Age trends:** Most users are in their 30s — also the age group with highest default occurrences.
- **Correlation analysis:**
  - Strong positive correlation among `PAY_0` to `PAY_6` and `BILL_AMT1` to `BILL_AMT6`.
- **Utilization rate:**
  - Median for defaulters ~0.5 vs ~0.2 for non-defaulters.
  - Some non-defaulters had extremely high utilization (>3.5).
- **Late payment ratio:**
  - Defaulters often had ratios between 0.5 and 1.0.
- **Repayment patterns:**
  - Defaulters showed more repayment inconsistency.
  - Low repayment-to-bill ratios correlated with default risk.

---

## 🔍 Key Features & Strategy

### 🧹 Data Preparation
- Cleaned missing values and anomalies.
- Handled class imbalance (~19% defaulters) using **SMOTETomek**.

### 🛠️ Feature Engineering
- Created custom features like:
  - **Longest Overdue Streak**
  - **Utilization Ratios**
  - **Repayment-to-Bill Ratio**
  - **Repayment Standard Deviation**

### 🧠 Modeling
- Compared **Random Forest**, **LightGBM**, and **XGBoost** models.
- Tuned hyperparameters and thresholds to optimize performance.
- **Final Model:** Random Forest (best F2-score)

---

## 🎯 Evaluation Metrics

| Metric       | Value     |
|--------------|-----------|
| Accuracy     | ~80.4%    |
| F1 Score     | ~0.52     |
| Recall       | ~0.70     |
| F2 Score     | ~0.54 ✅ |
| AUC          | ~0.77     |

- **F2-score prioritized** to reduce false negatives (missed defaulters).

---

## 📊 Key Insights

- **High credit utilization** and **delayed payments** are strong indicators of default.
- **Students and younger users** are more prone to risky behavior.
- **Repayment inconsistency** (high std dev) correlates with financial instability.

---

## 🔍 Tools & Libraries Used

- Python, Pandas, NumPy, Scikit-learn
- SMOTETomek (imbalanced-learn)
- LightGBM, XGBoost
- Matplotlib, Seaborn
- Jupyter Notebook

---

---

## 🏁 Business Impact

- Enables **risk-based customer segmentation**.
- Reduces losses by minimizing **false negatives** (missed defaulters).
- Allows credit teams to manually review **borderline high-risk cases**.

---

## ✅ Key Learnings

- **Repayment behavior** is the strongest predictor of default.
- **Class imbalance** handling is crucial for real-world performance.
- **Precision vs Recall** trade-off must be carefully managed.
- **F2-score optimization** aligns best with business goals.
