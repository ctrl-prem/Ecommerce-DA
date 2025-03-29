# 📊 E-commerce Data Analysis using SQL & Python

## 📌 Overview
This project leverages **SQL and Python** to analyze an **E-commerce dataset**. The analysis includes customer behavior, sales trends, revenue distribution, and retention rates to derive valuable business insights.

## 📁 Project Structure
```
📂 E-commerce Data Analysis
│── dataset_link.txt  # Contains the dataset link
│── csv_to_sql.py  # Script to convert CSV files into SQL tables
│── questions.txt  # List of queries to be solved
│── python+sql_ecommerce.ipynb  # Jupyter Notebook with analysis
│── README.md  # Project documentation
```

## 🛠️ Tools & Technologies
- **SQL** (MySQL/PostgreSQL) - Data extraction, transformation, and analysis
- **Python** (Pandas, NumPy, Matplotlib, Seaborn) - Data manipulation & visualization
- **Jupyter Notebook** - Interactive analysis environment

## 📊 Analysis Performed
### **Basic Queries**
✅ List unique customer locations 📍  
✅ Count orders placed in 2017 📆  
✅ Calculate total sales per category 💰  
✅ Percentage of installment payments 📊  
✅ Count customers from each state 🏢  

### **Intermediate Queries**
✅ Monthly order trends (2018) 📆  
✅ Average products per order by city 🏙️  
✅ Revenue share per product category 📈  
✅ Correlation between price & purchases 🔗  
✅ Seller-wise revenue ranking 🏆  

### **Advanced Queries**
✅ Moving average of order values 📉  
✅ Cumulative monthly sales 📊  
✅ Year-over-year sales growth 📈  
✅ Customer retention analysis 📌  
✅ Top 3 high-spending customers per year 💵  

## 🚀 Key Features & Justification
### 1️⃣ **Comprehensive Data Analysis with SQL & Python**
✔ Used SQL for efficient querying & Python for data visualization.
✔ Example: Monthly orders in 2018:
```sql
SELECT DATE_FORMAT(order_date, '%Y-%m') AS month, COUNT(*) AS total_orders
FROM orders
WHERE YEAR(order_date) = 2018
GROUP BY month;
```

### 2️⃣ **Advanced Query Techniques for Business Insights**
✔ Leveraged CTEs, window functions, and aggregations.
✔ Example: Moving average of order values:
```sql
SELECT customer_id, order_date,
       AVG(order_value) OVER (PARTITION BY customer_id ORDER BY order_date ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS moving_avg
FROM orders;
```

### 3️⃣ **Data-Driven Decision Making**
✔ Insights on retention rates, revenue trends & customer spending patterns.
✔ Example: Customer retention analysis:
```sql
WITH FirstPurchase AS (
    SELECT customer_id, MIN(order_date) AS first_order
    FROM orders
    GROUP BY customer_id
)
SELECT YEAR(o.order_date) AS year,
       COUNT(DISTINCT o.customer_id) AS repeat_customers,
       COUNT(DISTINCT fp.customer_id) AS total_customers,
       ROUND(COUNT(DISTINCT o.customer_id) / COUNT(DISTINCT fp.customer_id) * 100, 2) AS retention_rate
FROM orders o
JOIN FirstPurchase fp ON o.customer_id = fp.customer_id
WHERE DATEDIFF(o.order_date, fp.first_order) <= 180
GROUP BY year;
```

## 📥 Dataset
- The dataset can be accessed via **`dataset_link.txt`**.
- It contains **order details, customer information, product data, and sales transactions.**

## 🏗️ How to Run the Project
1️⃣ Clone the repository:
```sh
git clone https://github.com/your_username/ecommerce-sql-python.git
```
2️⃣ Install dependencies:
```sh
pip install pandas numpy matplotlib mysql-connector-python
```
3️⃣ Convert CSV data to SQL tables:
```sh
python csv_to_sql.py
```
4️⃣ Open **`python+sql_ecommerce.ipynb`** and run the analysis.

## 🤝 Contributing
Feel free to fork the repo and submit pull requests! 🚀

---
💡 *Transforming raw data into actionable insights with SQL & Python!*

