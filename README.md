# Power BI Sales Dashboard

## Description
This project is a beginner-level Power BI dashboard built to analyze sales performance from an orders dataset. It highlights key KPIs (Total Sales, Total Orders, Total Customers, AOV, and YoY% growth) and provides interactive visuals such as monthly trends, category-wise sales share, and summary tables. A calendar table and proper relationships were created to enable consistent time-based reporting, and slicers were added to make the dashboard easy to explore by different segments (e.g., year, category, region).

**Note:** This was made for learning purpose.

## Features
- KPI cards using DAX measures (Sales, Orders, Customers, AOV, YoY%)
- Monthly trend analysis (line/column charts)
- Category share of total sales (pie chart)
- Summary tables/matrix for quick breakdowns
- Slicers for interactive filtering (Year/Month/Region/Category)

## Tech Stack
- Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query (basic data cleaning/shaping)

## Screenshots

![Dashboard Overview](screenshots/Screenshot%202026-03-15%20020112.png)

![Dashboard Trends](screenshots/Screenshot%202026-03-15%20020131.png)

![Dashboard Details](screenshots/Screenshot%202026-03-15%20020149.png)

## Example DAX Measures
```DAX
Total Revenue = SUM('CSV UTF-8'[Sales])

Total Orders = DISTINCTCOUNT('CSV UTF-8'[Order ID])

Total Customers = DISTINCTCOUNT('CSV UTF-8'[Customer ID])

AOV = DIVIDE([Total Sales], [Total Orders])

Sales LY =
CALCULATE(
    [Total Sales],
    DATEADD('Calendar_Full'[Date], -1, YEAR)
)

YoY % = DIVIDE([Total Sales] - [Sales LY], [Sales LY])
```

## Project Structure
-  Power BI `.pbix` file
- `data/` – dataset 
- `screenshots/` – dashboard images

## Notes
- If your dataset has multiple rows per order (line items), use `DISTINCTCOUNT([Order ID])` for order counts.

