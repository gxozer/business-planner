# Agent Context Template

A companion document to the business plan, written for a **coding agent** that will implement the project — not a human stakeholder. Always produced, in every mode (full and lean): the point is a small, cheap file an implementing agent can load instead of pulling in the full document set to reconstruct the same information.

Keep it to build-relevant facts only. Leave out market sizing, competitive-landscape narrative, the patent/IP scan, financial projections, funding narrative, and team bios — real for the business plan, irrelevant to writing code. When in doubt, ask: "does this change what gets built, or just whether the business is worth building?" Only the former belongs here.

## What this is

One short paragraph: the idea in plain terms, the target user, the core value proposition. Enough to orient an agent that has never seen the business plan — not the full Problem/Opportunity/Market framing.

## Glossary

The project's own settled vocabulary — product name, key domain terms, anything intake or research fixed a specific meaning for. Definitions only, one line each. Skip this section if intake didn't settle any terms beyond generic ones.

## Decisions & constraints

Settled, build-relevant decisions and the constraints they operate under, one line each with a one-clause reason:

- The chosen build/operate option(s) from `cost-analysis.md` (hosting, key third-party services) — not the full comparison, just what was picked and why.
- Any resolved RFC (`rfcs.md`) that affects what gets built (pricing/metering model, channel integration, data model implications) — the decision made, not the options considered.
- Hard constraints from intake (budget, timeline, must-use/must-avoid technology) that bound implementation choices.

## Use cases

The Actor → Trigger → Scenario → Outcome scenarios from `use-cases.md`, restated as short bullets an agent can treat as acceptance criteria. Include the edge cases, not just the primary ones — they're often the more useful ones for spotting what a naive implementation would miss.

## Implementation plan

The phased build sequence and the Jira-ready ticket hierarchy from `implementation-plan.md` — copy it in directly rather than pointing to it, since this is the one section of that file an implementing agent needs in full, not condensed.

## Open assumptions

Anything still marked open in the Open Questions Log that bears on implementation (an unvalidated cost or pricing assumption, an undecided integration). State it as "assumed, not confirmed" so an agent doesn't silently treat it as settled fact.

## Sources

Only include this section if a build-relevant figure (a cost estimate, a technical constraint) needs to stay re-verifiable — don't duplicate the full source list from the other documents.
