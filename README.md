# ✈️ Airline Revenue & Profitability Dashboard

An interactive, two-page business intelligence dashboard analyzing route-level profitability, cost structure, and operational efficiency for an airline network operating out of Dubai (DXB). Built to answer the kind of questions a Revenue Management or Business Analytics team would ask.

---

## 📌 Project Overview

This project analyzes **7,974 flight records** across **30 routes** and **6 aircraft types** to uncover where an airline is making money, where it is losing money, and why. Instead of just displaying numbers, the dashboard is built to answer 13 real business questions that a Finance or Network Planning team would raise — including a genuine data-driven finding where the expected pattern (high demand, low load factor) simply did not exist in the data.

The dashboard is fully interactive: every KPI and chart recalculates live when you filter by Month, Season, Aircraft Type, Demand Level, or Route — similar to slicers in Power BI.

---

## 📸 Screenshots

**Page 1 — Executive Overview**
[Executive Overview](dashboard-executive-overview(1).png)

**Page 2 — Route & Aircraft Performance**
[Route & Aircraft Performance](dashboard-route-aircraft-performance.png)

---

## 🎯 Business Questions Answered

1. Total Revenue, Total Cost, Total Profit, Profit Margin (overall KPIs)
2. Total Revenue trend by month/season
3. Ticket Revenue vs Ancillary Revenue split
4. Total Cost breakdown by category (Fuel, Crew, Maintenance, etc.)
5. Fuel Cost as % of Total Cost
6. Top 10 most profitable routes
7. Bottom 10 loss-making routes
8. Profit Margin by route
9. Profit Margin by aircraft type
10. Average Load Factor by route (vs. an 80% target)
11. Load Factor by aircraft type
12. High-Demand but Low-Load-Factor routes (utilization gap check)
13. High-Load-Factor but Low-Profit routes (cost-vs-revenue problem)
14. Month-over-month profit trend

---

## 🧹 Data Cleaning & Modeling

Real-world data is never perfectly clean, and this dataset was no exception:

| Issue Found | Rows Affected | How It Was Fixed |
|---|---|---|
| Missing `Ancillary_Revenue` | 271 | Recalculated as `Total_Revenue − Ticket_Revenue` (exact, not estimated) |
| Missing `Catering_Cost` | 265 | Recalculated as `Total_Cost − sum(other 13 cost fields)` |
| Missing `Handling_Cost` | 256 | Recalculated as `Total_Cost − sum(other 13 cost fields)` |
| Duplicate flights | 0 found | Verified on Flight_Number + Flight_Date |

Rather than dropping rows or filling with averages (which would distort the numbers), every missing value was **derived from the dataset's own internal formulas** — a more accurate approach for financial data.

**Data modeling:**
- Built a calendar/date table from `Flight_Date` (Month, Month Name, Quarter) to support time-based aggregation.
- Aggregated flight-level data into Route-level and Aircraft-level summary tables for the performance charts.

---

## 📊 Key Insights

- **Total Profit Margin: 24.3%** across the network — a healthy baseline, but it varies sharply by route.
- **Fuel is the single largest cost category**, at ~20% of total cost — as expected for an airline, and a strong point for cost-control discussion.
- **No "high demand, low load factor" routes exist** in this network — every high-demand route already runs above the median load factor. This is a genuine data finding, not an assumption, and shows the value of checking a hypothesis before presenting it as an insight.
- **Several high-load-factor routes still run at low or negative margin** (e.g. DXB–BAH, DXB–DOH, DXB–KWI, DXB–LHR) — these routes are full, but not profitable, pointing to a **cost problem, not a demand problem**.
- Wide-body aircraft show a different margin profile than narrow-body aircraft, useful for fleet allocation discussions.

---

## 🖥️ Dashboard Features

- **Page 1 — Executive Overview:** KPI summary, revenue trend, revenue mix, cost breakdown, fuel cost gauge, month-over-month profit trend.
- **Page 2 — Route & Aircraft Performance:** Top/bottom 10 routes, margin and load factor by route and aircraft, and two diagnostic scatter plots for demand-utilization and load-vs-margin analysis.
- **Live filters (slicers):** Month, Season, Aircraft Type, Demand Level, and a searchable Route filter — all charts and KPIs update instantly.
- **One-screen layout:** each page is sized to fit a standard laptop screen without long scrolling, similar to a Power BI report canvas.
- **Dynamic insight notes:** the two diagnostic charts explain their own finding in plain language, and update automatically as filters change.

---

## 🛠️ Tools & Tech Stack

| Purpose | Tool |
|---|---|
| Data cleaning & aggregation | Python (Pandas) |
| Dashboard front-end | HTML, CSS, JavaScript |
| Charting | Chart.js |
| Design | Custom navy/sky-blue theme, styled to match a corporate Power BI report |

> This project intentionally mirrors a Power BI-style report using a code-based (HTML/JS) build, to demonstrate both dashboarding logic and front-end/data-handling skills.

---

---

## ▶️ How to View

1. Download `airline_dashboard.html`
2. Open it in any modern browser (Chrome, Edge, Firefox) with an internet connection (loads Chart.js and fonts from a CDN)
3. Use the filter bar at the top to explore the data — try selecting a single Route or Season to see everything update live

---

## 📈 Dataset

- **Source:** Simulated airline operations dataset, DXB network
- **Size:** 7,974 flight records
- **Columns:** 31, including revenue, cost breakdown (14 categories), load factor, demand level, and route/aircraft metadata

---

## 🙋 About This Project

Built as part of an independent Data Analytics portfolio, focused on translating raw operational data into business-ready insights. This project follows the same structure as the retail, real estate, banking, and logistics dashboards in this portfolio — each one answers real business questions rather than just displaying charts.

**Skills demonstrated:** data cleaning & validation, business question framing, KPI design, interactive dashboard development, and clear data storytelling.

---

⭐ If you found this project useful, consider giving it a star!
