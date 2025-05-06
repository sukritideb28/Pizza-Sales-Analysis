# Pizza-Sales-Analysis
This project analyzes pizza sales data to uncover valuable insights such as best-selling pizzas, busiest order times, and overall sales trends. 


  -- Total Revenue-- 
SELECT SUM(total_price) AS 'TOTAL_REVENUE' from pizza_sales$;

-- Average Order Values--
SELECT SUM(total_price)/ COUNT(DISTINCT order_id) AS 'AVG_ORDER_VALUE' 
 FROM PIZZA_SALES$;

 --Total Pizzas Sold --
 SELECT SUM(quantity) AS 'TOTAL_PIZZA_SOLD'
 FROM PIZZA_SALES$;

 --Total Orders--
 SELECT COUNT(DISTINCT order_id) AS 'TOTAL_ORDERS'


 --Average Pizzas Per Oreder--
 SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) /
 CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS 'AVG_PIZZA_PER_ORDER'
 FROM PIZZA_SALES$;

 --Daily Trend For Total Orders--
 SELECT DATENAME(DW ,order_date) AS 'ORDER_DAY', COUNT(DISTINCT order_id) AS 'TOTAL_ORDERS'
 FROM PIZZA_SALES$
 GROUP BY DATENAME(DW,order_date);

 --Hourly Trend For Totals Orders--
 SELECT DATENAME(MONTH,order_date) AS 'MONTH_NAME' ,COUNT(DISTINCT order_id) AS 'TOTAL_ORDERS'
 FROM PIZZA_SALES$
 GROUP BY DATENAME(MONTH, order_date)
 ORDER BY TOTAL_ORDERS DESC;

  --Percentage Of Sales By Pizza Category--
  SELECT pizza_category ,SUM(total_price) * 100 / (SELECT SUM(total_price) FROM PIZZA_SALES$) AS 'PCT'
  FROM PIZZA_SALES$
  GROUP BY pizza_category;

   --Percentage Of Sales By Pizza Size--
  SELECT pizza_size ,CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM PIZZA_SALES$) AS DECIMAL(10,2)) AS 'PCT' 
  FROM PIZZA_SALES$
  GROUP BY pizza_size
  ORDER BY PCT DESC;

  --Top 5 Best Seller By Revenue--
  SELECT TOP 5 pizza_name ,sum(total_price) AS 'TOTAL_REVENUE' 
  FROM PIZZA_SALES$
  GROUP BY pizza_name
  ORDER BY TOTAL_REVENUE DESC;

 
  -- Bottom 5 Best Seller By Revenue--
  SELECT TOP 5 pizza_name ,sum(total_price) AS 'TOTAL_REVENUE' 
  FROM PIZZA_SALES$
  GROUP BY pizza_name
  ORDER BY TOTAL_REVENUE ASC;
