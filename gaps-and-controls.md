# Gaps and Controls Log

A running list of weaknesses found in the process or in the project's own design, and the controls considered. Updated as the project develops.

## Gaps found

| ID | Gap | Why it matters | Found |
|---|---|---|---|
| G1 | **Dependent control.** An alert or log that relies on the person who forgot the second step fails in the same way as the original process. | A control must be independent of the failure it protects against. | Nov 2026 |
| G2 | **Roster dependency.** The morning recovery window assumes someone is rostered before the cutoff. | On days with no early coverage, the safety net does not exist. | Nov 2026 |
| G3 | **Status depends on time.** "At Risk" is only meaningful before the cutoff; after it, an order must be Complete, Recovered or Failed. | Status logic must use timestamps and the current time, not just flags. | Nov 2026 |
| G4 | **Two kinds of failure.** "Never ordered" and "ordered but unconfirmed" have different root causes. | They need different fixes, so they are tracked separately. | Nov 2026 |
| G5 | **No single owner.** Anyone working that day can place an order, so nobody is clearly responsible for completing step 2. | Shared responsibility makes it easy for each person to assume someone else will confirm. | Nov 2026 |
| G6 | **Time-of-day risk.** An order placed late in the day leaves little time to notice a missing step 2 before the last shift ends. | Late orders may carry higher risk and should be tracked by placement time. | Nov 2026 |
| G7 | *(add new gaps here as they appear)* | | |

## Control options considered

| ID | Control | Independent of the person who forgot? | Depends on roster? | Extra staff effort |
|---|---|---|---|---|
| C0 | Do nothing (current state) | No | n/a | None |
| C1 | Handover checklist at end of evening shift | Partly (anchored to a routine) | No | Low |
| C2 | Routine morning check of unsubmitted orders | Yes | **Yes** | Low |
| C3 | Mid-shift confirmation check at a fixed time | Partly | No | Low |
| C4 | Backup owner (duty manager or other department) when no early shift exists | Yes | No | Low-Medium |
| C5 | Automated exception report (system compares both steps) | Yes | No | None for staff; needs system support |
| C6 | Layered: C1 + C2 + C4 | Yes | Reduced | Medium |

Detection probabilities for each control will be set in `assumptions.md` and tested in the sensitivity analysis.

## Notes

- Layered controls are expected to be more robust than any single control.
- Add anything new that comes up while building the data model or simulation.
