# AdventureWorksCompany-PowerBI-Dashboard 

![](image.png)

## INTRODUCTION
This portfolio presents a Power BI project developed as part of my learning journey through the Maven Analytics online course titled "[Microsoft Power BI Desktop for Business Intelligence](https://www.udemy.com/course/microsoft-power-bi-up-running-with-power-bi-desktop/)." The project reflects hands-on exercises and guided challenges provided within the course framework, applied to a real-world business dataset Adventure Works Bike Shop (2020–2022).

The structure and flow of this project follow the curriculum designed by the Maven Analytics team, emphasizing practical, real-world applications of Power BI including data transformation, data modeling, DAX calculations, interactive reporting, AI-powered visuals, and performance optimization.

This repository serves both as a personal learning milestone and a reference point for others exploring Power BI for business intelligence and data analytics.

I started by connecting and shaping data using Power Query cleaning, transforming, and combining multiple data sources including sales transactions, customer lookup, product catalog, and calendar tables through applied steps, merges, and appends.

Next, I built a structured data model by defining table relationships, managing filter flow directions, and organizing a clean star schema to support accurate cross-table analysis.

From there, I created calculated fields using DAX writing measures and calculated columns for KPIs such as Total Revenue, Profit, Return Rate, Revenue per Customer, and dynamic period-over-period comparisons using CALCULATE, DIVIDE, DATEADD, HASONEVALUE, and SELECTEDVALUE.

I then visualized the data through interactive report pages including an Executive Summary, Customer Detail, and Product Detail dashboard featuring KPI cards, trend line charts, donut charts, gauge visuals, conditional formatting, drill-through, and dynamic tooltips styled with a consistent Slate & Sage theme.

I also explored Power BI's Artificial Intelligence features, including AI-powered visuals to surface automatic insights and anomaly detection within the trend data.

Last but not least, I applied Power BI Optimization Tools using Performance Analyzer to identify slow visuals and DAX queries, reducing model size through unused column removal, and structuring dedicated measure tables to keep the data model clean and maintainable.


## Table of Content
📁 1. [Problem Statement](#1-problem-statement)  

📁 2. [Skills Demonstrated](#2-skills-demonstrated)  

📁 3. [Data Sourcing](#3-data-sourcing)  

📁 4. [Data Transformation](#4-data-transformation)  

📁 5. [Data Modeling](#5-data-modeling)  

📁 6. [Data Visualization](#6-data-visualization)

📁 7. [Data Analysis](#7-data-analysis)  

📁 8. [Conclusions](#8-conclusions)  

📁 9. [Recommendations](#9-recommendations)  


## 1. Problem Statement
Adventure Works Bike Shop needed a centralized view of their business performance across sales, customers, and products. The goal was to build an interactive dashboard that enables data-driven decisions by tracking revenue, profit, orders, return rates, and customer behavior over a 2.5-year period (Jan 2020 – Jun 2022).
1. What is the total revenue, profit, and order volume for the business?
2. Which product categories and products drive the most orders and revenue?
3. How is monthly revenue and return rate trending over time?
4. How many unique customers does Adventure Works have and what is the average revenue per customer?
5. Which occupation and income segments place the most orders?
6. Who are the top revenue-generating customers and what are their profiles?
7. How is each product performing against its monthly orders, revenue, and profit targets?
8. Which products have the highest return rates and is it above or below the company average?
9. How is product profit trending over time and is it consistently hitting targets?

## 2. **Skills Demonstrated**
- **DAX** — custom measures for KPIs, dynamic labels, conditional logic, and time intelligence (DATEADD, DATESMTD)
- **Power Query** — data cleaning, column transformation, and table merging
- **Data Modeling** — star schema design with fact and dimension tables
- **Data Visualization** — KPI cards, gauge charts, line charts, donut charts, and matrix tables
- **Conditional Formatting** — dynamic colors based on performance vs target
- **UX Design** — consistent color theme, layout hierarchy, and slicer interactions

## 3. **Data Sourcing**
The dataset is based on the AdventureWorks sample database provided by Microsoft. It consists of 6 tables:

| Table | Description |
|---|---|
| Sales Data | Transaction-level fact table |
| Return Data | Return transaction-level fact table |
| Customer Lookup | Customer demographics and attributes |
| Product Lookup | Product names, categories, and pricing |
| Product Categories | Product category hierarchy |
| Product Subcategories | Product subcategory hierarchy |
| Territory Lookup | Sales region and continent |
| Calendar Lookup | Date dimension table |

## 4. **Data Transformation**  
Data was cleaned and transformed using Power Query (M Language):
- Removed duplicate and null rows from Sales Data
- Standardized date formats across all tables
- Created calculated column
- Merged Product Lookup with Product Categories to create a unified product dimension
- Filtered irrelevant columns to reduce model size and improve performance

## 5. **Data Modeling**
- **Fact Table**: Sales Data (transactions), Return Data (transaction)
- **Dimension Tables**: Customer, Product, Territory, Calendar, Category Product, and Subcategory Product
- All relationships are **single-direction** (one-to-many)
- A dedicated **measure table** (`Measures`) stores all DAX calculations separately from raw data tables
- No bi-directional relationships to maintain query performance

## 6. **Data Visualization**  
The dashboard consists of 3 report pages:
- Executive Summary
- Product Detail
- Customer Detail

## 7. **Data Analysis**  
Examines sales, customer, and product data to identify performance trends, behavioral patterns, and business risks across the 2020–2022 period.

## 8. **Conclusions**  
Summarizes key findings from the analysis, highlighting the most critical insights across revenue, customer segments, and product performance.

## 9. **Recommendations**  
Proposes actionable next steps based on the analysis findings to improve sales performance, customer retention, and product strategy.


_Source of Curriculum and Dataset: Maven Analytics_




--------------------------------------------------------------------------------------------------------------------------------------------------------------------
>[!TIP]
> - Interpreting nested subqueries can be overwhelming, so start from the inner subqueries and work your way out or use CTE instead.
> - Using subqueries within the JOIN clause is great for **speeding up queries**, since it allows you to join smaller tables.

- A **Common Table Expression (CTE)** creates a named, temporary output that can be referenced within another query.  
  CTE need to start with the "**WITH**" keyword, followed by **the alias** the "**AS**" keyword, and the query between **parentheses**  
  WHY USE CTE instead SUBQUERIES:
     - Readability: Complex queries with CTE's are much easier to read.
     - Reusability: CTE's can be referenced multiple times within a query
     - Recursiveness: CTE's can handle recursive queries  

- Unlike subqueries, CTE's can be referenced multiple times within a query which helps avoid repeating code.  
  You can use **multiple CTEs in a query** and even combine them with subqueries. You can using multiple CTEs by using **a single `WITH` keyword to create two CTEs and they are spearated by a "**COMMA (,)**".

> [!IMPORTANT]
> Despite all this, you shouldn't forget about subqueries:
> - Most modern RDBMS support CTE, but not all of them do.
> - For simple subqueries, sometimes a subquery is readable enough and works just fine.


### ASSIGNMENT: Subqueries and CTEs - [View SQL File](sql/sec5.subqueries_and_ctes.sql)

1. ASSIGNMENT: **Subqueries in the `SELECT` Clause**
- Our product team plans on evaluating our product prices later this week to see if any adjustments need to be made for nest year.  
  Can you give me a list of our products from most to least expensive, along with how much each product differs from the average unit price?
     | MySQL Query | Result |
     |----------|----------|
     | ![](/assets/sec5.assignment1_query.png) | ![](/assets/sec5.assignment1_output.png) |

2. ASSIGNMENT: **Subqueries in the `FROM` Clause**
- Our inventory management team would like to review the products produced by each factory.  
  Can you give me a list of our factories, along with the names of the products they produce and the number of products they produce?
     | MySQL Query | Result |
     |----------|----------|
     | ![](/assets/sec5.assignment2_query.png) | ![](/assets/sec5.assignment2_output.png) |

3. ASSIGNMENT: **Subqueries in the `WHERE` Clause**
- Our Wicked Choccy's factory has some extra badwidth and we'd like to see if there are any lower priced products that they can help produce going forward.  
  Can you help us identify products that have a unit price less than the unit price of all products from Wicked Choccy's? Please include which factory is currently producing them as well.
     | MySQL Query | Result |
     |----------|----------|
     | ![](/assets/sec5.assignment3_query.png) | ![](/assets/sec5.assignment3_output.png) |

4. ASSIGNMENT: **CTES**
- The sales director wants a list of our biggest orders. In addition to sending over a list of all the orders over $200, could you also tell him the number of orders over $200?
     | MySQL Query | Result |
     |----------|----------|
     | ![](/assets/sec5.assignment4_query.png) | ![](/assets/sec5.assignment4_output.png) |

5. ASSIGNMENT: **Multiple CTES**
- Our inventory management team would like to review the products produced by each factory.  
  Can you give me a list of our factories, along with the name of the products they produce and the number of products they produce?
     | MySQL Query | Result |
     |----------|----------|
     | ![](/assets/sec5.assignment5_query.png) | ![](/assets/sec5.assignment5_output.png) |
