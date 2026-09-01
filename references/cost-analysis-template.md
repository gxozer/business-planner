# Cost Analysis Template

A companion document comparing concrete implementation options and what they actually cost — not the high-level cost structure already in Business Model, but the operational decisions underneath it: which hosting provider, which manufacturer, which third-party service, at what price. Produce this when the idea has genuine build/operate options worth comparing; skip it for an idea with no real infrastructure or production decision to make (e.g. a pure consulting practice).

Pull the relevant categories from the idea's domain (`references/domain-questions.md`) rather than covering all of them:

- **SaaS / software**: cloud hosting (AWS/GCP/Azure/Vercel/Railway/etc.) at relevant scale, managed vs. self-hosted services, third-party API costs (payments, email, auth, analytics).
- **Physical product / hardware**: manufacturing options (in-house vs. contract manufacturer vs. white-label), tooling costs, fulfillment/3PL options.
- **Marketplace**: payment processing options and their fee structures, hosting.
- **Service business**: the software/tooling stack needed to deliver and scale (scheduling, CRM, delivery platform).
- **Content / media**: hosting/CDN, distribution platform fees (app store cuts, platform revenue splits).

## Entry format

One comparison per build/operate decision:

### <Decision — e.g. "Hosting provider">

| Option | Est. cost | Pros | Cons |
|---|---|---|---|
| Option A | $X/month at Y scale | ... | ... |
| Option B | $X/month at Y scale | ... | ... |

- State the scale assumption the cost estimates are based on (e.g. "at 1,000 monthly active users") — costs that don't scale together are useless to compare.
- Label every figure as an estimate with its source and date; prices change and vary by usage pattern.
- Close with a recommendation if one option is clearly better for this idea at its current stage — but frame it as a recommendation, not a foregone conclusion, especially where it doubles as an open decision (see `rfc-template.md` if the trade-off is genuinely close).

## Where this connects

- Feed the chosen or default option's cost into `implementation-plan.md`'s per-phase cost estimates, rather than leaving two disconnected numbers.
- Feed the ongoing operating cost into the Financial Projections cost table in `business-plan.md`.

## Sources

- Every pricing page, calculator, or benchmark used, with the date checked — cloud and manufacturing pricing changes often enough that a stale figure is worse than none.
