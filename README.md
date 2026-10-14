# Order Assurance in Two-Step Retail Ordering

A case study on detecting and preventing incomplete replenishment orders in a retail department where an order needs two separate submissions (a handheld device and a store computer).

> **Status:** In progress (started October 2026)

## Summary

When the second submission is missed and not caught before the supplier cutoff, the delivery arrives late or merges with the next day's delivery. This creates abnormal volumes, extra handling and added manual-handling risk for staff. This project compares controls that catch incomplete orders early enough to fix them, and estimates how much each one reduces failures and abnormal-load days.

## Data and confidentiality

- This is a **hypothetical case study**. All data is **synthetic**.
- No company data, internal system names, screens, reports or file formats are used.
- Process steps are described generically ("handheld ordering device", "store computer system").
- Assumptions behind the synthetic data (miss rate, recovery rate, roster coverage) are stated openly in `assumptions.md` and tested with sensitivity analysis. Results are conditional on those assumptions, not predictions.

## Planned structure

| Item | Description |
|---|---|
| `problem-statement.md` | The problem, scope and objective |
| `status-definitions.md` | Rules for classifying each order |
| `process-map/` | Current-state (AS-IS) and improved (TO-BE) process maps |
| `gaps-and-controls.md` | Running log of weaknesses found and the controls considered |
| `assumptions.md` | Assumptions behind the synthetic data |
| `data/` | Schema, generator script and synthetic CSVs |
| `analysis/` | Classifier, SQL queries, simulation and sensitivity analysis |
| `dashboard/` | Power BI dashboard screenshots |

## Limitations and dependencies

*To be completed as the project develops.*

## Tools

Python, SQL, Power BI, Excel
