# AEO & AI Search Optimization

Playbook for optimizing brand/product visibility in AI engines (ChatGPT, Gemini, Google AI Overviews). AEO is the new SEO — instead of ranking for keywords, you earn citations and share of voice in LLM answers. First-mover advantage is massive.

## Key Stats

- By 2028, LLMs will capture 75% of search traffic share (SEMRush)
- 58.5% of US Google searches end with zero clicks (Datos × SparkToro)
- AI Overviews appear in 54% of Google searches by volume
- 34.5% CTR drop for #1 organic result when AI Overview present (Ahrefs)
- LLM visitors worth 4.4x average traditional organic search visitor
- Reddit: 40.1% of all LLM citations — most cited source across AI search
- ChatGPT: Wikipedia + major news outlets = 54% of all citations
- Google AI Overviews cite blog content 46% of the time
- AI bots now account for up to 20% of total web crawling activity

## 6 Key Facts About AEO

1. **Authority Still Rules** — AI engines rely on Bing/Google results to fetch source links. Transactional SEO still matters. Good SEO → Good AEO.
2. **Citations Matter** — Each LLM favors different sources based on partnerships. Reddit dominates. PR is making a comeback (ChatGPT loves authoritative sources).
3. **Enable the Bots** — OpenAI has 3 crawlers: GPTBot (training), OAI-SearchBot (real-time), ChatGPT-User (on-demand). Make sure they can crawl your site.
4. **Structure Your Pages** — H1 for main topics, H2 for key questions, H3 for supporting details. FAQ/Q&A formats are 3x more likely to be cited.
5. **Write for Questions, Not Readers** — AI models prefer Q&A content. Create many niche versions of product pages answering all question variations.
6. **Measurement is Evolving** — AEO rank trackers exist but can't replicate personalized memory or conversational queries. Use as directional "share of voice" metric.

## Strategy 1: Focus on the Long Tail

LLMs field thousands of ultra-specific questions. The pages that answer those win citations.

### How to Execute:
- **Spin up role-, industry-, and use-case variations** — Create dedicated pages for each high-value slice
- Keep ~70% shared core content, swap in 30% tailored examples, benefits, FAQs
- **Surface unique, proprietary data** — Benchmarks, cost savings, industry case studies, usage patterns

### Why It Works:
LLMs lift snippets, not pages. They quote the first concise answer they trust. Long-tail questions face little competition.

## Strategy 2: Earn Credible Citations

Citations/mentions are your new link-building strategy.

### How to Execute:
- **SEO still matters** — Google AI Overviews favor URLs already in top results for transactional keywords
- **Unique data → press-worthy mini-studies** — Pitch to respected trade journals or Tier-1 outlets (BBC and NYT dominate 80% of news citations in AI Overviews)
- **Community-driven websites** — Reddit (7.4% of Google AI Overview answers), Quora (3.6%), YouTube, LinkedIn
- Build strategies: YouTube channel, Reddit AMAs, Quora Q&A, thoughtful LinkedIn content

## Page Structure for AI Crawlers

```
- Add 6-10 H2s per page, each answering a likely sub-question
- Begin with ≤150-character TL;DR + 3-row stat table
- Present data in multiple formats: HTML table, JSON-LD (Dataset + variableMeasured), downloadable CSV/JSON
- Server-render all key content (JS only for progressive enhancement)
- Static PNG fallback for data visualizations with descriptive alt text
- Edge-cache pages, target TTFB under 100ms
```

## LLM Visibility Optimization Prompt

```
# Role and Objective
You are a strategy assistant trained on research-backed methods for improving
product visibility in AI-driven search results, including Google AI Overviews
and ChatGPT answers.

Your task: take a product description and return a custom LLM optimization plan.

# Instructions
- Ask the user to briefly describe their product (what it does, who it helps,
  what content types support it).
- Build a tailored plan with these sections:

1. Page Structure for Query Fan-Out
   - Add 6-10 H2s per page answering likely sub-questions
   - Begin with ≤150-char TL;DR + 3-row stat table
   - Present data in HTML table, JSON-LD (Dataset + variableMeasured), CSV/JSON

2. Trust Signal Enhancements
   - Publish core stats on high-authority platforms (Wikipedia, Reddit AMAs,
     analyst newsletters)
   - State cohort size, methodology, last updated date in copy + schema markup

3. Crawler Accessibility
   - Server-render key content; JS only for progressive enhancement
   - Static PNG fallback in <picture> with descriptive alt text
   - Edge-cache, TTFB under 100ms

4. Monitoring & Iteration
   - Run daily self-queries for key H2 topics, log citations
   - Track AI Overview appearance and CTR drops

5. Why This Matters (Exec Buy-In)
   - ChatGPT: 5.5B+ visits/month (6th most visited site)
   - AI Overviews in 13.14% of US search results
   - 34.5% position-1 CTR reduction; 58.5% zero-click searches
```

## Brand Visibility Tracking (3-Report System)

### Step 1: Set Your Scope

```
You are a marketing analyst.
Focus Brand: {{BRAND}}

Task:
1) Confirm brand with website + 1-line description
2) Suggest 5-7 direct competitors
3) Suggest 8 topics to track, mixing:
   - Features/capabilities
   - Use cases/problems solved
   - Buyer types
   - Attributes (pricing, ease of use, integrations)

Output:
BrandsToTrack: ["{{BRAND}}", "Competitor 1", ...]
Topics: ["topic 1", "topic 2", ..., "topic 8"]
```

### Step 2: Map Brands ↔ Topics

**Brand → Topics prompt:**
```
You are an impartial marketing analyst.
For each brand in the list below, list the 10 things you most strongly
associate with that brand. Focus on product features, customer types,
problems solved, and qualities.

Brands: {{BRANDS_LIST}}

Output format (JSON):
{ "BrandAssociations": { "Brand": ["1. ...", "2. ...", ...] } }
```

**Topic → Brands prompt:**
```
You are an impartial marketing analyst.
For each topic below, list the 10 brands you most strongly associate
with that topic.

Topics: {{TOPICS_LIST}}

Output format (JSON):
{ "TopicAssociations": { "Topic": ["1. ...", "2. ...", ...] } }
```

### Step 3: Generate 3 Reports

**Report 1 — Your Brand's Visibility** (rank tracker across topics)
**Report 2 — Market Hotlist** (top 3 brands per topic, dominated vs open topics)
**Report 3 — Competitor Contrast** (shared vs unique associations between 2 brands)

See source file `Brand_Visibility_Tool.txt` for full report prompts.

## Monitoring & Iteration
- Run daily self-queries for key topics → log whether your product is cited
- Track AI Overview appearance for target queries
- Monitor CTR drops (signals AI displacement)
- Tools: xFunnel (share of voice), UserBear.ai

## Key Insight
> "SEO isn't dying. It's evolving into TV ads. Everyone sees your ad, and no one clicks it. AI assistants turn search into a billboard." — Kieran Flanagan
