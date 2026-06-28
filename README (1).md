# Executive Sales Dashboard — Tableau Project

**Repository:** `studentname_studentid_part4_tableau_dashboard`  
**Dataset Period:** January 2024 – December 2025  
**Total Records:** 4,200 orders  
**Tool:** Tableau Desktop (packaged workbook: `tableau/executive_dashboard.twbx`)

---

## Business Problem Summary

The retail leadership team needs a single, authoritative executive dashboard to monitor:

- Revenue and profit trends over time
- Regional and state-level sales performance
- Category and sub-category profitability
- Customer segment behaviour and return risk
- Discount policy impact on profitability
- Shipping mode efficiency and delivery delay patterns
- Return patterns by category, segment, and region

The dashboard must support fast, data-driven decisions — not just report history but highlight where action is needed.

---

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`  
**Sheet:** `dashboard_sales_data` (4,200 rows × 20 columns)

| Column | Data Type | Description |
|---|---|---|
| `order_id` | String | Unique order identifier |
| `order_date` | Date | Date the order was placed |
| `ship_date` | Date | Date the order was shipped |
| `customer_id` | String | Unique customer identifier |
| `customer_segment` | String | Consumer / Corporate / Home Office |
| `region` | String | North / South / East / West |
| `state` | String | Indian state |
| `city` | String | City name |
| `category` | String | Furniture / Office Supplies / Technology |
| `sub_category` | String | 13 sub-categories (Tables, Phones, etc.) |
| `product_name` | String | Product description |
| `ship_mode` | String | Standard Class / First Class / Second Class / Same Day |
| `sales` | Decimal | Order revenue (₹) |
| `quantity` | Integer | Units ordered |
| `discount` | Decimal | Discount rate (0.00 – 0.35) |
| `profit` | Decimal | Net profit (₹); can be negative |
| `return_flag` | Binary | 1 = returned; 0 = not returned |
| `delivery_days` | Integer | Days from order to delivery |
| `customer_rating` | Decimal | Customer satisfaction score (2.1–5.0); 32 nulls |
| `campaign_channel` | String | Organic / Social / Paid / Email / Referral; 24 nulls |

**Key Statistics:**
- Total Sales: ₹21.70 Cr
- Total Profit: ₹3.33 Cr
- Blended Profit Margin: 15.3%
- Overall Return Rate: 4.5%
- Date Range: 01-Jan-2024 to 31-Dec-2025

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The packaged workbook includes the embedded dataset and the following sheets:

| Sheet Name | Purpose |
|---|---|
| Sales Trend | Monthly sales and profit over time (line chart) |
| Regional Performance | Sales/profit by region and state (map + bar chart) |
| Category Profitability | Category and sub-category margins (bar chart + highlight table) |
| Customer Segment View | Sales, profit, and return rate by segment (grouped bar) |
| Shipping Performance | Ship mode and delivery delay analysis (bar chart) |
| Discount vs Profit | Relationship between discount level and profit (scatter plot) |
| Return Analysis | Return rates by category, segment, and region (highlight table) |
| Executive Dashboard | Combined dashboard with KPI cards, filters, and all views |

---

## Calculated Fields Created

All calculated fields are defined inside the Tableau workbook. Below are the 5 required fields plus 2 additional fields:

| Field Name | Formula | Purpose |
|---|---|---|
| **Profit Margin** | `[Profit] / [Sales]` | Measures profitability per rupee of revenue |
| **Cost** | `[Sales] - [Profit]` | Derives implicit cost from revenue and profit |
| **Average Order Value** | `SUM([Sales]) / COUNTD([Order ID])` | Revenue efficiency per transaction |
| **Return Rate** | `SUM([Return Flag]) / COUNT([Order ID])` | Proportion of orders returned |
| **Shipping Delay Bucket** | `IF [Delivery Days] <= 1 THEN "0-1 Days (Express)" ELSEIF [Delivery Days] <= 3 THEN "2-3 Days (Fast)" ELSEIF [Delivery Days] <= 5 THEN "4-5 Days (Standard)" ELSE "6+ Days (Slow)" END` | Categorises delivery speed for SLA monitoring |
| **Discount Bucket** | `IF [Discount] <= 0.05 THEN "0-5%" ELSEIF [Discount] <= 0.10 THEN "5-10%" ELSEIF [Discount] <= 0.20 THEN "10-20%" ELSEIF [Discount] <= 0.30 THEN "20-30%" ELSE "30-35%" END` | Groups discount tiers for impact analysis |
| **Profit Status** | `IF [Profit] > 0 THEN "Profitable" ELSE "Loss" END` | Binary profit flag for coloring scatter plot points |

---

## Dashboard Components

### KPI Cards (5 summary metrics at top)
1. **Total Revenue** — ₹21.70 Cr
2. **Total Profit** — ₹3.33 Cr
3. **Profit Margin** — 15.3%
4. **Return Rate** — 4.5%
5. **Total Orders** — 4,200

### Charts (7 views embedded in dashboard)
1. Sales & Profit Trend (line chart) — monthly granularity, 2024–2025
2. Regional Performance Map — state-level filled map + regional bar chart
3. Category/Sub-Category Profitability — horizontal bar chart sorted by margin
4. Customer Segment Comparison — grouped bar chart (sales, profit, return rate)
5. Shipping Mode & Delay Distribution — bar chart + delay bucket chart
6. Discount vs Profit Scatter Plot — with reference lines at 0% profit and 20% discount
7. Return Analysis Highlight Table — Category × Segment heat map

---

## Filters and Interactions

### Interactive Filters (applied globally across all views):
1. **Region** — Filter by North / South / East / West
2. **Category** — Filter by Furniture / Office Supplies / Technology
3. **Customer Segment** — Filter by Consumer / Corporate / Home Office
4. **Order Date Range** — Date range slider (Jan 2024 – Dec 2025)
5. **Ship Mode** — Filter by all four shipping modes
6. **Campaign Channel** — Filter by Organic / Paid / Social / Email / Referral

### Dashboard Actions:
- **Filter Action:** Clicking a region in the map filters all other charts to that region
- **Highlight Action:** Hovering over a category in the profitability chart highlights the same category in the return rate table
- **URL Action:** Clicking a state label opens a tooltip with state-level KPIs

---

## Key Business Insights

1. **Technology drives 84% of total profit** at an 18.2% margin — the clear profit engine.
2. **Furniture has a 6.9% margin** and 7.7% return rate — structurally underperforming.
3. **Tables and Bookcases have the worst margins** (5.7% each) across all 13 sub-categories.
4. **Discounts above 30% generate net losses** (-4.4% average margin on 64 orders).
5. **The South region leads in sales (₹6.47 Cr) and profit (₹1.00 Cr).**
6. **Rajasthan is the top-performing state** at ₹2.08 Cr in sales.
7. **Home Office has the highest return rate** (5.7%) — 3× Technology's rate.
8. **Organic channel generates 40% of all orders** and 40% of total profit.
9. **Standard Class handles 58% of orders** at 4.7-day average delivery.
10. **April is the weakest revenue month** in both 2024 and 2025.

---

## Dashboard Story Summary

The business is profitable and well-diversified across regions and customer segments, with Technology as the clear profit driver (84% of total profit). However, three structural risks need leadership attention:

1. **Furniture's low margins (6.9%) and high return rate (7.7%)** are compressing blended profitability. Pricing, COGS reduction, and return management are needed.
2. **Deep discounts (30–35%) are generating losses** — a discount policy overhaul with hard caps is required.
3. **April revenue gaps** are recurring and addressable with targeted promotional campaigns.

Opportunities include expanding in top states (Rajasthan, Telangana, Tamil Nadu), scaling the Email channel, and building a referral incentive program.

---

## Assumptions and Limitations

### Assumptions:
- All monetary values are in Indian Rupees (₹).
- `profit = sales - cost` — COGS breakdown is not available; profit is treated as net margin.
- `return_flag = 1` is a binary indicator; no return reason codes are available.
- `delivery_days` is calculated as ship_date − order_date (or an equivalent field already computed).
- Null `campaign_channel` values (24 records) are excluded from channel analysis but included in all other views.
- Null `customer_rating` values (32 records) are excluded from rating averages only.

### Limitations:
- No customer-level LTV data available — repeat purchase analysis is not possible.
- Return reasons are unknown — root cause analysis requires supplementary qualitative data.
- Cost structure is opaque — true margin (after overheads) cannot be calculated.
- City-level granularity is uneven across states, limiting reliable city-level decisions.
- No competitor or market share data for contextualising performance.

---

## Screenshots Included

| File | Description |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard with all views and filters |
| `screenshots/sales_trend_view.png` | Monthly sales and profit trend (2024–2025) |
| `screenshots/regional_performance_view.png` | State-level map and regional bar chart |
| `screenshots/category_profitability_view.png` | Sub-category margin bar chart and highlight table |
| `screenshots/filter_interaction_view.png` | Dashboard with Region filter applied (e.g., South region) |

---

## Repository Structure

```
part4_tableau_dashboard/
├── data/
│   └── dashboard_sales_data.xlsx       ← Source dataset
├── tableau/
│   └── executive_dashboard.twbx        ← Tableau packaged workbook
├── outputs/
│   ├── dashboard_story.md              ← Executive narrative for leadership
│   ├── business_insights.md            ← 10 data-backed insights with actions
│   └── chart_selection_justification.md ← Design rationale for each chart
├── screenshots/
│   ├── full_dashboard.png
│   ├── sales_trend_view.png
│   ├── regional_performance_view.png
│   ├── category_profitability_view.png
│   └── filter_interaction_view.png
└── README.md                           ← This file
```
