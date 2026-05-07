# Competitive Intelligence

Deep competitor research using AI agents (Manus + SimilarWeb), forensic traffic analysis, hiring audits, paid ads audits, and partnership discovery. Turn competitive data into actionable strategy.

## Competitor Research (Forensic Analysis)

Best run with **Manus PRO** (SimilarWeb integration) for real traffic data. Can also adapt for ChatGPT/Claude with publicly available data.

```
You're a seasoned growth strategist and data analyst. Our CMO has commissioned
deep competitive intelligence research on {{COMPETITOR}} to reverse-engineer
their exact growth playbook and identify exploitable weaknesses.

OBJECTIVE
Conduct forensic analysis using:
- Real-time traffic data from SimilarWeb API
- Public commentary, news, strategic announcements
- SEO and content strategy analysis
- Partnership and integration ecosystem mapping
- Funding and M&A activity

RESEARCH FRAMEWORK

1. TRAFFIC FORENSICS
   - Pull 12-month SimilarWeb data (desktop + mobile traffic sources)
   - Identify growing vs declining channels
   - Calculate growth rates and absolute changes
   - Map traffic composition shifts over time

2. GROWTH TACTIC IDENTIFICATION
   - For each growing channel, hypothesize specific tactics driving growth
   - Correlate with funding rounds, product launches, market events
   - Identify what they're doing that competitors aren't

3. STRATEGIC CONTEXT
   - Recent funding rounds and capital deployment
   - Geographic expansion priorities
   - Product evolution and positioning shifts
   - M&A activity and integration strategy
   - Stated strategic goals from leadership interviews

4. VULNERABILITY MAPPING
   - Which channels underperforming or declining?
   - Where overspending to compensate for weaknesses?
   - What market segments neglected?
   - Where is brand positioning creating blind spots?

OUTPUT: 2-page executive report with:

1. EXECUTIVE SUMMARY (3-4 sentences: core strategy, total traffic, focus areas)

2. GROWTH PLAYBOOKS (clustered by theme)
   For each: channel performance data, tactical commentary, confidence score
   (High 90%+ | Medium 70-89% | Low <70%)

3. THE ANTI-{{COMPETITOR}} PLAYBOOK
   3-5 specific disruption strategies exploiting weaknesses
   Prioritize asymmetric advantages
   Include quick wins and long-term plays

TONE: Top-tier strategy consultant presenting to a board. Confident,
data-driven, actionable. No fluff.
```

## Paid Ads Audit

```
Pull {{COMPETITOR}}'s last 30 days of active ads from Meta Ad Library and
LinkedIn Ad Library. Categorize by creative type (static/video/carousel),
hook pattern, and CTA. Flag any new campaigns or messaging shifts.
```

## Hiring Audit

```
Check {{COMPETITOR}}'s careers page and LinkedIn jobs. List open roles by
function. Flag any unusual hiring clusters — these signal where they're
investing ahead of announcements.
```

## Organic Disruption + Paid Supplement Analysis

```
Here's a list of {{BRAND}} competitors. For each one, pull 12-month organic
traffic trends from SimilarWeb. Flag any that dropped organic traffic by more
than 15%. For those, check if paid traffic or ad spend increased in the same
period.

Output table: Company | Organic Trend | Paid Trend | Verdict (Compensating Y/N) |
One-line takeaway on what it signals.

Competitors:
{{COMPETITOR_LIST}}
```

## Partnership Discovery

```
Here's a list of competitors. For each one, pull 12-month referral traffic
sources from SimilarWeb. Flag any that show a new referral source appearing
in the last 6 months that now drives 5%+ of traffic.

Output table: Company | New Referral Source | Traffic Share % | First Appeared |
One-line hypothesis (integration launch, co-marketing deal, acquisition channel,
affiliate program).

Competitors:
{{COMPETITOR_LIST}}
```

## Interactive Dashboards

After any analysis, ask the AI to turn reports into interactive dashboards:
- Manus creates interactive HTML dashboards automatically
- Claude can build artifact dashboards from raw data
- Add annotations for team collaboration

## Tools
- **Manus PRO** — Best for deep research with real SimilarWeb data (expensive credits)
- **Perplexity** — Good for competitor scope/topics identification
- **ChatGPT/Claude** — Works for analysis when you supply the data
- **Meta Ad Library / LinkedIn Ad Library** — Free access to competitor ads

## Key Insight
> Looking at who competitors are hiring is one of the best ways to reverse-engineer their strategy. Hiring clusters signal where they're investing ahead of announcements.
