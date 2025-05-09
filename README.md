# Pizza-Sales-Analysis 

##Project Objective

This project analyzes pizza sales data to uncover valuable insights such as best-selling pizzas, busiest order times, and overall sales trends. 

--QUESTIONS KPI"S--
 We need to analyze key indicators for our pizza sales data to gain insights into our business performance .We want to calculate the following metrics.

 1. Total Revenue-- 
SELECT SUM(total_price) AS 'TOTAL_REVENUE' from pizza_sales$;

2. Average Order Values
SELECT SUM(total_price)/ COUNT(DISTINCT order_id) AS 'AVG_ORDER_VALUE' 
 FROM PIZZA_SALES$;

 3. Total Pizzas Sold
 SELECT SUM(quantity) AS 'TOTAL_PIZZA_SOLD'
 FROM PIZZA_SALES$;

 4. Total Orders
 SELECT COUNT(DISTINCT order_id) AS 'TOTAL_ORDERS'


 5. Average Pizzas Per Oreder
 SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) /
 CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS 'AVG_PIZZA_PER_ORDER'
 FROM PIZZA_SALES$;

 6. Daily Trend For Total Orders
 SELECT DATENAME(DW ,order_date) AS 'ORDER_DAY', COUNT(DISTINCT order_id) AS 'TOTAL_ORDERS'
 FROM PIZZA_SALES$
 GROUP BY DATENAME(DW,order_date);

 7. Hourly Trend For Totals Orders
 SELECT DATENAME(MONTH,order_date) AS 'MONTH_NAME' ,COUNT(DISTINCT order_id) AS 'TOTAL_ORDERS'
 FROM PIZZA_SALES$
 GROUP BY DATENAME(MONTH, order_date)
 ORDER BY TOTAL_ORDERS DESC;

  8. Percentage Of Sales By Pizza Category
  SELECT pizza_category ,SUM(total_price) * 100 / (SELECT SUM(total_price) FROM PIZZA_SALES$) AS 'PCT'
  FROM PIZZA_SALES$
  GROUP BY pizza_category;

   9. Percentage Of Sales By Pizza Size
  SELECT pizza_size ,CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM PIZZA_SALES$) AS DECIMAL(10,2)) AS 'PCT' 
  FROM PIZZA_SALES$
  GROUP BY pizza_size
  ORDER BY PCT DESC;

  10. Top 5 Best Seller By Revenue
  SELECT TOP 5 pizza_name ,sum(total_price) AS 'TOTAL_REVENUE' 
  FROM PIZZA_SALES$
  GROUP BY pizza_name
  ORDER BY TOTAL_REVENUE DESC;

 
  11.  Bottom 5 Best Seller By Revenue
  SELECT TOP 5 pizza_name ,sum(total_price) AS 'TOTAL_REVENUE' 
  FROM PIZZA_SALES$
  GROUP BY pizza_name
  ORDER BY TOTAL_REVENUE ASC;

--Dashboard Interactions--
  - <a href="https://github.com/sukritideb28/Pizza-Sales-Analysis/commit/ef003f7ef9e153f47da7f2937ff745c79f40ae2b">View Dashboard</a>
