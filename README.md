# PowerBI_Practical_Exam_Melanie
# Power BI Exam Dashboard Overview

## Project Overview
This Power BI project demonstrates a comprehensive approach to analyzing sales, product, and customer data. The report is designed to provide interactive, drillable insights for business decision-making, with a focus on clarity, color consistency, and cross-filtering between visuals.

The dashboard includes:
- **Sales Overview:** Line chart showing Sales over Time with Year-over-Year growth, KPI cards for total revenue and profit, and a map of sales by region.
- **Product Analysis:** Bar charts, scatter plots, and decomposition tree for Top and Bottom performing products, with dynamic Top N filters and bookmarks for different views.
- **Customer Insights:** Table visual showing Top Customers by Sales, with conditional formatting to highlight low/high profit, and multi-row cards for key metrics such as Average Revenue per Customer, Repeat Customers, and Total Revenue.

---

## Key Features
- **Interactive Visuals:** Cross-filtering between line charts, maps, and bar charts.
- **Consistent Color Palette:** Titles, values, and category colors follow a ColorblindSafe palette for readability.
- **Dynamic Filters:** Top N slicers and year/category/region slicers allow users to explore different segments.
- **Navigation Menu:** Sidebar buttons enable quick access to different report pages, simulating a website-like experience.
- **DAX Calculations:** Includes Total Sales, Total Profit, Profit Margin, YoY Growth, Running Total, and Top/Bottom N product ranking.

---

## Challenges and Solutions
- Ensured **continuous date axis** for time series analysis by using the Date table.
- Implemented **Top N / Bottom N filtering** using calculated columns and slicers since visual-level filters cannot use measures directly.
- Conditional formatting for customers was implemented with DAX color measures to highlight performance.
- Avoided circular dependency in DAX measures by referencing base measures instead of recalculating totals.

---

## Report Link
[View Published Power BI Report](YOUR_POWERBI_SERVICE_LINK_HERE)

---



---

## Key Insights
- Electronics contributed **40% of total sales**.
- Top 5 products accounted for **60% of revenue**.
- Profit margins are highest in **Region X**, lowest in **Region Y**.
- Repeat customers make up **25% of total orders**, driving significant revenue.

---

## Assumptions and Limitations
- Forecast assumes linear trend and consistent seasonality.
- Data is only as accurate as the source tables; missing values may affect totals.
- Top/Bottom N views rely on current slicer selection for dynamic filtering.
---
## Section 1: Data Import and Transformation (20 Marks)

Dataset was imported into Power BI and cleaned using **Power Query Editor**.  

- **Imported tables:** Sales, Products, Customers, Dates.  
- **Transformations:**  
  - Calculated Profit = SalesAmount - (Quantity * Cost)  
  - Split Customer Name into FirstName / LastName  
  - Created Sales Category (High / Medium / Low)  
  - Aggregated Dates by Year/Month  
  - Removed duplicates and filtered out pre-2018 records  
- **Data Quality:** Checked for missing values and outliers; applied corrections.  

### Screenshot
Insert screenshot of Power Query Editor here:

![Power Query Editor](screenshots/powerquery_editor.png)

# Section 2: Data Modeling (15 Marks)

## 1. Relationships (8 Marks)

**Description:**  
Built a star schema with `Sales_data` as the central fact table and dimensions `Dates`, `Products`, `Customers`, `Geography`. All relationships are active and follow a many-to-one structure.

**Screenshots:**

![Model View](screenshots/model_view.png)
*Figure 1: Relationships in Model view, showing active links*

**Notes:**  
- Sales ↔ Dates via OrderDate → Date  
- Sales ↔ Products via ProductID  
- Sales ↔ Customers via CustomerID  
- Customers ↔ Geography via City/State  

---

## 2. Hierarchies and Measures (7 Marks)

**Date Hierarchy:**  
Year > Quarter > Month > Day  

**Product Hierarchy:**  
Category > Subcategory > ProductName  

**Measures Formatting:**  
- SalesAmount → Currency, 2 decimals  
- TotalCost → Currency  
- Profit → Currency  
- Budget Attainment → Percentage  

**Screenshots:**

![Date Hierarchy](screenshots/date_hierarchy.png)
*Figure 2: Date hierarchy in Dates table*

![Product Hierarchy](screenshots/product_hierarchy.png)
*Figure 3: Product hierarchy in Products table*

**Tips:**  
- Hide surrogate keys for cleaner Fields pane  
- Use hierarchies for drill-down in visuals  
- Format measures consistently for readability


