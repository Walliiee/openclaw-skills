# Courses & Deep Research

Create world-class courses on any topic and conduct McKinsey-style deep research. Includes the course creator prompt (weekly themes + daily hands-on modules) and the 5-component deep research prompt anatomy.

## World-Class Course Creator

Creates a hands-on, no-fluff course for senior marketers. Weekly themes with 5 daily modules (Mon-Fri), each producing a real executive-level deliverable.

**Best model:** o3 (but any model works)

**Note:** ChatGPT has output length limits. For multi-week courses, ask week by week: "Give me the first week" → "Now give me the next week." Or ask it to create a weekly task with notifications.

```
# Role and Objective
You are an elite AI course architect designing a hands-on, no-fluff,
high-leverage learning experience for senior marketers (CMO, VP Growth).
Create a personalized, time-boxed AI-for-marketing course that transforms
how a time-starved executive operates.

# Input Customization (ask before proceeding)
- Topic focus: What specific area of marketing/growth to enhance with AI?
- Experience level: Novice, intermediate, or expert with AI tools?
- Time commitment per week: Max weekly time budget (default: 45 mins)?
- Course duration: How many weeks (e.g., 1, 4, 6)?

# Instructions
- Do NOT include theory, background, or explanations of what AI is
- Every lesson must produce a REAL, executive-level deliverable
- Each week = standalone functional theme

## Weekly Format:

🗓️ Week Theme
A clear strategic function AI can enhance

### Daily Module (M-F):
- Module Title
- Objective: 1-2 crisp learning outcomes
- Brief Insight (300-500 words): CMO-ready, jargon-free clarity on why this matters
- 🧪 Step-by-Step Action Task:
  - Actionable steps (no fluff)
  - Specify tools, datasets, starter files
  - Include example inputs/outputs
- 🧠 Prompt to Run:
  - Usable prompt for GPT-4/Claude that drives the task
- 📦 Tools Used
- 📂 Deliverable Format (Google Doc, Notion page, Figma board, etc.)
- 🧭 Executive Reflection Prompt:
  - One strategic application question

📍 End-of-Week Capstone
- 20-minute integrative task combining week's skills into single deliverable

🧩 CMO Playbook
- 5-7 immediately deployable actions using this week's learnings

# Quality Filters
- Actionability (1-10): Only include tasks scoring 8+
- Expert Authority (1-10): Must draw from elite thinkers or proven case studies (8+)
- Reject anything below both thresholds

# Output Style
- Top-tier consultant coaching high-performing executive team
- No filler, no fluff — smart, high-leverage execution
- Modern, clear, executive tone
```

## Deep Research Prompt Anatomy

5 components for McKinsey-quality research output:

### 1. Context Matters
```
Your role and team (e.g., Marketing Ops, Product, RevOps)
Company size and industry
Who your customers are
Tools/systems you already use
Key goals or challenges
```

Example:
> "I'm a Content Marketing Manager at a 200-person B2B SaaS company targeting mid-market HR leaders. We use HubSpot and Jasper AI today, but we're evaluating new tools to scale content and grow audience faster."

### 2. Clear Assignment
```
The research question or topic
The kind of response (summary, comparison, list)
Timeframe (e.g., next 12 months)
```

### 3. Objectives & Key Metrics
```
Business outcomes you're aiming for
KPIs you're trying to improve (revenue, reply rates, adoption)
```

### 4. Scope & Priorities
```
Must-haves (case studies, pricing info)
What to avoid (tools not for your use case)
Special areas of interest (bleeding-edge tech, integrations)
```

### 5. Deliverable Format
```
Preferred format (report, bullets, table)
Style/tone (strategic, consultant-like, visual-first)
Content preferences (real citations, links, examples)
```

## Deep Research Prompt Template

```
{{CONTEXT: role, team, company, customers, tools, goals}}

{{ASSIGNMENT: research question, response type, timeframe}}

{{OBJECTIVES: business outcomes, KPIs to improve}}

{{SCOPE: must-haves, avoid, special interests}}

{{FORMAT: preferred format, style/tone, citation preferences}}
```

## Internal AI Team (3 Assistants)

Build these three to operate as a solo marketer + AI team:

### 1. Data Strategist
Upload data → get visualizations + insights + actions.
- Turn Google Sheets into interactive dashboards (Claude Opus)
- Move from data analysis to data actions

### 2. Chief of Staff
Tracks projects, flags blockers, surfaces risks.
- ChatGPT Project per initiative with docs/updates/meeting notes
- Run sprints, monthly KPI reviews, ongoing retros
- See `ai-productivity.md` for full setup

### 3. Content Strategist
Plugs into YouTube, podcasts → finds ideas, hooks, angles → turns into content.
- See `content-creation.md` for full pipeline

> "In 2026, a solo marketer + AI assistants will dominate a solo marketer every time." — Kieran Flanagan

## Tools
- **o3 / GPT-5** — Best for course generation (reasoning depth)
- **Claude** — Deep research, data visualization, artifacts
- **Perplexity** — External research with citations
- **ChatGPT Projects** — Chief of Staff setup with persistent context
- **NotebookLM** — Turn docs into podcast-style audio overviews
