# 🌟 Nile Review Prediction: Customer Positive Review Model

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24-orange?logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7-red?logo=xgboost&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-GBDT-green)

---

## 📌 Project Overview
This project predicts which customers are likely to leave **positive reviews** on Nile, a South American eCommerce platform. By leveraging **Gradient Boosted Decision Trees (GBDT)** and following the **CRISP-DM framework**, the model enables resource-efficient marketing and strengthens platform credibility.

---

## 🎯 Business Problem
Positive reviews directly impact **brand reputation and sales**. Nile lacked the ability to efficiently target customers likely to leave favorable reviews.  
**Objective:** Build a predictive model to identify high-potential reviewers and optimize marketing outreach.

---

## 📊 Data Understanding
- **Eight tables** provided, including customer, order, product, review, and payment data  
- **Target variable:** Review score  
  - 4–5 stars → Positive Review (1)  
  - 1–3 stars → Negative Review (0)  
- **Key Features:**  
  - `order_approving_time`, `delivery_time`, `delivery_date_diff` (time-phase features)  
  - Customer demographics, product attributes, and payment data  
- Dataset contains **~80,000 records**, slightly imbalanced towards positive reviews

---

## 🛠 Data Preparation
- **Duplicates removed** based on `order_id`  
- **Outliers handled** by removing top extreme timestamp differences  
- **Categorical encoding**:  
  - Low cardinality → One-Hot Encoding (`order_status`, `customer_state`)  
  - High cardinality → Frequency Encoding (`customer_unique_id`, `seller_id`)  
- **Feature engineering:** Time-based metrics, binary target variable

---

## 🧩 Modelling Approach
- **Algorithms tested:** GBDT, XGBoost, Random Forest  
- **Chosen Model:** GBDT for its high recall and F1-score for positive reviews  
- **Data split:** 80% training, 20% testing  
- **Evaluation Metrics:** Accuracy, Precision, Recall, F1-score (macro-averaged)  
- **Hyperparameter tuning:** RandomizedSearchCV optimizing for positive review detection

---

## 📊 Results Summary

| Insight | Observation | Business Implication |
|---------|------------|--------------------|
| Positive Review Prediction Accuracy | GBDT achieved 82% accuracy, 0.82 precision | Reliably identifies high-potential customers |
| Service Timeliness | Delivery time and delivery date accuracy most predictive | Faster and accurate delivery boosts positive reviews |
| Customer Demographics | Certain regions/purchase patterns correlate with positive reviews | Targeted marketing can enhance engagement |
| Imbalanced Data | Positive reviews dominate; recall for negatives is lower | Apply SMOTE/undersampling to better predict negative reviews |
| Operational Efficiency | Shorter order approval times correlate with higher review scores | Streamlining approvals improves review likelihood |

---

## 🔍 Model Evaluation
- **GBDT** outperformed XGBoost and Random Forest in recall and F1-score for Class 1 (positive reviews)  
- **Top features:** Delivery date difference, delivery time, order approval time, product category  
- **Imbalance handling:** Future improvement with SMOTE or undersampling recommended  

---

## 🚀 Deployment Plan
1. **Phase 1 – Model Deployment:** Cloud setup and ETL pipelines, pilot A/B testing  
2. **Phase 2 – System Integration:** CRM and logistics integration via APIs  
3. **Phase 3 – Continual Learning:** Automated retraining for data drift adaptation

---

## 📌 Key Recommendations
- Apply **SMOTE/undersampling** to handle imbalanced classes  
- Analyze **textual review comments** using NLP (sentiment analysis, topic modelling)  
- Focus on **operational metrics** like delivery and approval times  
- Roll out **gradually** for monitoring ROI and model performance  

---

## 📁 Repository Contents

| Folder/File | Description |
|-------------|-------------|
| `Data/` | Raw CSV datasets and processed data |
| `Code/` | Data cleaning, feature engineering, and model scripts |
| `Report/` | Full technical report with methodology, results, and recommendations |
| `Presentation/` | Pitch slides for Nile management board |

---

## 🔧 Skills & Tools Applied

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Pandas](https://img.shields.io/badge/Pandas-1.6-yellow)
![NumPy](https://img.shields.io/badge/NumPy-1.27-orange)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24-orange)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7-red)
![Gradient Boosting](https://img.shields.io/badge/GBDT-Decision_Trees-green)
![Random Forest](https://img.shields.io/badge/Random_Forest-green)
![Feature Engineering](https://img.shields.io/badge/Feature_Engineering-blueviolet)
![Data Cleaning](https://img.shields.io/badge/Data_Cleaning-lightgrey)
![Hyperparameter Tuning](https://img.shields.io/badge/Hyperparameter_Tuning-lightblue)

---

## 📌 Quick Links
- [Report PDF](./Report/Nile_Review_Prediction_Report.pdf)  
- [Presentation Slides](./Presentation/Nile_Review_Pitch.pdf)  
- [Jupyter Notebook / Code](./Code/Nile_Review_Prediction.ipynb)  
- [Data](./Data/)

