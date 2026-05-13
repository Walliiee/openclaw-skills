---
name: competitive-positioning-analyzer
description: Analyze competitors' positioning, messaging, pricing, and marketing to find white space and advantages. Triggers: competitive analysis, competitor research, market positioning, battlecard, white space analysis.
license: MIT
metadata: {"openclaw": {"emoji": "⚔️"}}
---

# Competitive Positioning Analyzer

## Overview

This skill creates a comprehensive competitive analysis by researching the user's company, identifying their top 4 competitors, and conducting deep analysis of positioning, messaging, pricing, features, and marketing tactics across all 5 companies.

## Input Required

The user needs to provide only **one input**: their company name or website URL.

**Examples:** "Acme Corp", "https://www.acmecorp.com", "Slack"

The skill automatically researches the company and identifies competitors.

> **Always run in the main workspace session.** This skill needs access to web search and file writes.

## Workflow

### Step 1: Research User's Company

Use `web_search` and `web_fetch` to understand:
- What the company does (products/services)
- Target market and customer segments
- Current positioning and messaging
- Key value propositions
- Product features and capabilities
- Pricing (if publicly available)

Visit key pages: Homepage, About, Product/Services, Pricing.

### Step 2: Identify Top 4 Competitors

Use `web_search` to find competitors:
- "[Company name] competitors"
- "[Company name] alternatives"
- "Companies like [company name]"
- "[Product category] top companies"

**Selection criteria:** Direct competitors, same market category, similar company stage, mix of established and emerging players. Select exactly 4.

### Step 3: Deep Competitor Research

For each competitor, research:
- Company overview, target market, positioning
- Key value propositions and messaging themes
- Product features and differentiators
- Pricing strategy and model
- Marketing channels and GTM approach
- Strengths, weaknesses, customer perception
- Recent activity (launches, funding, partnerships)

3-5 searches/fetches per competitor. See `{baseDir}/references/research-best-practices.md` for research strategy details.

### Step 4: Synthesize Analysis

After researching all 5 companies, synthesize into a structured report using the format in `{baseDir}/references/output-format.md`.

**Read `{baseDir}/references/output-format.md`** for the complete report template. The report covers:
- Executive summary
- Your company profile
- Competitive landscape overview
- Competitor profiles (4)
- Comparative analysis (positioning, messaging, features, pricing, GTM)
- Strategic insights (white space, advantages, threats)
- Positioning recommendations
- Action plan (0-30 days, 30-90 days, 90+ days)

## Quality Standards

- Comprehensive research (10-15+ searches total)
- Current information from latest sources
- All claims sourced with URLs
- Objective analysis (fair assessment across all competitors)
- Actionable insights (not just data collection)
- Strategic depth (go beyond surface comparison)

See `{baseDir}/references/research-best-practices.md` for detailed research strategy, source quality guidelines, and analysis depth expectations.

## Response Tone

Analytical, objective, insight-driven, action-oriented. Professional but direct.

## Downstream Skills

- `{baseDir}/../audience-intelligence-builder` — feeds customer context for positioning
- `{baseDir}/../linkedin-post-workflow` — competitive insights inform content angles