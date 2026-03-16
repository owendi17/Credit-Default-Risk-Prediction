
# 🏦 Home Credit Default Risk Prediction
**Model Performance:** `0.7483 ROC AUC` (LightGBM)

## 🎯 Executive Summary
This project moves beyond simple binary classification to provide a comprehensive risk-scoring tool. By leveraging **Gradient Boosting (LightGBM)**, I achieved a performance score that places the model in a competitive range for financial risk assessment.It aims to predict whether an applicant will default on a loan. Using a dataset of over 300,000 applications, I built a machine learning pipeline to identify high-risk borrowers while maintaining a balance that allows the bank to maximize loan approvals for reliable clients.

The accompanying **Tableau Dashboard** provides a "human-in-the-loop" interface for credit officers to validate these scores against real-world financial metrics.https://public.tableau.com/authoring/creditdefaultriskvisualisation/Sheet3/Credit%20Default%20Risk%20Analysis%20Dashboard#2

Key Steps & Methodology
1. Data Exploration & Cleaning

    Anomalies: Discovered a significant error in DAYS_EMPLOYED where approximately 55,000 rows had a value of 365,243 days (over 1,000 years). Replaced these with NaN to prevent model distortion.

    Correlation Analysis: Found that EXT_SOURCE features (External Credit Scores) had the strongest relationship with loan repayment.

2. Preprocessing Pipeline

    Imputation: Used Median Imputation to fill missing values. Chose Median over Mean to remain robust against outliers in income and credit amounts.

    Feature Scaling: Employed Min-Max Scaling to bring all features into a 0-1 range, ensuring the model treats small-scale credit scores and large-scale loan amounts with equal mathematical weight.

3. Model Development (The Experiment)

I followed a "Champion-Challenger" approach to find the best model:

    Baseline - Logistic Regression (AUC: 0.7343): Provided a fast, interpretable benchmark.

    Random Forest (AUC: 0.7332): Attempted to capture non-linear relationships, though it performed similarly to the baseline due to high class imbalance.

    Final Model - LightGBM (AUC: 0.7483): The winning model. By using gradient boosting and the is_unbalance=True parameter, it successfully prioritized learning from the rare "Defaulter" cases.

4. Business Evaluation

    Metric: Used ROC AUC instead of Accuracy because the dataset is imbalanced (92% Repayers). Accuracy would be misleading; AUC measures the model's actual ability to distinguish between classes.

    Strategy: Analyzed the Precision-Recall Tradeoff. For a bank, a "False Negative" (unpaid loan) is more expensive than a "False Positive" (missed customer), suggesting a conservative probability threshold is best for business.

Final Result

The final LightGBM model provides a 0.75 AUC score, offering a significant predictive lift over a simple baseline and providing the bank with a data-driven tool for risk assessment.# Credit-Default-Risk-Prediction
Project predicts wheather the customer will repay the loan or defalt basing on past data and external sources(CRB)
