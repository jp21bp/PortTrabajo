---
date : '2026-08-23T11:59:58-05:00'
draft : false
title : 'Project 1'
featured_image : 'proj1/TuristasMensuales.png'
summary: 'asfsaf'
---
# Table of Contents
1. [Project Background](#project-background)
    * [Insights, Reccomendations and focus areas](#insights-recommendations-and-focus-areas)
2. [Data Structure](#data-structure)
3. [Executive Summary](#executive-summary)
    * [Overview of Discoveries](#overview-of-discoveries)
    * [Discovery Trends](#discovery-trends)
4. [Insights Details](#insight-details)
    * [ARPU peaks in March, June, September, and December](#arpu-peaks-in-march-june-september-and-december)
    * [Category 'Meat' Contributes 27.13% of Monthly Revenue](#category-meat-contributes-2713-of-monthly-revenue)
    * [Average of 53.12% of Annual Stock is Thrown out](#average-of-5312-of-annual-stock-is-thrown-out)
5. [Recommendations](#recommendations)
    * [1. Advertising Combination: 'Meat' and 'Cookies and Snacks'](#1-advertising-combination-meat-and-cookies-and-snacks)
    * [2. Reduce all Product Stocks by 15%](#2-reduce-all-product-stocks-by-15)
    * [3. Offer discounts in February and November](#3-offer-discounts-in-february-and-november)
6. KPIs
    * [1. ARPU = Average Revenue Per User](#1-arpu--average-revenue-per-user)
    * [2. Percentage of Products Wasted](#2-percentage-of-products-wasted)
    * [3. Percent of Monthly Revenue per Category](#3-percent-of-monthly-revenue-per-category)
7. [Assumptions](#assumptions)

## Project Background
Bodega Ña Maria is a small business in rural Paraguay, and it supports a family household through its sales and revenue. The owner has noticed that the revenue oscillates on a monthly basis, but she wants the details about when the changes occur and the **difference between the high and low months**. She also mentioned a lot of her product goes to waste, but she doesn't know how much to reduce her products stored without going through a stockout.

Paraguay is a country with a strong livestock sector, contributing to its high consumption of meat products. Maria recognizes that her **meat products bring the most monthly revenue**, and she wants to know how the other product categories compare. 

The following analysis reveals the months with low revenues and how to create specific advertisements during these months in order to generate more revenue. Additionally, the products with the most waste are highlighted, along with strategies on how to convert them into revenue instead of simply throwing them away.  

<br><br><br>

### Insights, Recommendations, and Focus Areas
**ARPU and its seasonality**: The ARPU metric shows a predictable oscillation pattern throughout the year. Every 3 months there is a high ARPU, followed by 2 months of low ARPU. The average ARPU during the high months is 41,940 Gs. (Paraguayan currency), while the average during the low months is 39,384 Gs. This trend is used to recommend specific advertisements during the months with low ARPU. 

**Categories with high and low contribution to Monthly Revenue**: There are 8 product categories, and each available product is found in exactly one of these categories. 'Meat' and 'Dairy' have the highest impact, with a contribution of 27.13% and 15.61% of monthly revenue, respectively. On the other hand, 'Canned', 'Fruits and Vegetables', and 'Cookies and Snacks' have the lowest impact. These insights are used to combine advertisements without incurring additional costs. 

**Category with most products thrown out**: 53.12% of stored products are disposed of annually. The 'Cookies and Snacks' category has the most waste, with 68.22% of yearly stock lost. On the other hand, the 'Canned' category has the fewest products lost. This fact is considered when creating offerings in order to decrease the amount of products thrown out without sales. 

<br><br>
Pre-SQL data cleaning is found [HERE](https://github.com/jp21bp/MariaPY_EN/blob/main/cleaning_preSQL.py)

SQL queries are found [HERE](https://github.com/jp21bp/MariaPY_EN/blob/main/SQL.txt)

Data analysis and insights is found [HERE](https://github.com/jp21bp/MariaPY_EN/blob/main/insights.ipynb)

<br>

## Data Structure
Four database tables were used to perform this analysis; their CSV versions can be found [HERE](https://github.com/jp21bp/MariaPY_EN/tree/main/Data/Original). The table components are:

1. Table: categorias (categories) - fields: id_categoria (primary key), categoria (text), descripcion (text)
2. Table: clientes (clients) - fields: id_cliente (primary key), apellido (text), email (text), fecha_registrp (text)
3. Table: productos (products) - fields: id_producto (primary key), nombre (text), categoria (text), precio (smallint), stock (smallint)
4. Table: ventas (sales) - fields: id_venta (primary key), fecha (text), id_cliente (foreign key), id_producto (foreign key), cantidad (smallint)

Details:
* January is incomplete, so it is discarded.
* The last week of December is the first week of the following year, so it is discarded. 

<br><br><br>

## Executive Summary
### Overview of Discoveries
This Paraguayan small business is a representation of common family bodegas found in the rural aspects of the country. Due to limited electricity access, many of the products are thrown out throughout the year, creating a reality where those products don't produce any revenue. Additionally, Paraguayan culture influences client sales, where Holy Week and end-of-year festivities contribute to an increase in the corresponding ARPU. These patterns can be analyzed to create actionable recommendations that improve the small business's KPIs.
<br><br>

### Discovery Trends
**Months with fewer sales per client**: The three months of April, August, and October have an ARPU much lower than the average, accompanied by an average number of clients. This pattern implies that in these months clients buy fewer products.

**A good portion of products go to waste**: 53.12% of stored products are lost annually. It's discovered that the category 'Cookies and Snacks' and the month of December have the most products thrown out during the year. 

**'Meat' and 'Dairy' categories contribute the most to monthly revenue**: These categories obtain the most revenue from their sales, producing an average of 27.13% and 15.61% of the monthly revenue, respectively. On the other hand, 'Canned', 'Fruits and Vegetables', and 'Cookies and Snacks' had the least contributions to the monthly revenue.


## Insight Details
### ARPU peaks in March, June, September, and December
ARPU measures the average revenue per client, and the following are its emerging monthly patterns:

* **Peaks: ARPU and Revenue**: A monthly ARPU above average generally corresponds to a monthly revenue above average. The only exception is in February, where there is an anomalous lower amount of clients shopping.

* **June has an increase in the amount of clients**: This fact signals that there is an increase in transactions and sales during the month. It's further verified through the increase in ARPU, leading to the max monthly revenue throughout the year.

* **ARPU peaks in March, September, and December**: These three months also have an ARPU above average, but their corresponding number of clients stays about average. Although the higher ARPU implies that each client buys more than average, the average number of clients will lead to a monthly revenue slightly above average (but not near the peak seen in June). 

![ARPUs per month](./Images/arpu.png)

<br><br>


### Category 'Meat' Contributes 27.13% of Monthly Revenue
Of the existing eight product categories, there is a stark difference in each category's contribution to sales. 

* **27.13% of Monthly Revenue comes from 'Meats'**: Meat products consistently provide more than a quarter of the total monthly revenue. This is no surprise, considering Paraguay's livestock sector and heavy meat consumption. 

* **'Canned' vs 'Frozen'**:'Canned' and 'Frozen' products provide the least revenue contributions, with 'Frozen' products being slightly above 'Canned' goods. This fact signals that people prefer fresh, visible products over canned or frozen goods. 

* **'Dairy' is the second most contributing category**: Considering the strong livestock sector, it comes as no surprise that 'Dairy' is the second most contributing category to the monthly revenue. The majority of livestock are cows, which provide the milk basis for these dairy products.

![Categories and Monthly Revenue](./Images/category_revenue.png)

<br><br>

### Average of 53.12% of Annual Stock is Thrown out

Recognizing the electrical limitations in Paraguayan towns, it was expected that most products would be wasted due to a lack of refrigeration. The percentage of products lost revealed alarming figures.

* **53.12% Monthly Losses**: An average of 53.12% of stored products are lost annually because they are not sold.

* **February Has the Highest Losses**: In February, 58.1% of stored products were lost because they were not sold.

* **'Cookies and Snacks' Have the Highest Losses**: This category loses 68.22% of its products throughout the year. This figure worsens in February and December, with losses of 80.06% and 83.89%, respectively.

![Average products lost](./Images/waste.png)

<br><br><br>

## Recommendations

### 1. Advertising Combination: 'Meat' and 'Cookies and Snacks'
'Meat' was the category with the highest monthly revenue (27.13% of revenue) and the third most popular (with only 47.9% annual losses). In contrast, 'Cookies and Snacks' is the category with the highest annual losses (68.22% of its inventory). Given that 'Cookies and Snacks' suffered losses of more than 70% in February, June, November, and December, this advertisement can be activated during those months to reduce product losses and increase sales of 'Meat'.
<br><br>

### 2. Reduce all Product Stocks by 15%
Given that none of the products reached the stockout point in any of the months, it can be inferred that all products can reduce their losses by decreasing their inventory. Additionally, the lowest loss rate was 19.27%, with the 'Frozen' category in November. Therefore, a 15% reduction would not result in stockouts in any of the categories. All other loss rates do not fall below 24.31% across all categories and all months.

<br><br>

### 3. Offer discounts in February and November
During these months, the business attracted fewer customers than the monthly average, meaning that customers make fewer purchases during this time. Although the reason behind this decline is unknown, the small business could launch an initiative to attract more customers during these months. One way to encourage customer engagement is by offering general discounts on its products, which would attract more customers so they don’t miss out on this opportunity.
<br><br><br>

## KPIs

### 1. ARPU = Average Revenue Per User
Total Revenue / Number of Clients

Objective: Increase the average monthly ARPU from 40,314 Gs. to 45,000 Gs. 
<br><br>

### 2. Percentage of Products Wasted
((Available Stock - Products Sold)/Available Stock) * 100

Objective: Reduce the the average yearly products thrown out from 53.12% to 45% of total annual stock.
<br><br>

### 3. Percent of Monthly Revenue per Category
(Revenue of a Category / Total Revenue) * 100

Focus: Increase the sales of the category that generates the most revenue, 'Meat', from 27.13% to 30%. This will be achieved through advertisements with other categories that have a high percentage of waste. 
<br><br><br>

## Assumptions
This project has the following assumptions:

* To maintain confidentiality, these datasets are a combination of online data (from Argentina) and personal client data (from Paraguay).
* To simplify analysis, the costs and returns of products were not considered.
* A product's stock value represents the yearly stock.
* Products not sold at the end of the month are thrown out. 

