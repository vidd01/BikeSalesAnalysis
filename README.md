# BikeSalesAnalysis
In this project I analyzed the data to create an interactive Dashboard to make Intelligent Business decisions

### Introduction

Tableau is a powerful tool for data analysis and visualization, it helps to create reports, dashboards, and stories using different charts and graphs. The workbooks and the dashboards created using Tableau can be shared locally or publicly. Bike Sales Analysis is the process of identifying the Revenue of the sales in three years, who are the top customers of the store and which stores has highest revenue. This can help businesses to understand why they are losing customers and how to retain them, as well as to target new and existing customers more effectively.

### About this project

In this project, I used the following steps to create the bike sales analysis:

- I created a tables in SSMS and connected that to Excel data sources and imported the relevant tables into tableau.
- Created relationships between the tables based on production and sales.
- Created a tables of orders_ID, order_date, customers, products, categories and stores etc.
- Prepared reports with slicers for date range and country, and visuals such as bar, line, pie, and heat map to show the trends and breakdowns of Bike 
  sales.

### ETL

- I extracted the data from database
- Using the 'Concat' function transformed the data as customers,revenue, sales_rep
- Loaded the data in tableau desktop for analysis of the bake sales
  
Here is the SQL code of bike sales data

SELECT ord.order_id, CONCAT(cus.first_name, ' ',cus.last_name) AS 'customers',
cus.city,cus.state,ord.order_date, 
SUM(ite.quantity) AS 'total_units',
SUM(ite.quantity * ite.list_price) AS 'revenue',
pro.product_name,
cat.category_name,
sto.store_name,
CONCAT(sta.first_name,' ',sta.last_name) AS 'sales_rep'
FROM sales.orders ord
JOIN sales.customers cus
ON ord.customer_id=cus.customer_id
JOIN sales.order_items ite
ON ord.order_id=ite.order_id
JOIN production.products pro
ON ite.product_id=pro.product_id
JOIN sales.stores sto
ON ord.store_id=sto.store_id
JOIN production.categories cat
ON pro.category_id=cat.category_id
JOIN sales.staffs sta
ON ord.staff_id=sta.staff_id
GROUP BY 
ord.order_id, CONCAT(cus.first_name, ' ',cus.last_name),
cus.city,cus.state,ord.order_date, pro.product_name, 
cat.category_name,sto.store_name,
CONCAT(sta.first_name,' ',sta.last_name)

### Report

The chart below shows the executive dashboard of bike sales.
![image](https://github.com/vidd01/BikeSalesAnalysis/assets/122332733/78a44ae6-c336-441b-8360-7b4648c63421)

![image](https://github.com/vidd01/BikeSalesAnalysis/assets/122332733/c5c9c521-1399-408e-b743-777d4924a757)



