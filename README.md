# Microsoft Fabric Sales Analytics

An end-to-end **Sales Analytics and Data Engineering project** built using **Microsoft Fabric and Power BI**. The project demonstrates how raw sales data can be ingested, transformed, modeled, and visualized using a modern **Medallion Architecture (Bronze → Silver → Gold)**.

---

## 📌 Project Overview

This project processes sales data through Microsoft Fabric and creates an interactive Power BI dashboard for analyzing:

- Total Revenue
- Revenue by Region
- Revenue by Product Category
- Total Orders
- Quantity Sold
- Monthly Revenue & Orders
- Orders by Region
- Top Customers by Revenue
- Average Revenue per Order
- Average Quantity per Order

The solution follows an end-to-end analytics workflow:

**Raw Data → Bronze → Silver → Gold → Warehouse → Power BI**

---

## 🏗️ Architecture

```text
                    ┌─────────────────┐
                    │    Raw CSV      │
                    │   Sales Data    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Copy Data      │
                    │   Pipeline      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Bronze Layer    │
                    │    Lakehouse    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Silver Layer    │
                    │ Transformations │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Gold Layer      │
                    │ Business Model  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Fabric          │
                    │   Warehouse     │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Power BI     │
                    │    Dashboard    │
                    └─────────────────┘
