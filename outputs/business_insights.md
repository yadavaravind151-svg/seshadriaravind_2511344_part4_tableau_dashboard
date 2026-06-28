# Business Insights — Executive Sales Dashboard

**Dataset:** dashboard_sales_data.xlsx | **Period:** January 2024 – December 2025 | **Total Orders:** 4,200

---

## Calculated Fields Used

| Calculated Field | Logic | Purpose |
|---|---|---|
| **Profit Margin** | Profit ÷ Sales | Measures profitability efficiency per rupee of revenue |
| **Cost** | Sales − Profit | Determines total cost incurred per order |
| **Average Order Value** | Total Sales ÷ Total Orders | Benchmarks revenue per transaction |
| **Return Rate** | SUM(return_flag = 1) ÷ COUNT(orders) | Tracks product/segment return risk |
| **Shipping Delay Bucket** | IF delivery_days ≤ 1 → "Express"; ≤ 3 → "Fast"; ≤ 5 → "Standard"; ELSE "Slow" | Categorizes fulfillment speed for operational monitoring |

---

## Insight 1 — Sales Trend: Strong Mid-Year Spikes with Year-End Softness

**Observation:** Monthly sales ranged from ₹63 L (August 2024) to ₹108 L (August 2025), with recurring softness in April–August and peaks in September–October and July–August.

**Data Evidence:**
- August 2025: ₹1.09 Cr (highest month)
- April 2025: ₹71.9 L (lowest 2025 month)
- Year-over-year: 2025 trend line is notably stronger than 2024 in H2

**Business Interpretation:** The business shows clear cyclicality. Q1 softness may reflect post-holiday slow spend. Q3 peaks suggest seasonal demand or campaign effectiveness.

**Recommended Action:** Invest in promotional campaigns ahead of April and August to smooth revenue dips. Evaluate whether Q1 underperformance is avoidable with targeted incentives for Corporate and Home Office segments.

---

## Insight 2 — Regional Performance: South Dominates, but All Regions Are Close

**Observation:** The South region leads in both sales (₹6.47 Cr) and profit (₹99.9 L), followed closely by North (₹8.31 L profit) and East (₹7.6 L profit). West trails marginally.

**Data Evidence:**
- South: Sales ₹6.47 Cr | Profit ₹99.9 L | Margin ~15.4%
- North: Sales ₹5.46 Cr | Profit ₹83.1 L
- East: Sales ₹4.89 Cr | Profit ₹76.0 L
- West: Sales ₹4.89 Cr | Profit ₹74.0 L

**Business Interpretation:** Regional spread is relatively balanced, but South's leadership likely reflects stronger Technology adoption or higher-ticket orders in states like Rajasthan and Telangana.

**Recommended Action:** Study what sales tactics or product mix is working in the South and replicate in West and East. Consider targeting underpenetrated states within those regions.

---

## Insight 3 — Category Profitability: Technology Drives 84% of Total Profit

**Observation:** Technology contributes ₹2.80 Cr in profit on ₹15.4 Cr in sales (18.2% margin), while Furniture's margin is just 6.9% and Office Supplies 14.9%.

**Data Evidence:**
- Technology: ₹15.39 Cr sales | ₹2.80 Cr profit | **18.2% margin**
- Office Supplies: ₹1.15 Cr sales | ₹17.1 L profit | **14.9% margin**
- Furniture: ₹5.16 Cr sales | ₹35.6 L profit | **6.9% margin**

**Business Interpretation:** Technology is the profit engine. Furniture generates significant sales volume but very low margins, suggesting potential pricing or cost structure issues — especially in Tables and Bookcases.

**Recommended Action:** Review Furniture pricing strategy. Consider whether deep discounts on Tables and Bookcases are warranted, or whether supplier costs need renegotiation. Protect and grow the Technology category with account-based selling.

---

## Insight 4 — Sub-Category Deep Dive: Tables & Bookcases Are Margin Laggards

**Observation:** Tables (5.7% margin) and Bookcases (5.7% margin) are the weakest performers among all 13 sub-categories. Copiers (18.0%) and Phones (18.5%) lead.

**Data Evidence:**
- Tables: ₹1.29 Cr sales | ₹7.3 L profit | **5.7% margin**
- Bookcases: ₹1.25 Cr sales | ₹7.1 L profit | **5.7% margin**
- Copiers: ₹4.06 Cr sales | ₹73.1 L profit | **18.0% margin**
- Phones: ₹3.84 Cr sales | ₹71.0 L profit | **18.5% margin**

**Business Interpretation:** Furniture sub-categories are dragging category profitability. With margins under 8%, they likely don't cover overheads adequately after returns and discounts.

**Recommended Action:** Raise prices on Tables and Bookcases by 3–5%, reduce discount allowance, and set a floor margin policy. Allocate more marketing budget to Copiers and Phones given their strong unit economics.

---

## Insight 5 — Customer Segment Behavior: Home Office Leads Revenue, Corporate Most Efficient

**Observation:** Home Office generates the most sales (₹7.45 Cr) and profit (₹1.16 Cr). Consumer and Corporate are very similar.

**Data Evidence:**
- Home Office: Sales ₹7.45 Cr | Profit ₹1.16 Cr | Margin ~15.5%
- Consumer: Sales ₹7.19 Cr | Profit ₹1.10 Cr | Margin ~15.3%
- Corporate: Sales ₹7.06 Cr | Profit ₹1.07 Cr | Margin ~15.2%

**Business Interpretation:** All three segments are profitable and well-balanced, suggesting no major structural issue. However, Home Office customers also have the highest return rate (5.7%), which warrants monitoring.

**Recommended Action:** Develop dedicated account management for Home Office to reduce returns (possibly through better product guidance or demos). Run loyalty programs for all three segments to improve retention.

---

## Insight 6 — Discount Impact: High Discounts Destroy Profitability

**Observation:** Orders with 30–35% discounts generate a **negative average profit margin of -4.4%**. Every percentage point of discount above 20% materially erodes profits.

**Data Evidence:**
- Discount 0–5%: Avg margin **18.3%** | Total profit ₹1.92 Cr
- Discount 10–20%: Avg margin **12.5%**
- Discount 20–30%: Avg margin **6.8%**
- Discount 30–35%: Avg margin **-4.4%** | Total profit **-₹1.02 L** (loss)

**Business Interpretation:** Discounting is being used indiscriminately. The bottom discount tier (30–35%) actively destroys value. This policy likely exists for volume or customer retention reasons, but needs clear guardrails.

**Recommended Action:** Implement a discount authorization policy — require manager approval for any discount above 20%. Create a "minimum margin floor" rule of 10% below which no order should be approved without escalation.

---

## Insight 7 — Shipping Performance: Standard Class Carries 58% of Orders with Acceptable Delay

**Observation:** Standard Class is used for 2,435 orders (58%) with an average of 4.7 delivery days. Same Day is fastest (0.4 days) but used for only 241 orders (5.7%).

**Data Evidence:**
- Standard Class: 2,435 orders | 4.7 day avg delivery | ₹1.23 Cr sales
- Second Class: 894 orders | 2.7 days
- First Class: 630 orders | 1.8 days
- Same Day: 241 orders | 0.4 days

**Business Interpretation:** Most customers are served by the most cost-effective shipping mode. However, the 666 orders in the "6+ days" slow bucket may reflect customer dissatisfaction, especially if same-day or first-class was promised.

**Recommended Action:** Set a maximum delivery SLA of 6 days for Standard Class. Investigate the 666 "slow" shipments — if concentrated in specific regions or periods, address logistics partners accordingly.

---

## Insight 8 — Return Patterns: Furniture Has 3× Higher Return Rate Than Technology

**Observation:** Furniture has a return rate of 7.7%, compared to Office Supplies (3.7%) and Technology (3.0%). Home Office segment has the highest return rate (5.7%) among segments.

**Data Evidence:**
- Furniture: 88 returns out of 1,147 orders = **7.7% return rate**
- Office Supplies: 61 returns out of 1,669 orders = **3.7%**
- Technology: 42 returns out of 1,384 orders = **3.0%**
- Home Office segment: 82 returns out of 1,446 = **5.7%**
- East region: **4.9%** return rate (highest by region)

**Business Interpretation:** Furniture returns — likely due to size, quality expectations, or damage in transit — represent a hidden cost. Combined with already-low Furniture margins (6.9%), returns are further compressing profitability in this category.

**Recommended Action:** Introduce product quality checks and better packaging for Furniture. Offer detailed product videos and 3D previews to Home Office buyers to reduce expectation mismatches. Track return reasons explicitly to identify fixable root causes.

---

## Insight 9 — Business Risk: 64 Orders in the High-Discount Loss Zone

**Observation:** 64 orders at 30–35% discount collectively generated a **net loss of ₹1.02 L**. These are not fringe outliers — they represent a systemic pricing policy gap.

**Data Evidence:**
- 64 orders at 30–35% discount
- Average profit margin: -4.4%
- Total profit contribution: -₹1,02,494

**Business Interpretation:** While 64 orders is a small fraction, they signal a control gap in discount management. If unaddressed, this will scale as volume grows.

**Recommended Action:** Immediately identify the sales representatives or channels approving 30–35% discounts. Implement hard discount caps in the order management system, and retrain sales teams on the margin impact of deep discounts.

---

## Insight 10 — Business Opportunity: Rajasthan is the #1 State by Sales

**Observation:** Rajasthan generates ₹2.08 Cr in sales and ₹32.8 L in profit — the top-performing state, followed by Telangana (₹1.49 Cr) and Tamil Nadu (₹1.29 Cr).

**Data Evidence:**
- Rajasthan: ₹2.08 Cr sales | ₹32.8 L profit | ~15.8% margin
- Telangana: ₹1.49 Cr | ₹22.4 L profit
- Tamil Nadu: ₹1.29 Cr | ₹18.4 L profit

**Business Interpretation:** Geographic concentration in top states provides an opportunity for deeper market penetration. Rajasthan's outsized contribution may reflect strong Technology sales and/or a large Corporate customer base.

**Recommended Action:** Assign dedicated regional sales managers to Rajasthan, Telangana, and Tamil Nadu. Run state-specific campaigns. Simultaneously identify low-performing states and evaluate whether to invest or deprioritize.
