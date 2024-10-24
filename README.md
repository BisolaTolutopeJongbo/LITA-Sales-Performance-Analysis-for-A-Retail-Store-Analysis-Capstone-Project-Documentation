# DOCUMENTATION
### Project Title: Sales Performance Analysis for A Retail Store Analysis Capstone Project
### Project Overview
This project focuses on analyzing the sales performance of a retail store to uncover key business insights. Using tools like Excel for data cleaning and data summarization, SQL Server for analysis, and Power BI for visualization, I explored various metrics such as top selling products, regional performance, and monthly sales trends. The project demonstrates data preparation, exploratory data analysis (EDA), and actionable recommendations to drive strategic decision-making. The goal is to produce an interactive Power BI dashboard that highlights these findings.
### Data Source
The dataset used in this project is titled [[Sales Data.csv](https://github.com/user-attachments/files/17505520/Sales.Data.csv)
], which contains records of sales transactions including details such as product, region, quantity, unit price, and order date.
### Tools Used
1. Microsoft Excel: Used for data cleaning (removing duplicates) and summarizing the data using pivot tables.
2. SQL Server: Performed data analysis and created views for generating insights.
3. Power BI: Used to visualize the findings through interactive dashboards.

### Data Cleaning and Preparation
1. Duplicate Removal: Duplicates were identified and removed to ensure accurate analysis.
2.	New Columns: Two new columns were added to the dataset:
3. OrderMonth: Extracted the month from the OrderDate field.
4. OrderYear: Extracted the year from the OrderDate field.
5. Revenue: A calculated field representing total revenue per transaction (Quantity * Unit Price).
### SQL Code for New Columns Added
``` SQL
ALTER TABLE [dbo].[Sales Data]
ADD OrderMonth nvarchar(50);

UPDATE [dbo].[Sales Data]
SET OrderMonth = DATENAME(MONTH, OrderDate);

ALTER TABLE [dbo].[Sales Data]
ADD OrderYear int;

UPDATE [dbo].[Sales Data]
SET OrderYear = Year(OrderDate);

ALTER TABLE [dbo].[Sales Data]
ADD Revenue int;

UPDATE [dbo].[Sales Data]
SET Revenue = (Quantity * UnitPrice);
 ```

