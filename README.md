# Task 7 — Sales Data Analysis with SQLite & Python (Google Colab)

## 📌 Overview
This project connects **Python** to an **SQLite database**, processes sales data, runs SQL queries, and visualizes the results.  
The work is done in **Google Colab** using a provided dataset (`Online Sales Data.csv`) or generated demo data.

---

## 📂 Files in this Project
- `task7_colab.ipynb` — Colab notebook containing all steps and code.
- `sales_data.db` — SQLite database with the cleaned sales data.
- `sales_summary.csv` — Output of the SQL summary (Product, Total Quantity, Revenue).
- `sales_revenue_bar.png` — Bar chart of top products by revenue.
- Additional charts:
  - `top_qty_products.png` — Top 10 products by quantity sold.
  - `revenue_distribution.png` — Histogram of revenue distribution.
  - `quantity_vs_price.png` — Scatter plot of quantity vs price.
  - `revenue_vs_quantity_bubble.png` — Bubble chart of revenue vs quantity.
  - `top5_revenue_pie.png` — Pie chart of top 5 products by revenue share.

---

## 🛠 Steps Performed
1. **Data Loading**
   - Loaded the CSV file into a Pandas DataFrame.
   - Generated demo data if no file was uploaded.

2. **Data Normalization**
   - Standardized column names to `product`, `quantity`, and `price`.
   - Handled missing quantity or price values by calculating from `sales` column if available.
   - Removed negative values and empty products.

3. **SQLite Database Creation**
   - Created `sales_data.db` with a single table `sales`.
   - Inserted all cleaned sales data into the database.

4. **SQL Query Execution**
   - Ran a `GROUP BY product` query to calculate:
     - `total_qty` = Total quantity sold per product.
     - `revenue` = Total revenue (`SUM(quantity * price)`).
   - Sorted results by highest revenue.

5. **Data Visualization**
   - Bar chart of **Top N Products by Revenue**.
   - Additional charts for better insights (quantity ranking, revenue distribution, scatter plots, pie chart).

6. **File Export**
   - Saved the SQL summary to `sales_summary.csv`.
   - Saved all visualizations as PNG images.
   - Closed the database connection.

---

## 📊 Example SQL Query Used
```sql
SELECT 
  product, 
  SUM(quantity) AS total_qty, 
  SUM(quantity * price) AS revenue
FROM sales
GROUP BY product
ORDER BY revenue DESC;

