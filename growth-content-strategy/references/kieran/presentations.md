# Presentations

Create world-class marketing presentations using expert frameworks (Dunford, Raskin, Duarte, Pierri). A 3-phase master prompt system: select type → research expert principles → generate custom presentation prompt. Works best with GenSpark for visual output.

## The System (3 Phases)

### Phase 1: Select Presentation Type

Options:
- A) Product Positioning — market position, differentiation, value props
- B) Marketing Strategy — planning, budget, channel strategy
- C) Product Launch — GTM strategy, launch planning, campaigns
- D) Campaign Performance Review — results, ROI, optimization
- E) Brand Strategy — positioning, messaging, competitive analysis
- F) Customer Insights & Research — market research, personas
- G) Sales Enablement — tools, messaging, competitive intel, training
- H) Executive Marketing Update — delivery, metrics, blockers
- I) Other (specify)

Also provide: target audience, key business objective, time constraints.

### Phase 2: Expert Framework Research

AI identifies 3-5 recognized experts for the selected type, extracts their specific methodologies, and creates 6-8 guiding principles mapped to slide structure.

**Example for Product Positioning:**
- April Dunford → 5-component positioning framework
- Andy Raskin → strategic narrative arc
- Nancy Duarte → executive presentation structure
- Anthony Pierri → use case-based positioning

### Phase 3: Custom Presentation Prompt

Generated prompt references expert frameworks, applies principles to structure, provides slide-by-slide guidance.

## Master Prompt

```
You are an expert marketing presentation strategist. Work through 3 phases.

Phase 1: Presentation Type Selection
[List A-I options above]
Also provide: target audience, key objective, time constraints.

Phase 2: Expert Framework Research & Principle Generation
[CRITICAL]: Once user selects type:
- Identify 3-5 recognized experts for this presentation type
- Extract their specific methodologies
- Create 6-8 guiding principles synthesizing expert approaches
- Map principles to presentation structure

Format:
Principle 1 (from [Expert]): [Guideline]
Application: [How this shows up in slides]

Phase 3: Custom Presentation Creation Prompt
Create detailed prompt that:
- References specific expert frameworks from Phase 2
- Applies each principle to structure
- Provides slide-by-slide guidance
- Includes instructions for incorporating user content

To activate: tell me your presentation type (A-I), target audience,
key objective, and constraints.
```

## Product Positioning Prompt (Example Output)

Expert principles applied:
1. **Start with Best Customers, Not Product** (Dunford)
2. **Frame the Undeniable Market Shift First** (Raskin)
3. **Create Tension: Current State vs Future State** (Duarte)
4. **Position Against Alternatives, Not Just Competitors** (Dunford)
5. **Features as "Magic Gifts" Enabling Promised Land** (Raskin)
6. **Build Toward Memorable "Star Moment"** (Duarte)
7. **Align Positioning with Specific Use Cases** (Pierri)
8. **Create Context That Makes Value Obvious** (Dunford)

Slide structure:
1. **Opening: Strategic Shift** (Principles 2,3) — Old game vs new game + tension
2. **Evidence: Best Customer Success** (Principle 1) — Lead with 2-3 customer stories
3. **Problem Landscape** (Principle 4) — Map alternatives + true cost of status quo
4. **Promised Land** (Principles 3,7) — Specific use case scenario + business outcomes
5. **Magic Gifts** (Principle 5) — Capabilities as enablers, not features
6. **Star Moment** (Principle 6) — Live demo or dramatic before/after evidence
7. **Competitive Context** (Principle 8) — Frame where your strengths are obvious
8. **Path Forward** (Principles 1,7) — Use cases for ICP + implementation pathway

## Executive Marketing Update Prompt (Example Output)

Expert principles:
1. **Big Idea First** (Duarte) — One bold takeaway framing entire update
2. **Strategic Narrative** (Raskin) — Frame around the shift you're trying to win
3. **Plan vs Reality** (Duarte) — Before/after or planned vs actual
4. **Surface Blockers Honestly** (Kim Scott) — What didn't go to plan + why
5. **Highlight Consequences** (Raskin) — Why delays matter strategically
6. **End with Decisive Asks** (Duarte) — 1-2 specific things execs must do

Slide structure:
1. Big Idea Summary (one sentence)
2. Strategy Recap + Strategic Shift
3. What We Said We'd Do (3-5 priorities)
4. What We Actually Did (progress bars, color-coded)
5. Performance vs Plan (metrics: results vs target)
6. Blockers & Risks (root cause + impact)
7. Strategic Implications (what bets are at risk)
8. What We Need From You (binary asks — help execs say yes/no fast)

## Artifact Creation Prompts

### Deep Research (for Product/External Data)
```
Run a deep research project on {{PRODUCT}} covering:
1. ICP (industry, size, role, pain signals, buying triggers)
2. Customer Problem (unmet need in customer's language)
3. Value Proposition (transformation enabled — specific, measurable, emotional)
4. Differentiation (unique strengths tied to customer problems)
5. Category & Competitive Context
6. Proof & Social Credibility (case studies, testimonials, validation)
7. Messaging Architecture (headline, subhead, elevator pitch, 3-5 pillars)
8. Narrative Spine (shift → problems → current solutions fail → what winners need → our product)
Only cite credible external sources. Add citations.
```

### Internal Summary (Claude + Connectors)
```
You are an AI workplace productivity assistant with access to Asana, Google Drive, Email.
Generate a monthly report summarizing work delivered by {{TEAM}} in {{MONTH}},
bucketed under strategic initiatives.
Include: key work delivered, recommended AI automation, risks and delays.
```

## Visual Deck Creation
Take any presentation outline → paste into **GenSpark** with brand style guide → get professional visual deck. GenSpark handles internal decks well when mapped to your formats.

## Tools
- **GenSpark** — Best for turning outlines into visual decks
- **Claude** — Deep research, artifact creation, analysis
- **ChatGPT** — Master prompt system, expert framework research
- **Perplexity** — External data gathering for artifacts
