---
name: business-planner
description: Research a business idea and produce a full business plan document — market analysis, competitors, business model, go-to-market strategy, financial projections, and risks. Use when the user wants to explore, validate, research, or write a plan for a business idea, startup concept, side project, or new venture.
---

# Business Planner

Turns a business idea into a researched, structured business plan document.

## Workflow

### 1. Intake

If the user hasn't already given these, ask (use `AskUserQuestion` where a short menu fits):

- The idea itself, in a sentence or two.
- Target customer / market (who pays, and roughly where — country/region matters for market-size research and regulation).
- Stage: pure concept, validated with some customers, or already running.
- Anything they already know or have strong opinions about (don't re-research what they've told you with confidence — fold it in and cite it as "per user").

Don't over-interview — two or three questions is usually enough to start. Gaps can be filled in during drafting by flagging them as open assumptions.

### 2. Research

Load `references/research-checklist.md` for the full framework. In short: use `WebSearch` / `WebFetch` to gather market size, competitors, customer demand signals, trends/regulation, and pricing benchmarks. Rules:

- Cite every non-obvious factual claim with a source link and, where relevant, the data's date.
- Prefer primary sources (industry reports, government/statistics agencies, company filings) over blog aggregation.
- Where numbers are estimates or extrapolations, say so explicitly (e.g. "estimated," "rough order of magnitude") rather than presenting them as precise facts.
- If research turns up a strong reason the idea is weak (saturated market, dying trend, regulatory blocker), say so plainly in the plan rather than glossing over it.

### 3. Draft the plan

Load `references/business-plan-template.md` for the section-by-section structure and what belongs in each section, including the financial projections framework.

Write the plan as Markdown. Label every assumption or estimate inline (e.g. *"Assumption: $50 CAC based on comparable D2C brands — not validated with paid ads yet."*) so the user can tell researched facts apart from placeholders they still need to fill in or test.

### 4. Output

- Save the plan to `./business-plans/<idea-slug>/business-plan.md` in the user's current project (create the directory if needed). Tell the user the path.
- Ask if they'd like it published as a polished Artifact for easier reading/sharing — if so, follow the `artifact-design` skill before building it.
- Keep the research sources list at the bottom of the document (a "Sources" section) so claims stay checkable.

### 5. Iterate

Treat the first draft as a draft. Invite the user to challenge assumptions, request deeper research on a specific section, or supply real numbers (traction, costs, pricing) to replace estimates. Update the same file in place rather than creating new versions, unless the user asks to branch into an alternative direction.

## Notes

- This skill is for research and drafting, not financial or legal advice — say so if the user seems to be treating the projections as guaranteed rather than illustrative.
- If the user wants something lighter than a full plan (a one-page lean canvas, a quick gut-check), scale down the template rather than forcing every section — ask first if it's unclear which they want.
