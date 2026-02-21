# E‑commerce Customer Value Segmentation (RFM & Deciles)

## Situation – The Business Context

An online retailer was generating steady order volumes, but revenue was heavily skewed towards a small share of customers. Marketing spend was spread too widely through blanket discounts, while the most valuable customers were not clearly identified or protected.[file:1]  
Without a structured view of customer value and behaviour, it was difficult to decide who to retain, who to grow, and where win‑back spend was being wasted.[file:1]  

## Task – What Needed to Change

The goal of this project was to build a customer value hierarchy from transaction‑level data and quantify how concentrated revenue really was across the base.[file:1]  
The analysis needed to surface high‑value and at‑risk customers, estimate the commercial size of dormant and low‑value groups, and provide a defensible framework for retention, growth, and win‑back budget allocation.[file:1]  

## Action – What I Did

- Converted raw e‑commerce invoices into a customer‑level view using Recency, Frequency and Monetary (RFM) definitions aligned to a clear snapshot date.[file:1]  
- Applied business‑safe data cleaning with an audit trail (removing cancellations, non‑positive quantities/prices, missing customer IDs, and tagging bulk invoices instead of deleting them).[file:1]  
- Analysed monthly revenue, new vs returning customers, top products and countries, and the revenue Pareto curve to understand seasonality, retention dynamics, and commercial focus areas.[file:1]  
- Built RFM segments (e.g. Champions, Loyal, Needs Attention, At Risk, Dormant, Lost/Low Value) to describe behaviour in terms that marketing and CRM teams can act on.[file:1]  
- Ranked customers into 10 monetary deciles and calculated customer share, revenue share, transaction share, and cumulative revenue for each decile to support budget and targeting decisions.[file:1]  
- Produced decision‑ready CSV outputs (customer‑level RFM, segment and decile summaries, decision packs and uplift scenarios) so non‑technical stakeholders can explore results without running the notebook.[file:1]  

## Result – Impact and Opportunities

- Confirmed that the top 10% of customers generate around 61.5% of total revenue, and the top 20% generate 74.7%, with 80% of revenue reached by Decile 3 – a clear case for a retention‑first strategy.[file:1]  
- Showed that Champions and Loyal customers contribute a disproportionate share of revenue, while a large dormant/low‑value pool adds minimal revenue despite its size, highlighting where spend can be reduced.[file:1]  
- Identified “At Risk / Can’t Lose Them” customers with high historical value but worsening recency, providing a prime audience for tightly controlled, margin‑aware win‑back offers.[file:1]  
- Used deciles as a simple budgeting tool to prioritise richer perks, early access and bundles for top deciles, structured growth tests for mid‑tier segments, and low‑cost or suppressed contact strategies for low‑value groups.[file:1]  
- Created a reusable analysis pipeline and metric set (revenue concentration, RFM segment revenue, revenue by decile) that can plug into CRM and campaign planning to track uplift over time.[file:1]  

## Tools Used (brief)

- Python 3.10 notebook for data cleaning, RFM scoring and customer decile analysis.[file:1]  
- Python visualisations to answer commercial questions (revenue concentration, retention dynamics, product and country focus)._[file:1]  
- CSV outputs for stakeholders: cleaned transactions, customer‑level RFM, segment and decile summaries, decision packs, and uplift scenarios.[file:1]  

## Who This Project Is For

This project is relevant for **Data Analyst**, BI Analyst, and Customer / CRM Insights Analyst roles in e‑commerce, retail or subscription businesses.  
It demonstrates the ability to turn granular transaction data into customer value segments, quantify revenue risk and opportunity, and propose targeted retention, growth and win‑back actions that a commercial team can use immediately.[file:1]  
