# Real-Time Credit Card Fraud Detection

An end-to-end fraud detection pipeline built with Databricks, PySpark,
Structured Streaming, Auto Loader, Delta Lake, Unity Catalog, and
Medallion Architecture.

## Business Problem

Financial institutions must identify suspicious credit-card transactions
quickly while minimizing false alerts and preventing invalid data from
entering downstream systems.

## Architecture

Transaction Events  
→ Auto Loader  
→ Bronze Delta Table  
→ Validation and Quarantine  
→ Silver Transactions  
→ Customer, Card, and Merchant Enrichment  
→ Fraud Risk Scoring  
→ Gold Alerts  
→ Investigation Cases  
→ Disputes and Operational Actions  
→ Monitoring and Reconciliation

## Data Sources

- Customers
- Cards
- Merchants
- Historical transactions
- Simulated real-time JSON transaction events

## Medallion Architecture

- **Bronze:** Raw historical and streaming transactions
- **Silver:** Validated, deduplicated, and enriched records
- **Gold:** Fraud scores, alerts, cases, disputes, actions, and metrics
- **Quarantine:** Invalid records with rejection reasons

## Fraud Rules

The explainable risk score considers:

- Transaction amount
- Amount compared with previous card behavior
- Customer risk profile
- Merchant risk score
- Merchant category
- Credit score
- Card status

Risk decisions:

- Score below 35: Approve
- Score 35–59: Manual review
- Score 60 or above: Urgent investigation

## Project Results

- Historical transactions processed: 15,000
- Historical fraud transactions: 579
- Real-time events tested: 5
- Valid real-time records: 4
- Quarantined records: 1
- Fraud alerts generated: 2
- Confirmed fraud case: 1
- Disputed amount: $4,500
- Reconciliation status: Passed

## Production Features

- Explicit schemas
- Incremental Auto Loader ingestion
- Structured Streaming checkpoints
- Watermark-based deduplication
- Data-quality validation
- Quarantine processing
- Stream-static enrichment
- Explainable fraud scoring
- Idempotent Delta MERGE operations
- Investigation and dispute workflow
- Pipeline reconciliation
- Databricks Workflow orchestration
- Failure and duration notifications

## Repository Structure

```text
notebooks/
├── 01_realtime_bronze_ingestion
├── 02_realtime_validation
├── 03_realtime_enrichment_scoring
├── 04_fraud_case_processing
└── 05_monitoring_reconciliation
