# RFC Template

Most research findings are just facts to report. But sometimes a research track turns up a genuine decision point — multiple viable options with real trade-offs, where picking one silently would paper over a call that's actually the user's to make. For those, draft a lightweight RFC (Request for Comments) entry instead of just stating a conclusion.

Produce this only when there's a real decision with more than one defensible option — not for every finding. If research clearly points one way with no real trade-off, that's a fact for the plan, not an RFC.

## Entry format

One entry per decision point, appended to `rfcs.md`:

### <Decision, phrased as a question — e.g. "Pricing model: per-seat vs. usage-based?">

- **Context**: why this decision matters for this idea specifically, and what triggered it (a research finding, a competitor pattern, a cost trade-off).
- **Options considered**: 2–4 options, each with a one-line trade-off — what you gain, what you give up. Not an exhaustive list; the options that are actually plausible for this idea.
- **Recommendation** *(optional)*: if research points clearly toward one option, say so — but frame it as a recommendation for the user to accept or override, not a decision already made on their behalf.
- **Open question**: the actual question for the user, phrased so it's easy to answer directly. When raised during round two (`SKILL.md` step 3), present it numbered with the recommendation (or a one-line default if none was given above) on its own line — `❓ **Q<n> — <short title>**: <question>` then `➡️ <recommended answer>` — so the user can answer by number instead of composing a reply.

## Where this connects

- Raise each entry's open question during round-two intake (`SKILL.md` step 3), numbered with its recommendation, rather than letting it sit unasked in a file the user might not read closely.
- Once the user answers, resolve the entry: note the choice made and why, and fold the decision into the relevant plan section (pricing, go-to-market, etc.) instead of leaving both options standing.
- Skip producing `rfcs.md` entirely if no research track turns up a genuine multi-option decision — most ideas will have at least one (pricing or channel strategy are common ones), but don't force it.
