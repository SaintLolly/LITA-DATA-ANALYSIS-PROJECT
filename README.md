# LITA-CAPSTONE-PROJECT

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

![image](https://github.com/user-attachments/assets/306eced4-48af-4fe4-b275-1288f280947f)

### Inference

#### Total Sales by Product
This report outlines the total sales for each product based on the quantity sold. The data provided indicates the number of units sold for each product.
1. Best-Selling Product: Hat leads the sales with a total of 15,929 units sold. This indicates strong customer preference and suggests high demand for this item compared to others.
2. Other Top Performers: Shoes and Shirts follow closely, with 14,402 units and 12,388 units sold, respectively. These products also contribute significantly to the overall sales, with numbers that are comparable to the top seller (Hat).
3. Moderate Sales: Gloves sold 12,369 units, slightly trailing behind Shirts, but still reflecting solid demand in the market.
4. Lowest Sales: Jacket recorded the lowest sales with 5,452 units sold. This may indicate weaker demand, or that it is a more niche product compared to others like hats and shoes.

#### Recommendations
Focus on High Performers (Hat, Shoes, Shirt): Given their high sales figures, these products could be the focus of additional marketing efforts, promotional campaigns, or bundling strategies to further boost sales.

i. Review Jacket and Socks: Since Jackets have the lowest sales, it may be useful to assess the market demand, pricing, or promotional strategies. For Socks, explore the possibility of increasing visibility or introducing variations in style or material to attract more customers.

ii. Inventory and Replenishment Strategy: The high sales volumes for Hat, Shoes, and Shirts suggest that these items should be prioritized in inventory management to prevent stockouts, especially in peak sales periods.

#### Conclusion
This report shows a diverse range of product sales, with Hat emerging as the highest performer. By analyzing these sales trends, businesses can adjust strategies to capitalize on strong sellers and explore ways to boost the performance of lower-selling products.

#### Total Sales by Region
This report presents the total sales by region, based on the quantity of items sold. The data is categorized by region, with the quantity representing the total number of units sold in each region. South Region has the highest sales with 24,298 units, accounting for 28.11% of the total sales. This indicates that the South region is the most significant contributor to overall sales. East Region follows with 20,361 units, contributing 23.18% to the total sales. North Region sold 12,402 units, making up 14.26% of the total sales. This suggests a moderate contribution to overall sales but still a notable part of the total sales mix. West Region has the lowest sales with 11,400 units, representing 13.43% of the total sales. While the West region contributes the least in terms of quantity, it still makes up a significant portion of the total sales.

#### Insights and Recommendations
The South Region is the clear leader in sales, so further targeted marketing efforts or sales strategies in this region could yield even higher growth.
The East Region performs well but lags behind the South. It might benefit from increased promotion or additional sales resources to close the gap.
The North and West Regions are underperforming compared to the South and East, contributing relatively smaller shares of total sales. A deeper dive into market conditions or consumer behavior in these regions could help identify opportunities to improve performance.

#### Conclusion
The South region leads in total sales, followed by the East, North, and West regions. Analyzing regional performance is critical for identifying areas of opportunity. Focusing efforts on the regions with lower sales or leveraging the strengths of the higher-performing regions could help optimize sales across all regions.


