# PowerBI_Practical_Exam_Melanie
# Power BI Exam Dashboard Overview

## Project Overview
This Power BI project demonstrates a comprehensive approach to analyzing sales, product, and customer data. The report is designed to provide interactive, drillable insights for business decision-making, with a focus on clarity, color consistency, and cross-filtering between visuals.

The dashboard includes:
- **Sales Overview:** Line chart showing Sales over Time with Year-over-Year growth, KPI cards for total revenue and profit, and a map of sales by region.
- **Product Analysis:** Bar charts, scatter plots, and decomposition tree for Top and Bottom performing products, with dynamic Top N filters and bookmarks for different views.
- **Customer Insights:** Table visual showing Top Customers by Sales, with conditional formatting to highlight low/high profit, and multi-row cards for key metrics such as Average Revenue per Customer, Repeat Customers, and Total Revenue.
-
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

![Power Query Editor](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-13%20(5).png)

# Section 2: Data Modeling (15 Marks)

## 1. Relationships (8 Marks)

**Description:**  
Built a star schema with `Sales_data` as the central fact table and dimensions `Dates`, `Products`, `Customers`, `Geography`. All relationships are active and follow a many-to-one structure.

**Screenshots:**

![Model View](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(4).png)


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




# Section 3: Visualizations

## 1. Basic Visuals (10 Marks)

### Bar Chart – Top 10 Products by SalesAmount
**Description:**  
Shows the top 10 products sorted by SalesAmount in descending order. Data labels and tooltips display Profit for each product.  
**Screenshot:**  
![Bar Chart](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(9).png)

---

### Line Chart – SalesAmount Over Time (by Month)
**Description:**  
Displays monthly SalesAmount trends with a trend line and 6-month forecast. Useful for identifying seasonal patterns and projecting future sales.  
**Screenshot:**  
![Line Chart](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(5).png)

---

### Pie Chart – Sales Distribution by Category
**Description:**  
Illustrates the proportion of sales by product category. Limited to avoid clutter. Legend and percentages shown for clarity.  
**Screenshot:**  
![Pie Chart](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(8).png)

---

### Map – Sales by Country/State
**Description:**  
Bubble map showing sales quantity by Country/State. Drill-down enabled to City level for detailed insights. Tooltips show SalesAmount.  
**Screenshot:**  
![Map](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(13).png)

---

## 2. Advanced Visuals (15 Marks)

### Scatter Plot – Quantity vs Profit
**Description:**  
Visualizes Quantity vs Profit, colored by Sales Category. Includes a Play Axis for Year to see trends over time.  
**Screenshot:**  
![Scatter Plot](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(10).png)

---

### KPI Card – Total SalesAmount
**Description:**  
Shows Total SalesAmount with a target (e.g., 10% growth from previous year) and variance for quick insight.  


---

### Gauge – Profit Margin
**Description:**  
Displays Profit Margin (Profit / SalesAmount) with a target of 30%. Color-coded for quick assessment of performance.  
**Screenshot:**  
![Gauge](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(6).png)

---

### Decomposition Tree – SalesAmount Breakdown
**Description:**  
Breaks down SalesAmount by Customer → Product → Region. Enables interactive exploration of key drivers.  
**Screenshot:**  
![Decomposition Tree](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(12).png)

---

### Custom Visual – Bullet Chart (Sales vs Budget)
**Description:**  
Shows Total Sales against Budget (assume Budget = 1.2 × Cost). Highlights attainment and performance ranges with optional qualitative bands.  
**Screenshot:**  
![Bullet Chart](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(7).png)

---

**Notes:**  
- All visuals are interactive (cross-filtering, slicers).  
- Color-blind friendly theme applied.  
- Avoided clutter and ensured scales are accurate.  



# Section 4: Building Reports and Dashboards

## 3. Report Pages (12 Marks)

### Page 1 – Sales Overview
**Description:**  
Includes the line chart for SalesAmount over time, KPI for Total Sales, and Map for sales by region. Slicers for Year, Category, and Region are added and synced across pages.

**Screenshot:**
![Sales Overview](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(15).png)
*Figure 1: Sales Overview page with line chart, KPI, and map*

---

### Page 2 – Product Analysis
**Description:**  
Contains a Bar Chart, Scatter Plot, and Decomposition Tree. Bookmarks are created to toggle between Top vs. Bottom performers for quick insights.

**Screenshot:**
![Product Analysis](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(17).png)
*Figure 2: Product Analysis page showing charts and decomposition tree*

---

### Page 3 – Customer Insights
**Description:**  
Table visual for Top Customers by Sales with conditional formatting. Multi-row card visual for key metrics.

**Screenshot:**
![Customer Insights](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(16).png)
*Figure 3: Customer Insights page with table and multi-row card*

---

## 4. Dashboard (8 Marks)
**Description:**  
Pinned visuals from report pages to Power BI Service dashboard. Tiles added for quick insights, Q&A enabled for natural language queries. Mobile layout optimized, consistent theme applied.

**Screenshot:**
![Dashboard](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/Dashboard%20Screenshots/2025-08-15%20(24).png)
*Figure 4: Dashboard showing pinned visuals and tiles*

![Dashboard](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/Dashboard%20Screenshots/2025-08-15%20(23).png)

# Section 5: Advanced Features and DAX (15 Marks)

This section demonstrates the implementation of advanced DAX measures and row-level security (RLS) in Power BI. Measures include Year-over-Year growth and Running Total Sales to analyze trends and cumulative performance. RLS ensures data is visible only to authorized roles (e.g., US Manager, Europe Manager).

---

## 1. DAX Measures

### Year-over-Year (YoY) Growth
**Measure Description:**  
Shows the percentage growth of sales compared to the same period last year. Useful for trend and performance analysis.

**Screenshot / Visual:**  
![YoY Growth Visual](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(20).png)

---

### Running Total Sales
**Measure Description:**  
Displays cumulative sales up to the current date, allowing tracking of progress over time.

**Screenshot / Visual:**  
![Running Total Sales Visual](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(21).png)

---

## 2. Row-Level Security (RLS)

### Roles Implemented:
- **US Manager:** Filters data to `Country = "United States"`.
- **Europe Manager:** Filters data to countries in Europe.

**Screenshot / Visual:**  
![RLS Setup](https://github.com/Melaniemweru/PowerBI_Practical_Exam_Melanie/blob/main/BI%20SCREENSHOTS/2025-08-15%20(22).png)

**Notes:**  
- Test RLS using "View as Role" in Power BI Desktop or Service.  
- Ensure DAX measures are efficient and free of errors.  
- Use these measures in visuals for interactive insights across the report.


