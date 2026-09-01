# Business Plan Template

Section-by-section structure for the plan document. Use Markdown headings matching these, in this order. Omit a section only if it's genuinely not applicable (say why in one line rather than silently dropping it).

## Executive Summary

Write this **last**, even though it's first in the document. One page max: the idea, the target customer, the size of the opportunity, the business model in one line, and what's being asked for (funding, a decision, or just a plan to work from).

## Problem & Opportunity

- The specific problem, for a specific customer, today — not a vague pain point.
- Evidence the problem is real and worth solving (from research and/or the user's own experience).
- Why now — what's changed that makes this a good time (tech shift, regulatory change, behavior change).

## Solution

- What the product/service actually is, concretely.
- Why this approach beats existing alternatives (including "do nothing" / manual workarounds).
- Stage of the solution today (idea, prototype, live with users).
- One or two of the strongest use cases from the companion `use-cases.md`, to make the solution concrete rather than abstract — with a pointer to that file for the full set.

## Market Analysis

- TAM / SAM / SOM with sources (see `research-checklist.md`).
- Growth trend of the market.
- Target segment(s), ranked by priority for early traction.

## Competitive Landscape

- Table of direct and indirect competitors: name, offering, pricing, apparent traction, weakness/gap.
- The idea's actual differentiation — be specific, not "better UX."

## Business Model

- Revenue streams and pricing model.
- Cost structure: fixed vs. variable, major cost drivers.
- Unit economics if estimable: CAC, gross margin, LTV, payback period — label all as estimates unless the user has real data.

## Go-to-Market Strategy

- How the first 10, first 100, first 1,000 customers get acquired — these are usually different channels.
- Concrete marketing channel ideas suited to the target segment and domain — name the specific channels (content/SEO, paid acquisition, community, partnerships, PR, direct sales, etc.) and why each fits this idea, not a generic "do marketing."
- How the monetization approach shapes the acquisition motion — e.g. a freemium model supports self-serve/viral channels, a high-price offering supports a sales-led motion. Cross-reference the pricing model from Business Model rather than repeating it.
- Positioning/messaging in one or two sentences.
- Partnerships or distribution advantages, if any.

## Intellectual Property

- Summary of the patent/IP landscape scan (see `research-checklist.md`): what prior art exists near the idea's core mechanism, and whether it looks like adjacent art or a freedom-to-operate risk.
- One line pointing to the companion `patent-applications.md` for the full breakdown, if one was produced.
- Explicit statement that this is a research scan, not a legal opinion — recommend a registered patent attorney or agent before filing or relying on it.

## Operations Plan

- What needs to be built, bought, staffed, or licensed to deliver the product.
- Key suppliers/vendors/platforms the business depends on.
- Any regulatory/compliance steps identified in research.

## Team

- Founders/key people and relevant background (only if provided by the user — don't fabricate).
- Known gaps to hire or contract for.

## Financial Projections

Keep this simple and clearly labeled as illustrative unless the user supplies real figures:

- Revenue projection table, 12–24 months, with the driving assumptions stated explicitly (e.g. customers × price × conversion rate).
- Cost projection covering the same period.
- Break-even estimate.
- Funding ask and use of funds, if applicable.

## Risks & Mitigations

- The 3–5 biggest risks (market, execution, competitive, regulatory, financial, patent/IP) — be honest, including risks that make the idea look weaker.
- A mitigation or monitoring plan for each, not just a list of scary things.
- One line pointing to the companion `risks.md` for the full risk register, if one was produced.

## Milestones / Roadmap

- Next 3–6 concrete milestones with rough timing (e.g. "validate pricing with 10 customer interviews — 4 weeks").
- A condensed phase-by-phase summary (one line per phase: goal, rough cost, exit criteria) from the companion `implementation-plan.md`, with a pointer to that file for the full breakdown.

## Open Questions Log

Every question asked during intake — both fixed rounds and adaptive follow-ups — with its outcome, as a table: **Question** | **Answer / Status**. For an answered question, give the answer in a few words. For one the user skipped, write "Open — treated as assumption" and point to where in the plan that assumption is labeled, so it doesn't just disappear. Keep this section updated across iterations (step 6 of `SKILL.md`) as open items get answered later.

If research turned up any genuine multi-option decisions (see `rfc-template.md`), add one line per decision pointing to its entry in the companion `rfcs.md`, so open decisions are visible from the same log rather than only living in a separate file.

## Sources

- Every source cited in the document, as a flat list of links, so claims stay checkable and re-verifiable later.
