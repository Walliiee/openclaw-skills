# Customer Intelligence

Build digital twins of your customers, simulate purchase intent, extract real language from customer data, and create AI-powered feedback loops. Combines behavioral science (SSR technique from PyMC Labs × Colgate research) with practical marketing workflows.

## Digital Twin Customer (4-Step Tutorial)

### Step 1: Collect Real-World Customer Data

Gather from 3 sources (or generate synthetic data for testing):

**a) Sales Call Transcripts (5+)**
```
Act as a B2B SaaS sales rep at {{COMPANY}}. Simulate five 20-minute sales
calls with decision-makers evaluating our {{PRODUCT}}. Each call should include:
- Buyer's role (e.g., VP Marketing, RevOps Lead, Head of Sales)
- Key pain points and goals
- Questions about pricing, ROI, integrations
- Rep's responses and discovery notes
- Natural dialogue (approx. 20-25 turns per call)
Output: Call # | Persona | Company Size | Transcript
```

**b) Reviews / Case Studies / G2 Quotes**
```
Act as a research assistant analyzing public user sentiment for {{PRODUCT}}.
Synthesize 25 realistic review-style snippets. Mix:
- 50% positive, 30% neutral/mixed, 20% negative
For each: Persona | Company Size | Sentiment | Quote (1-3 sentences) | Theme
Output as markdown table.
```

**c) CRM Notes (Objections, Motivations, Deal Killers)**
```
Create 20 synthetic CRM entries for B2B SaaS deals.
Each entry: Account Name | Industry | Company Size | Contact Role | Stage |
Motivations | Objections | Closed-Lost Notes (2-3 sentence natural CRM log)
Ensure variation across company sizes, roles, stages, reasons for loss.
```

### Step 2: Summarize Behavioral Insights

```
Analyze the following customer data (sales calls, reviews, CRM notes).
Identify recurring motivations, emotional drivers, objections, and buying triggers.
Summarize into 5-7 clear behavioral insights using marketing-friendly language.
For each, add one sentence explaining why it matters for GTM or messaging.
Output: Category | Insight | Why It Matters
```

### Step 3: Create Anchor Statements (SSR Technique)

The SSR (Semantic Similarity Rating) technique: instead of asking AI to rate 1-5, compare free-text responses to anchor statements for realistic intent measurement.

```
Based on the customer insights uploaded, create five anchor statements
representing how a customer might respond to a new product/message —
from "definitely not interested" to "definitely yes."

Statements should:
- Sound like real customer language
- Reflect emotional tone and reasoning
- Be short, clear, natural

Output:
1. Definitely not → [statement]
2. Probably not → [statement]
3. Unsure → [statement]
4. Probably yes → [statement]
5. Definitely yes → [statement]
```

**Example output:**
- Definitely not: "This sounds too complex for our team — not worth switching."
- Probably not: "It's interesting, but I'm not sure it solves our core problem."
- Unsure: "I can see the value, but I'd need proof it integrates with our stack."
- Probably yes: "This could replace two of our current tools — I'd want a demo."
- Definitely yes: "This is exactly what we've been looking for — I'd buy it today."

### Step 4: Build the Digital Twin in Claude Projects

Create a new project: `Digital Twin – {{PERSONA_NAME}}`

**System prompt:**
```
You are a digital twin of {{PERSONA_NAME}}, a {{ROLE}} at a {{COMPANY_TYPE}}.
You make decisions like this persona, based on the following insights:

{{PASTE BEHAVIORAL INSIGHTS FROM STEP 2}}

When you evaluate new marketing messages, products, or campaigns, respond
in your own words — as if you were that buyer.
Then rate your overall likelihood to act using these five anchors:

{{PASTE ANCHOR STATEMENTS FROM STEP 3}}

Always explain your reasoning briefly before giving your rating.
```

**Test it:** Feed it a landing page screenshot, email draft, ad copy, or product description. Get realistic buyer feedback with reasoning + rating.

## 5 Quick Customer Knowledge Prompts

### 1. Digital Twin Role-Play
```
Act as a {{ROLE}} at {{COMPANY_SIZE}} company.
Read this page + email draft and tell me:
- Would you buy? Why/why not?
- What language would flip you?
```

### 2. Persona Research from Real Language
```
Upload: Gong calls, G2/Reddit quotes, win/loss notes.
From these files, list top 10 pains, exact phrases, and 'buy/no-buy' signals.
```

### 3. Differentiated Product Positioning
```
Using this persona summary + these 5 competitor pages, identify 3 defensible
positioning territories and write a category narrative.
```

### 4. Content Outlines from Primary Sources
```
From these transcripts, produce an outline with thesis, pull-quotes, data
cites, and 5 spicy take subheads.
```

### 5. Programmatic Landing Pages from Community Questions
```
Cluster these 300 questions. For each cluster, draft an FAQ landing page:
headline, answer, proof, CTA.
```

## Claude Artifact Use Cases

### Build Interactive Customer Personas
```
I've uploaded customer feedback from different sources. Figure out what types
of customers we have based on actual behavior and problems.
Create an interactive artifact where I can explore each persona and see their
journey. Show goals, frustrations, and include actual quotes.
Make the artifact professionally designed for sharing.
```

### Analyze Paid Campaigns (Interactive Dashboard)
```
I'm running three campaigns targeting different segments. I have Q3 data
showing impressions, clicks, conversions, and spend across social, search, email.
Analyze performance and tell me:
- Which campaigns and channels are working
- Where to reallocate budget for Q4
- What patterns I'm missing across segments
Create a dashboard and analysis report.
Context: Target ROI 300%+. Enterprise customers have 3x higher LTV than SMB.
Industry benchmark 200-250% ROI. Can shift up to 30% of budget.
```

### Content Remixing Hub
```
Repurpose this blog post about {{TOPIC}}:
- LinkedIn carousel, Twitter thread, Email nurture (5 emails),
  Podcast talking points, Infographic outline
Create a beautiful interactive artifact to review everything in one place.
Provide individual files for each format.
```

## Key Insight: SSR Research Finding
> LLMs can simulate human purchase intent with 90% accuracy when using Semantic Similarity Rating instead of numeric scales. Traditional AI surveys fail because models default to "neutral" (3) on 1-5 scales. SSR compares free-text responses to anchor statements — getting realistic variance and reasoning. (PyMC Labs × Colgate-Palmolive)
