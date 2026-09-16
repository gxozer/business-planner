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

That's the full round-one list — six items, but short factual ones rather than open-ended, so it stays quick. Don't add more before moving to step 2; anything beyond this belongs in round two once research is already running.

### 2. Research — launched in parallel, not sequentially

As soon as the idea, target market, and geography are known, kick off research immediately and run it in parallel with the rest of intake (step 3), not after it. Use the `Agent` tool to fork independent research tracks — e.g. one for market sizing, one for competitors, one for patent/IP landscape, one for trends/regulation, one for build/operating cost options — rather than researching each area one after another. Load `references/research-checklist.md` for the full framework covering all of these areas: market size, competitors, customer demand signals, trends/regulation, pricing benchmarks, the existing patent/IP landscape, and concrete build/operating cost options (hosting, manufacturing, fulfillment, third-party services — whatever the idea's domain actually needs).

Tell the user what's running before moving on — name each track and roughly what it's checking (e.g. "kicking off five research tracks in the background: market sizing, competitors, patent landscape, regulation, and build/operating costs — I'll fold results in as they land"). This is a terminal session, not a UI with live progress bars, so visibility means saying what's happening in the conversation: post a short one-line status update whenever a track finishes while round two continues (e.g. "patent scan is back — no blocking prior art found; market sizing, competitor, and cost research still running"), rather than going silent until everything is done.

Rules:

- Cite every non-obvious factual claim with a source link and, where relevant, the data's date.
- Prefer primary sources (industry reports, government/statistics agencies, company filings, patent office databases) over blog aggregation.
- Where numbers are estimates or extrapolations, say so explicitly (e.g. "estimated," "rough order of magnitude") rather than presenting them as precise facts.
- If research turns up a strong reason the idea is weak (saturated market, dying trend, regulatory blocker, blocking patent), say so plainly in the plan rather than glossing over it.
- For patent research specifically, follow `references/research-checklist.md`'s Patent & IP landscape section — it's a landscape scan, not a legal clearance search, and must be labeled as such (see Notes).
- When a track turns up a genuine decision point — multiple viable options with real trade-offs (pricing model, target segment, channel strategy) — don't just pick one silently. Draft an RFC-lite entry per `references/rfc-template.md` instead, laying out the options and ending in an explicit open question for the user. Most findings are plain facts, not RFCs — only do this for real multi-option decisions.

### 3. Intake — round two, adaptive

While round-one research runs in the background, continue the interview with a second, more thorough round covering the rest of the business-plan surface: business model and pricing intuition, go-to-market channels already considered, operational constraints, team, and financial assumptions. Don't run the same generic list for every idea — load `references/domain-questions.md` and use the question set for the idea's actual business-model domain (SaaS, physical product, marketplace, service, hardware, content/media), pulling from more than one set when an idea spans domains.

Treat this as a frontier, not a fixed form: a question belongs in the current round only if what it depends on is already settled — an earlier answer, or a specific research track that's already landed. A question that depends on something still open (an unanswered question, or a research track still running) waits for a later round instead of being asked as a guess dressed up as a question. Most round-two questions are independent of each other and can go in the first round of this step; hold back only the ones with a real dependency — e.g. don't ask about pricing tiers before you know whether the model is freemium or usage-based. This is scoped to ordering within round two itself; it's not a full dependency tree across the whole intake, and it doesn't apply to round one's fixed list (step 1) at all. Let the user skip anything they don't know even when it's in the current round — mark it as an open assumption instead of blocking on it.

Once research results start coming back, treat that as settling a prerequisite too, not just as color for the plan: if a strong incumbent turns up, ask how the idea differs from it; if the market looks saturated or a blocking patent surfaces, raise it immediately and ask how they want to proceed (narrow the niche, pivot, or continue anyway) rather than waiting until the full draft to surface it. A newly-landed research fact can unblock a question that was waiting on it — fold it into the next round rather than treating research and round-two questions as separate tracks.

Any RFC entry from step 2 gets its open question raised here too — don't let a real decision point sit unasked in a file the user might not read closely. Present each RFC's open question numbered, with its recommendation on its own line, so the user can answer by number instead of composing a reply:

```
❓ **Q1 — Pricing model**: Per-seat or usage-based?

➡️ Usage-based — comparable tools in this space bill by API calls, and per-seat pricing under-monetizes the low-seat/high-usage segment this idea targets.
```

The recommendation is a default to accept or override, not a decision already made on the user's behalf — say so if they push back on it.

Keep a running log of every question asked across both rounds — the question, the answer given, or "open" if the user skipped it — as you go rather than trying to reconstruct it at the end. This becomes the plan's Open Questions Log (see `references/business-plan-template.md`).

Before moving to step 4, summarize the shared understanding in a few lines — the idea as refined, the key decisions made (including resolved RFCs), and what's still marked as an open assumption — and ask the user to confirm it before drafting starts. Don't draft on a summary they haven't confirmed; a quick correction here is far cheaper than redoing seven documents after the fact.

### 4. Draft the plan

Load `references/business-plan-template.md` for the section-by-section structure and what belongs in each section, including the financial projections framework.

Write the plan as Markdown. Label every assumption or estimate inline (e.g. *"Assumption: $50 CAC (Customer Acquisition Cost) based on comparable D2C brands — not validated with paid ads yet."*) so the user can tell researched facts apart from placeholders they still need to fill in or test.

### 5. Output

The file set below is the default (full-plan) output. If the user wants something lighter, see **Lean mode** below instead — it changes which of these get written, not the drafting step that precedes it.

- Save the plan to `./business-plans/<idea-slug>/business-plan.md` in the user's current project (create the directory if needed). Tell the user the path.
- Save a separate `./business-plans/<idea-slug>/patent-applications.md` alongside it, using `references/patent-applications-template.md` — one entry per plausible patent application angle found during research, each with the prior art it was checked against and a clear "not legal advice" flag. Skip this file only if research turns up genuinely nothing patentable (e.g. a pure business-model idea with no novel mechanism) — say so instead of forcing an empty document.
- Save a separate `./business-plans/<idea-slug>/risks.md` alongside it, using `references/risk-document-template.md` — the full risk register (more risks, more mitigation/monitoring detail than fits in the plan's own Risks & Mitigations section). Skip this file if the main plan's own Risks & Mitigations section already covers everything adequately — don't force a companion doc with nothing extra in it. Keep a condensed top-5 summary and a pointer to this file in the main plan whenever it is produced.
- Save a separate `./business-plans/<idea-slug>/implementation-plan.md` alongside it, using `references/implementation-plan-template.md` — always include this one. Sequence it in incremental phases ordered by cost/benefit: the cheapest ways to validate the riskiest assumptions come first, capital- or time-intensive work is deferred until earlier phases validate it's worth doing. Keep a condensed phase summary and a pointer to this file in the main plan's Milestones / Roadmap section. Include the Jira-ready ticket hierarchy (Epic → Story → Sub-task, as a nested outline) directly in this document, per `references/implementation-plan-template.md` — no separate export file for it.
- Save a separate `./business-plans/<idea-slug>/rfcs.md` alongside it, using `references/rfc-template.md` — one entry per genuine multi-option decision point research turned up. Skip it entirely if none did; don't force an entry where research pointed clearly one way.
- Save a separate `./business-plans/<idea-slug>/use-cases.md` alongside it, using `references/use-cases-template.md` — always include this one. Concrete Actor → Trigger → Scenario → Outcome scenarios for the target segments identified in Market Analysis, not personas or a feature list. Include a couple of edge-case scenarios that stress-test the value proposition, not only flattering ones.
- Save a separate `./business-plans/<idea-slug>/cost-analysis.md` alongside it, using `references/cost-analysis-template.md` — concrete implementation-option comparisons (hosting providers, manufacturing options, third-party services, whatever the domain needs) with estimated costs at a stated scale, not just a cost-structure line. Skip it only if the idea genuinely has no build/operate decision to compare (e.g. a pure consulting practice). Feed the chosen option's cost into `implementation-plan.md`'s phase estimates and the Financial Projections cost table, rather than leaving disconnected numbers.
- Save a separate `./business-plans/<idea-slug>/agent-context.md` alongside it, using `references/agent-context-template.md` — always include this one, in every mode including Lean mode. Written for a coding agent that will later implement the project, not a human stakeholder: settled vocabulary, the chosen build/cost options, resolved decisions that affect what gets built, use-case scenarios, and the full implementation plan — the things code decisions hinge on, kept small enough to load cheaply instead of pulling in the whole document set. Leaves out market sizing, competitive analysis, patent landscape, and financial projections entirely — those stay in the other documents.
- Ask once, offering to publish **all** of the documents produced (not just the main plan) as polished Artifacts together, rather than picking one — if they say yes, follow the `artifact-design` skill for each before building it. Mention that Artifacts support inline comments, and explicitly invite them (and anyone they share the links with) to leave feedback there — that's a good way to gather input across the whole plan rather than one section at a time.
- Keep the research sources list at the bottom of each document (a "Sources" section) so claims stay checkable.

### 6. Iterate

Treat the first draft as a draft. Invite the user to challenge assumptions, request deeper research on a specific section, or supply real numbers (traction, costs, pricing) to replace estimates. Update the same file in place rather than creating new versions, unless the user asks to branch into an alternative direction. When a previously open question gets answered during iteration, update both the relevant section and the Open Questions Log entry — don't leave it marked open once it's resolved. Likewise, when the user answers an RFC's open question, record the choice and reasoning in that `rfcs.md` entry and fold the decision into the relevant plan section instead of leaving both options standing.

Up to eight files can exist per idea by this point in full mode (fewer in Lean mode, below) — don't re-read all of them on every iteration turn. `business-plan.md` already carries a condensed pointer into each companion file (Solution summarizes `use-cases.md`, the IP section summarizes `patent-applications.md`, Risks summarizes `risks.md`, Milestones summarizes `implementation-plan.md`, Financial Projections summarizes `cost-analysis.md`, the Open Questions Log points at `rfcs.md`, and a note near the top points at `agent-context.md`), so it works as its own index. Re-read `business-plan.md` first when resuming work, and only open a specific companion file in full when the user's request is actually about that file's details.

## Lean mode

Two lighter alternatives to the full plan exist — ask which the user wants if it's unclear:

- **One-page canvas** — a genuinely quick gut-check. No fixed procedure: just scale the template down ad hoc to whatever fits on a page.
- **Lean mode** — more than a one-line gut-check but not a commitment to the full eight-document treatment (e.g. "is this idea worth pursuing further" rather than "give me the full plan to raise money on"). Unlike the one-page canvas, this has a concrete, repeatable procedure. Research (step 2) stays exactly as-is — parallel, all tracks — lean mode only changes what gets *written*, not what gets researched:
  - **Output** (step 5): produce a single condensed `business-plan.md` instead of the full file set —
    - Fold `use-cases.md` and `implementation-plan.md` into short sections of the condensed doc instead — a handful of use-case bullets under Solution, a short phased-milestone list under Milestones/Roadmap — rather than the separate files they always get in full mode.
    - Fold any RFC's open question inline into the Open Questions Log, in the same numbered ❓/➡️ format, instead of a separate `rfcs.md`.
    - Only write `risks.md`, `patent-applications.md`, or `cost-analysis.md` as a standalone file if research clears the same bar an RFC entry needs — a genuine blocking finding (a real patent conflict, a saturated market, a real build/operate trade-off) — not just "there's something to say" about the topic. Otherwise cover it briefly inline in the condensed doc's own section (Risks & Mitigations, IP section, Financial Projections cost table) and skip the file.
    - The confirmation gate before drafting (end of step 3) still applies — lean mode changes what gets written, not whether the user confirms the shared understanding first.
  - **Upgrading later**: if the user decides mid-iteration they want the full treatment after all, split the folded sections out into their own files using the templates and what's already been researched — don't restart research from scratch.
  - `agent-context.md` is still produced as its own file in Lean mode, same as full mode — it's the one companion document that's always separate, in every mode, since its whole purpose is being small and separately loadable.

## Notes

- This skill is for research and drafting, not financial or legal advice — say so if the user seems to be treating the projections as guaranteed rather than illustrative.
- Patent research is a landscape scan, not legal advice — the disclaimer belongs in both the business plan's IP section and at the top of `patent-applications.md`, not just one of them. See `references/patent-applications-template.md` for the exact wording; don't restate or paraphrase it elsewhere.
