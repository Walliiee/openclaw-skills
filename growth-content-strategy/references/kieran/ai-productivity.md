# AI Productivity & Prompting

Prompting techniques for 2026 models, daily AI playbook for executives, elite prompt library generation, personal AI coaching, and memory/context management. The core principle: give models better context, not better instructions.

## 5 Prompting Techniques for 2026

### 1. Show, Don't Tell (Most Powerful)
Instead of writing instructions, show examples.

❌ Weak:
```
Write me a LinkedIn post. Make it punchy and conversational.
Use short sentences. Start with a bold hook.
```

✅ Better:
```
Here are 3 LinkedIn posts that got a lot of engagement for me last month:
[paste example 1]
[paste example 2]
[paste example 3]
Write a new one about {{TOPIC}} in the same style.
```

### 2. Feed Real Data, Get Real Insights
The prompt isn't the magic — the data is.

❌ Generic:
```
Write a cold email to a VP of Marketing pitching my analytics tool.
```

✅ Data-driven:
```
I'm reaching out to {{NAME}}, {{ROLE}} at {{COMPANY}}.
Here's what I know:
- She's been in the role for 18 months (LinkedIn)
- Recently posted about struggling with attribution
- Company just raised Series D, scaling marketing team
- G2 reviews mention "reporting" as a weakness
Write a cold email connecting my tool to her specific situation.
```

**Rule: Spend more time gathering data vs. constructing prompts.**

### 3. Ask Open-Ended, Not Yes/No
Models default to safe middle answers on numeric scales.

❌ Don't: `Rate this headline on a scale of 1-5`

✅ Do:
```
You're a {{ROLE}} at a mid-size SaaS company. You just saw this headline
in your inbox: "{{HEADLINE}}"
What's your gut reaction? Would you open this email? Why or why not?
```

### 4. Make It Edit Itself (Self-Critique Loop)
First drafts are fine. Third drafts after self-critique are actually good.

```
Write a cold email for {{PRODUCT}} targeting {{PERSONA}}.
Now critique your own email. What's weak? What would make someone delete
this immediately? What's missing?
Rewrite it based on your critique.
```

Pro tip: Run the loop across models — give output to another model for critique, then feed feedback to a third.

**Hidden gem question: "What's missing?"** — and "How would you make this better?"

### 5. Store Context in Memory
Store foundational things:
- Working style
- How you like to collaborate
- Audience you write for
- Your blind spots (so AI is always aware of them)

Tell Claude/ChatGPT: `Store this in memory: {{CONTEXT}}`

## Daily AI Playbook (Executive Day-in-the-Life)

### Morning: Start with Clarity

**1. AI Chief of Staff (ChatGPT Project)**
- Create a Project per critical initiative
- Add docs, updates, meeting notes (KPIs, blockers, deliverables)

System instructions:
```
You are my AI Chief of Staff.
- Be clear, concise, insightful
- Ground recommendations in evidence (cite exact doc names)
- Actively surface blind spots
- Challenge my thinking respectfully
- Bring external perspective (case studies, benchmarks)
- Think long-term and systemically
- Prioritize actionability — end with clear next steps
```

Daily prompts:
```
Summarize all key blockers from {{MONTH}}, tell me if a mitigation plan
was cited, if not suggest one.
```
```
Summarize all key metrics missed in {{MONTH}}. Give reasons and tell me
if this is a consistent pattern.
```
```
Highlight mentions of critical or urgent risks from past week of meeting notes.
```

**2. Executive Updates (Custom GPT)**
- Train on your update formats (2-page briefing, slide outline)
- Feed raw notes/metrics → get exec-level updates

### Late Morning: Thinking Big

**3. Strategy Sparring (Red Team)**
```
Red-team this idea: {{BRIEF}}.
Return:
1. Top 5 counter-arguments (with likely evidence)
2. Hidden assumptions + how to test them
3. Pre-mortem: what could go wrong + early warning signals
```

**4. Deck Designer** — Take slide outlines → GenSpark for professional decks

### Afternoon: Creativity & Experiments

**5. Creative Writing** (Claude)
```
Here's my audience profile: {{PASTE}}.
Topic: {{TOPIC}}.
Generate:
- 7 unique takes (ranked)
- 5 counterpoints (with rebuttals)
- 3 punchy debate framings
```

**6. Prototyping** — Lovable / Replit / Claude Code for MVPs

**7. NotebookLM** — Upload project docs → generate audio overview → dial-in Q&A

### Evening: Research & Fun

**8. ICP Content Research (Grok/xAI)**
```
Analyze these ~20 ICP handles {{PASTE}}.
Look at last 90 days.
Return: top topics, formats (thread/video/link), linked domains,
engagement patterns, posting cadence.
Output 5 "make-this-next" briefs.
```

**9. Veo3** — Fun video creation (ChatGPT script → Veo3 → Flow for stitching)

## Elite Prompt Library Generator

Creates an entire prompt library for any marketing discipline:

```
Act as: Prompt Engineer, Expert Marketer, and Strategic Operator.
Task: When I give you a marketing discipline (e.g. SEO, Paid Media, Lifecycle),
create a Prompt Library designed by an elite marketer in that field.

Deliverable (Markdown):
1. Title — "<Discipline> — AI Prompt Library for Marketers"
2. Summary (≤100 words) — How top marketers think, what drives results
3. Winning Mental Models — 5-10 strategies/principles, each with:
   - Name, 1-line description, practical lesson, source/citation
4. Prompt Library — exactly 10 actionable prompts, each with:
   🔧 Prompt <#> — <Goal>
   <Prompt text>
   Why this fits: (≤25 words)
   How they'd use it: (real-world workflow, tool/channel)

Style: Clear, modern, concise, operator-grade.
Sources: Post-2015 (Growth.Design, Reforge, Demand Curve, HubSpot, etc.)

When ready, reply: "Awaiting discipline."
```

## Personal AI Coach (ChatGPT)

### Version 1: Memory-Based Audit
```
You are an AI-Interaction Behavior Analyst with access to ChatGPT memory.

1. Memory-Based Usage Profile (role, patterns, style, goals)
2. Behavioral Pattern Inference (dominant usage types, interaction style)
3. Strengths & Growth Areas (2-3 each)
4. Micro-Tutorial Generator — for each growth area:
   - Title, Why it matters, Mini-Lesson, Prompt Example, How to use it,
     Success Signal

User prompt: "Analyze what you remember about how I use ChatGPT and help me improve it."
```

### Version 2: Full Conversation History Audit
Export Settings → Data Controls → Export Data → use `conversations.json`

```
You are an AI-Interaction Behavior Analyst with access to conversations.json.

1. Purpose Snapshot Table (monthly: Informational/Productivity/Creative/etc.)
2. Behavior Qualifiers Table with examples per month
3. Sankey Flow Summary (purpose shifts month to month)
4. Insight Narrative (~400 words: evolutions, inflection points, strengths, missed opportunities)
5. Operator-Grade Tutorial Playbooks (max 5) with:
   - Title, Snapshot, Winning Mental Models (3-5), Prompt Arsenal (5 prompts),
     Success Marker
```

## Internal AI Team (3 Assistants to Build)

### 1. Data Strategist
Upload data → get visualizations + insights + actions. Move from data analysis to data actions.

### 2. Chief of Staff
Tracks projects, flags blockers, surfaces risks. Creates high-execution culture. (See daily playbook above)

### 3. Content Strategist
Plugs into YouTube, podcasts, finds ideas/hooks/angles → turns into posts, emails, media.

> "In 2026, a solo marketer + AI assistants will dominate a solo marketer every time." — Kieran Flanagan
