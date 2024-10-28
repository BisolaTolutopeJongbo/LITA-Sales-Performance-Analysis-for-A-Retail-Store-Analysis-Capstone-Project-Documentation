# DOCUMENTATION

### Project Title: Sales Performance Analysis for A Retail Store Analysis Capstone Project
---
[Project Overview](#project-overview)

[Data Source](#Data-source)

[Tools Used](#Tool-Used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Pivot Table Report](#pivot-table-report)

[SQL Code for New Columns Added](#sql-code-for-new-columns-added)

[Exploratory Data Analysis(EDA)](#exploratory-data-analysis)

[SQL Queries Analysis](#SQL-Queries-Analysis)

[Data Visualization](#data-visualization)

[Conclusion](conclusion)

---
### Project Overview
This project focuses on analyzing the sales performance of a retail store to uncover key business insights. Using tools like Excel for data cleaning and data summarization, SQL Server for analysis, and Power BI for visualization, I explored various metrics such as top selling products, regional performance, and monthly sales trends. The project demonstrates data preparation, exploratory data analysis (EDA), and actionable recommendations to drive strategic decision-making. The goal is to produce an interactive Power BI dashboard that highlights these findings.

---

### Data Source
The dataset used in this project is titled [[Sales Data.csv](https://github.com/user-attachments/files/17505520/Sales.Data.csv)
], which contains records of sales transactions including details such as product, region, quantity, unit price, and order date.

---

### Tools Used
1. Microsoft Excel: Used for data cleaning (removing duplicates) and summarizing the data using pivot tables.
2. SQL Server: Performed data analysis and created views for generating insights.
3. Power BI: Used to visualize the findings through interactive dashboards.

---

### Data Cleaning and Preparation
1. Duplicate Removal: Duplicates were identified and removed to ensure accurate analysis.
2.	New Columns: Two new columns were added to the dataset:
3. OrderMonth: Extracted the month from the OrderDate field.
4. OrderYear: Extracted the year from the OrderDate field.
5. Revenue: A calculated field representing total revenue per transaction (Quantity * Unit Price).

---

### Pivot Table Report

<img width="927" alt="Sales Pivot Table" src="https://github.com/user-attachments/assets/4543b634-d872-4e21-bc85-d607f5f68a02">

---

### SQL Code for New Columns Added
``` SQL
ALTER TABLE [dbo].[Sales Data]
ADD OrderMonth nvarchar(50)

UPDATE [dbo].[Sales Data]
SET OrderMonth = DATENAME(MONTH, OrderDate)

ALTER TABLE [dbo].[Sales Data]
ADD OrderYear int

UPDATE [dbo].[Sales Data]
SET OrderYear = Year(OrderDate)

ALTER TABLE [dbo].[Sales Data]
ADD Revenue int

UPDATE [dbo].[Sales Data]
SET Revenue = (Quantity * UnitPrice)
 ```

---

### Exploratory Data Analysis(EDA)
1.  Total Sales per Product Category
2.  Sales Transactions in Each Region
3.  Top Selling Product
4.  Revenue Per Product
5.  Monthly Sales for Year 2024
6.  Top 5 Customers
7.  Percentage of  Sales Contributed by Region
8.  Products with No Sales in the Last Quarter


---

  ### SQL Queries Analysis
1. Total Sales for Each Product Category 
```sql
CREATE VIEW VW_LITA_SALES_CAPSTONE_PROJECT
AS
SELECT Product,SUM(Quantity) as Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Product
```
2. Number of Sales Transactions in Each Region
```sql
CREATE VIEW VW2_LITA_SALES_CAPSTONE_PROJECT AS
SELECT Region, SUM(Quantity) AS Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Region
```
3. Highest-Selling Product by Total Sales Value
```sql
CREATE VIEW VW3_LITA_SALES_CAPSTONE_PROJECT AS
SELECT Product, SUM(Quantity) AS Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Product
ORDER BY Total_Sales DESC
```
4. Total Revenue Per Product
```sql
CREATE VIEW VW4_LITA_SALES_CAPSTONE_PROJECT AS
SELECT Product, SUM(Quantity * UnitPrice) AS Total_Revenue
FROM [dbo].[Sales Data]
GROUP BY Product
```
5. Monthly Sales Totals for the Current Year (2024)
```sql
CREATE VIEW VW5_LITA_SALES_CAPSTONE_PROJECT AS
SELECT OrderMonth, SUM(Quantity) AS Total_Sales
FROM [dbo].[Sales Data]
WHERE OrderYear = 2024
GROUP BY OrderMonth
```
6. Top 5 Customers by Total Purchase Amount
```sql
CREATE VIEW VW6_LITA_SALES_CAPSTONE_PROJECT AS
SELECT TOP 5 Customer_Id, SUM(Quantity) AS Total_Purchase
FROM [dbo].[Sales Data]
GROUP BY Customer_Id
ORDER BY Total_Purchase DESC
```
7. Percentage of Total Sales Contributed by Each Region
```sql
CREATE VIEW VW7_LITA_SALES_CAPSTONE_PROJECT AS
SELECT Region, SUM(Revenue) / SUM(Quantity) * 0.1 AS Percentage_of_Total_Sales
FROM [dbo].[Sales Data]
GROUP BY Region
ORDER BY Percentage_of_Total_Sales
```
8. Products with No Sales in the Last Quarter
```sql
CREATE VIEW VW8_LITA_SALES_CAPSTONE_PROJECT AS
SELECT Product, SUM(Quantity) AS Sales
FROM [dbo].[Sales Data]
WHERE MONTH(OrderDate) BETWEEN 10 AND 12
```
---
### Data Visualization

---

### Conclusion

