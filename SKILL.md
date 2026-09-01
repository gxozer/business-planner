---
name: business-planner
description: Research a business idea and produce a full business plan document — market analysis, competitors, business model, go-to-market strategy, financial projections, patent/IP landscape, and risks. Use when the user wants to explore, validate, research, or write a plan for a business idea, startup concept, side project, or new venture.
---

# Business Planner

Turns a business idea into a researched, structured business plan document.

## Workflow

### 1. Intake — round one

Ask a first, tight round of core questions (use `AskUserQuestion` where a short menu fits):

- The idea itself, in a sentence or two.
- Target customer / market (who pays, and roughly where — country/region matters for market-size research and regulation).
- Stage: pure concept, validated with some customers, or already running.
- Anything they already know or have strong opinions about (don't re-research what they've told you with confidence — fold it in and cite it as "per user").
- What decision this plan needs to support (deciding whether to pursue it at all, pricing, which market to enter first, raising money) — use the answer to prioritize which research tracks in step 2 go deep versus shallow, rather than researching everything to the same depth by default.
- Any hard constraints (budget, timeline) or sources/data they already trust — keeps the research scoped to what's actually decision-relevant instead of exhaustive for its own sake.

That's enough to start research — don't wait for a full interview before moving to step 2.

### 2. Research — launched in parallel, not sequentially

As soon as the idea, target market, and geography are known, kick off research immediately and run it in parallel with the rest of intake (step 3), not after it. Use the `Agent` tool to fork independent research tracks — e.g. one for market sizing, one for competitors, one for patent/IP landscape, one for trends/regulation, one for build/operating cost options — rather than researching each area one after another. Load `references/research-checklist.md` for the full framework covering all of these areas: market size, competitors, customer demand signals, trends/regulation, pricing benchmarks, the existing patent/IP landscape, and concrete build/operating cost options (hosting, manufacturing, fulfillment, third-party services — whatever the idea's domain actually needs).

Tell the user what's running before moving on — name each track and roughly what it's checking (e.g. "kicking off four research tracks in the background: market sizing, competitors, patent landscape, and regulation — I'll fold results in as they land"). This is a terminal session, not a UI with live progress bars, so visibility means saying what's happening in the conversation: post a short one-line status update whenever a track finishes while round two continues (e.g. "patent scan is back — no blocking prior art found; market sizing and competitor research still running"), rather than going silent until everything is done.

Rules:

- Cite every non-obvious factual claim with a source link and, where relevant, the data's date.
- Prefer primary sources (industry reports, government/statistics agencies, company filings, patent office databases) over blog aggregation.
- Where numbers are estimates or extrapolations, say so explicitly (e.g. "estimated," "rough order of magnitude") rather than presenting them as precise facts.
- If research turns up a strong reason the idea is weak (saturated market, dying trend, regulatory blocker, blocking patent), say so plainly in the plan rather than glossing over it.
- For patent research specifically: search Google Patents / USPTO / WIPO (via `WebSearch`/`WebFetch`) for prior art covering the idea's core mechanism or method. This is a landscape scan, not a legal clearance search — always say so explicitly (see Notes).
- When a track turns up a genuine decision point — multiple viable options with real trade-offs (pricing model, target segment, channel strategy) — don't just pick one silently. Draft an RFC-lite entry per `references/rfc-template.md` instead, laying out the options and ending in an explicit open question for the user. Most findings are plain facts, not RFCs — only do this for real multi-option decisions.

### 3. Intake — round two, adaptive

While round-one research runs in the background, continue the interview with a second, more thorough round covering the rest of the business-plan surface: business model and pricing intuition, go-to-market channels already considered, operational constraints, team, and financial assumptions. Don't run the same generic list for every idea — load `references/domain-questions.md` and use the question set for the idea's actual business-model domain (SaaS, physical product, marketplace, service, hardware, content/media), pulling from more than one set when an idea spans domains. Split this across a couple of focused rounds rather than one long form, and let the user skip anything they don't know — mark it as an open assumption instead of blocking on it.

Once research results start coming back, use them to drive further questions instead of sticking to a fixed script: if a strong incumbent turns up, ask how the idea differs from it; if the market looks saturated or a blocking patent surfaces, raise it immediately and ask how they want to proceed (narrow the niche, pivot, or continue anyway) rather than waiting until the full draft to surface it. Any RFC entry from step 2 gets its open question raised here too — don't let a real decision point sit unasked in a file the user might not read closely.

Keep a running log of every question asked across both rounds — the question, the answer given, or "open" if the user skipped it — as you go rather than trying to reconstruct it at the end. This becomes the plan's Open Questions Log (see `references/business-plan-template.md`).

### 4. Draft the plan

Load `references/business-plan-template.md` for the section-by-section structure and what belongs in each section, including the financial projections framework.

Write the plan as Markdown. Label every assumption or estimate inline (e.g. *"Assumption: $50 CAC based on comparable D2C brands — not validated with paid ads yet."*) so the user can tell researched facts apart from placeholders they still need to fill in or test.

### 5. Output

- Save the plan to `./business-plans/<idea-slug>/business-plan.md` in the user's current project (create the directory if needed). Tell the user the path.
- Save a separate `./business-plans/<idea-slug>/patent-applications.md` alongside it, using `references/patent-applications-template.md` — one entry per plausible patent application angle found during research, each with the prior art it was checked against and a clear "not legal advice" flag. Skip this file only if research turns up genuinely nothing patentable (e.g. a pure business-model idea with no novel mechanism) — say so instead of forcing an empty document.
- Save a separate `./business-plans/<idea-slug>/risks.md` alongside it, using `references/risk-document-template.md` — the full risk register (more risks, more mitigation/monitoring detail than fits in the plan's own Risks & Mitigations section). Keep a condensed top-5 summary and a pointer to this file in the main plan either way.
- Save a separate `./business-plans/<idea-slug>/implementation-plan.md` alongside it, using `references/implementation-plan-template.md` — always include this one. Sequence it in incremental phases ordered by cost/benefit: the cheapest ways to validate the riskiest assumptions come first, capital- or time-intensive work is deferred until earlier phases validate it's worth doing. Keep a condensed phase summary and a pointer to this file in the main plan's Milestones / Roadmap section. Include the Jira-ready ticket hierarchy (Epic → Story → Sub-task, as a nested outline) directly in this document, per `references/implementation-plan-template.md` — no separate export file for it.
- Save a separate `./business-plans/<idea-slug>/rfcs.md` alongside it, using `references/rfc-template.md` — one entry per genuine multi-option decision point research turned up. Skip it entirely if none did; don't force an entry where research pointed clearly one way.
- Save a separate `./business-plans/<idea-slug>/use-cases.md` alongside it, using `references/use-cases-template.md` — always include this one. Concrete Actor → Trigger → Scenario → Outcome scenarios for the target segments identified in Market Analysis, not personas or a feature list. Include a couple of edge-case scenarios that stress-test the value proposition, not only flattering ones.
- Save a separate `./business-plans/<idea-slug>/cost-analysis.md` alongside it, using `references/cost-analysis-template.md` — concrete implementation-option comparisons (hosting providers, manufacturing options, third-party services, whatever the domain needs) with estimated costs at a stated scale, not just a cost-structure line. Skip it only if the idea genuinely has no build/operate decision to compare (e.g. a pure consulting practice). Feed the chosen option's cost into `implementation-plan.md`'s phase estimates and the Financial Projections cost table, rather than leaving disconnected numbers.
- Ask once, offering to publish **all** of the documents produced (not just the main plan) as polished Artifacts together, rather than picking one — if they say yes, follow the `artifact-design` skill for each before building it. Mention that Artifacts support inline comments, and explicitly invite them (and anyone they share the links with) to leave feedback there — that's a good way to gather input across the whole plan rather than one section at a time.
- Keep the research sources list at the bottom of each document (a "Sources" section) so claims stay checkable.

### 6. Iterate

Treat the first draft as a draft. Invite the user to challenge assumptions, request deeper research on a specific section, or supply real numbers (traction, costs, pricing) to replace estimates. Update the same file in place rather than creating new versions, unless the user asks to branch into an alternative direction. When a previously open question gets answered during iteration, update both the relevant section and the Open Questions Log entry — don't leave it marked open once it's resolved. Likewise, when the user answers an RFC's open question, record the choice and reasoning in that `rfcs.md` entry and fold the decision into the relevant plan section instead of leaving both options standing.

Up to seven files can exist per idea by this point — don't re-read all of them on every iteration turn. `business-plan.md` already carries a condensed pointer into each companion file (the IP section summarizes `patent-applications.md`, Risks summarizes `risks.md`, Milestones summarizes `implementation-plan.md`, the Open Questions Log points at `rfcs.md`), so it works as its own index. Re-read `business-plan.md` first when resuming work, and only open a specific companion file in full when the user's request is actually about that file's details.

## Notes

- This skill is for research and drafting, not financial or legal advice — say so if the user seems to be treating the projections as guaranteed rather than illustrative.
- Patent output is a prior-art landscape scan done by an AI assistant with web search, not a freedom-to-operate opinion or a patentability opinion. State this explicitly in both the business plan's IP section and at the top of `patent-applications.md`, and recommend a registered patent attorney or agent before filing anything or relying on the novelty assessment.
- If the user wants something lighter than a full plan (a one-page lean canvas, a quick gut-check), scale down the template rather than forcing every section — ask first if it's unclear which they want.
- Parallel research (step 2) trades some cost/latency for speed — if the user is doing a very quick gut-check rather than a full plan, it's fine to research sequentially instead and skip forking agents.
