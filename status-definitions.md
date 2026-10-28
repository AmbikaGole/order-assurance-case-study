# Status Definitions

Every order is classified using **full timestamps** (date and time, not time of day alone), because the cutoff falls on the next calendar day.

## Process in plain terms

- **Step 1:** the order is placed on the handheld device. This can happen at **any time on day D**, by **anyone working that day** (for example 07:00, 09:00 or 18:00).
- **Step 2:** the order is submitted on the store computer. This must happen **at or before the cutoff: 05:00 on day D+1** for the delivery to arrive on the correct day.

## Key times (assumptions, adjustable)

| Term | Meaning | Example value |
|---|---|---|
| Step 1 time | When the handheld order is placed (varies by order and person) | Any time on day D |
| Last shift end | When the last person on day D finishes; after this, nobody is on site to fix a missed step | 22:00 on day D |
| Cutoff | Last moment the computer submission counts | 05:00 on day D+1 |

A submission **at or before** the cutoff (05:00:00) counts as on time.

## Statuses

| Status | Rule | Type |
|---|---|---|
| **Complete** | Step 2 done by the end of day D's last shift (nobody needed to rescue it) | Final |
| **At Risk** | Step 1 done, step 2 missing, cutoff not yet passed | Temporary (exists only before the cutoff) |
| **Recovered** | Step 2 done after day D's last shift ended but at or before the cutoff | Final |
| **Failed: unconfirmed** | Step 1 done, step 2 still missing at the cutoff | Final |
| **Failed: never ordered** | Neither step done at the cutoff | Final |

## Decision logic

Evaluate in this order:

1. Neither step done at the cutoff → **Failed: never ordered**
2. Step 1 done, step 2 not done by the cutoff → **Failed: unconfirmed**
3. Step 2 done at or before last shift end on day D → **Complete**
4. Step 2 done after last shift end, at or before the cutoff → **Recovered**
5. Step 1 done, step 2 missing, current time before cutoff → **At Risk**

Once the cutoff has passed, no order can be At Risk. Every order must be in a final state.

## New variables this creates

Because orders can be placed at any time, these become part of the analysis:

- **Time of day step 1 was placed.** An order placed at 07:00 leaves many hours to remember step 2. One placed at 18:00 leaves very few.
- **Gap between step 1 and step 2** (minutes or hours). A long gap is an early warning sign.
- **Who placed it.** Because anyone can order, nobody is clearly responsible for step 2. This is a gap in its own right (see G5).
- **Hours remaining before last shift end** when step 1 is placed. This is likely a strong predictor of a missed step 2.

## Edge cases to test

| Case | Expected status |
|---|---|
| Step 1 at 07:00, step 2 at 07:10 | Complete |
| Step 1 at 09:00, step 2 never done, no one notices | Failed: unconfirmed |
| Step 1 at 18:00, step 2 at 21:30 (before last shift end) | Complete |
| Step 1 at 18:00, step 2 at 04:21 next day | Recovered |
| Step 2 at 04:59:59 | Recovered |
| Step 2 at exactly 05:00:00 | Recovered |
| Step 2 at 05:00:01 | Failed: unconfirmed |
| Step 2 recorded before step 1 | Invalid event; flag for data check |
| Two people each place part of the same order | Treat as one order; flag for data check |
| No events at all for an expected order | Failed: never ordered |

## Open questions to resolve later

- Should a Recovered order still count as a "near miss" in the KPIs? (Likely yes.)
- Is the cutoff the same every day of the week?
- How should public holidays or changed delivery days be handled?
- How many orders are placed per day, and at what times? (This will be a synthetic assumption.)
