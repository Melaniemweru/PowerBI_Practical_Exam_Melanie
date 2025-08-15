# PowerBI_Practical_Exam_Melanie
# Power BI Exam Dashboard Overview

## Project Overview
This Power BI project demonstrates a comprehensive approach to analyzing sales, product, and customer data. The report is designed to provide interactive, drillable insights for business decision-making, with a focus on clarity, color consistency, and cross-filtering between visuals.


---
## Insights, Assumptions, and Limitations

### **Insights**
Based on the visuals, measures, and dashboards implemented, the following insights emerge:

1. **Sales Overview**
   - **Total Sales:** $8,080,000  
   - **Total Profit:** $3,380,000  
   - **Sales Trends:** Line chart with running total and 6-month forecast shows steady growth with seasonal peaks.  
   - **YoY Performance:** Year-over-Year growth reveals months where sales underperformed relative to the previous year.  
   - **Geography Insights:** Map visual shows that the United States and selected states contribute the majority of sales. Drill-down to city level identifies localized high-performing areas.

2. **Product Analysis**
   - **Top Products:** Bar chart identifies the Top 10 products by sales.  
   - **Category Contribution:** Bikes contribute **95.17%** of category sales.  
   - **Profit vs Quantity:** Scatter plot shows a positive correlation between quantity sold and profit, with Year as play axis revealing trends over time.  
   - **Decomposition Tree:** Highlights which customers, products, and regions contribute most to sales, aiding targeted strategies.

3. **Customer Insights**
   - **Total Customers:** 18,484  
   - **Top Customers:** Table visual identifies high-value customers; conditional formatting highlights low-profit customers.  
   - **Key Metrics:** Multi-row card shows total sales, total profit, and other aggregated metrics at a glance.

4. **Advanced Features (DAX Measures & RLS)**
   - **Running Total Sales:** Shows cumulative sales over time for trend analysis.  
   - **YoY Growth:** Highlights periods with strong or weak growth.  
   - **Top N Products:** Dynamic filter allows identification of best-performing products.  
   - **Row-Level Security:** US Manager sees only United States sales; Europe Manager sees only European regions.

5. **Custom Visuals**
   - **Bullet Chart (Sales vs Budget):** Shows attainment of budget, helping identify gaps and over-performing products or regions.  
   - **Gauge Visual:** Displays profit margin against a 30% target; allows quick assessment of performance.

---

### **Assumptions**
- The `Dates` table is complete and continuous, supporting time intelligence functions.  
- Sales, product, and customer data are accurate and cleaned.  
- All currency values are consistent (USD).  
- Top N filters are based on total sales only.  
- Forecast assumes trends continue and does not account for external disruptions (e.g., promotions or supply chain issues).  

---

### **Limitations**
1. **Data Granularity:** Analysis is at product, customer, and date levels; transaction-level data could provide deeper insights.  
2. **Forecast Accuracy:** Predictions rely solely on historical trends and may be affected by sudden market changes.  
3. **Performance:** Measures like RANKX and cumulative totals may slow down reports with very large datasets.  
4.   
5. **Excluded Factors:** Macroeconomic events, promotions, and supply chain issues are not included.  
6. **Visual Clarity:** Scatter plots with many points or decomposition trees may appear cluttered without filters.

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


