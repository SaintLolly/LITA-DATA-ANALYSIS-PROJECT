# LITA-DATA-ANALYSIS-CAPSTONE-PROJECT

## PROJECT TITLE: SALES PERFORMANCE ANALYSIS
PROJECT OVERVIEW: 
In this project, I am tasked with analyzing the sales performance of a retail store. I will be exploring the sales data to uncover and understand patterns and trends such as total sales by product, region, month, average sales per product and total revenue by region. The focus of this project is to produce an interactive and interesting Power BI dashboard that highlights these findings.

### DATA SOURCE
- Excel
- SQL

### TOOLS USED IN THIS PROJECT
- Microsoft Excel [Download Here].(https://wwww.microsoft.com)
1. for Data Cleaning
2. Analysis
3. Visualization

- SQL - Structured Query Language
1. Quering of Data

- Power BI - Power Business Intelligent
1. Data visualisation
2. Report

### DATA COLLECTED
The dataset includes the following key columns:
1. OrderID: This is the number of each product sold
2. CustomerID: This is the number attached to each customer whon bought one product or the other
3. Product: These are the items available for sale
4. Region: This is the different locations where the product are sold and bought
5. OrderDate: This is the date on which a particular sale or transaction was made
6. Quantity: The number of units sold for a given transaction
7. Unit Price: The amount of unit sold for a given transaction
8. Revenue/Total Sales: The total monetary value generated from the sale

### DATA CLEANING AND PREPARATION
In this initial phase of the Data cleaning and preparations, I performed the following actions:
1. Data loading and Inspection
2. Removing duplicates
3. Cleaning and changing the data types
4. Performing analysis to get the Revenue and Total Sales

### EXPLORATORY DATA ANALYSIS
This involves the exploring of the data to answerf some questions about the data. Such as:
- Total Sales by Product
- Total sales by Region
- Total Sales by Month
- Total Revenue by Region
- Average Sales by Product
- Total Revenue by Product
- Quantity of Product by Region

### DATA ANALYSIS
This is where I include some line of codes, queries or some of the DAX expressions to answer the questions above

```SQL
SELECT Product,SUM(Quantity) as Total_Sales
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Product
```

