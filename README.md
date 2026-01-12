# E-commerce Customer Value Segmentation (RFM + Deciles) — Portfolio Project

## 1) Project Overview (business-first)
This project turns raw e-commerce transactions into an actionable customer hierarchy.  
It identifies which customers and segments drive revenue, who is at risk of churn, and how to prioritise marketing spend using RFM scoring and decile ranking.

The output is designed for decision-making: who to retain, who to grow, who to win back, and how to allocate budget defensibly.

---

## 2) Business Problem & Why It Matters
E-commerce revenue is typically concentrated: a small share of customers often drives a large share of sales.  
Without structured segmentation, marketing teams tend to over-spend on broad discounts and under-invest in retention.

This analysis answers:
- Which customers generate the most revenue and should be protected (VIP focus)?
- Which customers are slipping away and need win-back?
- Which segments deserve incremental budget vs low-cost reactivation?

---

## 3) Key Business Questions Answered
**Customer Value**
- Who are the highest-value customers by revenue contribution?
- How concentrated is revenue across the customer base (Pareto risk)?

**Retention & Engagement**
- Which customers are “at risk” (high past value, long time since last purchase)?
- How large is the dormant pool, and is it worth reactivating?

**Marketing & Budget Allocation**
- Which deciles generate the most revenue and should receive priority spend?
- Which segments should receive retention vs growth vs win-back campaigns?

**Cross-questions explored during EDA**
- When do customers buy (hourly / daily / monthly patterns)?
- Which products and countries drive revenue (commercial focus)?

---

## 4) Dataset Overview
Input: a cleaned e-commerce transactions dataset (CSV).  
Expected fields (Online Retail style):
- `InvoiceNo`, `InvoiceDate`, `CustomerID`, `StockCode`, `Quantity`, `UnitPrice`, `Country`  
Revenue is computed as: `Quantity × UnitPrice`.

**Cleaning rules (business-justified):**
- Remove cancellations (`InvoiceNo` starting with "C") to avoid negative/invalid revenue.
- Remove rows with missing `CustomerID` (cannot segment customers without identity).
- Remove non-positive quantity or price (returns/free items/data errors distort Monetary).

---

## 5) Methodology (simple, step-by-step)
### Step 1 — Load & Validate
- Load CSV
- Validate required columns
- Parse dates and standardise key types

### Step 2 — Clean & Audit
- Remove duplicates, bad dates, cancellations, missing CustomerID, invalid quantity/price
- Produce an audit summary showing how many rows were removed by each rule

### Step 3 — Business EDA
- Revenue trend over time (seasonality / volatility)
- Order value distribution (heavy tails typical in e-commerce)
- Revenue concentration curve (Pareto) to quantify reliance on top customers
- Bulk invoice tagging (flags potential wholesale behaviour instead of deleting it)

### Step 4 — RFM Segmentation (customer-level)
Definitions:
- **Recency**: days since last purchase (relative to snapshot date = max date + 1 day)
- **Frequency**: number of distinct invoices (transactions)
- **Monetary**: total revenue per customer

Customers are scored into 5 bins per metric and grouped into practical segments
(e.g., Champions, Loyal, At Risk, Dormant).

### Step 5 — Decile Ranking
- Customers are ranked into 10 deciles by Monetary (total revenue)
- **D1 = top customers**, D10 = lowest
- For each decile the project quantifies customer share, revenue share, and transaction share

---

## 6) Key Insights & Results (what you should look at)
### Revenue contribution
- Revenue is typically concentrated: the Pareto curve shows how much revenue the top X% of customers generate.
- This is the justification for retention-first strategy and VIP safeguards.

### Customer segments
- Champions / Loyal: protect and retain with high-touch benefits (avoid over-discounting).
- At Risk / Can't Lose Them: highest priority win-back (high historical value).
- Dormant / Low value: low-cost reactivation only; suppress chronic non-responders.

### Decile performance
- Deciles provide a clean hierarchy for budget allocation and targeting rules.
- D1–D2 generally deserve retention spend; D3–D6 are good for controlled growth tests.

---

## 7) Business Metrics Used (and why they matter)
- **Total Revenue**: commercial impact baseline
- **AOV (Average Order Value)**: helps design threshold offers and bundles
- **RFM metrics (R/F/M)**: customer value and churn risk
- **Decile revenue share**: budget allocation and targeting priority
- **Bulk invoice share**: identifies potential B2B/wholesale behaviour

---

## 8) Visual Highlights (what each major chart shows)
- **Revenue trend over time**: seasonality and volatility (planning + forecasting context)
- **Order value distribution**: heavy-tail behaviour (why outliers should be tagged, not deleted)
- **Pareto / concentration curve**: quantifies reliance on top customers
- **Revenue share by decile**: simple rule for prioritising spend
- **Segment summary charts**: where revenue sits by behavioural segment
- **Bulk invoice distribution**: flags potential wholesale signal

---

## 9) Strategic Recommendations
**Retention (D1–D2 / Champions / Loyal)**
- Offer loyalty benefits, early access, and proactive churn alerts when recency worsens.
- Limit discounting; use perks and bundles to protect margin.

**Growth (D3–D6)**
- Best segment for incremental uplift tests (personalisation, cross-sell, threshold shipping).
- Run A/B tests and optimise to incremental revenue per customer.

**Win-back (At Risk / Can't Lose Them)**
- Triggered win-back journeys based on recency thresholds and past spend.
- Focus on margin-aware offers rather than blanket % discounts.

**Dormant / Low value**
- Low-cost reactivation only (email/SMS), then suppression to avoid wasted spend.

---

## 10) Why This Project Stands Out (differentiators)
- Production-style pipeline structure (not a one-off notebook)
- Transparent cleaning audit (counts removed by rule)
- Correct RFM definitions with snapshot date
- Bulk invoices are tagged instead of deleted (avoids bias against VIP/wholesale behaviour)
- Deciles are implemented safely with D1 = top customers and guardrails

---

## 11) Skills Demonstrated (technical + business)
**Technical**
- Python (pandas, numpy, matplotlib/seaborn), modular scripting, data validation, reproducible outputs
- Robust data cleaning for real e-commerce patterns (cancellations, invalid lines)
- Customer analytics: RFM, segmentation, deciles, revenue concentration

**Business**
- Turning analysis into targeting rules and budget allocation logic
- Stakeholder-friendly narrative and decision framing
- Practical next actions (retention, win-back, growth experiments)

---

## 12) How This Project Adds Value to a Business
This project provides a repeatable method to:
- Identify and protect the customers who fund the business
- Reduce churn by prioritising high-value customers at risk
- Allocate marketing budget based on measured return potential (deciles)
- Build a segmentation foundation for lifecycle marketing and testing

---

## How to Run
1) Ensure Python 3.10+ and install dependencies:
   - pandas, numpy, matplotlib (seaborn and plotly optional)

2) Run the script:
   `python rfm_portfolio_pipeline.py --data-path data.csv --output-dir outputs`

Outputs:
- Cleaned transactions CSV
- Customer-level RFM table + segments
- Decile summary table
- Saved charts in the figures directory
