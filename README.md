# 🌟 Nile Review Prediction: Customer Positive Review Model

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24-orange?logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7-red?logo=xgboost&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-GBDT-green)

---

# Nile Review Prediction Project

## 📝 Project Overview

This project focuses on predicting **customers likely to leave positive reviews** for Nile, a major South American eCommerce platform. By leveraging **Gradient Boosted Decision Trees (GBDT)** and **feature engineering** based on operational, customer, and transactional data, the model enables **targeted review requests**, improving customer engagement, operational efficiency, and platform credibility.

> **Goal:** Enable Nile to engage high-potential customers for reviews, optimize marketing resources, and enhance customer satisfaction.

---

## 📌 Business Problem

For eCommerce platforms like **Nile**, **positive reviews drive trust, reputation, and sales**. Current challenges:

- Inefficient targeting of customers likely to leave positive reviews  
- Wasted marketing resources requesting reviews from low-potential customers  
- Missed insights to improve service quality based on reviews  

**Problem Statement:**  
> How can Nile efficiently identify and engage customers most likely to leave positive reviews, optimizing resources and enhancing platform reputation?

---

## 💡 Business Impact

Implementing a predictive review model allows Nile to:

1. **Increase Positive Reviews** – Target customers predicted to leave 4-5 star reviews  
2. **Optimize Marketing Resources** – Reduce campaigns for low-potential customers  
3. **Enhance Customer Experience** – Improve operational factors like delivery time and order approval speed  
4. **Drive Revenue Growth** – Trust from reviews → higher conversions and repeat purchases  

> **Bottom Line:** Predictive analytics enables strategic engagement, operational efficiency, and maximized ROI.

---

## 🗂 Dataset Overview

Nile provided **8 tables** in CSV format:

| Table Name | Description |
|------------|-------------|
| `olist_customers_dataset` | Customer demographics and unique IDs |
| `olist_orders_dataset` | Order details (timestamps, status, customer ID) |
| `olist_order_items_dataset` | Products in each order (ID, quantity, price, freight) |
| `olist_products_dataset` | Product details (category, weight, seller ID) |
| `olist_order_reviews_dataset` | Customer reviews (`review_score` and textual comments) |
| `olist_sellers_dataset` | Seller IDs and locations |
| `olist_order_payments_dataset` | Payment type and transaction values |
| `product_category_name_translation.csv` | Product category translation to English |

**Dataset Stats:**

- ~80,000 orders  
- ~60,000 unique customers  
- 100+ unique product categories  
- Class distribution: Positive reviews (4-5 stars) ~75%, Negative reviews (1-3 stars) ~25%

**Key Insight:**  
- Central table: `olist_order_reviews_dataset`  
- Orders connect customers, products, reviews, and payments  
- Rich relational dataset enables feature engineering for operational and behavioral analysis  

---

## 🧹 Data Preparation & Feature Engineering

**Key Steps:**

1. **Handling Duplicates** – Retained the first occurrence of `order_id`.  
2. **Outliers Removal** – Extreme delays in timestamps removed.  
3. **Data Joins** – Combined tables into one comprehensive dataset:  
   - `Order Reviews` + `Order Items` + `Products`  
   - `Order Reviews` + `Customers` + `Orders`  
   - `Order Reviews` + `Order Payments`  
4. **Missing Values** – Removed ~1.5% records with missing data.  
5. **Feature Engineering:**  
   - `order_approving_time` = approval timestamp – purchase timestamp  
   - `delivery_time` = delivered date – purchase date  
   - `delivery_date_diff` = delivered date – estimated delivery date  
   - Binary classification: 4-5 stars → 1 (positive), 1-3 stars → 0 (negative)  
6. **Encoding Categorical Features:**  
   - One-Hot Encoding for low-cardinality features (`order_status`, `customer_state`, `product_category_name`, `payment_type`)  
   - Frequency Encoding for high-cardinality features (`customer_unique_id`, `seller_id`)  

**Key Challenge:**  
> Handling imbalanced data (positive vs negative reviews) and integrating multiple tables while preserving data quality.

**Visual Placeholder:**  
![Review Distribution](images/review_distribution.png)  
*Figure: Positive vs. negative review distribution*

---

## 🤖 Modelling

- **Algorithm:** Gradient Boosted Decision Trees (GBDT) – robust for structured, imbalanced datasets  
- **Alternative Models Tested:** XGBoost, Random Forest  
- **Dataset Split:** 80% training (~67k), 20% testing (~16k)  

**Performance Metrics (Macro Average, Binary Classification):**

| Metric | Training | Testing | Notes |
|--------|---------|--------|-------|
| Accuracy | 0.822 | 0.821 | Correctly classified high proportion |
| Precision | 0.815 | 0.807 | Minimizes false positives |
| Recall | 0.607 | 0.595 | Moderate detection of true positives |
| F1-Score | 0.627 | 0.611 | Balanced trade-off |

---

## 📊 Results Summary

**Best Model:** GBDT, chosen for high recall and F1-score for positive reviews  

**Top Features Driving Predictions:**  

1. `delivery_date_diff` – difference between actual and estimated delivery  
2. `delivery_time` – faster deliveries increase positive review likelihood  
3. `order_approving_time` – shorter approval times → positive reviews  
4. Customer demographics, product category, payment type  

**Business Insight:**  
> Customers receiving faster, on-time deliveries are more likely to leave positive reviews. Targeting these customers maximizes review generation efficiency.

---

## ⚙️ Deployment Plan

1. **Phase 1 – Model Deployment**  
   - Cloud infrastructure & ETL pipelines  
   - Pilot testing and A/B tests to validate strategy  

2. **Phase 2 – System Integration**  
   - Integrate with CRM and logistics systems  
   - Automate targeting using APIs for real-time predictions  

3. **Phase 3 – Continual Learning**  
   - Monitor data drift and retrain model regularly  
   - Maintain high predictive accuracy  

---

## 📌 Recommendations

1. **Handle Imbalanced Data** – Apply SMOTE or undersampling to improve negative review detection  
2. **Analyze Review Comments** – Use NLP for sentiment analysis & topic modeling  
3. **Optimize Marketing Strategy** – Focus resources on customers predicted to leave positive reviews  

---

## 🔑 Conclusion

The **GBDT model** effectively identifies customers likely to leave positive reviews, enabling Nile to:

- Improve customer engagement  
- Optimize marketing spend  
- Enhance platform reputation  
- Drive revenue growth through targeted strategies  

**Key Takeaways:**  
> Feature engineering, time-phase operational metrics, and careful data preparation were critical. Continuous deployment ensures sustained business value.

---

## 📁 Repository Contents

| Folder/File | Description |
|-------------|-------------|
| `Data/` | Processed & cleaned dataset |
| `Code/` | Scripts for data cleaning, feature engineering, and modelling |
| `Report/` | Technical report with methodology, results, and recommendations |
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

- [Report PDF](Report/group_number_32_report.pdf)  
- [Presentation Slides](Presentation/group_number_32_presentation.pdf)  
- [Jupyter Notebook / Code](Code/group_number_32_code.ipynb)  
- [Data](Data.zip)

---
