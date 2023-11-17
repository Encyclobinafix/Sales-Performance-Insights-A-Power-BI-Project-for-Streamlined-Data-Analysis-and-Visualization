# Sales Performance Insights: A Power BI-Project for Streamlined Data Analysis and Visualization

This report offers business users and stakeholders insights into the company's performance, focusing on sales, revenue, and profit. The metrics are further dissected by different managers, sales country, customers' age groups,  etc. 

Here is a link to my interactive Power BI dashboard: 👇

https://app.powerbi.com/groups/me/reports/27093a3f-0147-4cb4-81cb-da7f80b53189/ReportSection75fb6b750fcd4989e1ba?experience=power-bi&bookmarkGuid=Bookmark61231584d0887d5a16ba

![](DB_2.png)

## Introduction:

Welcome to the dynamic world of data insights! My Power BI project dives deep into the realms of sales and profits, offering a comprehensive analysis across diverse regions, countries, products, and age groups. Uncover the trends, discover correlations, and explore the narrative that unfolds within the visual representations. Let the visualizations guide you through a journey of understanding and decision-making, empowering you with actionable insights for strategic business growth and success.

_**Note**: The dataset utilized and the reports generated do not depict any specific company, institution, or country. It is a simulated dataset employed for the purpose of showcasing Power BI skills._

## Dynamic Data Analysis Expressions (DAX Measures):

1. FOR THE CALCULATED START OF WEEK COLUMN:
  
       Start of Week = 'Calendar'[Date] - WEEKDAY('Calendar'[Date],1)+ 1
   
2. FOR THE 14 DAY ROLLING PROFIT:
  
       14 Days rolling total profit = CALCULATE( SUMX(VALUES('Calendar'[Month Number]),
         [Total Profit]), DATESINPERIOD('Calendar'[Date], MAX('Calendar'[Date]), -14,DAY))

4. FOR THE 14 DAY TITLE:
  
        14 Day Trend Title 2 = VAR SelectedYear = SELECTEDVALUE('Calendar'[Year], "All Year") VAR SelectedCategory = SELECTEDVALUE('7 DSP_Products Table'[ProductCategories], "All categories") VAR SelectedCountry = SELECTEDVALUE('4 DSP - Regions'[Country], " All Countries") RETURN CONCATENATE(SelectedYear, " Weekly Revenue and 14-Days Profit for ") & CONCATENATE(SelectedCategory, " in ") & SelectedCountry

5. FOR MANAGERS SUMMARY:
  
       Managers Summary = SELECTEDVALUE('4  DSP - Regions'[TerritoryManager], "Manager") & "'s Summary"

6. FOR MONTH ON MONTH REVENUE:

            MoM Revenue Growth = 
        DIVIDE([Total Revenue 2]-[Previous Month Revenue],
        [Previous Month Revenue], "N/A"
        )

7. FOR YEAR ON YEAR REVENUE:

       YoY Revenue Growth =
       DIVIDE([Total Revenue 2]-[Previous Year Revenue],
       [Previous Year Revenue], "N/A"
       )

8. FOR TOP PRODUCT BY PROFITS:

        Top Product By Profit Title = "Top Product By Profit - " & FORMAT([Total Profit], "$0,0")

9. FOR MONTHLY REVENUE TITLE:

           Monthly Total Revenue Title = 
        CONCATENATE("Monthly Total Revenue - " , FORMAT([Total Revenue 2], "$0,00"))

10. FOR TOP PRODUCT BY ORDERS:

        Top Product by Orders = "Top Product by Orders - " & [Total Orders]


## Problem Statement 1:

As an expert Data Analyst, your company has tasked you to create the measures below that can used in a table to provide Senior Management a quick insight into the monthly and yearly number of products in stock in comparison to number of products sold. The Manangement is planning to revamp their products supply chain but needs to determine the impact on products inventory.

Measures Required
1. Quantity sold.
2. Quantity sold rolling total.
3. Total Quantity Sold Per Year
4. Percentage of Quantity Sold Yearly (e.g., 550/7937 = 6.93%)
5. 3-Months Rolling Average (e.g., for 2015 March, (550+518+596)/3 = 554.67)
6. Stock Quantity
7. Stock Quantity Rolling Total
8. Stock 3-Months Rolling Average (e.g., For 2014 October, (149+234+384)/3 = 255.67)

![](Table_2.png)
