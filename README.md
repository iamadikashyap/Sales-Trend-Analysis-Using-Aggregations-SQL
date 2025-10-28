# 📊 Sales Trend Analysis Using Aggregations

## 🎯 Objective
Analyze **monthly revenue** and **order volume** using SQL aggregation techniques.

---

## 🧰 Tools
- PostgreSQL / MySQL / SQLite  
- Google Colab (for running SQL with SQLite in Python)

---

## 🗃️ Dataset
**Table:** `online_sales`  
**Columns:**
- `order_id` → Unique order identifier  
- `order_date` → Date of the order  
- `amount` → Order amount (revenue)  
- `product_id` → Product identifier  

---

## 🧠 Hints / Mini Guide
- Use `EXTRACT(MONTH FROM order_date)` (or `strftime('%m', order_date)` in SQLite) for month.  
- `GROUP BY` year/month.  
- Use `SUM()` for total revenue.  
- Use `COUNT(DISTINCT order_id)` for total order volume.  
- Use `ORDER BY` for sorting.  
- Add `WHERE` clauses to limit by year or specific time periods.

---

## 🧾 SQL Query
```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders
FROM 
    online_sales
GROUP BY 
    order_year, order_month
ORDER BY 
    order_year, order_month;
