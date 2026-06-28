# Chart Selection Justification
### Executive Sales Dashboard — Visualization Design Decisions

---

## Overview

Every chart in this dashboard was selected to answer a specific business question using the most appropriate visual encoding. This document explains the rationale behind each chart type, the fields used, the design principles applied, and the mistakes deliberately avoided.

---

## Chart 1 — Sales Trend Over Time (Line Chart)

**Business Question Answered:**  
How are total monthly sales and profit evolving over the two-year period? Are we growing, declining, or plateauing?

**Why This Chart Type:**  
A line chart is the standard and most effective chart for continuous time-series data. It clearly communicates direction, rate of change, and seasonal patterns. The human eye naturally tracks lines across time, making acceleration and deceleration immediately visible.

**Fields Used:**
- **X-Axis:** Order Date (Month granularity)
- **Y-Axis:** SUM(Sales) — with a secondary axis for SUM(Profit)
- **Color:** Two lines — Sales (blue) and Profit (green) for contrast
- **Label:** Year markers and peak month annotations

**Design Principle Applied:**  
Dual-axis line chart with clearly labeled axes. Color chosen to be distinguishable without being garish. Month labels rotated 45° to prevent overlap.

**Mistake Avoided:**  
Did not use a bar chart for this view — while bars work for discrete periods, a line chart better communicates continuity and trend. Also avoided using too many data series on one chart, which would create visual clutter.

---

## Chart 2 — Regional Performance (Filled Map + Bar Chart)

**Business Question Answered:**  
Which regions generate the most sales and profit? Are there geographic blind spots?

**Why This Chart Type:**  
A geographic map provides immediate spatial context — leadership can see where revenue is concentrated without reading labels. A companion bar chart provides the precise numbers the map cannot convey. Together they answer "where" and "how much."

**Fields Used:**
- **Map:** State (geographic dimension) → color-encoded by SUM(Sales) using a blue gradient (light = low, dark = high)
- **Bar Chart:** Region on the Y-axis; SUM(Sales) and SUM(Profit) as dual bars
- **Tooltip:** Region, State, Sales, Profit, Profit Margin

**Design Principle Applied:**  
Sequential color scale (single hue) for the map — avoids confusion between diverging scales. Bar chart sorted descending by sales to allow instant rank reading.

**Mistake Avoided:**  
Did not use a pie chart for regional share — pie charts are poor at showing magnitude differences between similar-sized slices. Did not use rainbow/multi-color maps which make comparison difficult.

---

## Chart 3 — Category & Sub-Category Profitability (Horizontal Bar Chart / Highlight Table)

**Business Question Answered:**  
Which product categories and sub-categories drive profit — and which are dragging it down?

**Why This Chart Type:**  
A horizontal bar chart sorted by profit margin allows immediate comparison across 13 sub-categories. Labels are easy to read horizontally. A companion highlight table (heat map) shows absolute profit in color intensity, making both size and efficiency visible at a glance.

**Fields Used:**
- **Bar Chart Y-Axis:** Sub-Category (sorted by Profit Margin ascending — worst to best)
- **X-Axis:** Profit Margin (%)
- **Color:** Category (Furniture = orange, Office Supplies = blue, Technology = green) for grouping
- **Highlight Table:** Sub-Category rows × Category columns, colored by SUM(Profit) with red–white–green diverging palette

**Design Principle Applied:**  
Diverging color palette (red for loss/low margin, green for high margin) makes underperformers immediately visible. Sorted ordering prevents the need to scan the entire chart.

**Mistake Avoided:**  
Did not use a 3D bar chart — 3D charts distort bar heights and are impossible to read accurately. Did not mix categories into one unsorted bar chart without color coding, which would make category-level patterns invisible.

---

## Chart 4 — Customer Segment Performance (Grouped Bar Chart)

**Business Question Answered:**  
How do Consumer, Corporate, and Home Office segments compare in sales, profit, and return rates?

**Why This Chart Type:**  
A grouped bar chart (side-by-side bars) allows direct comparison of multiple metrics across three discrete categories. The grouping allows viewers to instantly see which segment leads on each metric without switching between charts.

**Fields Used:**
- **X-Axis:** Customer Segment (3 categories)
- **Y-Axis:** SUM(Sales) as primary; SUM(Profit) and Return Rate (%) as secondary metrics
- **Color:** Metric type (Sales = blue, Profit = teal, Return Rate = red)
- **Label:** Values on bar tops for precision

**Design Principle Applied:**  
Consistent color per metric across segments. Y-axis starts at zero to avoid misleading magnitude impressions. Clear segment labels.

**Mistake Avoided:**  
Did not use a stacked bar chart — stacking prevents accurate comparison of individual segment metrics. Did not omit the return rate, which provides critical risk context alongside revenue.

---

## Chart 5 — Discount vs. Profit Scatter Plot

**Business Question Answered:**  
Is there a relationship between the level of discount offered and the profitability of orders? At what discount level does profitability break down?

**Why This Chart Type:**  
A scatter plot is the only chart type that effectively shows the relationship (or lack thereof) between two continuous variables. It reveals whether high discounts correlate with low profits at the individual order level, and whether there are outlier orders where deep discounts still generated profit (or vice versa).

**Fields Used:**
- **X-Axis:** Discount (0–35%)
- **Y-Axis:** Profit (or Profit Margin)
- **Color:** Category (to see if the discount-profit relationship differs by product type)
- **Size:** Sales amount (larger bubbles = higher revenue orders)
- **Reference Line:** At 0% profit and at 20% discount threshold

**Design Principle Applied:**  
Reference lines make the "loss zone" (negative profit) and the "risky discount zone" (>20%) visually explicit. Color by category reveals that Furniture orders at high discounts are almost always loss-making.

**Mistake Avoided:**  
Did not use a bar chart of average profit by discount bucket alone — while insightful, averages hide the variance in individual orders. A scatter plot shows the full distribution. Did not connect points with lines, which would imply sequential ordering that doesn't exist.

---

## Chart 6 — Shipping Mode & Delivery Performance (Bar Chart + Table)

**Business Question Answered:**  
Which shipping modes are used most? How do they compare on delivery speed? Where are delays concentrated?

**Why This Chart Type:**  
A horizontal bar chart of order count by ship mode with a color overlay for average delivery days provides both volume and performance in one view. The "Shipping Delay Bucket" chart shows the distribution of orders across speed categories.

**Fields Used:**
- **Ship Mode Bar Chart:** Y-Axis = Ship Mode; X-Axis = Count of Orders; Color = Avg Delivery Days (light to dark)
- **Delay Bucket Chart:** X-Axis = Shipping Delay Bucket ("Express" to "Slow"); Y-Axis = Order Count; Color = Bucket (green to red)

**Design Principle Applied:**  
Color-coded delay severity (green = fast, red = slow) makes the performance gap visually intuitive. Bar charts are sorted from slowest to fastest for a natural reading flow.

**Mistake Avoided:**  
Did not use a pie chart for shipping mode share — proportional area is hard to read and doesn't convey delivery speed. Did not use line chart since ship mode is a discrete category, not a continuous variable.

---

## Chart 7 — Return Analysis (Highlight Table / Bar Chart)

**Business Question Answered:**  
Where are returns concentrated — by category, segment, and region? What is the risk profile?

**Why This Chart Type:**  
A highlight table (cross-tab with color intensity) allows simultaneous analysis of return rates across multiple dimensions (Category × Segment × Region) in a compact space. A companion bar chart ranks categories by return rate for a clear headline takeaway.

**Fields Used:**
- **Highlight Table Rows:** Category; Columns: Customer Segment
- **Color:** Return Rate (%) — white (low) to red (high) diverging scale
- **Bar Chart:** Category on Y-axis; Return Rate on X-axis, colored red for emphasis

**Design Principle Applied:**  
Red color for return rate signals risk — an intentional and intuitive choice for a "bad" metric. White-to-red scale avoids misrepresenting neutral return rates as positive.

**Mistake Avoided:**  
Did not use absolute return counts alone — a large segment might show more returns simply because it has more orders. Return *rate* normalises for volume and is the correct metric. Did not use 3D charts or bubble charts which would add unnecessary complexity.

---

## KPI Cards Design

**Three KPI summary cards are placed prominently at the top of the dashboard:**

| KPI Card | Metric | Design Choice |
|---|---|---|
| Total Revenue | ₹21.7 Cr | Large, bold number; blue |
| Net Profit | ₹3.33 Cr | Green (positive signal) |
| Blended Profit Margin | 15.3% | Teal, with trend arrow |
| Overall Return Rate | 4.5% | Amber (caution) |
| Total Orders | 4,200 | Grey (neutral context) |

**Design Principle:** KPI cards are scannable in under 3 seconds. Color carries meaning (green = good, amber = watch, red = concern). No decoration, no 3D effects, no unnecessary borders.

---

## Overall Dashboard Design Principles Applied

| Principle | Application |
|---|---|
| **Hierarchy** | KPI cards at top, trend in centre, detail charts below |
| **Minimal clutter** | No gridlines on clean charts; tooltips for detail |
| **Consistent color** | Blue = Sales, Green = Profit, Red = Risk/Returns, Teal = Margin throughout |
| **Proper sorting** | All bar charts sorted by value (not alphabetically) |
| **Readable titles** | Every chart has a plain-English question as its title |
| **Interactive filters** | Region, Category, Segment, Date Range, Ship Mode at the top |
| **No misleading scales** | All Y-axes start at zero; no truncated axes |
| **Business-first labels** | Axes labeled in business terms, not field names |
