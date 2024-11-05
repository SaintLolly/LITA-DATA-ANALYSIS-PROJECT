# LITA-DATA-ANALYSIS-CAPSTONE-PROJECT

## PROJECT TITLE: SALES PERFORMANCE ANALYSIS

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used-in-this-project)

[Data Collected](#data-collected)

[Data Cleaning and Preparations](#data-cleaning-and-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Inference](#inference)

PROJECT OVERVIEW: 
In this project, I am tasked with analyzing the sales performance of a retail store. I will be exploring the sales data to uncover and understand patterns and trends such as total sales by product, region, month, average sales per product and total revenue by region. The focus of this project is to produce an interactive and interesting Power BI dashboard that highlights these findings.

### DATA SOURCES
- Excel
- SQL

### TOOLS USED IN THIS PROJECT
- Microsoft Excel [Download Here].(https://www.microsoft.com)
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

### DATA CLEANING AND PREPARATIONS
In this initial phase of the Data cleaning and preparations, I performed the following actions:
1. Data loading and Inspection
2. Removing duplicates
3. Cleaning and changing the data types
4. Performing analysis to get the Revenue and Total Sales

### EXPLORATORY DATA ANALYSIS
This involves the exploring of the data to answer some questions about the data. Such as:
- Total Sales by Product
- Total sales by Region
- Total Sales by Month
- Total Revenue by Region
- Average Sales by Product
- Total Revenue by Product
- Quantity of Product by Region

### DATA ANALYSIS
This is where I include some line of codes, queries or some of the DAX expressions to answer the questions above.
The following analysis were done in Excel:

Q1.  ![image](https://github.com/user-attachments/assets/b531ae12-161e-4a88-a32f-cba9f1e14634)

![image](https://github.com/user-attachments/assets/96ec0ea6-94ee-4087-ad0e-f0d2a963d9ff)

Q2.   ![image](https://github.com/user-attachments/assets/caf76543-658f-433b-a70c-a6e4d56ef0a1)

![image](https://github.com/user-attachments/assets/c22bae29-d6ff-4fd1-afc2-7cfe66f51648)

Q3.   ![image](https://github.com/user-attachments/assets/26dc5c9c-3792-493b-b470-1a240295bfef)

![image](https://github.com/user-attachments/assets/55bebd27-dd9b-40ca-8988-5076b3a9bbcb)

Q4.   ![image](https://github.com/user-attachments/assets/3bc20ca6-e391-450d-9ec1-9eb4484437e5)

![image](https://github.com/user-attachments/assets/801919f2-f91e-4123-a709-cd638d99642b)

Q5.   ![image](https://github.com/user-attachments/assets/881d82f2-1cf6-47ba-9e84-b6c0784e361f)

![image](https://github.com/user-attachments/assets/bfbe5557-af7b-4ea6-9fe0-e440ed905015)

Q6.   ![image](https://github.com/user-attachments/assets/4ffa4764-0157-4336-bf48-0dce48a6f1f7)

![image](https://github.com/user-attachments/assets/0f51ac31-a7f5-4083-9824-2b31e6326dc9)

Q7.   ![image](https://github.com/user-attachments/assets/57766dd7-9b9a-4440-833c-b17f0886e663)

![image](https://github.com/user-attachments/assets/c327dfc5-b313-4780-b3f4-0269bf76f1b8)


### The following are the analysis conducted on SQL

Q1  Retrieve the total sales for each product category
```SQL
SELECT Product,SUM(Quantity) as Total_Sales
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Product
```

![image](https://github.com/user-attachments/assets/8b42e593-0d70-4a1d-b6ea-87372fb5c1f8)

Q2 Find the number of sales transactions in each region
```SQL
SELECT Region,SUM(Quantity) as Total_Sales
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Region
```

![image](https://github.com/user-attachments/assets/d3b05283-8ac8-409f-96f1-ccca9638ec79)

Q3 Find the highest-selling product by total sales value
```SQL
SELECT  Product, SUM(Quantity) as Total_Sales
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Product
Order By Total_Sales Desc
```

![image](https://github.com/user-attachments/assets/b9923eea-6b5f-46f5-a7fa-6a6c916dd0e7)

Q4 Calculate total revenue per product
```SQL
SELECT Product,SUM(Quantity*UnitPrice) as Total_Revenue
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Product
```

![image](https://github.com/user-attachments/assets/f1735187-0b20-4633-a0e8-3e156dfceeb3)

Q5 Calculate monthly sales totals for the current year(2024)
```SQL
SELECT  OrderMonth,SUM(Quantity) AS Total_Sales
FROM [dbo].[LITA_SALES.DATA]
WHERE OrderYear = 2024
GROUP BY OrderMonth
```

![image](https://github.com/user-attachments/assets/65a83758-b2b0-4806-b56c-ef985297db5e)

Q6 find the top 5 customers by total purchase amount
```SQL
SELECT  Top 5 Customer_Id,SUM(Quantity) AS Total_Purchase
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Customer_Id
ORDER BY Total_Purchase DESC
```

![image](https://github.com/user-attachments/assets/c35d2a99-b13a-4bb4-bb82-fe10f49f76dc)

Q7 calculate the percentage of total sales contributed by each region
```SQL
SELECT Region, SUM(Revenue)/SUM(Quantity)*0.1 AS Percentage_of_Total_Sales
FROM [dbo].[LITA_SALES.DATA]
GROUP BY Region
ORDER BY Percentage_of_Total_Sales
```

![image](https://github.com/user-attachments/assets/fbdfa8e9-b50c-467a-b147-03fe6d8c1bec)

Q8 Identify products with no sales in the last quarter
```SQL
SELECT Product,SUM(Quantity) AS Sales
FROM [dbo].[LITA_SALES.DATA]
WHERE MONTH(OrderDate) BETWEEN 10 AND 12  -- Months 10, 11, and 12 (October to December)
GROUP BY Product
HAVING SUM(Quantity)= 0
```

![image](https://github.com/user-attachments/assets/e03392e8-b2bb-43c5-809f-252b0dc24c1f)


### The following are the visualization done on Power BI

![image](https://github.com/user-attachments/assets/42155bcb-5401-484c-a83d-4590d033f7a3)

### Inference

- Regional Performance: The South maintains an increase in the number of purchased items, total revenue showing consistency in its performance.
- Strategic Implications: The stability in revenue across regions suggests that while some areas are performing well, there may be opportunities for growth in regions like the West and North. Targeted marketing strategies could help enhance their performance. The Southern region's strong performance should be leveraged as a model for other regions, potentially sharing successful strategies or practices.
