# MIS Financial Performance Dashboard
**Tools:** PostgreSQL 18 | Power BI | DAX

## Objective
Centralize fragmented multi-source financial records into a unified,
actionable reporting tool to eliminate reporting delays.

## Data Sources
6 accounting datasets for FY 2024-25:
- Accounts Receivable & Payable
- General Ledger
- Sales & Purchase Register
- Bank Statement

## What I Built

### SQL Pipeline (PostgreSQL 18)
- Imported 6 raw Excel exports into PostgreSQL as structured tables
- Wrote cleaning views to standardize date formats, strip text from
  numeric columns, and rename to snake_case
- Built bank reconciliation logic by joining bank statement against
  GL on matching date + amount — flagged 978 reconciled /
  640 unreconciled transactions
- Materialized cleaned views into fact tables for Power BI consumption

### Power BI Data Model
- Built a star schema with 7 relationships — all fact tables
  connecting to a shared Date dimension, no fact-to-fact joins
- Created dim_account_details for account classification

### DAX Measures (18 total)
- Gross Margin %
- AR Aging buckets (0-30, 31-60, 61-90, 91-120, 121+ days)
- % AR Overdue 90+
- Average Collection Period (Days)
- % Reconciled, Unreconciled Amount
- Latest Bank Balance

### Dashboard Pages
1. Executive Summary — Sales, Profit, Margin, AR/AP, Reconciliation KPIs
2. AR Aging Analysis — Aging bucket breakdown by customer
3. Bank Reconciliation — Reconciled vs Unreconciled with transaction list
4. GL Drill-Down — Account-level debit/credit detail with filters

## Impact
- Eliminated 30% of manual data consolidation
- Saved ~6 hours/week previously spent on Excel reporting
- Delivered real-time visibility for executive leadership

## Screenshots
![Executive Summary](screenshots/executive_summary.png)
![AR Aging](screenshots/ar_aging.png)
![Bank Reconciliation](screenshots/bank_reconciliation.png)
![GL Drill Down](screenshots/gl_drilldown.png)
