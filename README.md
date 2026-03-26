# Customer Churn Analysis & Prediction

> **Predicting account churn before it happens — powering smarter retention for E-Commerce & DTH providers.**

---

## Overview

In a fiercely competitive market, retaining existing customers is far more cost-effective than acquiring new ones. This project builds an end-to-end **churn prediction pipeline** for an E-Commerce / DTH provider, combining machine learning models, behavioral analytics, and Tableau dashboards to identify at-risk accounts — and recommend targeted, revenue-conscious retention campaigns.

Since a **single account can represent multiple customers**, every churn event carries amplified business impact. The goal is not just prediction — it's actionable intelligence that the revenue assurance team can actually approve and deploy.

---

## Problem Statement

An E-Commerce company / DTH provider is facing intense market competition and struggling to retain existing customers. The key challenges are:

- **Account-level churn** is critical — one lost account = multiple lost customers
- The company lacks a proactive system to identify potential churners before they leave
- Retention campaigns need to be **financially viable** — offers that are overly generous will not pass revenue assurance review
- Segmented, data-driven offers are needed instead of blanket discounts

**Objective:** Develop a machine learning–based churn prediction model and deliver business-approved, ROI-positive campaign recommendations for at-risk customer segments.

---

## About Dataset

The dataset contains customer account-level information from an E-Commerce / DTH provider, including:

| Feature Category | Description |
|---|---|
| **Demographics** | Account age, region, customer count per account |
| **Transactional Data** | Purchase frequency, order value, payment history |
| **Behavioral Data** | Login activity, app/web usage, support interactions |
| **Subscription Info** | Plan type, tenure, renewal history |
| **Churn Label** | Binary target — `1` (Churned) / `0` (Retained) |

> *Data was cleaned and validated before modelling. Missing values, duplicates, and inconsistent entries were handled during preprocessing.*

---

## Tools & Technologies

| Category | Tools |
|---|---|
| **Programming Language** | Python 3.12 |
| **Data Manipulation** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn, Tableau |
| **Machine Learning** | Scikit-learn |
| **Deep Learning** | TensorFlow / Keras (ANN) |
| **Decision Trees** | CART (Classification & Regression Trees) |
| **Environment** | Jupyter Notebook |

---

## Methods

### 1. Data Cleaning & Preprocessing
- Handled missing values using median/mode imputation
- Removed duplicate account entries
- Encoded categorical variables (Label Encoding / One-Hot Encoding)
- Scaled numerical features using StandardScaler

### 2. Exploratory Data Analysis (EDA)
- Analysed churn rate by plan type, region, account tenure, and usage patterns
- Identified behavioural patterns: declining logins, reduced transactions, increased support tickets
- Probability analysis revealed customers with **30-day declining activity** have significantly higher churn risk

### 3. Model Building
- CART was selected for interpretability and stakeholder communication;
- ANN for capturing non-linear feature interactions;
- Random Forest for robust ensemble-based prediction with built-in feature importance;
- Logistic Regression with Backward Elimination for a statistically rigorous baseline with reduced multicollinearity;
- Logistic Regression with SMOTE to specifically address class imbalance and maximise recall on the minority churn class.

**CART (Classification & Regression Tree)**
- Interpretable decision-tree model
- Feature importance used to identify top churn drivers
- Pruned to avoid overfitting

**Random Forest Classifier**
- Ensemble of decision trees trained using bootstrap aggregation (bagging)
- `n_estimators` tuned to balance bias-variance tradeoff
- Handles class imbalance better than single tree models due to voting mechanism
- Best hyper parameters retained using Grid Search cross validation

**Artificial Neural Network (ANN)**
- Multi-layer perceptron architecture
- Layers: Input → Dense (ReLU) → Dropout → Dense (ReLU) → Output (Sigmoid)
- Optimised using Adam optimizer with binary cross-entropy loss

**Logistic Regression with Backward Elimination (Feature Selection)**
- Started with all features and iteratively removed the least statistically significant ones
- Used p-value threshold of 0.05 — features with p > 0.05 were eliminated at each step
- Implemented using `statsmodels` OLS / Logit for p-value tracking
- Final reduced feature set improved model interpretability and reduced multicollinearity

**Logistic Regression with SMOTE (Handling Class Imbalance)**
- Dataset had a significant class imbalance — churners were a minority class
- Applied **SMOTE (Synthetic Minority Over-sampling Technique)** on the training set only to avoid data leakage
- SMOTE synthetically generates minority class samples by interpolating between existing ones

### 4. Model Evaluation
- Metrics: Accuracy, Precision, Recall, F1-Score, AUC-ROC
- Focus on **Recall** to minimise missed churners (false negatives are costly)
- Confusion Matrix analysis for business threshold tuning

### 5. Customer Segmentation
- Churners segmented by risk score and value tier (High Value / Mid Value / Low Value)
- Segmentation used to design targeted, cost-controlled retention offers

---

## Key Insights

-  **30-day activity drop** is the strongest leading indicator of churn — customers showing declining logins and purchase frequency are **significantly more likely to churn**
-  **Account tenure < 6 months** has the highest churn rate — onboarding experience is critical
-  **High support ticket volume** correlates strongly with churn — unresolved complaints are a major risk signal
-  **Single-customer accounts** churn faster than multi-customer accounts — bundling and family plans aid retention
-  **Plan downgrades** are a strong precursor to full churn — early intervention at downgrade stage can prevent exits

---

### Model Output
```
                        Precision   Recall   F1-Score   Support
     Retained (0.0)         0.96      0.95      0.95      1880
     Churned (1.0)          0.84      0.88      0.86       372

     Accuracy                                   0.92      2252
     AUC-ROC Score:         0.95
```

>  ANN model outperformed all other models.

---

### Folder Structure
```
customer-churn-analysis/
│
├── data/
│   ├── Customer Churn Data.xlsx           # Original dataset
│
├── notebooks/
│   ├── Capstone Project Final.ipynb
│
├── report and presentation/
│   ├── Customer Churn Report.pdf
│   └── Presentation.pptx
│
└── README.md
```

---

## Results & Conclusion

| Metric | CART | ANN | RF | Logit | SMOTE
|---|---|---|---|---|---|
| Accuracy | 90% | 92% | 92% | 89% | 82%
| Recall (Churn) | 68% | 81% | 64% | 48% | 77% 
| AUC-ROC | 0.93 | 0.95 | 0.95 | --- | 0.74

### Business Impact
-  **20% improvement** in customer retention through proactive churn intervention
-  Segmented campaigns enabled **targeted offers** instead of blanket discounts
-  Revenue assurance–compliant recommendations ensured campaign profitability
-  Early identification of at-risk accounts reduced response time from reactive to proactive

### Campaign Recommendation Snapshot
> Rather than offering free services, the recommended campaigns focus on **value-add offers** — such as priority support tiers, loyalty reward points, and feature unlocks — targeted at high-risk, high-value accounts. This approach retains customers without eroding margins.

---

## Author

**[Shraddha Suman Guru]**  
Data Science & Analytics  
📧 ssumanguru2000@gmail.com 
🔗 [LinkedIn](https://linkedin.com/in/ssumanguru) | [GitHub](https://github.com/SSumanGuru)

---
