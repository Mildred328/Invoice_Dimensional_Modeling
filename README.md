#  Invoice-Based Dimensional Modeling 

This repository contains a complete dimensional modeling project based on an invoice dataset. Designed for advanced retail analytics, the model supports efficient querying, detailed reporting, and historical tracking using best practices in data warehousing.

---

##  Project Overview

This project presents a comprehensive dimensional data model built from an invoice dataset, designed to support robust analytical reporting and business intelligence in a retail context, which includes:
- Star schema design
- ETL/ELT strategy
- Slowly Changing Dimensions (SCD) implementation
- Scalability and performance enhancements
- Alignment with key business intelligence objectives

---

##  Star Schema Components

###  Fact Table
- `Fact_Sales`
  - `Fact_ID` (Surrogate Key)
  - `Invoice_ID` (Degenerate Dimension)
  - `Customer_Key`, `Product_Key`, `Store_Key`, `Date_Key` (FKs)
  - `Quantity`, `Unit_Price`, `Line_Total`

###  Dimension Tables
- `Dim_Customer`: Customer_ID, Customer_Name
- `Dim_Product`: Product_ID, Product_Name, Category, Brand
- `Dim_Store`: Store_ID, Store_Name, Region, Manager
- `Dim_Date`: Full_Date, Day, Month, Quarter, Year, Weekday

---

##  ETL/ELT Strategy

###  Load Types
- Initial Full Load (Batch)
- Incremental Load (CDC or timestamp-based)

###  Data Quality Checks
- Null and data type validation
- Duplicate record detection
- Referential integrity enforcement
- Logging for ETL failures and audits

---

##  SCD (Slowly Changing Dimensions)

| Dimension     | SCD Type | Description                               |
|---------------|----------|-------------------------------------------|
| Customer      | Type 2   | Tracks changes in customer attributes     |
| Product       | Type 2   | Captures historical changes in details    |
| Store         | Type 2   | Stores versioned store management data    |
| Date          | Static   | No historical changes required            |

---

##  Hierarchies for Drill-Down Analysis

- Time: Hour → Day → Month → Quarter → Year
- Product: Product → Category → Brand
- Store: Store → Region

---

##  Performance Optimization

- Partitioning: Fact table by date
- Indexing: Foreign keys and date fields
- Materialized Views: For pre-aggregated summaries
- Surrogate Keys: Improve join efficiency
- Parallel Processing: Optimized ETL jobs

---

##  Business Objectives Fulfilled

| Objective             | Model Feature                          | Benefit                             |
|-----------------------|----------------------------------------|-------------------------------------|
| Analytical Reporting  | Star schema, facts & dimensions        | Easy reporting and flexible queries |
| Drill-down Capability | Hierarchies in time, product, store    | In-depth trend analysis             |
| Historical Tracking   | SCD Type 2                             | Auditability and history retention  |
| Scalability           | Indexing, partitioning, surrogate keys | Efficient querying on large data    |

---

##  Star Schema Diagram



---

