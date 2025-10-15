# 🧹 Online Retail II – Data Cleaning, RFM Segmentation & CLTV Prediction

## 📄 Overview
This project performs **data cleaning, feature engineering, and advanced customer analytics** on the **Online Retail II dataset (`online_retail_II.xlsx`)**.  
The dataset contains real-world e-commerce transactions, and the notebook focuses on creating a clean dataset suitable for **RFM analysis**, **customer segmentation**, and **Customer Lifetime Value (CLTV)** prediction using statistical and machine learning models.

---

## 🧰 Tech Stack
- **Python 3.10+**
- **Libraries Used**
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `scikit-learn`
  - `lifetimes`
  - `openpyxl`

---

## 📦 Dataset Description
**File:** `online_retail_II.xlsx`

| Column Name | Description |
|--------------|-------------|
| `Invoice` | Invoice number (starting with “C” = cancelled order) |
| `StockCode` | Unique product code |
| `Description` | Product name |
| `Quantity` | Quantity of items purchased |
| `InvoiceDate` | Date and time of transaction |
| `Price` | Price per unit |
| `Customer_ID` | Unique customer identifier |
| `Country` | Customer’s country of residence |

---

## 🧼 Data Cleaning Steps
1. **Load and Inspect Data**
   ```python
   df = pd.read_excel("online_retail_II.xlsx")
   ```
2. **Handle Missing Values**
   ```python
   df['customer_id'].fillna('anonymous', inplace=True)
   df['description'].fillna('Unknown item', inplace=True)
   ```
3. **Data Type Conversion**
   ```python
   df['invoicedate'] = pd.to_datetime(df['invoicedate'])
   df['customer_id'] = df['customer_id'].astype(str)
   ```
4. **Feature Engineering**
   - Created `month`, `day_of_week`, and `hour` columns.
   - Added `total = quantity * price`.
5. **Remove Duplicates & Invalid Records**
   - Removed cancelled invoices.
   - Dropped duplicates and negative quantities.
6. **Export Cleaned Data**
   ```python
   df.to_csv("data_cleaned.csv", index=False)
   ```

---

## 📊 RFM Analysis
Calculated **Recency, Frequency, Monetary (RFM)** metrics for each customer and segmented them into groups like **VIP**, **Loyal**, **Promising**, and **At Risk**.

---

## 🧠 Customer Segmentation
Performed clustering on RFM data using:
- **DBSCAN**
- **Gaussian Mixture Models (GMM)**
- Visualized clusters with **PCA**

---

## 💰 Customer Lifetime Value (CLTV)
Used `lifetimes` models:
- **BetaGeoFitter (BG/NBD)** for purchase prediction
- **GammaGammaFitter** for monetary value prediction  
Predicted **6-month CLTV** and visualized distribution.

---

## 📈 Key Insights
- 6,859 duplicate transactions and 11,793 invalid records removed  
- 4,339 unique customers identified  
- Customers segmented by value and behavior  
- CLTV model estimated top revenue-generating users

---

## 📂 File Structure
```
├── data_cleaning.ipynb
├── online_retail_II.xlsx
├── data_cleaned.csv
└── README.md
```

---

## ✍️ Author
**Vikrant Singh**  
*Data Science Enthusiast | IIT Jodhpur*
