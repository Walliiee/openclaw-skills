---
name: audience-intelligence-builder
description: Build research-backed audience profiles. Two modes: --content (content audience) and --marketing (buyer persona). Triggers: audience profile, buyer persona, ICP, target audience, who am I writing for, who is my customer.
license: MIT
metadata: {"openclaw": {"emoji": "👥"}}
---

# Audience Intelligence Builder

## Overview

Builds a research-backed profile of a target audience. Two modes:

- **`--content`** — One-page content audience profile. Who you're writing for, what pulls them in, how they talk, what they trust. Feeds into `talking-point-extractor`, `lookalike-content`, and `linkedin-post-workflow`.
- **`--marketing`** — Comprehensive buyer persona. Demographics, psychographics, jobs-to-be-done, buying journey, channel preferences. Built for marketing strategy and positioning.

Both modes use external research. Both produce structured markdown files.

> **Always run in the main workspace session.** This skill needs access to web search and file writes.

## Mode Selection

- User mentions content, writing, LinkedIn, posts, newsletter → `--content`
- User mentions marketing strategy, ICP, buyer persona, sales, campaigns → `--marketing`
- User mentions both → ask: "Are you building this for content creation or marketing strategy?"

## Inputs Required

**Both modes need:**
1. **Target Audience** — who are you trying to reach? (e.g., "SaaS CMOs", "Early-stage startup founders")
2. **Core Topic / Product** — for `--content`: what's the primary topic? For `--marketing`: brief description of what you're selling

## Workflow

### Step 1: Confirm Mode & Collect Inputs

If mode unclear, ask one question. If inputs missing, ask before starting.

### Step 2: Research (Both Modes)

Use `web_search` with "latest" in queries. Conduct 4-7 searches covering:
- Core: audience challenges, pain points, priorities, trusted sources
- Content mode adds: content preferences, terminology, engagement patterns
- Marketing mode adds: demographics, buying decisions, channel preferences, purchase process

**Source quality:** Prioritize industry research firms (Gartner, Forrester, McKinsey), government data, peer-reviewed studies. Use forums for language and pain points, not statistics.

### Step 3: Build the Profile

Synthesize into the output format for the selected mode. **Read `{baseDir}/references/output-formats.md`** for the complete template structures.

Every major claim should reference a source inline.

## Writing Guidelines

**Content mode:** Be specific, not generic. Include data inline. Use their language. Keep to one page. Density beats length. Actionable insights over descriptive ones.

**Marketing mode:** Research-backed (every major claim needs a source). Specific and detailed. Actionable guidance on reaching and converting. Third person about the persona. Never rely solely on assumptions.

## Edge Cases

- **Very niche audience:** Do your best with available data. Flag where you're extrapolating and suggest validation.
- **Broad audience ("marketers"):** Push back. Ask for specific role and seniority level.
- **Missing inputs:** Ask before starting. Both inputs are required.
- **Multiple profiles:** Create separate files per audience. Each is self-contained.

## Delivery

**Content mode:** Save to `{baseDir}/../linkedin-post-workflow/references/audience-profiles/<audience-name>.md`. Brief summary of which sections had strongest research, flag thin areas.

**Marketing mode:** Save to `{baseDir}/../../research/personas/<audience-name>.md`. Brief summary of strongest-evidenced sections, gaps to validate.

## Downstream Skills

**Content mode** feeds into:
- `{baseDir}/../talking-point-extractor` — uses audience profile to filter relevance
- `{baseDir}/../lookalike-content` — needs audience profile as input
- `{baseDir}/../linkedin-post-workflow` — uses audience for targeting

**Marketing mode** feeds into:
- `{baseDir}/../competitive-positioning-analyzer` — customer context for positioning
- `{baseDir}/../linkedin-post-workflow` — targeting context