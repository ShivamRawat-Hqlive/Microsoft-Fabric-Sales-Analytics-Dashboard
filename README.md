# Microsoft Fabric Sales Analytics

An end-to-end **Sales Analytics and Data Engineering project** built using **Microsoft Fabric and Power BI**. The project demonstrates how raw sales data can be ingested, transformed, modeled, and visualized using a modern **Medallion Architecture (Bronze → Silver → Gold)**.

---

Project Overview

This project processes sales data through Microsoft Fabric and creates
an interactive Power BI dashboard to analyze:

Total Revenue

Total Orders

Total Quantity Sold

Revenue by Region

Orders by Region

Revenue by Product Category

Quantity Sold by Product Category

Monthly Revenue & Orders Trend

Top 10 Customers by Revenue

Average Revenue per Order

Average Quantity per Order

End-to-End Flow

Raw CSV Data → Bronze → Silver → Gold → Warehouse → Power BI

Architecture

Raw CSV Sales Data
        |
        v
Microsoft Fabric Pipeline
        |
        v
Bronze Lakehouse
        |
        v
Silver Layer
(Data Cleaning & Transformation)
        |
        v
Gold Layer
(Business-Ready Data)
        |
        v
Fabric Warehouse
        |
        v
Power BI Semantic Model
        |
        v
Interactive Sales Dashboard

Technologies Used

Microsoft Fabric

OneLake

Data Pipelines

Lakehouse

Fabric Warehouse

Notebooks

SQL

Power BI

DAX

Medallion Architecture

Star Schema

Data Pipeline

The Fabric pipeline orchestrates the complete data processing workflow:

CopyRawSalesCSV
        ↓
Copydatatodelta
        ↓
TransformBronzeToSilver
        ↓
BuildGoldLayer
        ↓
TransformSilverToWarehouse
        ↓
nb_build_tables

Pipeline Components

Step   Component   Purpose

1      Copy Data   Ingest raw sales CSV data
2      Notebook    Process data into Delta format
3      Notebook    Clean and transform Bronze data
4      Notebook    Build the Gold analytical layer
5      Copy Data   Load transformed data into the Warehouse
6      Notebook    Build final analytical tables

Medallion Architecture

Bronze Layer

The Bronze layer stores the ingested sales data with minimal
transformation.

Main table:

bronze_sales

Main columns:

OrderID
OrderDate
CustomerName
Region
ProductCategory
Revenue
Quantity
Status

The Bronze layer provides a raw and traceable representation of the
source data.

Silver Layer

The Silver layer contains cleaned and transformed data.

Typical transformations include:

Data type conversion

Date standardization

Handling missing values

Removing invalid records

Standardizing categorical values

Data cleansing

Preparing data for analytical modeling

Gold Layer

The Gold layer contains business-ready data using a
dimensional/star-schema approach.

Fact table:

fact_sales

Dimension tables:

dim_customer
dim_date
dim_product
dim_region

The star schema separates measurable business events from descriptive
attributes and provides a clean structure for Power BI analysis.

Fabric Warehouse

The transformed analytical data is loaded into the Fabric Warehouse.

wh_sales
└── analytics
    ├── dim_customer
    ├── dim_date
    ├── dim_product
    ├── dim_region
    └── fact_sales

Power BI Dashboard

The final Power BI report provides a Sales Analytics Overview with
interactive filtering and business-focused KPIs.

KPI Cards

The dashboard includes:

Total Revenue

Total Revenue (USD)

Total Orders

Total Quantity Sold

Average Revenue per Order

Average Quantity per Order

Visualizations

Monthly Revenue & Orders Trend

Shows monthly revenue and order volume to identify sales trends
throughout the year.

Revenue by Region

Compares revenue performance across:

West

North

East

South

Orders by Region

Compares order volume across different regions.

Revenue by Product Category

Shows revenue contribution from:

Electronics

Furniture

Office Supplies

Quantity Sold by Product Category

Shows the quantity distribution across product categories.

Top 10 Customers by Revenue

Ranks customers based on revenue and displays:

Customer Rank

Customer Name

Total Revenue

Total Orders

Interactive Filters

The dashboard includes filters for:

Date

Month

Quarter

Year

These filters allow users to dynamically analyze sales performance
across different time periods.

DAX Measures

The Power BI semantic model contains business measures such as:

Total Orders
Total Quantity
Total Revenue
Total Revenue USD
Avg Order Value
Avg Quantity Per Order
Customer Rank

Example DAX

Total Orders =
DISTINCTCOUNT(fact_sales[order_id])

Total Quantity =
SUM(fact_sales[quantity])

Total Revenue =
SUM(fact_sales[revenue])

Key Business Questions

This dashboard helps answer:

What is the total revenue generated?

Which region generates the highest revenue?

Which region has the highest number of orders?

Which product category generates the most revenue?

How does revenue change month over month?

Which customers generate the most revenue?

What is the average revenue per order?

Which product category sells the highest quantity?

How does sales performance change by quarter or year?

Project Structure

microsoft-fabric-sales-analytics/
│
├── README.md
│
├── pipeline/
│   └── pl_ingest_sales
│
├── notebooks/
│   ├── Copydatatodelta
│   ├── TransformBronzeToSilver
│   ├── BuildGoldLayer
│   └── nb_build_tables
│
├── lakehouse/
│   ├── bronze_sales
│   ├── silver_sales
│   ├── dim_customer
│   ├── dim_product
│   ├── dim_region
│   └── fact_sales
│
├── warehouse/
│   └── wh_sales
│
├── powerbi/
│   └── sales_report_main
│
└── screenshots/
    └── dashboard.png

End-to-End Workflow

1. Raw CSV Sales Data
          ↓
2. Microsoft Fabric Pipeline
          ↓
3. Bronze Lakehouse
          ↓
4. Data Cleaning & Transformation
          ↓
5. Silver Layer
          ↓
6. Business Transformations
          ↓
7. Gold Layer
          ↓
8. Fabric Warehouse
          ↓
9. Star Schema
          ↓
10. Power BI Semantic Model
          ↓
11. DAX Measures
          ↓
12. Interactive Dashboard

Skills Demonstrated

Data Engineering

ETL / ELT

Microsoft Fabric

Data Pipelines

Lakehouse Architecture

Medallion Architecture

Delta Tables

Data Cleaning

Data Transformation

Data Warehousing

Star Schema Modeling

SQL

DAX

Power BI

Business Intelligence

Dashboard Development

KPI Analysis

Data Visualization

Project Objective

The objective of this project is to demonstrate an end-to-end modern
analytics solution using Microsoft Fabric, from raw data ingestion to a
business-ready Power BI dashboard.

It combines data engineering, data warehousing, dimensional modeling,
business intelligence, and data visualization into one complete
workflow.

Conclusion

This project demonstrates how Microsoft Fabric can be used to build a
modern data analytics solution by combining pipelines, Lakehouse,
notebooks, Warehouse, dimensional modeling, and Power BI.

The final dashboard transforms processed sales data into
business-focused insights that can support analysis of revenue, orders,
products, regions, customers, and sales trends.
