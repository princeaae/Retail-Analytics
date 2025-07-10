# 👕 Men’s Retail Analytics Dashboard (Power BI + BigQuery)

> **Type:** BI Dashboard  
> **Tools Used:** Power BI, BigQuery, DAX, Power Query  
> **Domain:** Retail | **Focus:** Sales, Profit %, Discount %, Brand Comparison

---

## 📌 Overview

This project analyzes branded men’s t-shirt sales data to extract key business insights like top/bottom performing brands, pricing trends, discounting strategy, and profitability. The goal is to help retail teams optimize inventory and marketing based on data.

---

## 🎯 Objectives

- Analyze brand-level performance by profit, discount, and variety
- Clean and model raw sales data using Power BI and DAX
- Visualize key KPIs using interactive dashboards
- Practice BigQuery as a data source for real-world BI use

---

## 🔄 Steps Followed

1. **Uploaded dataset to BigQuery** and ran basic SQL queries to understand schema
2. **Connected BigQuery to Power BI** and loaded the dataset
3. Cleaned and transformed data using **Power Query**:
   - Fixed headers
   - Converted text columns to proper data types (e.g., dates, decimals)
   - Handled missing values in Sales Price
4. Created custom logic to estimate **missing Marked Prices**:
   - Added a `Factor` column:  
     `= IF(Original Price is blank, 1.5, 0)`
   - Created a new column:  
     `= Sales Price * Factor`
   - Used this to fill missing Marked Prices
5. Removed temporary columns after transformation

---

## 🧮 Key DAX Calculations

```DAX
-- Profit %
Profit % = RANDBETWEEN(2, 17)

-- Cost Price
Cost Price = DIVIDE(100 * [Sales Price], 100 + [Profit %])

-- Discount %
Discount % = DIVIDE([Marked Price] - [Sales Price], [Marked Price]) * 100
