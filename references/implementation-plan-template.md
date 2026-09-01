# Implementation Plan Template

A companion document to the business plan: a phased build-out sequence, always produced (unlike the patent and risk documents, which are conditional). The sequencing principle is cost/benefit, not chronology for its own sake — order phases and tasks within them so the cheapest ways to validate the riskiest assumptions come first, and capital- or time-intensive work is deferred until an earlier phase has validated it's worth doing.

Open with a one-line statement of that principle applied to this specific idea (what's cheap-and-risky here, what's expensive-and-safe-to-defer), so the ordering below reads as a deliberate argument rather than a generic checklist.

## Phases

Use as many phases as the idea actually needs — most ideas land somewhere between 3 and 5. A typical shape:

- **Phase 0 — Validate**: the cheapest possible test of the riskiest assumption (customer interviews, a landing page and ads, a manual/concierge version of the service) before building anything real.
- **Phase 1 — Minimum viable version**: the smallest version that delivers the core value to real customers, prioritizing the highest-benefit, lowest-cost features first and deferring anything "nice to have."
- **Phase 2 — Early traction**: channel testing and iteration once the MVP is in front of real customers, spending only where Phase 0/1 signal justified it.
- **Phase 3+ — Scale**: capital- or headcount-intensive investment, gated on the traction signals from earlier phases actually showing up.

For each phase:

- **Goal**: what this phase is trying to prove or deliver, in one line.
- **Key tasks**: the concrete work, ordered so the highest-benefit/lowest-cost items come first within the phase too.
- **Estimated cost**: rough — time, money, or both — labeled as an estimate.
- **Expected benefit**: what it unlocks or de-risks, concretely (not "builds momentum").
- **Dependencies**: what has to be true or finished before this phase can start.
- **Exit criteria**: the concrete result that means it's time to move to the next phase — or to stop/pivot if it doesn't show up.

## Jira-ready ticket hierarchy

Restate the phases and tasks above as a ticket hierarchy, directly in this document — no separate export file:

- Each phase becomes an **Epic**.
- Each key task within it becomes a **Story** (or **Task**) under that Epic.
- Any further breakdown of a task into concrete steps becomes **Sub-tasks** under that Story.

Render it as a nested outline, e.g.:

```
Epic: Phase 0 — Validate
  Story: Run 10 customer interviews (3 pts)
    Sub-task: Draft interview script (1 pt)
    Sub-task: Recruit 10 target customers (2 pts)
Epic: Phase 1 — MVP
  Story: ...
```

Don't force three levels where two are enough — a simple task can stay a Story with no sub-tasks. This is meant to be read and copied by hand into Jira (or any tracker) as-is, not imported from a file.

## Sources

- Any cost or timeline benchmarks used (e.g. typical MVP build costs for comparable products), so estimates can be re-verified or tightened later.
