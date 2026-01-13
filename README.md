# E-commerce Customer Value Segmentation (RFM + Deciles)

## 1) Project Overview (business-first)
This project turns raw e-commerce transactions into an **actionable customer value hierarchy**.  
It identifies **which customers and segments drive revenue**, **who is at risk of churn**, and **how to prioritise marketing spend** using correct RFM scoring and customer decile ranking.

The output is designed for **decision-making**, not just analysis:
- Who to retain (protect revenue)
- Who to grow (incremental uplift)
- Who to win back (cost-efficient reactivation)
- How to allocate marketing budget defensibly

---

## 2) Business Problem & Why It Matters
E-commerce revenue is rarely evenly distributed. In most businesses, **a small share of customers generates the majority of revenue**, while large parts of the base deliver minimal return.

Without structured segmentation:
- Marketing teams overspend on broad discounts
- High-value customers are under-protected
- Win-back efforts target the wrong customers

This project addresses a **retention-first optimisation problem**:
> How can we protect top customers, grow mid-tier value, and minimise wasted spend on low-return segments?

---

## 3) Key Business Questions Answered

### Customer Value
- Who are the highest-value customers by revenue contribution?
- How concentrated is revenue across the customer base (Pareto risk)?

### Retention & Engagement
- Which customers are “at risk” (high past value, long time since last purchase)?
- How large is the dormant pool, and is it commercially worth reactivating?

### Marketing & Budget Allocation
- Which customer deciles generate the most revenue?
- Which segments deserve retention spend vs growth testing vs low-cost win-back?

### Cross-questions explored during EDA
- When do customers buy (hourly / monthly patterns)?
- Which products and countries drive revenue (commercial focus)?

---

## 4) Dataset Overview
Input: a cleaned e-commerce transactions dataset (CSV).

Expected fields (Online Retail–style):
- `InvoiceNo`, `InvoiceDate`, `CustomerID`
- `StockCode`, `Quantity`, `UnitPrice`
- `Country`

Revenue is computed as: Revenue = Quantity × UnitPrice


### Cleaning rules (business-justified)
- Remove cancellations (`InvoiceNo` starting with "C") to avoid invalid revenue
- Remove rows with missing `CustomerID` (cannot segment unidentified customers)
- Remove non-positive quantity or price (returns/free items distort Monetary)
- Deduplicate exact duplicates
- Tag bulk invoices instead of deleting them (possible B2B behaviour)

---

## 5) Methodology (simple, step-by-step)

### Step 1 — Load & Validate
- Load CSV
- Validate required columns
- Parse dates and standardise data types

### Step 2 — Clean & Audit
- Apply business-safe cleaning rules
- Produce a transparent audit showing how many rows were removed by each rule

### Step 3 — Business EDA
- Monthly revenue trend (seasonality / volatility)
- New vs returning customers over time
- Top products by revenue
- Revenue concentration (Pareto curve)
- Bulk invoice tagging (flagged, not deleted)

### Step 4 — RFM Segmentation (customer-level)
Definitions:
- **Recency**: days since last purchase  
- **Frequency**: number of distinct invoices (transactions)  
- **Monetary**: total revenue per customer  

Snapshot date = `max(InvoiceDate) + 1 day`.

Customers are scored and grouped into practical segments:
Champions, Loyal, Needs Attention, At Risk, Dormant, Lost / Low Value.

### Step 5 — Decile Ranking
- Customers ranked into **10 equal-sized deciles by Monetary**
- **D1 = highest-value customers**, D10 = lowest
- For each decile:
  - Customer share
  - Revenue share
  - Transaction share
  - Cumulative revenue contribution

---

## 6) Key Insights & Results (from outputs)

### Revenue concentration
- **Top 10% of customers generate ~61.5% of total revenue**
- **Top 20% generate ~74.7%**
- ~80% of revenue is reached by **Decile 3**

This strongly supports a **retention-first strategy**.

### Customer segments
- Champions & Loyal customers drive disproportionate revenue
- “At Risk / Can’t Lose Them” customers have high historical value but worsening recency
- Dormant and low-value segments contribute minimal revenue despite large customer share

### Decile performance
- Deciles provide a clean, defensible framework for:
  - Budget allocation
  - Campaign targeting
  - Frequency caps and safeguards

---

## 7) Business Metrics Used (and why they matter)
- **Total Revenue** – commercial baseline
- **AOV (Average Order Value)** – bundling and threshold offers
- **Recency / Frequency / Monetary** – value and churn risk
- **Revenue Share by Decile** – prioritisation logic
- **Bulk Invoice Share** – identifies potential wholesale behaviour

---

## 8) Visual Highlights (included in the repository)
- **Monthly revenue trend** – seasonality and volatility
- **New vs returning customers** – retention dynamics
- **Top products by revenue** – merchandising and promotion focus
- **Revenue Pareto curve** – customer concentration risk
- **Revenue share by decile** – budget allocation logic
- **Cumulative revenue by decile** – 80/20 validation
- **RFM segment revenue** – behavioural value breakdown
- **Customer value map** – frequency vs AOV with monetary weight

Each chart answers a **specific business question**, not just descriptive analysis.

---

## 9) Strategic Recommendations

### Retention (D1–D2 / Champions / Loyal)
- Prioritise retention and protection
- Use perks, early access, bundles (not blanket discounts)
- Monitor churn risk via rising recency

### Growth (D3–D6)
- Best segment for controlled growth experiments
- Test cross-sell, personalisation, threshold free shipping
- Optimise for incremental revenue per customer
- New / Promising customers: early-life customers with good recency but limited history. Prioritise onboarding journeys, first-to-second purchase nudges, and low-friction bundles to accelerate habit formation.

### Win-back (At Risk / Can’t Lose Them)
- Triggered win-back based on recency + past value
- Margin-aware offers only

### Dormant / Low Value
- Low-cost reactivation only (email/SMS)
- Suppress chronic non-responders to avoid wasted spend

---

## 10) Why This Project Stands Out
- Production-style pipeline (not a one-off notebook)
- Transparent cleaning audit with business justification
- Correct RFM methodology with snapshot date
- Bulk invoices tagged, not deleted (avoids bias)
- Deciles used as a **budgeting and decision tool**
- Includes decision packs and uplift scenarios, not just charts

---

## 11) Project Outputs (Included)
The following CSV outputs are included for easy review:

- `transactions_clean.csv`
- `rfm_customer_level.csv`
- `segment_summary.csv`
- `decile_summary.csv`
- `decision_pack.csv`
- `uplift_scenarios.csv`

These allow reviewers to inspect results **without running the pipeline**.

---

## 12) How to Run

1) Ensure Python 3.10+ and install dependencies:

