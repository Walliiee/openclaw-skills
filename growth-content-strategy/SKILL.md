---
name: growth-content-strategy
description: Dharmesh Shah + Kieran Flanagan toolkit. Routes to reference modules by topic: AEO, AI adoption, GTM, content, agents, prompting. Triggers: AEO, AI growth, Dharmesh, Kieran, content strategy.
license: MIT
metadata: {"openclaw": {"emoji": "📈"}}
---

# Growth Content Strategy
> Dharmesh Shah + Kieran Flanagan combined toolkit

Practical frameworks, mental models, prompts, and playbooks distilled from:
- **Dharmesh Shah** — Founder/CTO @ HubSpot, builder of agent.ai, simple.ai. Strategy, philosophy, AI adoption.
- **Kieran Flanagan** — SVP Marketing @ HubSpot, co-host Marketing Against The Grain. Execution, GTM, content systems.

## LinkedIn Post Workflow Integration

For LinkedIn post creation: loaded in Step 2 (Strategic Framing) of `linkedin-post-workflow`.
- `{baseDir}/references/kieran/content-creation.md` — hooks, structure, content systems
- `{baseDir}/references/dharmesh/content-creation.md` — human moat framing, authenticity, "share what you think"

Load both files in Step 2 for maximum framing coverage.

## How This Skill Works

This is a **router skill**. Based on the user's task, load the relevant reference module(s) from `{baseDir}/references/dharmesh/` or `{baseDir}/references/kieran/` and apply the frameworks within.

**Only load what you need.** Most tasks require 1-2 modules.

## Reference Modules

| Module | Source | File | Use When |
|--------|--------|------|----------|
| **AI Adoption Mastery** | Dharmesh | `{baseDir}/references/dharmesh/ai-adoption-mastery.md` | AI adoption strategy, 60/30/10 framework, daily AI habits, developing AI intuition, keeping up with AI, blank slate mindset |
| **Context Engineering** | Dharmesh | `{baseDir}/references/dharmesh/context-engineering.md` | Context windows, prompt → context engineering evolution, Context Quotient (CQ), context graphs, AI memory problem, RAG, custom instructions, context-first platforms |
| **AEO & AI Search** | Dharmesh | `{baseDir}/references/dharmesh/aeo-ai-search.md` | AI distribution strategy, binary outcomes, deserve-to-rank philosophy, why the distribution shift matters |
| **Agents & Future of Work** | Dharmesh | `{baseDir}/references/dharmesh/agents-future-of-work.md` | AI agent strategy, IQ×EQ×CQ formula, agent managers, LLM evolution, tools→teammates shift, $1B one-person company, career positioning with agents |
| **Content Creation Strategy** | Dharmesh | `{baseDir}/references/dharmesh/content-creation.md` | Content in the AI era, human experience moat, LinkedIn personal brand, authenticity vs AI slop, "share what you think" |
| **Prompting Techniques** | Dharmesh | `{baseDir}/references/dharmesh/prompting-techniques.md` | Meta prompting, metaprompt.com, model selection, ImageGen for business visuals, prompt optimization |
| **AEO & AI Search** | Kieran | `{baseDir}/references/kieran/aeo-ai-search.md` | Answer Engine Optimization, LLM visibility, share of voice, citations, page structure for AI crawlers, SEO → AEO migration |
| **GTM Strategy** | Kieran | `{baseDir}/references/kieran/gtm-strategy.md` | Go-to-market planning, marketing roles for AI era, intent engines, micro-audience campaigns, marketing dashboards/metrics |
| **Content Creation** | Kieran | `{baseDir}/references/kieran/content-creation.md` | Content systems, writing craft, creative teams via AI, YouTube→social repurposing, hooks, talking points |
| **Customer Intelligence** | Kieran | `{baseDir}/references/kieran/customer-intelligence.md` | Digital twin customers, purchase intent simulation (SSR), persona research from real language, customer vocabulary |
| **Competitive Intel** | Kieran | `{baseDir}/references/kieran/competitive-intel.md` | Competitor research, growth forensics, hiring audits, paid ads audits, partnership discovery |
| **AI Productivity** | Kieran | `{baseDir}/references/kieran/ai-productivity.md` | Prompting techniques, daily AI playbook, AI coaching, prompt libraries, memory/context management |
| **Presentations** | Kieran | `{baseDir}/references/kieran/presentations.md` | Marketing presentations using expert frameworks (Dunford, Raskin, Duarte), master prompt system, GenSpark workflows |
| **Video & Ads** | Kieran | `{baseDir}/references/kieran/video-ads.md` | Video ad creation (VEO3 storyboard process), YouTube script outlines, B2B ad templates |
| **Courses & Research** | Kieran | `{baseDir}/references/kieran/courses-research.md` | Course creation for any topic, deep research prompt anatomy (McKinsey-style) |

## Routing Logic

1. Read the user's request
2. Map to 1-2 relevant modules (rarely more)
3. Load those modules with `read`
4. Apply frameworks to the user's specific context

> **AEO Routing Note:** For AEO tactical questions (stats, execution playbooks, page structure, share-of-voice measurement) → use `{baseDir}/references/kieran/aeo-ai-search.md`. For AI distribution strategy or philosophy (binary outcomes, deserve-to-rank thinking, why the distribution shift matters) → load `{baseDir}/references/dharmesh/aeo-ai-search.md` instead or in addition.

### Common Routing Examples

| User Request | Module(s) |
|---|---|
| "Help me adopt AI better" | Dharmesh: AI Adoption Mastery |
| "How should I structure context for my AI tools?" | Dharmesh: Context Engineering |
| "How do I rank in ChatGPT?" | Kieran: AEO & AI Search *(strategic/philosophical angle → also Dharmesh: AEO & AI Search)* |
| "What's the future of AI agents?" | Dharmesh: Agents & Future of Work |
| "LinkedIn content strategy" | Dharmesh: Content Creation Strategy + Kieran: Content Creation |
| "GTM for my new product" | Kieran: GTM Strategy |
| "Build customer personas" | Kieran: Customer Intelligence |
| "Research competitors" | Kieran: Competitive Intel |
| "Create a course on X" | Kieran: Courses & Research |
| "Make a presentation" | Kieran: Presentations |
| "Script a video ad" | Kieran: Video & Ads |
| "Deep research on market Y" | Kieran: Courses & Research |
| "AI adoption + content marketing" | Dharmesh: AI Adoption Mastery + Dharmesh: Content Creation |

## Dharmesh Mental Models (Strategy & Philosophy)

These recur across Dharmesh's modules — use them as framing devices:

- **You^AI** — AI as exponential amplifier, not replacement
- **60/30/10 Rule** — 60% repetition, 30% iteration, 10% experimentation
- **IQ × EQ × CQ** — Agent success is multiplicative (zero context = zero value)
- **Context is Queen** — Better context > better model
- **Blank Slate Advantage** — Assume AI can do more than you think
- **Human Experience Moat** — Share what you think, not just what you've done
- **The PhD Intern** — Treat AI like a brilliant intern with no company context

## Kieran Principles (Execution & Tactics)

- **Show, don't tell** — examples > instructions. Always provide concrete prompts and expected outputs.
- **Data > prompting** — better inputs beat better prompt engineering. Feed real data.
- **Prototype > pitch** — build the thing, don't just propose it.
- **Create > consume** — ship more than you save.
- **AI is the foam mat** — it makes experimentation cheap. Break formulas, take risks.

## Companion Note: Source Routing

Both Dharmesh and Kieran now live in this skill. Routing is based on the **dimension** of the question:

| Dimension | Source | Why |
|-----------|--------|-----|
| Strategy & philosophy | Dharmesh | AI adoption frameworks, context engineering, agent thinking, human experience moat |
| Execution & tactics | Kieran | AEO playbooks, GTM campaigns, content systems, customer personas, competitive intel |
| AEO — strategic/philosophical | Dharmesh | Binary outcomes, deserve-to-rank, distribution shift |
| AEO — tactical/execution | Kieran | Stats, page structure, share-of-voice measurement |
| LinkedIn content — positioning | Dharmesh | Human moat, authenticity, "share what you think" |
| LinkedIn content — hooks & systems | Kieran | Hook engineering, content repurposing, talking points |
| Prompting — meta/context | Dharmesh | Meta prompting, Context Quotient, context-first platforms |
| Prompting — libraries/workflows | Kieran | Prompt libraries, daily AI playbook, AI coaching |

When building a full marketing or content strategy, consider loading modules from **both** sources for maximum coverage.
