# Content Creation System

End-to-end system for creating high-performing content using AI — from audience research to hooks to finished posts. Includes the full content pipeline, content ICP creation, creative writing techniques, tiny AI creative teams, and YouTube-to-social repurposing.

## The Full Content System (Pipeline)

Six skills that form a complete content workflow:

1. **Content Scraper** — Collects 5-20 writing samples from any creator (LinkedIn, X, Substack). Feed it a name → clean file of best content.
2. **Style Analyzer** — Analyzes scraped content to extract voice, patterns, structure.
3. **Viral Talking Points** — Researches what audience is discussing now (Reddit, X, web). Real conversations with engagement data.
4. **Hook Creator** — Generates 5 scroll-stopping openers per talking point. Uses psychological triggers: cognitive dissonance, curiosity gaps, surprise via data, narrative tension, loss aversion. Researches what hook patterns are performing in your niche from last 30 days.
5. **Post Enricher** — Finds the story, case study, or authority quote that elevates a post. Searches web for narratives (business, sports, science, history), verifies facts, checks attribution, finds case studies with real numbers.
6. **Content ICP** (see below) — Audience profile stored in memory for all prompts.

## Content ICP Creation (3-Step Process)

### Step 1: Internal Research (Claude + Connectors)

```
Search my Google Drive and email for customer insights for content creation.

SEARCH FOR:
- Customer interviews, sales calls, survey responses
- Win/loss notes or CRM records
- Content performance reports, email campaign results

EXTRACT:
1. CUSTOMER LANGUAGE
   - Problems they mention (5-10 quotes with emotional words)
   - Why they bought or didn't buy
   - Their terms vs your terms

2. CONTENT PERFORMANCE (IF AVAILABLE)
   - What content worked
   - What content influenced purchases

3. BASIC PERSONA INFO
   - Job titles, company size/type

OUTPUT: Summary with persona, challenges, language notes, confidence level
(HIGH 20+ quotes / MEDIUM 10-20 / LOW <10)
```

### Step 2: External Enrichment (Perplexity)

```
I'm creating a content guide for our target persona. Based on internal research:
{{PASTE INTERNAL RESEARCH}}

Research and provide:
1. CONTENT CONSUMPTION HABITS (when, where, how long, triggers)
2. CONTENT PREFERENCES & FORMATS (formats, length, visual vs text)
3. HEADLINES & HOOKS THAT WORK (formulas, emotional triggers, power words)
4. MESSAGING & LANGUAGE GUIDE (jargon, tone, technical depth, credibility markers)
5. TOPICS & ANGLES (hot topics, controversial topics, pain points, future trends)
6. TRUST & CREDIBILITY MARKERS (analysts, thought leaders, publications)
7. CONTENT STRUCTURE PREFERENCES (organization, scanning patterns, CTA preferences)
8. WRITING STYLE EXAMPLES (opening paragraph, CTA, proof point)

Format as: "CONTENT CREATION PLAYBOOK: {{PERSONA}} at {{COMPANY_TYPE}}"
```

### Step 3: Store in Memory

Ask ChatGPT: `Store this description of {{PERSONA}} in memory under ${{VARIABLE_NAME}}`

Then reference in any prompt: `{{$VP_Marketing}}`

## Viral Talking Points Extraction (YouTube → Content)

> For the full talking-point extraction workflow and category definitions (Educational, Spicy Take, Data Nugget, Story Spark), use the `talking-point-extractor` skill.

Kieran's YouTube-specific prompt template:

```
You are a content analyst extracting high-value talking points from YouTube
video transcripts.

Target Audience: {{audience_role}}
Channel: {{YouTube Channel}}
Video: {{YouTube Video}}

OUTPUT: Summary table of all talking points, then detailed extractions grouped
by category.
```

## Tiny AI Creative Team (Billboard/Ad Workflow)

Build a team of AI specialists for creative projects:

### Step 1: Audience Strategist
```
Act as an Audience Strategist.
Research who {{PRODUCT}} is built for.
Pull signals from: site, product pages, help docs, customer stories, YouTube
reviews, Reddit threads, SaaS comparison sites.
Summarise in 5 bullets:
- Who they are (role + seniority)
- Their workflow pain
- What {{PRODUCT}} automates for them
- What outcome they're chasing
- What a billboard/ad must communicate to hit instantly
```

### Step 2: Copywriter (Headline Writer Onboarding)
```
Create a short onboarding doc that teaches a new copywriter how to craft
world-class billboard headlines.
Base it on principles of Ogilvy, Sugarman, Halbert, Bencivenga, and modern
B2B SaaS advertisers.
Cover: core principles, psychological triggers, structure/patterns, timeless formulas.
```

### Step 3: Art Director
```
Create a short onboarding doc for a junior Art Director on how to turn a
headline into a world-class billboard concept.
Base on: Steve Jobs, Paula Scher, Dan Wieden, modern digital brand designers.
Cover: visual hierarchy for 2-second attention, copy→imagery translation,
layout fundamentals, outdoor readability, timeless visual patterns.
```

### Step 4: Brand Guardian
```
Research {{BRAND}}'s current brand style from public sources.
Summarise into a style guide: typography, colour palette, layout/spacing,
iconography/illustration, tone of voice, what makes a visual instantly
feel '{{BRAND}}'.
```

### Step 5: Creative Brief → Headlines → Visual Concept → Image Prompt
Chain the outputs: Brief → Copywriter generates headlines → Art Director creates visual concept → Convert to image generation prompt (Nano Banana/Midjourney/DALL-E).

## 5 Creative Writing Prompts (GPT-5 Optimized)

### 1. Creative Devices Hook Test
```
Generate 10 headline hooks for {{PRODUCT}} to {{ICP}}.
Use a different device for each: contrast, curiosity gap, metaphor, number,
mini-story, paradox, taboo, villain, social proof, future-cast.
≤12 words each. No buzzwords.
```

### 2. Cross-Domain Analogy
```
Explain {{COMPLEX_BENEFIT}} to {{ICP}} using an analogy from a surprising
but fitting domain you choose.
Domain must be unrelated to marketing/business, yet make concept tangible.
~120 words, vivid, concrete, at least one sensory detail.
End with one-sentence CTA. Name the chosen domain in brackets at start.
```

### 3. Tone-Shifting Ad Script
```
You are an elite ad creative strategist.
Product: {{PRODUCT}} | ICP: {{ICP}}

Step 1: Determine the single most compelling core claim for this ICP.
Step 2: Create a 52-second ad (7 clips × 8 seconds for Veo3).
Tone shifts: Clips 1-2: Paranoid | Clips 3-4: Pragmatic | Clips 5-7: Playful + CTA
```

### 4. Category Creation
```
Invent 5 new category names for {{PRODUCT}}.
For each: tagline (≤8 words), 1-sentence origin story, 5-word rallying cry.
Must feel distinct from existing categories.
```

### 5. Constraint Creativity
```
Describe {{PRODUCT}} for {{ICP}} without using {{BANNED_WORDS: brand name,
'AI', 'platform', 'innovative', 'leverage'}}.
Write: one 50-word micro-story, one 6-word title, one 10-word CTA.
Make it specific and sensory.
```

## Content Remixing (Claude)

```
Repurpose this blog post about {{TOPIC}}:
- LinkedIn carousel
- Twitter thread
- Email nurture sequence (5 emails)
- Podcast talking points
- Infographic outline
All content should feel cohesive to brand but fitting for platform.
Create an interactive artifact to review everything in one place.
```

## Gemini 3 YouTube → Social Media Posts

> For category definitions (Spicy Take, Data Nugget, etc.), use the `talking-point-extractor` skill.

```
Role: Social Media Trend Hunter and expert Content Strategist.

Task:
1. Search YouTube for high-signal videos posted in last 4 weeks related to
   '{{TOPIC}}'. Identify 3 highest engaged videos.
2. List the videos (1-3)
3. Analyze each for talking points matching categories: Spicy Take, Data Nugget.

Include timestamps: Start (MM:SS) {first sentence} | End (MM:SS) {last sentence}
```

## Key Principle
> "The gap isn't between marketers who know more and know less. Everyone has access to the same information. The gap is between marketers who consume and marketers who create." — Kieran Flanagan
