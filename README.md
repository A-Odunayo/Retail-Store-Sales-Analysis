# Retail Sales Analysis

## Project Overview
This project involves a detailed analysis of sales data from a retail store. The goal is to identify top-selling products, assess regional performance, and uncover monthly sales trends. The findings are presented through an interactive Power BI dashboard with key visuals.

## Table of Content

- [Data Source](#Data-Source)

- [Project Structure](#Project-Structure)

- [Data Extraction, Transformation, and Loading](#Data-Extraction-Transformation-and-Loading)

- [Data Analysis](#Data-Analysis)

- [Data Visualization](#Data-Visualization)

- [Instructions](#Instructions)

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

### Folder Structure
Retail_Sales_Analysis
├── Excel
│   └── Sales_Analysis.xlsx               # Pivot tables, formulas, and exploratory analysis
├── SQL
│   ├── total_sales_by_category.sql       # Query for total sales by product category
│   ├── transactions_by_region.sql        # Query for count of sales transactions by region
│   ├── highest_selling_product.sql       # Query for highest-selling product by total sales value
│   ├── total_revenue_per_product.sql     # Query for total revenue per product
│   ├── monthly_sales_totals.sql          # Query for monthly sales totals for the current year
│   ├── top_5_customers.sql               # Query for top 5 customers by purchase amount
│   ├── sales_percentage_by_region.sql    # Query to calculate percentage of total sales by region
│   └── products_no_sales_last_quarter.sql # Query to identify products with no sales in the last quarter
├── PowerBI
│   └── Sales_Dashboard.pbix              # Power BI dashboard file for visual insights
└── README.md                             # Project overview and instructions


## Data Cleaning and Preparation

Before analysis, the data underwent the cleaning and preparation steps below:

1. **Data Type Conversion**: Ensured that fields were in the correct format (e.g., converting date fields to Date format, numerical fields to Numeric format).
2. **Removing Duplicates**: Checked for and removed any duplicate records in the dataset to ensure accuracy.
3. **Data Transformation**: Created new calculated fields, such as Revenue, to facilitate analysis.

## Data Exploration

The exploratory data analysis (EDA) phase included:

1. **Descriptive Statistics**: Generated summary statistics for numerical variables to understand distributions.
2. **Data Visualizations**: Created initial visualizations to identify patterns and trends in the data.
3. **Correlations**: Examined correlations between different variables like sales vs. region, sales vs. product category etc to identify relationships.
4. **Segment Analysis**: Analyzed data segments (e.g., by region, product category) to uncover insights and inform business decisions.

## Analysis Details

### 1. Excel

The **Excel** workbook includes:
- **Pivot Tables**: Summarize total sales by product, region, and month.

   | Product Sales | Regional Sales | Monthly Sales Trend |
   |---------------|----------------|---------------------|
   |![Sales by Product](https://github.com/user-attachments/assets/8ff91a9d-5969-4d01-b38e-6ac47ba76305)|![Sales by Region](https://github.com/user-attachments/assets/46829599-5bf3-4590-9748-9e6cb1938972)|![Sales per Month](https://github.com/user-attachments/assets/ba125d99-bfde-4fe5-a3eb-401ae0232645)

- **Calculated Metrics**:

   | Average Sales Per Product | Top Products |
   |---------------------------|-------------------|
   |![Average Sales by Product](https://github.com/user-attachments/assets/3f2e8ca2-5579-4845-ad3c-cf8af40f5e3a)|![Top Products by Quantity Sold](https://github.com/user-attachments/assets/5ea1dcdf-2f81-493f-b26f-a49f76eaf0d7)|

### 2. SQL Queries

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
- **Monthly Sales Totals**: Monthly sales for the current year.
  ```SQL
  Select Datefromparts(Year(OrderDate), Month(OrderDate), 1) as Sales_Month, Sum(Revenue) as Monthly_Total  
  From [dbo].[Sales Data]
  Where Year(OrderDate) = Year(GETDATE())
  Group by Datefromparts(Year(OrderDate), Month(OrderDate), 1)
  Order by Sales_Month;
- **Top 5 Customers by Purchase Amount**:
  ```SQL
  Select Top 5 CustomerId, Sum(Revenue) as Total_Purchase From [dbo].[Sales Data]
  Group by CustomerId
  Order by Total_Purchase Desc
- **Sales Percentage by Region**: Each region's contribution to total sales.
  ```SQL
- **Products with No Sales in Last Quarter**: Products without sales in the last quarter.
  ```SQL

### 3. Power BI Dashboard

The **Power BI** dashboard showcases key insights in an interactive, visual format:
- **Sales Overview**: Includes total sales and key performance metrics.
  ![Sales Overview](./screenshots/powerbi_sales_overview.png)
- **Top-Performing Products**: Highest-selling products by total sales.
  ![Top-Performing Products](./screenshots/powerbi_top_products.png)
- **Regional Breakdown**: Sales distribution by region.
  ![Regional Breakdown](./screenshots/powerbi_regional_breakdown.png)
- **Monthly Trends**: Visualization of sales trends over months.
  ![Monthly Trends](./screenshots/powerbi_monthly_trends.png)

## Visualizations

### Power BI Dashboard
- **Pivot Table Visualizations**:
  - **Product Sales by Category**: A bar chart showing sales by product category.
  - **Regional Sales**: Heat map to display sales differences across regions.
  - **Monthly Sales Trends**: Line graph for monthly sales patterns.

- **Calculated Metrics**:
  - **Conditional Formatting**: Highlights high-performing regions and products.
  - **Top Products**: Bar chart for easy comparison.

### SQL (for Power BI)
- Export SQL query results into Power BI for advanced visualizations:
  - **Total Sales by Product Category**: Pie chart for visualizing category proportions.
  - **Sales Transactions by Region**: Map visual to display sales density by region.
  - **Monthly Sales Totals**: Line or column chart for monthly sales tracking.
  - **Top 5 Customers**: Horizontal bar chart to represent top customers visually.


- **Overview Cards**: KPI cards to show key metrics such as total sales, average sales, and revenue by region.
- **Top-Performing Products**: Horizontal bar chart to rank products by sales.
- **Regional Sales**: Map or stacked bar chart for regional performance insights.
- **Monthly Sales Trends**: Line chart to show trends across months interactively.

## Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Retail_Sales_Analysis.git

2. Open the Excel Workbook:

Explore Sales_Analysis.xlsx in the Excel folder for pivot tables, metrics, and visualizations.

3. Run SQL Queries:

- Import the data into your SQL environment.

- Execute the queries from the SQL folder. 

- Export the results to Power BI if needed.

4. Power BI Dashboard:

Open Sales_Dashboard.pbix in Power BI to interact with and customize the dashboard visuals.

