# 🌟 Nile Review Prediction: Customer Positive Review Model

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24-orange?logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7-red?logo=xgboost&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-GBDT-green)

---

# Nile Review Prediction Project

## 📝 Project Overview

This project focuses on predicting **customers likely to leave positive reviews** for Nile, a major South American eCommerce platform. By leveraging **Gradient Boosted Decision Trees (GBDT)** and feature engineering based on operational and customer data, the model aims to optimize **targeted review requests**, improving customer engagement, operational efficiency, and overall platform credibility.

---

## 📌 Business Problem

For eCommerce platforms like **Nile**, **positive customer reviews are crucial** for brand reputation, customer trust, and sales growth. Currently, Nile faces challenges:  

- Inefficient targeting of customers likely to leave positive reviews  
- Wasted marketing resources when requesting reviews from customers unlikely to provide favorable feedback  
- Missed opportunities to improve service quality based on review insights  

**Problem Statement:**  
> How can Nile efficiently identify and engage customers who are most likely to leave positive reviews, optimizing resources and enhancing platform reputation?  

---

## 💡 Business Impact

Implementing a predictive review model enables Nile to:  

1. **Increase Positive Reviews** – Target customers likely to leave 4-5 star reviews, improving overall review scores.  
2. **Optimize Marketing Resources** – Focus efforts on high-potential customers, reducing campaign costs.  
3. **Enhance Customer Experience** – Analyze operational factors like delivery time and order approval speed, improving satisfaction.  
4. **Drive Revenue Growth** – Positive reviews build trust → higher conversion rates and repeat purchases.  

**Bottom Line:**  
> Predictive analytics allows Nile to **strategically engage customers**, improve operational efficiency, and maximize ROI on marketing campaigns.  

---

## 🗂 Dataset Overview

Nile provided **8 tables** in CSV format:

| Table Name | Description |
|------------|-------------|
| `olist_customers_dataset` | Customer demographics and unique customer IDs |
| `olist_orders_dataset` | Order details including timestamps, status, and customer IDs |
| `olist_order_items_dataset` | Information on products in each order (product ID, quantity, price, freight) |
| `olist_products_dataset` | Product details including category, weight, and seller IDs |
| `olist_order_reviews_dataset` | Customer reviews with `review_score` and textual comments |
| `olist_sellers_dataset` | Seller IDs and locations |
| `olist_order_payments_dataset` | Payment type and transaction values for each order |
| `product_category_name_translation.csv` | Translation of product categories to English |

**Key Points:**

- Central table: `olist_order_reviews_dataset` (contains the review score)  
- Relationships: Orders link customers, products, reviews, and payments  
- Dataset size: ~80,000 orders  

---

## 🧹 Data Preparation

1. **Handling Duplicates** – Retained first occurrence of `order_id` to ensure unique entries.  
2. **Outliers Removal** – Removed extreme delays in timestamps impacting review predictions.  
3. **Data Joins** – Combined tables to form a comprehensive dataset:  
   - `Order Reviews` + `Order Items` + `Products`  
   - `Order Reviews` + `Customers` + `Orders`  
   - `Order Reviews` + `Order Payments`  
4. **Missing Values** – Removed ~1.5% of records with missing data.  
5. **Feature Engineering** – Created time-phase features:  
   - `order_approving_time` = approval timestamp – purchase timestamp  
   - `delivery_time` = delivered date – purchase date  
   - `delivery_date_diff` = delivered date – estimated delivery date  
   - Converted `review_score` to binary: 4-5 stars → positive (1), 1-3 stars → negative (0)  
6. **Encoding Categorical Features** –  
   - One-Hot Encoding for low-cardinality features  
   - Frequency Encoding for high-cardinality features  

---

## 🤖 Modelling

- **Algorithm:** Gradient Boosted Decision Trees (GBDT) – effective for structured, imbalanced datasets  
- **Alternative Models Tested:** XGBoost, Random Forest  
- **Dataset Split:** 80% training, 20% testing (~67k train, 16k test)  

**Performance Metrics (Macro Average, Binary Classification):**

| Metric | Training | Testing | Notes |
|--------|---------|--------|-------|
| Accuracy | 0.822 | 0.821 | High proportion correctly classified |
| Precision | 0.815 | 0.807 | Strong ability to minimize false positives |
| Recall | 0.607 | 0.595 | Moderate ability to detect true positives |
| F1-Score | 0.627 | 0.611 | Balanced trade-off between precision and recall |

---

## 📊 Results Summary

- **Best Model:** GBDT, due to high recall and F1-score for positive reviews  
- **Top Features Driving Predictions:**  
  1. `delivery_date_diff` – actual vs. estimated delivery difference  
  2. `delivery_time` – faster deliveries increase positive review probability  
  3. `order_approving_time` – shorter approval times → more positive reviews  
  4. Customer demographics, product category, payment type  

**Business Insight:**  
> Customers who receive orders faster and as expected are more likely to leave positive reviews. Targeting these customers maximizes review generation efficiency.  

---

## ⚙️ Deployment Plan

1. **Phase 1 – Model Deployment** – Cloud infrastructure, ETL pipelines, pilot A/B testing  
2. **Phase 2 – System Integration** – Integrate with CRM and logistics systems, automate targeting using APIs  
3. **Phase 3 – Continual Learning** – Monitor data drift, retrain model regularly to maintain accuracy  

---

## 📌 Recommendations

1. **Handle Imbalanced Data** – Apply SMOTE or undersampling to improve detection of negative reviews  
2. **Analyze Review Comments** – Use NLP for sentiment analysis and topic modeling  
3. **Optimize Marketing Strategies** – Focus resources on customers predicted to leave positive reviews  

---

## 🔑 Conclusion

The **GBDT model** effectively identifies customers likely to leave positive reviews, enabling Nile to:  

- Improve customer engagement  
- Optimize marketing spend  
- Enhance platform reputation  
- Drive revenue growth through targeted strategies  

**Key Takeaways:**  
> Time-phase features and careful feature engineering were critical in boosting predictive performance. Continuous deployment and retraining ensure sustained business value.

---

## 📁 Repository Contents

| Folder/File | Description |
|-------------|-------------|
| `Data/` | Processed data |
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
- [Report PDF](Report/group_number_32_report.pdf)  
- [Presentation Slides](Presentation/group_number_32_presentation.pdf)  
- [Jupyter Notebook / Code](Code/group_number_32_code.ipynb)  
- [Data](Data.zip)

