# 🪐 OmniChain : Enterprise Global Logistics & Telemetry Cockpit

![Power BI](https://img.shields.io/badge/PowerBI-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0072C6?style=for-the-badge&logo=Microsoft&logoColor=white)
![Data Architecture](https://img.shields.io/badge/Architecture-17--Table_Star_Schema-0D9488?style=for-the-badge)
![UI/UX](https://img.shields.io/badge/UX-Decoupled_Z--Layer-34D399?style=for-the-badge)

> *"Most enterprise dashboards fail because they try to shove fifty different metrics into a single chaotic viewport. OmniChain decouples data density from the C-Suite UX."*

An enterprise-grade business intelligence platform built to monitor **$4.37 Billion** in global gross merchandise volume. Engineered from the ground up to solve the three major choke points of legacy corporate reporting: multi-page horizontal sprawl, unformatted 9-digit cognitive overload, and slicer-lock during deep SKU drill-throughs.

| Telemetry Vector | Operating Parameter |
| :--- | :--- |
| **Gross Financial Volume** | `$4.37 Billion USD` |
| **Active Inventory Granularity** | `500 Master SKUs` |
| **Surface Fleet Tracking** | `500 Deployed Assets` |
| **Human Capital Audited** | `2,000 Active Personnel` |
| **Underlying Engine** | `17-Table Star Schema` |

---

## 🏛️ The 4-Tier Cockpit Anatomy

Rather than forcing stakeholders to hunt through standard horizontal page pagination, the model is segmented into four dedicated, high-definition executive hubs:

### 1. Executive Sales (`Exec1_Global Summary`)
* **The Mission:** Top-level financial velocity and high-roller Pareto distribution.
* **Engine Logic:** Features dynamic DAX tokenization to automatically isolate peak revenue inflection points (e.g., flagging July's **$373.0M** peak without requiring manual trendline hover). 
* **Sub-Routing:** Instantaneous, zero-lag internal bookmark snaps to `Exec2_Products` (SKU profit-margin scatters) and `Exec4_Whale Tracking` (Tier-1 enterprise account retention).

### 2. Supply Chain Hub (`SC1_Network Capacity`)
* **The Mission:** Warehouse throughput verification and bottleneck forecasting.
* **Engine Logic:** Incorporates active `Stockout Risk` modeling. Indexes real-time warehouse inventory against trailing average daily sales velocity to isolate critical stockout windows before assembly line failure (e.g., catching the Aerospace division at a 91% Q3 stockout probability 14 days pre-impact).

### 3. Fleet & Logistics Hub (`L2_Route Efficiency`)
* **The Mission:** Asset physical decay and fuel-burn isolation.
* **Engine Logic:** Employs a dynamic DAX Weight Capacity parameter slider (`< 3,500kg`). Instantly isolates lightweight commercial vans operating in the semi-truck fuel-burn stratosphere, translating raw GPS scatter plots into immediate maintenance work orders.

### 4. Human Resources Hub (`HR2_Compensation`)
* **The Mission:** Headcount optimization and payroll bloat auditing.
* **Engine Logic:** Driven by an interactive Base Salary Tier slicer (`> $100,000`). Proves structural labor concentration instantly by collapsing visible headcount from 2,000 down to 480 while retaining **$195M (60%)** of the gross cash payroll.

---

## ⚡ Interface & UX Engineering

To achieve a native "SaaS desktop application" feel inside the restrictive web browser sandbox, the UI relies on three strict architectural overrides:

* **The Immortal Monolith (`SYS_Navbar`):** A permanent `52px` left-anchored navigation rail poured strictly onto Z-Layer 0. Completely decoupled from page bookmarking to guarantee 100% persistent global state as the user travels through the sub-modules.
* **The Flyout Slicer Tray (`PANEL_FilterTray`):** Re-anchored to Canvas coordinate `X: 175px`. Triggered via an un-indexed `Data: OFF` bookmark toggle, allowing executives to stack complex regional and temporal filters without kidnapping the primary UI or resetting active drill-down states.
* **The Off-White Depth Lift:** Canvas wallpaper hard-coded to `#F1F5F9` (Slate Off-White) at `0%` transparency against `#FFFFFF` visual containers, utilizing human optical contrast to physically "lift" data cards off the monitor.

---

## 🧬 Core DAX Infrastructure

```dax
// 1. Automated Widescreen Peak Revenue Tokenizer
Peak_Revenue_Token = 
VAR __MaxMonthVal = MAXX(VALUES('D_Time'[MonthShort]), CALCULATE(SUM('F_Sales'[Revenue])))
VAR __MaxMonthName = CALCULATE(SELECTEDVALUE('D_Time'[MonthShort]), FILTER(VALUES('D_Time'[MonthShort]), CALCULATE(SUM('F_Sales'[Revenue])) = __MaxMonthVal))
RETURN
"Peak volume hit $" & FORMAT(__MaxMonthVal, "#,##0.0,,M") & " in " & __MaxMonthName


// 2. Dynamic Predictive Stockout Index
Stockout_Risk_Flag = 
VAR __CurrentStock = SUM('F_Inventory'[UnitsOnHand])
VAR __DailyVelocity = CALCULATE(AVERAGE('F_Sales'[Quantity]), ALLEXCEPT('D_Products', 'D_Products'[SKU]))
VAR __RunwayDays = DIVIDE(__CurrentStock, __DailyVelocity, 999)
RETURN
IF(__RunwayDays <= 14, "🔴 CRITICAL (< 14 Days)", "🟢 STABLE")


// 3. Widescreen Telemetry Sanity Stamp
Data_Timestamp = 
"BASE ONLINE // TELEMETRY LIVE AS OF: " & UPPER(FORMAT(LASTDATE('D_Time'[Date]), "MMM DD, YYYY"))
