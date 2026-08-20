# Case Study: Apex Logistics – Last-Mile Delivery Analytics

## 1. Executive Summary & Business Context

- **Course**: BUS 324 – Introduction to Business Analytics
- **Unit**: Data Visualization & Descriptive Analytics (Weeks 3 & 4)
- **Domain**: Last-Mile Logistics & Supply Chain Operations
- **Key Persona**: **Elena Rostova**, Director of Operations at *Apex Logistics*
- **Student Role**: Junior Data Analytics Intern reporting directly to Elena
- **Business Context**:
	Apex Logistics is a regional last-mile delivery provider operating four
	major fulfillment hubs (North, South, East, and West). Over the past
	quarter, the company has faced mounting challenges: volatile delivery
	turnaround times, inconsistent Customer Satisfaction (CSAT) ratings, and
	rising fuel and maintenance expenditures.
	
	Simultaneously, executive leadership and the Board of Directors are
	actively debating the company's multi-million-dollar **Green Transition
	Strategy**—a proposal to retire legacy Gas Vans in favor of Electric
	Vans (EVs) and urban Bike Couriers.
	
	The Board of Directors convenes in two weeks. CEO Sofia Mendoza has tasked
	Elena with delivering a comprehensive data-driven operational review.
	Elena has brought you on board to turn 1,000 raw point-of-sale delivery
	records into clear visual stories, diagnostic distribution charts, and
	an executive-ready operations dashboard.

- **Unit of Analysis**: **A Single Delivery Event** (`Delivery_ID`). Every row
  in the dataset represents one distinct completed delivery transaction.

---

## 2. Pedagogical Objectives & Excel Tool Alignment

By completing this case study, students will master:

- **PivotTables & Crosstabulations (Module 1)**:
	- Constructing 2-way frequency crosstabs for categorical variables.
	- Grouping continuous numeric metrics into custom bins (5-mile intervals).
	- Computing relative frequencies using `% of Row Total` (regional fleet
	  adoption) and `% of Column Total` (fleet distance profiles).
	- Aggregating non-count metrics (Average Delivery Time).
- **Standard Bar & Column Charts (Module 2)**:
	- Building standalone Column and Bar charts from aggregated summary tables.
	- Choosing optimal chart orientations for categorical labels.
- **Distribution & Spread Analytics (Module 3)**:
	- Constructing single Box Plots to evaluate fleet spread, median, IQR,
	  and outlier dots.
	- Creating comparative side-by-side Box Plots across vehicle categories.
- **Bivariate Relationships & Time-Series Trends (Module 4)**:
	- Creating Scatter Plots with linear trendlines to evaluate cost curves.
	- Constructing Single Line Charts to monitor daily delivery duration
	  stability.
- **Dynamic Multi-Series PivotCharts (Module 5)**:
	- Generating multi-line PivotCharts directly from raw transaction records.
	- Building stacked and grouped column PivotCharts for delay root causes.
- **Executive Operations Dashboard (Module 6)**:
	- Designing high-impact KPI summary cards for executive metrics.
	- Assembling charts and KPI cards into a professional 1-page grid layout.

---

## 3. Interactive Weblet Architecture & Pedagogical Flow

This case study is engineered for delivery via an interactive web application
(weblet, modeled after [week2-desc-stats.vercel.app](https://week2-desc-stats.vercel.app/)).
Each sub-step follows a strict **3-Phase Pedagogical Sequence**:

```
+-------------------------------------------------------------------------+
| Phase 1: Business Challenge & Action                                    |
|   - Guiding Business Question (Elena's operational dilemma)             |
|   - Step-by-Step Excel Action (Building the table or chart)             |
+-------------------------------------------------------------------------+
                                    |
                                    v
+-------------------------------------------------------------------------+
| Phase 2: Verification Checkpoint                                        |
|   - Multiple-Choice Question (Validates numerical/visual accuracy)      |
|   - System gates progression until correct answer is confirmed          |
+-------------------------------------------------------------------------+
                                    |
                        (Correct Answer Verified)
                                    |
                                    v
+-------------------------------------------------------------------------+
| Phase 3: Post-Verification Insight Debrief & Critical Thinking          |
|   - Revealed dynamically upon verification                              |
|   - Unpacks analytical traps, managerial interpretations, & Food for    |
|     Thought to prepare students for the Module 6 Strategy Memo          |
+-------------------------------------------------------------------------+
```

```
Module 1: PivotTables  --> Module 2: Standard Bar Charts --> Module 3: Distribution Spread
(Crosstabs & Averages)     (From Aggregated Summaries)      (Single & Multi Box Plots)
                                                                       |
Module 6: Exec Dashboard <-- Module 5: Dynamic PivotCharts <-- Module 4: Bivariate & Trends
(KPIs & Grid Layout)       (Multi-Line & Column)            (Scatter & Single Line)
```

---

## Module 1: Operational Summaries & Crosstabulations

### Business Situation & Elena's Briefing

> **Elena's Memo to You:**
> *"Welcome to the team! Before we jump into high-level visuals for the
> Board, we need to understand the baseline structure of our operations.
> I have several pressing questions: How is our delivery workload divided
> across our four regional hubs? Which regional hub has embraced our Green
> Transition the most by utilizing Electric Vans? And what do our typical
> delivery distances and customer ratings look like? Let's start by building
> clean PivotTables from our raw transaction records."*

### Learning Objectives
- Master 2-way frequency crosstabulations in Excel.
- Convert raw observation counts into row proportions to normalize comparisons.
- Change aggregation functions from `SUM` / `COUNT` to `AVERAGE`.
- Group continuous variables into discrete analytical intervals.

### Scaffolded Tasks & Step-by-Step Instructions

- **Step 1.1: Regional Fleet Distribution (2-Way Crosstabulation)**
	- **Guiding Business Question**: *How is our total delivery volume divided
	  across regional hubs, and how are vehicle types allocated within each
	  region?*
	- **Excel Action**:
		- Insert a PivotTable on a new worksheet.
		- Place `Warehouse_Region` in Rows and `Vehicle_Type` in Columns.
		- Add `Delivery_ID` to Values as `Count of Delivery_ID`.
	- **Verification Checkpoint**:
		- *Question*: How many Bike Courier deliveries were completed in the
		  North regional hub?
			- A) 34
			- B) 58 (Correct)
			- C) 83
			- D) 133
	- **Phase 3 Debrief (Critical Thinking)**: Notice the large difference in
	  total delivery volume between the West hub (~390 deliveries) and the
	  South hub (~138 deliveries). Keep this volume disparity in mind for the
	  next step when comparing EV adoption across regions.

- **Step 1.2: Normalizing Adoption Rates (% of Row Total)**
	- **Guiding Business Question**: *Which regional hub utilizes Electric Vans
	  (EVs) the most?*
	- **The Analytical Trap**: If you look only at the raw counts from Step 1.1,
	  you might see ~152 EV deliveries in the West and only ~84 in the South,
	  and conclude that the West is the clear leader. But is that a fair
	  comparison when the West hub is nearly three times larger overall?
	- **Excel Action**:
		- Duplicate your crosstabulation from Step 1.1 on the same sheet.
		- In Value Field Settings, change `Show Values As` to `% of Row Total`.
	- **Verification Checkpoint**:
		- *Question*: What percentage of deliveries in the South region were
		  handled by Electric Vans (EVs)?
			- A) 38.97%
			- B) 43.46%
			- C) 60.87% (Correct)
			- D) 23.19%
	- **Phase 3 Debrief (Critical Thinking)**: Notice how row percentages
	  normalize comparisons across unequal group sizes. While West has more
	  total EVs in absolute terms, the South hub dedicates nearly 61% of its
	  operations to EVs, making it the relative leader in green fleet adoption.

- **Step 1.3: Aggregating Averages (Average Delivery Duration)**
	- **Guiding Business Question**: *How do average delivery durations compare
	  across regional hubs and vehicle types? Which vehicle fleet completes
	  orders in the shortest time, and which hub experiences the longest
	  average delivery durations?*
	- **Excel Action**:
		- Build a PivotTable with `Warehouse_Region` in Rows and `Vehicle_Type`
		  in Columns.
		- Add `Delivery_Time_Mins` to Values.
		- Change Value Field Settings from `Sum` to `Average`.
	- **Verification Checkpoint**:
		- *Question*: What is the average delivery time (in minutes) for EV Vans
		  operating out of the East region?
			- A) 16.44 mins
			- B) 31.12 mins (Correct)
			- C) 35.56 mins
			- D) 55.64 mins
	- **Phase 3 Debrief (Critical Thinking)**: Notice the baseline turnaround
	  hierarchy across fleets (Bike Couriers fastest for local trips, Gas Vans
	  longest for regional routes). Does this table give us enough information
	  about extreme delay risks, or does looking only at averages conceal
	  critical variability?

- **Step 1.4: Route Distance Distribution by Fleet (% of Column Total)**
	- **Guiding Business Question**: *What proportion of each vehicle fleet's
	  trips fall into different distance brackets? How do vehicle operating
	  ranges constrain and dictate route assignments?*
	- **Excel Action**:
		- Create a new PivotTable with `Distance_Miles` in Rows, `Vehicle_Type`
		  in Columns, and `Delivery_ID` (Count) in Values.
		- Right-click any distance value in the row labels and select `Group...`.
		- Set the grouping parameters: Start at `0`, End at `40`, by `5`.
		- In Value Field Settings, change `Show Values As` to `% of Column Total`.
	- **Verification Checkpoint**:
		- *Question*: What percentage of EV Van deliveries fall in the 5 to 10
		  mile distance bracket?
			- A) 17.85%
			- B) 34.55% (Correct)
			- C) 31.12%
			- D) 16.48%
	- **Phase 3 Debrief (Critical Thinking)**: Notice how column percentages
	  evaluate each fleet's unique operating profile:
		- **Bike Couriers**: 100% concentrated in the `0-5` mile bracket.
		- **EV Vans**: Concentrated in short-to-moderate trips (under 20 miles).
		- **Gas Vans**: Broadly distributed across long routes (up to 35 miles),
		  though some still run short routes where EVs could replace them.

---

## Module 2: Categorical Comparison with Standard Bar & Column Charts

### Business Situation & Elena's Briefing

> **Elena's Memo to You:**
> *"The Board of Directors will not read through dense summary tables during a
> fast-paced 20-minute strategy session. We must translate our Module 1
> findings into intuitive standalone charts. Specifically: Which warehouse
> hub has the longest average delivery duration? And what is the overall
> fleet volume share across vehicle types? Let's build clean, executive-grade
> Column and Bar charts from our summary tables."*

### Learning Objectives
- Create standard Excel Column and Bar charts from summary tables.
- Distinguish when to use vertical column charts versus horizontal bar charts.
- Apply clean data labels, axis titles, and sorting to improve readability.

### Scaffolded Tasks & Step-by-Step Instructions

- **Step 2.1: Regional Delivery Duration Comparison (Column Chart)**
	- **Guiding Business Question**: *How large is the average delivery
	  duration gap across our four regional fulfillment hubs?*
	- **Excel Action**:
		- Copy the summary table of `Average Delivery Time` by `Warehouse_Region`
		  into a new worksheet.
		- Insert a standard 2D Column Chart.
		- Format the visual: Add a clear chart title, remove unnecessary
		  gridlines, and add data labels showing the average minutes.
	- **Verification Checkpoint**:
		- *Question*: Between the East and North regional hubs, which one
		  achieved shorter delivery times on average?
			- A) East (Correct)
			- B) North
	- **Phase 3 Debrief (Critical Thinking)**: Notice that the East hub averages
	  37.57 mins while North averages 41.41 mins—a gap of nearly 4 minutes.
	  While all hubs look fairly comparable around the 30-40 min mark on
	  average, this sets up the need to investigate outlier delays in Module 3.

- **Step 2.2: Fleet Volume Breakdown (Horizontal Bar Chart)**
	- **Guiding Business Question**: *How is our total delivery volume
	  distributed across our three vehicle types?*
	- **Excel Action**:
		- In your PivotTable of delivery volume by `Vehicle_Type`, right-click
		  any count value $\rightarrow$ select `Sort` $\rightarrow$ `Sort
		  Smallest to Largest` (reverse numerical sorting).
		- Insert a standard 2D Horizontal Bar Chart from the sorted table.
	- **Verification Checkpoint**:
		- *Question*: What is the total delivery volume completed by Electric
		  Vans (EVs) across the fleet?
			- A) 197 deliveries
			- B) 366 deliveries
			- C) 437 deliveries (Correct)
			- D) 1,000 deliveries
	- **Phase 3 Debrief (Critical Thinking)**: Notice that sorting the
	  PivotTable Smallest to Largest causes Excel to place the highest-volume
	  fleet (`EV Van`) at the very top of the horizontal bar chart. Horizontal
	  bar charts are ideal for displaying category rankings with long labels.

---

## Module 3: Delivery Distributions & Outlier Spotting

### Business Situation & Elena's Briefing

> **Elena's Memo to You:**
> *"Looking at average delivery times alone is risky. A hub might report a
> respectable 28-minute average, but if 10% of customers wait over 90 minutes,
> our reputation suffers. I have been receiving severe customer complaints
> regarding extreme delays. We need to look beyond the mean and examine the
> full distribution spread, quartiles, and extreme delay outliers using Box
> Plots."*

### Learning Objectives
- Construct single and multi-series Box and Whisker plots in Excel.
- Identify Median, Q1 (25th percentile), Q3 (75th percentile), and IQR.
- Detect and diagnose isolated delay outliers (points beyond whiskers).

### Scaffolded Tasks & Step-by-Step Instructions

- **Step 3.1: Overall Fleet Delivery Spread (Single Box Plot)**
	- **Guiding Business Question**: *What is the true spread and typical
	  delivery time across our fleet, and do we have extreme delay outliers?*
	- **Excel Action**:
		- Select the entire `Delivery_Time_Mins` column from the raw dataset.
		- Insert a Box and Whisker chart on a new sheet.
		- Identify the Median line, the box boundaries (Q1 and Q3), the whiskers,
		  and the isolated outlier dots.
	- **Verification Checkpoint**:
		- *Question*: What is the overall fleet median delivery time in minutes?
			- A) 20.0 mins
			- B) 35.0 mins (Correct)
			- C) 40.2 mins
			- D) 55.0 mins
	- **Phase 3 Debrief (Critical Thinking)**: Notice the isolated outlier dots
	  at the top of the box plot (88-125 mins). While the median is 35 mins,
	  these long-tail outliers explain the surge in customer escalations.

- **Step 3.2: Comparative Fleet Variability (Multiple Box Plots)**
	- **Guiding Business Question**: *How does delivery time variability and
	  consistency differ between Bike Couriers, Electric Vans, and Gas Vans?*
	- **Excel Action**:
		- Select both `Vehicle_Type` and `Delivery_Time_Mins` columns together.
		- Insert side-by-side Box and Whisker charts comparing all three fleets.
	- **Verification Checkpoint**:
		- *Question*: In the comparative box plot, which vehicle fleet exhibits
		  the tightest delivery time predictability (smallest IQR)?
			- A) Bike Courier (Correct)
			- B) EV Van
			- C) Gas Van
			- D) All fleets have equal spread
	- **Phase 3 Debrief (Critical Thinking)**: Bike Couriers have a narrow IQR
	  (~7 mins), while Gas Vans exhibit wide spread (IQR ~28 mins) and extreme
	  outliers up to 125 mins due to long-haul transit risks.

- **Step 3.3: Delay Root Cause Breakdown (Frequency & Speed Impact)**
	- **Guiding Business Question**: *What is causing these outliers? Across our
	  entire delivery operation, what are the most frequent causes of delays,
	  and how severely does each delay reason impact average delivery times?*
	- **Excel Action**:
		- Insert a PivotTable with `Delay_Reason` in Rows.
		- Add `Delivery_ID` to Values as `Count of Delivery_ID`.
		- Add `Delivery_Time_Mins` to Values and change its aggregation to
		  `Average`.
	- **Verification Checkpoint**:
		- *Question*: Across all deliveries in the dataset where an operational
		  delay occurred (excluding 'None'), which delay reason occurred most
		  frequently?
			- A) Traffic (104 deliveries) (Correct)
			- B) Weather (72 deliveries)
			- C) Package Issue (41 deliveries)
			- D) Vehicle Breakdown (0 deliveries)
	- **Phase 3 Debrief (Critical Thinking)**: When Traffic is cited, average
	  delivery duration surges from 33 mins to nearly 65 mins, confirming that
	  road congestion is both the most common and most damaging delay driver.

---

## Module 4: Bivariate Relationships & Time-Series Trends

### Business Situation & Elena's Briefing

> **Elena's Memo to You:**
> *"To optimize our delivery routing and improve customer arrival estimates,
> we need to understand how delivery duration scales with travel distance.
> Is there a strong, predictable linear relationship between how far our
> drivers travel and how long a delivery takes? Furthermore, leadership wants
> to verify whether our network-wide delivery times have remained stable
> across our 30-day monitoring window or if specific calendar days suffered
> operational bottlenecks."*

### Learning Objectives
- Build Scatter Plots and fit visual linear trendlines to evaluate bivariate
  relationships.
- Compute and interpret the Correlation Coefficient using Excel's `=CORREL`
  function.
- Create single-series Line Charts to track time-series metrics over 30 days.

### Scaffolded Tasks & Step-by-Step Instructions

- **Step 4.1: Trip Distance vs. Delivery Duration (Scatter Plot & Correlation)**
	- **Guiding Business Question**: *How strongly is delivery route distance
	  associated with total delivery duration across our fleet?*
	- **Excel Action**:
		- Select `Distance_Miles` (X-axis) and `Delivery_Time_Mins` (Y-axis).
		- Insert a standard Scatter Plot on a new worksheet.
		- Add a linear trendline to visualize the directional relationship.
		- In an adjacent cell, calculate the correlation coefficient using the
		  formula `=CORREL(Distance_Miles, Delivery_Time_Mins)`.
	- **Verification Checkpoint**:
		- *Question*: What is the approximate correlation coefficient (\(r\))
		  between route distance (`Distance_Miles`) and delivery time
		  (`Delivery_Time_Mins`)?
			- A) -0.76 (Strong negative)
			- B) 0.00 (No correlation)
			- C) +0.76 (Strong positive) (Correct)
			- D) +0.20 (Weak positive)
	- **Phase 3 Debrief (Critical Thinking)**: A correlation of +0.76 confirms a
	  strong positive linear association between mileage and delivery time.
	  Points scattered high above the trendline represent localized traffic and
	  weather disruptions.

- **Step 4.2: 30-Day Daily Delivery Time Tracking (Line Chart)**
	- **Guiding Business Question**: *Have our daily average delivery durations
	  remained stable over the past month, or are there visible operational
	  bottlenecks?*
	- **Excel Action**:
		- Build a summary table aggregating daily `Average Delivery Time` across
		  the 30-day date range (`2026-02-01` to `2026-03-02`).
		- Insert a standard 2D Line Chart showing day-by-day delivery times.
	- **Verification Checkpoint**:
		- *Question*: In the Step 4.2 line chart, what does each plotted point
		  along the line represent?
			- A) The total volume of deliveries completed each hour
			- B) The average delivery duration (in minutes) for that specific
			  day (Correct)
			- C) The cumulative fuel cost accumulated over the 30-day period
			- D) The percentage of on-time deliveries per week
	- **Phase 3 Debrief (Critical Thinking)**: Tracking daily averages across
	  the 30-day window reveals day-to-day delivery stability and highlights
	  specific calendar spikes where network performance degraded.

---

## Module 5: Dynamic Multi-Series PivotCharts

### Business Situation & Elena's Briefing

> **Elena's Memo to You:**
> *"Static summary charts are great for reports, but leadership wants dynamic
> visuals that update automatically when new data is loaded. PivotCharts give
> us powerful multi-category views directly from raw data. Let's construct a
> multi-line trend chart tracking daily delivery durations by fleet type, and
> a stacked column chart diagnosing delay root causes by regional hub."*

### Learning Objectives
- Construct dynamic PivotCharts linked directly to underlying PivotTables.
- Build Multi-Line PivotCharts with date hierarchies and category series.
- Design Stacked and Grouped Column PivotCharts for multi-variable breakdowns.

### Scaffolded Tasks & Step-by-Step Instructions

- **Step 5.1: Multi-Line Daily Fleet Comparison (Delivery Duration & Stability)**
	- **Guiding Business Question**: *How do daily average delivery durations
	  compare across Bike Couriers, EV Vans, and Gas Vans throughout the 30-day
	  period, and which fleet provides the most stable turnaround times?*
	- **Excel Action**:
		- Create a PivotTable on a new worksheet.
		- Place `Date_Time` (grouped by Date) in Rows, `Vehicle_Type` in Columns,
		  and `Average Delivery Time` in Values.
		- Insert a Line PivotChart.
	- **Verification Checkpoint**:
		- *Question*: In the Multi-Line PivotChart, which vehicle fleet
		  maintains the shortest daily average delivery duration on the vast
		  majority of days across the 30-day period?
			- A) Gas Van
			- B) EV Van
			- C) Bike Courier (Correct)
			- D) All fleets are equal
	- **Phase 3 Debrief (Food for Thought)**:
		- *Distinct Operational Tiers*: Gas Vans consistently require the longest
		  durations (50-65 mins), EV Vans maintain a steady middle tier (30-42
		  mins), and Bike Couriers achieve the shortest times (10-25 mins).
		- *Isolated Spikes vs. Fleet Consistency*: Bike Couriers show occasional
		  sharp spikes (Feb 19 & 27) where localized weather jumped durations
		  above 40 mins, while EV Vans demonstrate remarkable day-to-day
		  stability.
		- *Quantifying Relative Variability*: To compare volatility across fleets
		  with different baseline durations, analysts evaluate **relative
		  dispersion** (such as \(\text{CV} = \frac{s}{\bar{x}}\) or the
		  **IQR-to-Median ratio**) rather than raw minutes.

- **Step 5.2: Regional Delay Cause Breakdown (Stacked Column PivotChart)**
	- **Guiding Business Question**: *What are the primary operational root
	  causes of delays in each regional fulfillment hub?*
	- **Excel Action**:
		- Create a PivotTable with `Warehouse_Region` in Rows and `Delay_Reason`
		  in Columns.
		- Add `Delivery_ID` (Count) to Values.
		- Insert a 100% Stacked Column PivotChart and filter out the reason
		  "None" to focus exclusively on delayed deliveries.
	- **Verification Checkpoint**:
		- *Question*: In the West regional hub, what is the single largest
		  identified operational cause of delivery delays?
			- A) Weather
			- B) Traffic (Correct)
			- C) Package Issue
			- D) Vehicle Breakdown
	- **Phase 3 Debrief (Critical Thinking)**: The West hub suffers primarily
	  from severe Traffic congestion (~50% of delays), whereas the North hub
	  experiences higher Weather disruptions. Elena can use this to tailor
	  regional operational interventions.

---

## Module 6: Executive Board Operations Dashboard

### Business Situation & Elena's Briefing

> **Elena's Memo to You:**
> *"The Board meeting is tomorrow morning. We need to assemble our visual
> discoveries and top-line operational KPIs into a single, polished executive
> dashboard. When CEO Sofia Mendoza and the Directors open this workbook, they
> should immediately see our total workload, service level, customer
> satisfaction, and fuel expenditure, backed by our key diagnostic charts."*

### Learning Objectives
- Design executive KPI summary metric cards in Excel.
- Arrange charts and metrics into an aligned visual dashboard grid layout.
- Synthesize quantitative analytics into strategic business recommendations.

### Scaffolded Tasks & Step-by-Step Instructions

- **Step 6.1: High-Impact Executive KPI Cards**
	- **Guiding Business Question**: *What are the four vital high-level metrics
	  that summarize our operational health, service quality, and cost?*
	- **Excel Action**:
		- Create a clean dashboard worksheet.
		- Construct 4 formatted KPI summary cards across the top:
			1. **Total Delivery Volume**: Total completed transactions (`1,000`).
			2. **On-Time Service Level %**: Proportion of deliveries \(\le 45\) mins.
			3. **Customer Satisfaction (CSAT)**: Fleetwide average rating (out of 5.0).
			4. **Total Carbon / Fuel Spend ($)**: Total fleet fuel expenditure.
	- **Verification Checkpoint**:
		- *Question*: What is the fleetwide On-Time Service Level percentage
		  (deliveries \(\le 45\) minutes)?
			- A) 25.4%
			- B) 41.7% (Correct)
			- C) 60.9%
			- D) 85.0%
	- **Phase 3 Debrief (Critical Thinking)**: At 41.7% on-time performance and
	  a 3.47 CSAT score, Apex has substantial room for service improvement,
	  highlighting the urgent need to expand fast, agile EV and bike routes.

- **Step 6.2: Professional Dashboard Grid Assembly**
	- **Guiding Business Question**: *How do we arrange our diagnostic visuals
	  into an intuitive, executive-grade presentation layout?*
	- **Excel Action**:
		- Position the 4 KPI cards across the top row of the dashboard canvas.
		- Arrange four core diagnostic visuals in a balanced 2x2 grid below the
		  KPI cards:
			1. **Top-Left (Where)**: Regional Delivery Duration Column Chart
			   (Module 2).
			2. **Top-Right (Which Fleet)**: Comparative Fleet Duration & Outliers
			   Box Plot (Module 3).
			3. **Bottom-Left (Why / Root Cause)**: Regional Delay Root Cause Mix
			   100% Stacked Column Chart (Module 5).
			4. **Bottom-Right (When / Trend)**: 30-Day Daily Fleet Duration &
			   Stability Multi-Line PivotChart (Module 5).
		- Remove gridlines, apply consistent corporate colors, and format
		  container headers.
	- **Phase 3 Debrief (Design Best Practices)**: Executive dashboards must
	  prioritize visual hierarchy and narrative coherence: top-line summary
	  metrics on top, followed by a 360-degree operational diagnosis below
	  answering **Where** (hub), **Which Fleet** (dispersion), **Why** (root
	  cause), and **When** (time-series stability).

- **Step 6.3: Executive Briefing Memo to Leadership**
	- **Guiding Business Question**: *What concrete strategic recommendations
	  should Elena present to CEO Sofia Mendoza and the Board of Directors?*
	- **Deliverable**: Write a 3-paragraph executive synthesis memo:
		1. **Operational Health**: Volume distribution, delivery duration
		   disparities, and CSAT.
		2. **Fleet Transition Strategy**: The financial and operational case for
		   accelerating EV and Bike Courier deployment.
		3. **Targeted Regional Action Plan**: Specific operational interventions
		   for hubs facing severe traffic or package bottlenecks.

---

## 4. Synthetic Data Schema & Data Dictionary

| Field Name | Data Type | Format / Range | Description & Business Rules |
| :--- | :--- | :--- | :--- |
| `Delivery_ID` | String | `DEL-10001` to `DEL-11000` | Unique delivery transaction identifier. |
| `Date_Time` | Datetime | `YYYY-MM-DD HH:MM` | Timestamps spanning 30 days (`2026-02-01` to `2026-03-02`). |
| `Warehouse_Region` | Categorical | `North`, `South`, `East`, `West` | Regional hub (`38%` West, `28%` North, `20%` East, `14%` South). |
| `Vehicle_Type` | Categorical | `EV Van`, `Gas Van`, `Bike Courier` | Vehicle fleet type (`45%` EV, `35%` Gas, `20%` Bike). |
| `Distance_Miles` | Quantitative | `0.5` to `35.0` miles | Trip distance from hub to destination. |
| `Delivery_Time_Mins` | Quantitative | `8` to `125` minutes | Total elapsed delivery time in minutes. |
| `Fuel_Carbon_Cost_$` | Quantitative | `$0.10` to `$23.00+` | Energy/fuel and carbon cost for the trip. |
| `Customer_Rating_CSAT` | Quantitative | Integer `1` to `5` | Customer rating based on delivery speed. |
| `Delay_Reason` | Categorical | `None`, `Traffic`, `Weather`, `Package Issue` | Root cause recorded for operational delays. |
