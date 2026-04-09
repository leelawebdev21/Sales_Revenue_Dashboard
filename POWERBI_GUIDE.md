# Power BI Dashboard Guide
## Sales & Revenue Analysis — FY 2024

This guide walks you through building a Power BI dashboard using the `Sales_Revenue_Dashboard.xlsx` file step by step.

---

## What You'll Build

A 4-page Power BI report with:
- **Page 1** — Executive Summary (KPI cards + trend line)
- **Page 2** — Monthly Trends (line + bar charts)
- **Page 3** — Category & Product Analysis (bar charts, donut)
- **Page 4** — Regional Performance (map + table)

---

## Step 1 — Install Power BI Desktop (Free)

1. Go to **https://powerbi.microsoft.com/desktop**
2. Click "Download free" → install it
3. Open Power BI Desktop (no account needed to start)

---

## Step 2 — Load the Excel File

1. Click **Home → Get Data → Excel Workbook**
2. Browse to `Sales_Revenue_Dashboard.xlsx` and click **Open**
3. In the Navigator window, tick these sheets:
   - ✅ Sales Data
   - ✅ Monthly Summary
   - ✅ Category Analysis
   - ✅ Region Analysis
4. Click **Transform Data** (opens Power Query Editor)
5. In Power Query: click **"Use First Row as Headers"** if headers aren't detected
6. Click **Close & Apply**

---

## Step 3 — Check Your Data (Data View)

Click the **table icon** on the left sidebar (Data view).

Make sure:
- `Sales Data` has columns: Order ID, Month, Quarter, Region, Sales Rep, Category, Product, Units Sold, Unit Price, Gross Revenue, Discount, Discount Amount, Net Revenue
- Numbers look correct (not text)
- No blank rows at the top

> **Tip:** If any number column shows as "ABC" (text), click the column → go to **Transform → Data Type → Whole Number**

---

## Step 4 — Create Measures (Calculated KPIs)

In the **Data view**, right-click `Sales Data` → **New Measure**. Add these one by one:

```
Total Revenue = SUM('Sales Data'[Net Revenue (₹)])
```
```
Total Orders = COUNTROWS('Sales Data')
```
```
Total Units = SUM('Sales Data'[Units Sold])
```
```
Avg Order Value = DIVIDE([Total Revenue], [Total Orders], 0)
```
```
Gross Revenue = SUM('Sales Data'[Gross Revenue (₹)])
```
```
Total Discount = SUM('Sales Data'[Discount Amount (₹)])
```

---

## Step 5 — Build Page 1: Executive Summary

Click **Report view** (bar chart icon on left sidebar).

### Add KPI Cards
1. Click **Insert → Text Box** → type "Sales & Revenue Dashboard FY 2024" (title)
2. From Visualizations panel, click the **Card** visual (rectangle with number)
3. Drag **Total Revenue** measure into the "Fields" box → format to ₹
4. Repeat for: **Total Orders**, **Total Units**, **Avg Order Value**
5. Arrange 4 cards in a row at the top

### Add a Revenue Trend Line
1. Click **Line Chart** visual
2. X-axis: `Month` (from Monthly Summary)
3. Y-axis: `Net Revenue (₹)` (from Monthly Summary)
4. Title: "Monthly Net Revenue Trend"

### Add a Donut Chart (Revenue by Category)
1. Click **Donut Chart** visual
2. Legend: `Category` (from Category Analysis)
3. Values: `Net Revenue (₹)` (from Category Analysis)

---

## Step 6 — Build Page 2: Monthly Trends

Right-click the page tab at the bottom → **Add Page**

### Clustered Bar Chart — Revenue by Month
1. Click **Clustered Bar Chart**
2. Y-axis: `Month` (Monthly Summary)
3. X-axis: `Net Revenue (₹)` (Monthly Summary)
4. Title: "Net Revenue by Month"

### Line & Clustered Column Chart — Orders vs Revenue
1. Click **Line and Clustered Column Chart**
2. X-axis: `Month`
3. Column values: `Gross Revenue (₹)`
4. Line values: `Orders`
5. Title: "Orders vs Revenue by Month"

---

## Step 7 — Build Page 3: Category Analysis

Add a new page.

### Bar Chart — Revenue by Category
1. **Clustered Bar Chart**
2. Y-axis: `Category`, X-axis: `Net Revenue (₹)`
3. Sort descending by revenue

### Table — Category Details
1. Click **Table** visual
2. Add columns: Category, Orders, Units Sold, Net Revenue, % of Total Revenue
3. Enable **Conditional Formatting** on Net Revenue (Home → Conditional Formatting → Background Color)

---

## Step 8 — Build Page 4: Regional Performance

Add a new page.

### Map Visual
1. Click **Map** visual (may need to enable in Settings → Security → Map visuals)
2. Location: `Region`
3. Size: `Net Revenue (₹)`

### Bar Chart — Region Comparison
1. **Clustered Column Chart**
2. X-axis: `Region`, Y-axis: `Net Revenue (₹)`
3. Add a second series: `Gross Revenue (₹)` (to show discount impact)

---

## Step 9 — Add Slicers (Filters)

Slicers let you filter the whole report interactively.

1. Click **Slicer** visual
2. Field: `Quarter` → makes a clickable Q1/Q2/Q3/Q4 filter
3. Add another slicer: `Category`
4. Add another slicer: `Region`
5. Copy slicers to all pages (right-click → Copy, then paste on other pages)

---

## Step 10 — Polish & Save

1. Go to **View → Themes** → pick a professional theme (e.g., "Executive")
2. Add a text box title to each page
3. Align visuals using **Format → Align**
4. Click **File → Save As** → name it `Sales_Revenue_Dashboard.pbix`

---

## Step 11 — Export for GitHub

Power BI `.pbix` files can be uploaded directly to GitHub like any other file.

To share screenshots:
1. **File → Export → Export to PDF** — great for README preview images
2. Take screenshots of each page and save to a `screenshots/` folder
3. Add screenshots to your README.md

---

## Key Visuals Checklist

| Page | Visual | Done? |
|------|--------|-------|
| Executive Summary | 4 KPI Cards | ☐ |
| Executive Summary | Revenue Trend Line | ☐ |
| Executive Summary | Category Donut Chart | ☐ |
| Monthly Trends | Revenue Bar Chart | ☐ |
| Monthly Trends | Orders vs Revenue Combo | ☐ |
| Category Analysis | Category Bar Chart | ☐ |
| Category Analysis | Detail Table | ☐ |
| Regional Performance | Map Visual | ☐ |
| Regional Performance | Region Comparison Bar | ☐ |
| All Pages | Quarter/Category/Region Slicers | ☐ |

---

## Tips for Beginners

- **Ctrl+Z** undoes any mistake in Power BI
- Right-click any visual → **Format** to change colors, fonts, titles
- Click anywhere outside a visual to deselect it
- The **Fields** panel on the right shows all your data columns
- Yellow lightning bolt = a Measure you created

---

*Project: Sales & Revenue Dashboard | Tools: Excel + Power BI Desktop*
