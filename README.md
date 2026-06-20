# global-sales-transaction-analytics
Advanced SQL analysis and database optimization scripts for the Kaggle Sample Sales ledger.
# Global Sales Transaction Ledger Analytics

## 📌 Project Overview
This repository showcases an analytics pipeline built for a denormalized flat-file database containing enterprise global sales metrics. The technical focus center stages extensive data cleaning, complex variable calculations, account concentration modeling, and dynamic casting.

## 🛠️ Technical Stack & Frameworks
- **Database Engine:** MySQL Server 9.7
- **Interface:** MySQL Workbench
- **Advanced Core Concepts:** Text-to-Date Dynamic Parsing (`STR_TO_DATE`), Aggregations (`SUM`, `AVG`, `COUNT`), Financial Outlier Filtering, and Corporate CRM Indexing.

## 🚀 Key Milestones & Business Use Cases

### 1. Text-to-Date Dynamic Casting
* **Problem:** The `ORDERDATE` field was imported as an amorphous text string (`VARCHAR`), preventing chronological sequencing and time-series extraction.
* **Resolution:** Implemented dynamic string parsing parameters:
STR_TO_DATE(ORDERDATE, '%m/%d/%Y %H:%i')
This cleanly isolated continuous variables like YEAR() and MONTH() to correctly plot Year-over-Year revenue momentum and retail seasonality patterns without converting the underlying table architecture.

2. Enterprise Account Concentration Modeling
Aggregating sales values by unique corporate identifiers, structural locations, and country bounds highlighted the company's dependency on enterprise revenue lines:

High-Value Thresholds: Isolated orders exceeding $5,000 to spot logistics workflows.

Product Dominance: Categorized segments exceeding $500,000 to optimize supply chain inventory capital.

Client Concentration: Profiled the top 5 global corporate buyers based on cumulative spending to drive customized enterprise account management plans.

3. CRM Performance Indexing
Provisioned a performance B-Tree index (idx_sales_customer) on the CUSTOMERNAME column. Query tracing via EXPLAIN verified that automated CRM interface checks avoided full table sweeps, shifting from a full table scan to an index range retrieval.
