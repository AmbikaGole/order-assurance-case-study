# Problem Statement

## Context

In many retail departments, a replenishment order requires two separate submissions: one on a handheld device and one on a store computer. Completing the first step does not guarantee the second.

## Problem

When the second step is missed and not caught before the supplier cutoff, the delivery arrives late or merges with the next day's delivery. This creates:

- abnormal delivery volumes on a single day
- extra handling and stock-room pressure
- higher manual-handling risk for staff
  
  
## Why existing practice falls short

- Nothing independent of the person placing the order checks that both steps are complete.
- Any control that relies on the same person remembering fails in the same way as the original process (a *dependent control*).
- Recovery before the cutoff assumes someone is rostered early enough to act.

## Objective

Compare controls that detect incomplete orders early enough to correct them, and estimate how much each one reduces:

1. failed orders
2. abnormal-load (double-delivery) days

while keeping extra staff effort low.

## Key questions

1. How often does a missed second submission occur, and when is it caught?
2. How much does the morning recovery check depend on early-morning roster coverage?
3. Which control (or combination) gives the biggest reduction in failures for the least effort?
4. How sensitive are the conclusions to the assumptions made?

## Scope

**In scope:** process mapping, status definitions, a synthetic dataset, a classifier, a control-options simulation, sensitivity analysis, a dashboard.

**Out of scope:** real company data, building a notification app, claims about real-world results.

## Assumptions and limits

- All data is synthetic and the scenario is hypothetical.
- Results are conditional on the stated assumptions (see `assumptions.md`).
- Findings are a comparison of control designs, not a prediction of real outcomes.
