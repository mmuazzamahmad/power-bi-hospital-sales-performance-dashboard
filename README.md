# Hospital Sales Performance Dashboard - Power BI Project

This repository contains a Power BI project focused on analyzing pharmaceutical sales data from a network of hospitals. The goal was to create a dynamic, single-page dashboard to provide key business insights at a glance and allow for deep-dive analysis through interactive filters.

## Dashboard Preview

![Dashboard Screenshot](https://raw.githubusercontent.com/mmuazzamahmad/power-bi-hospital-sales-performance-dashboard/main/Power%20BI%20-%20Hospital%20Sales%20Performance%20Dashboard%20-%20Muhammad%20Muazzam%20Ahmad.png)

## Project Description

This project was designed to serve as a central "source of truth" for sales and marketing teams. By connecting transactional sales data with detailed hospital information, the dashboard answers critical business questions about performance, trends, and market segmentation. It transforms raw data into actionable insights, helping stakeholders understand what products are selling, where they are selling, and to which types of facilities.

## Key Business Questions Answered

The dashboard was designed to answer the following questions:

1.  What are the total sales revenue and total quantity of drugs sold for any given period?
2.  How many hospitals are we actively selling to and what is our total transaction volume?
3.  How are sales trending over time? Are there seasonal patterns?
4.  Which drug categories and specific drugs are the top revenue drivers?
5.  What is the geographical distribution of our sales? Which cities are the most profitable?
6.  Which type of hospital (e.g., General, Government, Private) contributes the most to sales?
7.  Who are our top 10 hospital clients by sales revenue?

## Technical Stack

*   **Data Analysis & Visualization:** Microsoft Power BI Desktop
*   **Data Transformation & Modeling:** Power Query (M Language)
*   **Calculations & KPIs:** Data Analysis Expressions (DAX)

## Data Model

The data model consists of two tables linked by a one-to-many relationship, forming a simple star schema.

#### 1. Hospitals Data (Dimension Table)
A lookup table containing details for each hospital.
*   `Hospital ID` (Primary Key)
*   `Hospital Name`
*   `Location` (City)
*   `Type`
*   `Bed Capacity`

#### 2. Sales Data (Fact Table)
A transactional table containing records of each sale.
*   `Transaction ID`
*   `Date`
*   `Hospital ID` (Foreign Key)
*   `Drug Name`
*   `Category`
*   `Quantity Sold`
*   `Unit Price`
*   `Total Sales` (Calculated Column: `[Quantity Sold] * [Unit Price]`)

**Relationship:** `Hospitals[Hospital ID]` is connected to `Sales[Hospital ID]` in a **one-to-many** relationship (one hospital can have many sales transactions).

## Dashboard Components Breakdown

The dashboard is a single page composed of the following elements:

#### **1. Slicers (Filters)**
*   **Date Range Slicer:** Allows users to select a specific time frame for analysis.
*   **Hospital Type Dropdown:** Filters the entire report for specific hospital types (e.g., General, Specialty).
*   **City Dropdown:** Filters the entire report for one or more cities.
*   **Drug Category Dropdown:** Filters the report for specific drug categories.

#### **2. KPI Cards**
Four cards provide an immediate, high-level summary of the business, based on the following DAX measures:
*   **Total Sales ($):** `SUM(Sales[Total Sales])`
*   **Total Drug Quantity Sold:** `SUM(Sales[Quantity Sold])`
*   **Total Number of Hospitals:** `DISTINCTCOUNT(Hospitals[Hospital ID])`
*   **Total Number of Transactions:** `COUNT(Sales[Transaction ID])`

#### **3. Visualizations**
*   **Donut Chart – Total Sales by Drug Category:** Shows the proportion of sales contributed by each drug category.
*   **Line Chart – Total Sales trend over Time:** Plots total sales against a continuous date axis to spot trends and seasonality.
*   **Bar Chart – Total Sales by Drug:** A vertical bar chart that ranks individual drugs by their total sales.
*   **Map – Total Sales by City and Hospital Type:** A bubble map where bubble size represents total sales in a city.
*   **Table – Top Hospitals by Sales:** A sortable table showing the top hospitals ranked by total sales, along with their location and type.
