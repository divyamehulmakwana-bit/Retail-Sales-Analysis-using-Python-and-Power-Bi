# 🛒 Retail Sales Analysis – Data Cleaning (Python) & Dashboard (Power BI)  

## 📌 Project Overview  
This project demonstrates the **end-to-end workflow** of cleaning a real-world retail sales dataset in Python and building an **interactive dashboard in Power BI**.  
The dataset was sourced from Kaggle:  
🔗 [Retail Store Sales (Dirty Dataset)](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)  

The dataset contained **~12,000 rows** with multiple data quality issues (missing values, inconsistent categories, incorrect totals, datatype mismatches, etc.).  
I performed **data cleaning in Python (Jupyter Notebook)**, exported the clean data, and then built a **Power BI dashboard** to analyze sales, customer behavior, and transaction trends.  

---

## 📂 Dataset Details  

| Column             | Description                                                                 | Example Values     |
|--------------------|-----------------------------------------------------------------------------|--------------------|
| **Transaction ID** | Unique identifier for each transaction                                      | `TXN_1234567`      |
| **Customer ID**    | Unique identifier for each customer (25 unique customers)                   | `CUST_01`          |
| **Category**       | Purchased item category                                                     | `Food`, `Furniture`|
| **Item**           | Name of the purchased item (may contain nulls)                              | `Item_1_FOOD`, `None` |
| **Price Per Unit** | Static price of a single unit (may contain nulls)                           | `4.00`, `None`     |
| **Quantity**       | Quantity purchased (may contain nulls)                                      | `1`, `None`        |
| **Total Spent**    | Transaction total = Price Per Unit × Quantity (may contain nulls)           | `8.00`, `None`     |
| **Payment Method** | Payment method used (may contain invalid values)                            | `Cash`, `Credit Card` |
| **Location**       | Transaction location (may contain invalid values)                           | `In-store`, `Online` |
| **Transaction Date** | Date of the transaction (always valid)                                    | `2023-01-15`       |
| **Discount Applied** | Boolean field indicating discount applied (many nulls)                    | `True`, `False`, `None` |

---

## 🛠 Data Cleaning (Python)  

I used **Pandas** in Jupyter Notebook to clean the dataset. Key steps:  

1. **Exploration** – Used `.describe()`, `.info()`, `.shape` to understand structure & issues.  
2. **Duplicates** – Checked and removed duplicate rows.  
3. **Null Values Handling**  
   - Dropped `Discount Applied` column (too many missing values, no reliable way to impute).  
   - If `Quantity` & `Price Per Unit` were available but `Total Spent` missing → recalculated it.  
   - If `Total Spent` available but either `Quantity` or `Price Per Unit` missing → derived missing value.  
   - Filled remaining nulls in `Quantity` with its **mode**.  
4. **Category Fixes** – Removed extra characters (`Food.` → `Food`), corrected invalid entries.  
5. **Datatypes** – Converted columns into proper datatypes (`Date` → datetime, `Price/Quantity` → numeric, etc.).  
6. **Renaming Columns** – Standardized column names for readability.  
7. **New Feature** – Created a **Spending Behavior** column to classify transactions as **High / Low spending**.  

📤 Final cleaned dataset was exported as **Excel file** for Power BI.  

---

## 📊 Power BI Dashboard  

The cleaned data was loaded into Power BI for visualization.  
I also created a **Date Table** to support time intelligence (YoY growth, trends).  

### **KPIs Created**  
- **Total Revenue** with comparison to Previous Year  
- **Sales Growth %**  
- **Best Customer** (Emma) with:  
  - Total Transactions: **13K**  
  - Avg Quantity per Transaction: **6**  
  - Avg Price per Transaction: **23.37**  
- **Total Customers**: 25  

### **Visuals**  
- **Line + Column Chart** → Total Revenue & Transactions by Customers  
- **Treemap** → Transactions by Weekday  
- **Bar Charts** → Transactions by Category, Revenue by Category  
- **Donut Charts** →  
  - Payment Distribution (Cash, Credit Card, etc.)  
  - Transactions by Mode (Online vs In-store)  
- **Line Chart** → Sales & Transactions over Time (Yearly trend)  

📷 Dashboard Preview:  
![Retail Sales Dashboard](https://github.com/divyamehulmakwana-bit/Retail-Sales-Analysis-using-Python-and-Power-Bi/blob/main/Screenshots/Report.png)  
![Retail Sales Dashboard](https://github.com/divyamehulmakwana-bit/Retail-Sales-Analysis-using-Python-and-Power-Bi/blob/main/Screenshots/Report.png) 
---

## 🚀 Tech Stack  
- **Python (Pandas, Jupyter Notebook)** → Data Cleaning & Preprocessing  
- **Power BI** → Data Modeling & Dashboard Creation  
- **Excel** → Intermediate storage of cleaned dataset  

---

## 📈 Key Insights  
- Emma is the **most valuable customer**, contributing the highest revenue and transactions.  
- **Food** is the leading category by both transactions and revenue.  
- **In-store** purchases dominate over online.  
- **Weekdays** show higher transaction volume compared to weekends.  
- Consistent **year-over-year growth** in both sales & transactions.  

---

