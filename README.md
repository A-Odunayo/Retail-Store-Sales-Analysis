# Retail Store Sales Analysis

## Project Overview
This project involves a detailed analysis of sales data from a retail store. The goal is to identify top-selling products, assess regional performance, and uncover monthly sales trends. The findings are presented through an interactive Power BI dashboard with key visuals.

## Table of Content

- [Data Source](#Data-Source)

- [Project Structure](#Project-Structure)
  - [Tools Used](#Tools-Used)

- [Data Cleaning and Preparation](#Data-Cleaning-and-Preparation)

- [Data Exploration](#Data-Exploration)

- [Analysis Details](#Analysis-Details)
  - [Excel](#Excel)
  - [SQL Queries](#SQL-Queries)

- [Power BI Dashboard (Visualizations)](#Power-BI-Dashboard-Visualizations)

- [Recommendations](#Recommendations)
  
- [Project Instructions](#Project-Instructions)

## Data Source

The dataset used for this analysis is ["the retail store's sales data"](https://github.com/A-Odunayo/Capstone-Project/blob/main/Sales%20Data.csv). It includes transactional data on sales, products, and customers, enabling comprehensive sales performance analysis.

## Project Structure

The project consists of three main components, each managed in Excel, SQL, and Power BI.

### Tools Used

- **Excel**: Initial data exploration, including pivot tables and metric calculations.

  [Download here](https://microsoft-excel-2016.en.download.it/#google_vignette)
  
- **SQL**: Complex queries to retrieve and summarize targeted insights.

  [Download here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
  
- **Power BI**: Interactive dashboard to visually present insights.

  [Download here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)

## Data Cleaning and Preparation

Before analysis, the data underwent the cleaning and preparation steps below:

1. **Data Type Conversion**: Ensured that fields were in the correct format (e.g., converting date fields to Date format, numerical fields to Numeric format).
2. **Removing Duplicates**: I removed 40,079 duplicate records to prevent skewed results and ensure accuracy in my insights. This left me with 9,921 unique records that accurately reflect the necessary information for analysis. With this refined dataset, I can now deliver insights that are both reliable and actionable.
3. **Data Transformation**: Created new calculated fields, such as Revenue, to facilitate analysis.

## Data Exploration

The exploratory data analysis (EDA) phase included:

1. **Descriptive Statistics**: Generated summary statistics for numerical variables to understand distributions.
2. **Data Visualizations**: Created initial visualizations to identify patterns and trends in the data.
3. **Correlations**: Examined correlations between different variables like sales vs. region, sales vs. product category etc to identify relationships.
4. **Segment Analysis**: Analyzed data segments (e.g., by region, product category) to uncover insights and inform business decisions.

## Analysis Details

### Excel

The **Excel** workbook includes:

- **Pivot Tables**: Summarize total sales by product, region, and month.

   | Product Sales | Regional Sales | Monthly Sales Trend |
   |---------------|----------------|---------------------|
   |![Sales by Product](https://github.com/user-attachments/assets/8ff91a9d-5969-4d01-b38e-6ac47ba76305)|![Sales by Region](https://github.com/user-attachments/assets/46829599-5bf3-4590-9748-9e6cb1938972)|![Sales per Month](https://github.com/user-attachments/assets/ba125d99-bfde-4fe5-a3eb-401ae0232645)

- **Calculated Metrics**:

   | Average Sales Per Product | Top Products |
   |---------------------------|-------------------|
   |![Average Sales by Product](https://github.com/user-attachments/assets/3f2e8ca2-5579-4845-ad3c-cf8af40f5e3a)|![Top Products by Quantity Sold](https://github.com/user-attachments/assets/5ea1dcdf-2f81-493f-b26f-a49f76eaf0d7)|

### SQL Queries

The **SQL** queries aim to answer specific business questions:

- **Total Sales by Product Category**: Product performance by category in desending order.
  ```SQL
  Select [Product], sum(Revenue) as Total_Revenue from [dbo].[Sales Data]
  Group by [Product]
  Order by Total_Revenue desc
  
- **Sales Transactions by Region**: Count of sales transactions per region.
  ```SQL
  Select Region, COUNT(*) as Transaction_Count 
  From [dbo].[Sales Data] Group by Region
  
- **Highest-Selling Product**: Product with the highest sales value.
  ```SQL
  Select top 1 [Product], sum(Revenue) as Total_Revenue from [dbo].[Sales Data]
  Group by [Product]
  Order by Total_Revenue desc
  
- **Monthly Sales Total**: Monthly sales for the current year.
  ```SQL
  Select Datefromparts(Year(OrderDate), Month(OrderDate), 1) as Sales_Month, Sum(Revenue) as Monthly_Total  
  From [dbo].[Sales Data]
  Where Year(OrderDate) = Year(GETDATE())
  Group by Datefromparts(Year(OrderDate), Month(OrderDate), 1)
  Order by Sales_Month;
  
- **Sales Percentage by Region**: Each region's contribution to total sales.
  ```SQL
  With Region_Sales as (Select Region, Sum(Revenue) as Regional_Sales From [dbo].[Sales Data]
  Group by Region),Total_Sales as (Select Sum(Revenue) as Total_Sales From [dbo].[Sales Data])
  Select r.Region, (Cast(r.Regional_Sales as Decimal(10, 2)) / Cast(t.Total_Sales as Decimal(10, 2)) * 100) as Sales_Percentage 
  From Region_Sales r,Total_Sales t

- **Products with No Sales in Last Quarter**: Products without sales in the last quarter.
  ```SQL
  Select Distinct [Product] From [dbo].[Sales Data]
  Where [Product] Not in (
    Select [Product] From [dbo].[Sales Data]
    Where Datepart(Quarter, OrderDate) = Datepart(Quarter, DATEADD(Quarter, -1, Getdate())) And Year(OrderDate) = Year(Dateadd(Quarter, -1, Getdate()))
    Group by [Product])

## Power BI Dashboard (Visualizations)

The **Power BI** [Dashboard](https://github.com/user-attachments/files/17607372/Sales.Data.Visualization.pdf) Showcase the key insights below in an interactive, visual format:

- **Bar charts** showing

  - *Product Sales*
  - *Regional Sales*
  - *Monthly Sales*
  - *Quantity Sold by Product*

- **Pie Chart and Doughnut Chart** showing Region and Product Contribution to sales respectively
  
- Lastly, Cards, Slicer, and tables showing different parameters

## Results

Below are the analysis result summary:

1. Products:
  - Shoes and Shirts are the top revenue-generating products, with Shoes leading at $613,380, followed by Shirts at $485,600.
  - Socks and Jackets generated the lowest revenue, indicating potential challenges in customer interest or pricing.
  - Shoe is the top revenue-generating product and the second-best seller by quantity sold

2. Regional Performance:
  - The South region is the highest contributor, accounting for 44.16% of total sales, while the West region lags behind at 14.29%.
  - Despite having the highest number of transactions, the East region shows lower total revenue, which may suggest smaller average order sizes.

3. Monthly Sales Trends:
  - Sales fluctuate significantly by month, with February 2024 showing peak sales at $298,800, possibly due to seasonal demand or promotions.
  - April 2023 recorded the lowest monthly revenue at $7,425, highlighting a need for targeted sales strategies during low-demand periods.

4. Products with No Sales in Q4 2023:
  - Hats, Shirts, and Shoes had no sales in the last quarter of 2023, suggesting a possible seasonal trend, stock issues, or reduced customer interest during this period.

## Recommendations

1. Focus on High-Selling Products:
  - Consider expanding the product lines for the top revenue-generating products (Shoes and Shirt) or introducing new variations and accessories to capture additional market share.
  - Socks and Jackets have lower revenue, suggesting a need for promotions or discounts to stimulate sales.
  - Shoes consistently perform well across regions, whereas lower-performing items (like Socks and Jackets) might benefit from bundling or targeted promotions in underperforming regions like the West.

2. Boost Sales in Low-Performing Regions:
  - The West region has the lowest sales share (14.29%). To drive growth, consider region-specific promotions, partnerships with local influencers, or a tailored marketing approach targeting 
    regional preferences.
  - Conduct market research in the West region to identify potential barriers to purchasing and adjust product offerings or messaging accordingly.

3. Optimize for Seasonal Trends:
  - February and January recorded high sales, possibly due to seasonal demand. Capitalize on these trends by introducing early-bird promotions or bundled offers in advance of peak months.
  - Monthly planning should include focused campaigns in January and February to maximize revenue potential during this period.

4. Leverage the South Region’s Sales Strength:
  - With the South region contributing 44% of total sales, maintain high engagement here by tailoring campaigns to customer preferences. Regional promotions and high-visibility advertising could 
    further boost sales.
  - Identify the factors driving high performance in the South and apply similar strategies to other regions where applicable.

## Project Instructions

1. Open the Excel Workbook:

Explore Sales_Analysis.xlsx in the Excel folder for pivot tables, metrics, and visualizations.

2. Run SQL Queries:

- Import the data into your SQL environment.

- Execute the queries from the SQL folder. 

- Export the results to Power BI if needed.

3. Power BI Dashboard:

- Create a dashboard that visualizes the insights found in Excel and SQL.

🙂

💻

