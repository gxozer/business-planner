# business-planner

A [Claude Code](https://claude.com/claude-code) skill that researches a business idea and drafts a full business plan: market analysis, competitive landscape, business model, go-to-market strategy, financial projections, and risks — with sources cited and assumptions clearly labeled.

## What it does

Given a business idea (a sentence or two is enough to start), the skill:

1. Asks a few quick intake questions (target customer, stage, geography).
2. Researches the market using web search — market size, competitors, demand signals, trends/regulation, pricing benchmarks — citing sources throughout.
3. Drafts a structured business plan document, clearly flagging anything that's an assumption or estimate rather than a researched fact.
4. Saves it as Markdown in your project (`./business-plans/<idea-slug>/business-plan.md`), and can optionally publish it as a polished, shareable Artifact.
5. Iterates with you from there — refine sections, swap in real numbers, or dig deeper on a specific risk or competitor.

See [`SKILL.md`](./SKILL.md) for the full workflow, and [`references/`](./references) for the research checklist and plan template it draws on.

## Install

**As a personal skill** (available in every project):

```bash
git clone https://github.com/<your-username>/business-planner.git ~/.claude/skills/business-planner
```

**As a project skill** (only for one repo, e.g. as a submodule):

```bash
git submodule add https://github.com/<your-username>/business-planner.git .claude/skills/business-planner
```

Claude Code picks up skills automatically from `~/.claude/skills/` (personal) or `.claude/skills/` (project-local) — no further configuration needed.

## Use

In Claude Code, just describe the idea:

> I've got an idea for a subscription box for specialty coffee roasters in Canada — can you help me research and plan it out?

Claude will recognize this as a business-planning task and invoke the skill. You can also invoke it directly by name if you've given it a slash-command alias, or just ask "use the business-planner skill on this."

## Scope

This skill produces research and drafting output, not financial or legal advice. Market sizing, competitor data, and financial projections are estimates unless you supply real figures — the plan will say so explicitly wherever that applies. Always validate assumptions before acting on them (raising money, signing leases, quitting a job, etc.).

## License

MIT — see [LICENSE](./LICENSE).
