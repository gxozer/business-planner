# business-planner

A [Claude Code](https://claude.com/claude-code) skill that researches a business idea and drafts a full business plan: market analysis, competitive landscape, business model, go-to-market strategy, financial projections, patent/IP landscape, and risks — with sources cited and assumptions clearly labeled.

## What it does

Given a business idea (a sentence or two is enough to start), the skill:

1. Asks a first, quick round of intake questions (idea, target customer, stage, geography), then immediately kicks off market/competitor/patent research in parallel using forked agents — it doesn't wait for a full interview before starting.
2. While that research runs, continues the interview with a more thorough second round (business model, go-to-market, team, financials) tailored to the idea's actual domain — SaaS, physical product, marketplace, service, hardware, or content — and adapts new questions to what the research is actually finding, surfacing a strong competitor or a blocking patent right away rather than waiting for the final draft.
3. Drafts a structured business plan document, clearly flagging anything that's an assumption or estimate rather than a researched fact, and logs every intake question asked alongside its answer (or its open status) in an appendix.
4. Saves it as Markdown in your project (`./business-plans/<idea-slug>/business-plan.md`), always alongside a phased `implementation-plan.md` sequenced by cost/benefit — which includes its own Jira-ready Epic/Story/Sub-task hierarchy as a readable outline, no separate export file — and a `use-cases.md` of concrete Actor → Trigger → Scenario → Outcome scenarios for the target segments (including a couple of edge cases, not just flattering ones), plus companion `patent-applications.md`, `risks.md`, and `rfcs.md` documents when there's enough material to warrant them — `rfcs.md` lays out any genuine multi-option decisions research surfaced (pricing model, channel strategy) as options with trade-offs and an explicit open question, rather than the skill silently picking one — and offers to publish all of them together as polished, commentable Artifacts so you (and anyone you share them with) can leave feedback right on the documents.
5. Iterates with you from there — refine sections, swap in real numbers, or dig deeper on a specific risk, competitor, patent, or phase. `business-plan.md` carries a condensed pointer/summary into each companion file, so it doubles as an index: later sessions re-read it first and only open a specific companion file in full when the request is actually about that file's details, instead of re-reading everything on every turn.

See [`SKILL.md`](./SKILL.md) for the full workflow, and [`references/`](./references) for the research checklist, domain-specific question sets, and the business plan / patent application / risk / implementation plan / RFC / use-case templates it draws on.

## Install

**As a personal skill** (available in every project):

```bash
git clone https://github.com/gxozer/business-planner.git ~/.claude/skills/business-planner
```

**As a project skill** (only for one repo, e.g. as a submodule):

```bash
git submodule add https://github.com/gxozer/business-planner.git .claude/skills/business-planner
```

Claude Code picks up skills automatically from `~/.claude/skills/` (personal) or `.claude/skills/` (project-local) — no further configuration needed.

## Use

In Claude Code, just describe the idea:

> I've got an idea for a subscription box for specialty coffee roasters in Canada — can you help me research and plan it out?

Claude will recognize this as a business-planning task and invoke the skill. You can also invoke it directly by name if you've given it a slash-command alias, or just ask "use the business-planner skill on this."

## Scope

This skill produces research and drafting output, not financial or legal advice. Market sizing, competitor data, and financial projections are estimates unless you supply real figures — the plan will say so explicitly wherever that applies. The patent research is a prior-art landscape scan, not a patentability or freedom-to-operate opinion — consult a registered patent attorney or agent before filing or relying on it. Always validate assumptions before acting on them (raising money, signing leases, filing a patent, quitting a job, etc.).

## License

MIT — see [LICENSE](./LICENSE).
