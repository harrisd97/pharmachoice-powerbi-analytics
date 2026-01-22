# PharmaChoice Performance Analytics Dashboard

### **Project Overview**
This is an end-to-end Power BI solution designed to analyze store performance, improve data quality, and identify profitability opportunities for a pharmacy network. The solution moves beyond simple reporting to provide actionable insights for three distinct audiences: Executives, Operations Managers, and Clinical Directors.

### **Business Problem**
* **Profitability:** The company was losing margin by over-selling National Brands (low margin) vs. Private Label (high margin).
* **Data Hygiene:** Operational reports were inaccurate due to missing cost data in transaction records.
* **Industry Shift:** The business is transitioning from retail-focused to service-focused (clinical services), requiring new metrics to track growth.

---

### **The Solution**
I built a robust data model and three targeted dashboards to solve these problems.

#### **1. Strategy Dashboard (Executive View)**
* **Goal:** Identify lost revenue and drive Private Label conversion.
* **Key Insight:** Identified **$118K in Missed Profit Opportunity**.
* **Action:** Highlighted "Allergy Relief" as the top category for intervention and created a "Switch List" for store staff.

![Strategy Dashboard](Strategy_Dashboard.png)

#### **2. Operations & Quality Dashboard (Manager View)**
* **Goal:** Monitor store efficiency and fix data errors.
* **Key Insight:** Flagged **2.2% of transactions** with missing costs, calculating a Data Integrity Score of **97.78%**.
* **Action:** Used conditional formatting to spot underperforming stores (e.g., Ottawa at -1.68% growth).

![Ops Dashboard](Ops_Dashboard.png)

#### **3. Clinical Dashboard (Director View)**
* **Goal:** Track the shift from Retail to Healthcare.
* **Key Insight:** Clinical services now contribute **12.08%** of total revenue.
* **Action:** Validated that 'RxHealthMed' banner stores outperform standard locations in service delivery.

![Clinical Dashboard](Clinical_Dashboard.png)

---

### **Technical Implementation**

#### **Data Modeling (Backend)**
I designed a **Snowflake Schema** to ensure data integrity and performance.
* **Normalization:** Separated `Dim_Vendor` from `Dim_Product` to reduce redundancy.
* **Date Table:** Created a dedicated `Dim_Date` table using DAX to support Time Intelligence functions like `SAMEPERIODLASTYEAR`.
* **Relationships:** Established One-to-Many relationships between the Fact table and Dimensions.

![Data Model](Data_Model.png)

#### **DAX Complexity**
* **Iterators (SUMX):** Used `SUMX` to calculate the *Missed Profit Opportunity* row-by-row at the Sub-Category level, ensuring accurate margin calculations despite varying product costs.
* **Time Intelligence:** Calculated YoY Growth and YTD trends.
* **Data Quality Flags:** Created logic to identify and flag `NULL` or zero-cost transactions without breaking the report.

---

### **Tools Used**
* **Power BI Desktop** (Data Modeling, DAX, Visualization)
* **Power Query** (ETL and Data Cleaning)
* **Excel** (Source Data)
