# Amazon-Sales-Dashboard

## Table of Content
---
###  Project Overview
 **The Amazon Sales Dashboard** is a Power BI project created to analyze Amazon sales data. It offers a high-level overview of sales performance, customer preferences, product categories, and other key insights. The dashboard aims to support data-driven decision-making in product management, marketing strategies, and customer engagement.

<img width="602" alt="amazon sales page 1" src="https://github.com/user-attachments/assets/12c82150-68f9-4687-b33b-e5be9b304928" />

<img width="602" alt="amazon sales page 1" src="https://github.com/user-attachments/assets/13029a55-fb34-4682-86d8-91741943e90f" />


### Data<img width="602" alt="amazon sales page 1" src="https://github.com/user-attachments/assets/f545b43e-2ec5-42ee-8bb2-629a5b717a93" />
<img width="607" alt="amazon sales details" src="https://github.com/user-attachments/assets/16b45687-a96a-4fe6-89a6-5eabc0bbe485" />
![Uploading amazon sales details.PNG…]()
 Sources
1. Sales Transactions Dataset:
- Source: Amazon Sales Data available from kaggle.com
### Tools
- Power BI Desktop: Download from Microsoft Power BI.
- Excel or CSV Viewer: For initial data inspection and cleaning.
  
### Data Cleaning/Preparation
- Remove Duplicates
- Handle Missing Values
- Standardize Data Types
- Validate Data Integrity

### Data Modelling
- Define Data Model
- Create Tables and Relationships
- Create Calendar date
- Create Measures and Calculated Columns
  
### Dashboard Features
The Amazon Sales Dashboard consists of two main pages: **Overview Page and Details Page**. Each page provides a unique perspective and interactive features to analyze Amazon sales data effectively. Below are the key features of each page:

1. Overview Page
   
   The Overview Page provides a high-level view of essential Key Performance Indicators (KPIs) and visual insights to help users quickly understand the sales performance across various dimensions.
  - *KPI Section*: displays essential KPIs such as **Total Revenue**, **Total Transactions**, **Cost of Goods Sold(COGS)**, **Profit, Profit Margin and Average Ratings**
  - *Revenue Insights*:
      Revenue Contribution by Product Line  
  - *Sales Trends*:
       Monthly Revenue Trend
  - *Customer Preferences*:
       Transactions Across Payment Platforms 
  - *Regional Performance*:
       Revenue by City and Branch
2. The Details Page

- The **Details Page** offers a comprehensive view of sales data with tabular information and additional KPIs for deeper analysis.

### Navigating the Dashboard
- Filters and Slicers: Filters for Month, Region, Product line, and Customer Type
- Interactive Charts: Click on chart elements (e.g., product line to filter data across the dashboard.
  
### Data Analysis
 **Here's a breakdown of some of the DAX measures provided**
 ```
1.  1. Total Revenue Calculation
Revenue = SUMX('Amazon', ('Amazon'[Selling Price] * 'Amazon'[Quantity]) + 'Amazon'[Tax 5%])

2.  Reference to Previous Month's Revenue
Ref: Previous Revenue = 
VAR _PreviousMonthView =
    CALCULATE(
        MAX(Calender[Month]),
        PREVIOUSMONTH(Calender[Date])
    )

VAR _Previous_Revenue = [Previous Revenue]

RETURN
    IF(
        _PreviousMonthView <> BLANK(),
        _PreviousMonthView & " : " & FORMAT([Previous Revenue], "$#,##"),
        0
    )
3. Variance Calculation and Indicator
  VAR _Arrow =
    IF(_PctChange > 0, "▲+", "▼")

RETURN 
    IF(
        SELECTEDVALUE(Calender[Month]) = BLANK() || 
        SELECTEDVALUE(Calender[Month]) = "Jan",
        "Variance = 0.0",
        "Variance: " & _Arrow & FORMAT(_PctChange, "0.0%")
    )
```
### Key Questions and Insights
The dashboard answers the following business questions:

- What are the Total Qty, Total Sales, Total Revenue, Cost of Goods Sold,Profit and Profit Margin for different periods?
- How does the current period’s performance compare to previous periods?
- What are the most and least profitable products
- What payment platforms was utilized most?
- What are the trends in sales and profit over time?
- Which branches are most profitable in different cities?
- How do customer demographics (gender and customer type) affect buying trends?

 ### Key Findings and Insights
 **Revenue Trend**
   - Annual Revenue Decline: Revenue significantly decreased by 86.30% from January to December 2019, indicating a sharp downward trend over the year.
 - Monthly Revenue Drop: The revenue trend began to decline notably in May 2019, with a total decrease of 24.85% (equivalent to $3,331.79) over the following six months.
- Steepest Revenue Decline: The largest decline was observed between January 2019 and March 2019, with revenue dropping from $90,684.62 to $76,213.88.

**Transaction Insights**
- E-wallet Transactions: The E-wallet payment method accounted for 34.50% of the total number of transactions, showing strong usage of digital wallets among customers.

**Branch Performance**
 - **Revenue Contribution by Branch and Location**
   
   **Branch B (Naypyitaw)** contributed 14.91% of the total revenue, making it a notable revenue generator for its location.
   
    **Highest Average Revenue by Branch**: Branch B had the highest average revenue at $41,376.44, followed by Branch A with $39,768.59, and Branch C with $31,637.40. This ranking highlights Branch B’s relative performance advantage.

**Customer Demographics - Gender Analysis**
- Gender Distribution: The customer base is almost evenly split, with 49.99% male and 50.1% female customers.

- Balanced Customer Engagement: This near-equal distribution indicates balanced engagement across genders, which can help in planning marketing and customer engagement strategies that appeal to both male and female customers equally.

**Customer Type Revenue Analysis**
  1. **Revenue Decline Trends:**
 - **Member Customers:** Revenue for member customers declined significantly by **88.40% from January to December 2019**. This decline began in **May 2019**, with a slight **0.39% decrease ($24.26)** over 6 months. The sharpest drop for member customers occurred between **January and March**, where revenue decreased from **$45,345.99 to $38,109.53**.
   
- **Normal Customers:** For normal customers, revenue also trended downward by 84.20% over the same year. The decline started earlier, in **April 2019**, with a more substantial drop of **29.94% ($1,678.04)** over 7 months. The most considerable decline was between **January and March**, where revenue fell from **$45,338.63 to $38,104.35**.
     
2.**Preferred Transaction Methods by Customer Type**:

- **Member Customers:** The most common payment method for member customers was **Ewallet**, accounting for **36.87% of all transactions**. This suggests a preference for digital wallet payments among loyal customers.

- **Normal Customers:** For normal customers, **credit card transactions** were the top choice, making up **34.33% of transactions**. This indicates a slight difference in payment preferences between customer types.

##### This analysis reveals distinct purchasing behaviors and revenue contributions for member and normal customers, highlighting areas for targeted strategies to address each customer segment's specific needs and preferences.

### Summary
The Amazon Sales Dashboard offers an interactive and user-friendly experience by combining high-level insights on the **Overview Page** with detailed data exploration options on the **Details Page**. These features enable users to monitor key sales metrics, identify trends, and make data-driven decisions.
