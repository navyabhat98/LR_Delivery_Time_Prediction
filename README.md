# 📦 Order Delivery Time Prediction

This project builds a **regression model** to predict the delivery time for food orders placed through Porter. The model leverages multiple order- and market-related features to optimize operational efficiency and improve delivery time predictions.

---

## 🎯 Objectives
- Predict delivery time for an order based on multiple input features.  
- Improve delivery time predictions to optimize logistics efficiency.  
- Understand key factors influencing delivery time to enhance accuracy.  

---

## 🛠️ Data Pipeline
1. **Data Loading** – Import and inspect raw dataset (`porter_data_1.csv`).  
2. **Data Preprocessing & Feature Engineering**  
   - Convert timestamps to datetime.  
   - Handle categorical variables.  
   - Create new features such as `time_taken_minutes`, `hour`, `day`, and `isWeekend`.  
3. **Exploratory Data Analysis (EDA)**  
   - Feature distributions (numeric & categorical).  
   - Correlation and scatter plots.  
   - Outlier detection and handling.  
4. **Model Building**  
   - Train-test split.  
   - Feature scaling.  
   - Linear Regression model.  
   - Recursive Feature Elimination (RFE) for feature selection.  
5. **Model Inference** – Evaluate results and analyze coefficients.  

---

## 📊 Dataset Overview
The dataset contains **175,777 orders** with the following fields:

| Feature | Description |
|---------|-------------|
| `market_id` | Market where restaurant is located |
| `created_at` | Order creation timestamp |
| `actual_delivery_time` | Delivery completion timestamp |
| `store_primary_category` | Restaurant type/category |
| `order_protocol` | Order channel (Porter app, phone, etc.) |
| `total_items` | Total items ordered |
| `subtotal` | Order value |
| `num_distinct_items` | Count of unique items in the order |
| `total_onshift_dashers` | Delivery partners on duty |
| `total_busy_dashers` | Delivery partners currently occupied |
| `total_outstanding_orders` | Pending orders |
| `distance` | Distance from restaurant to customer |

---

## 📈 Key Results
- **Final Model:** Linear Regression with 9 selected features.  
- **Performance:**  
  - RMSE: **3.27 minutes**  
  - R²: **0.856**  

This means the model predicts delivery time within ~3 minutes of actual values and explains ~86% of the variance.  

---

## 🔑 Feature Insights
- **`total_outstanding_orders` (+17.0 min)** → More pending orders increase delivery time.  
- **`total_onshift_dashers` (−12.0 min)** → More dashers on duty reduces delivery time.  
- **`distance` (+4.0 min)** → Longer distance increases delivery time.  
- **`isWeekend` (+1.5 min)** → Weekend deliveries take slightly longer.  
- **`subtotal` (+2.4 min)** → Higher-value orders tend to take longer.  

---

