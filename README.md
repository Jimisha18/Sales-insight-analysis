# Sales Data Analysis Project

**1) Problem statement:**

A retail company's manager wants to understand the sales insights of the business. Understanding how the company is doing in different regions he/she can work-out the weak areas of the business by attracting more customers using promotions and offers. Build an automated dash-board which provides quick and latest sales insights in-order to support data managers take data-driven decisions.
Dashboard should include features like Revenue breakdown by cities, Revenue breakdown by months and years, top 5 customers by revenue and sales quantity, top 5 products by revenue numbers.

**2) Data Exploartion using SQL:**

SQL database dump is in db_dump.sql file, you need to import it MySQL. Upon successful import one can understand that how the sales schema has 5 tables namely customers, date, markets, products and transactions.

**3) Data Analysis using SQL:**

Various SQL queries to understand the data well:

i) Show all customer records
```
SELECT * 
FROM customers;
```

ii) Show total number of customers
```
SELECT count(*) 
FROM customers;
```

iii) Show transactions for Chennai market (market code for chennai is Mark001)
```
SELECT * 
FROM transactions where market_code='Mark001';
```

iv) Show distrinct product codes that were sold in Chennai
```
SELECT distinct product_code 
FROM transactions where market_code='Mark001';
```

v) Show transactions where currency is US dollars
```
SELECT * 
from transactions where currency="USD"
```

vi) Show transactions in 2020 join by date table
```
SELECT transactions.*, date.* 
FROM transactions INNER JOIN date 
ON transactions.order_date=date.date 
where date.year=2020;
```

vii) Show total revenue in year 2020,
```
SELECT SUM(transactions.sales_amount) 
FROM transactions INNER JOIN date ON transactions.order_date=date.date 
where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";
```

viii) Show total revenue in year 2020, January Month
```
SELECT SUM(transactions.sales_amount) 
FROM transactions INNER JOIN date ON transactions.order_date=date.date 
where date.year=2020 and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");
```

ix) Show total revenue in year 2020 in Chennai
```
SELECT SUM(transactions.sales_amount) 
FROM transactions INNER JOIN date ON transactions.order_date=date.date 
where date.year=2020 and transactions.market_code="Mark001";
```

**4) ETL and data cleaning using Tableau:**

Connect MySQL to Tableau and the 5 tables namely customers, date, markets, products and transactions appears under sales schema for Tableau. Create a data model using STAR schema where the transcations is the center point connecting all tables building relationships.

Further, data cleaning is performed to remove Null values and outliers. Where the transactions data table has negative values where the range needs to be fixed. Standardize the dataset incase needed.

**5) Build dashboard using Tableau:**

Build different sheets of visualizations on various parameters by plotting relationships using line chart, pie-chart, bar graph and various other data visualization metrices. Finally, create a dashboard merging them together and make it interactive. Further, you can present the dashboard to the sales manager.


