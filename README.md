# Toy-Store-PowerBI-Analysis

## Problem Statement

A toy store chain with 50 stores across 29 cities in Mexico, needed a dynamic and interactive reporting solution to monitor key business metrics and identify sales trends. The company lacked a centralised dashboard to analyse revenue, profit, and order volume across multiple locations and product categories.

This project aimed to develop a Power BI dashboard that enables leadership to:
- Track total orders, revenue, and profit over time
- Compare sales performance across different store locations
- Identify best-selling product categories
- Filter and explore data interactively

By implementing a star schema data model, defining key DAX calculations, and visualizing insights through intuitive charts and KPIs, this report empowers data-driven decision-making for business growth.


## Steps followed 

### 1️⃣ Data Connection & Profiling  
- Connected to four CSV files: **Sales, Products, Stores, and Calendar.**
- Uisng **column distribution, column quality & column profile** options, reviewed table structures, checked for **missing values**, and ensured correct **data types**.
- By default, profile will be opened only for 1000 rows so   column profiling based on entire dataset is selected
- Identified **primary** and **foreign keys** for relational modeling.
- Profiled key dataset insights:
    - Total Transactions: 829,262
    - Stores: 50 across 29 cities
    - Lowest Priced Product: Play-Doh Can ($2.99)
    - Highest Priced Product: LEGO Set ($39.99)
- Added **calculated columns**  in the Calendar table for ‘Start of Month’ and ‘Start of Week’.

### 2️⃣ Data Modeling  

- Built a star schema with the Sales table as the fact table and Products, Stores, and Calendar as dimension tables.
- Established 1-to-Many relationships between tables.
- Created a date hierarchy for time-series analysis (Date → Start of Week → Start of Month).
- Hid foreign keys from the report view for clarity.

### 3️⃣ Data Transformation & DAX Calculations

- Created calculated columns in the Sales table:
    - The `RELATED()` function was used to pull cost and price from the Products table.

         - Revenue: `sales[Units] * sales[Price]`
        - Profit: `sales[Revenue] - (sales[Cost] * sales[Units])`
- Defined key measures using DAX:
    - `Total Orders = DISTINCTCOUNT(sales[Sale_ID])`
    - `Total Revenue: SUM(sales[Revenue])`
    - `Total Profit: SUM(sales[Profit])`

- Formatted values with commas for readability.

### 4️⃣ Data Visualization & Report Design  

- Created an interactive Power BI dashboard with:
    -  KPI Cards for Total Orders, Total Revenue, and Total Profit (with monthly trends).
    - Visual filters (Slicer) was added to report page to filter all charts by location named Aiport, Commercial, Downtown and Residential.
    - Bar Chart: Total Orders by Product Category.
    - Line Chart: Total Revenue over time using the Date    Hierarchy.
- Optimized layout, formatting, and alignment for a clean and intuitive report.

## Recommendations for Business Growth

- Capitalise on High-Performing Toy Sales
     - Since toys are the highest-selling category, increase inventory and variety to meet demand.
    - Introduce bundled deals or exclusive toy collections to boost average order value.
    - Implement seasonal promotions (e.g., holiday discounts) to further drive toy sales.

-  Improve Electronics Category Sales
    - Offer discounts, bundle deals, or special promotions to attract buyers.
    - Conduct customer feedback surveys to understand demand for electronic toys and accessories.

- Leverage High-Performing Downtown Locations 📍 
    - Since downtown stores generate the highest revenue, focus on:
        - Expanding inventory in these locations to meet demand.
        - Running localized promotions (e.g., "Weekend Toy Deals" for city shoppers).
        - Optimising store layout to improve in-store customer experience.

- Boost Sales in Low-Performing Airport Locations
    - Since airport stores have the lowest revenue, consider:
        - Stocking travel-friendly toys (small, compact, low-cost items).
       - Offering impulse-buy products near checkout (e.g., mini figurines, puzzle games).
        - Running airport-specific promotions (e.g., “Buy 1, Get 1 50% Off” for travelers).
     
## 📊 Power BI Report Preview  

![Power BI Dashboard Preview](https://github.com/folakeobalakun/Toy-Store-PowerBI-Analysis/blob/main/Toy%20store%20Project-1.png)  

📄 **Full Report:** ## 📂 Power BI Project File 📊 **Power BI (.pbix) file:**  
[🔗 Click here](https://github.com/folakeobalakun/Toy-Store-PowerBI-Analysis/blob/main/Toy%20store%20Project.pbix)
