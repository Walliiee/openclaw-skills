# Context Engineering

Frameworks for understanding and optimizing context in AI systems. Sourced from Dharmesh Shah's Context Engineering, Context Quotient, Context Graphs, AI Memory Problem, and Custom Instructions.

---

## The Core Principle: Context is Queen

> "Prompting tells the model how to think, but context engineering gives the model the training and tools to get the job done."

Better context beats a better model. Every time.

---

## Context Quotient (CQ)

### The Formula: Agent Success = IQ × EQ × CQ

- **IQ** = Model intelligence (reasoning, capability)
- **EQ** = How well the agent relates to and works with humans
- **CQ** = How much relevant context the agent has at decision time

**Critical:** This is **multiplicative, not additive**. If CQ = 0, the result = 0, no matter how high IQ is.

### The Thought Experiment
- **Agent A:** 200 IQ genius. Knows nothing about you.
- **Agent B:** 150 IQ brilliant. Knows your business cold.
- **You pick Agent B every time.** Raw intelligence without context is "confident guessing" (aka management consulting 😀).

### What High CQ Looks Like

| Domain | High-CQ Agent Knows... |
|--------|------------------------|
| **Sales** | Top rep's actual closing patterns, pricing exception reasoning, real lost-deal reasons (not CRM dropdowns) |
| **Support** | Angriest detractor's NPS comments, happiest promoter's renewal notes, known issues + workarounds |
| **Marketing** | Brand voice + what messaging works, audience segments + responses, campaign performance history |

### Building High CQ
1. **Capture the right context** — Not just what happened, but *why* (decision reasoning, exception precedents)
2. **Maintain context over time** — Agents must learn from interactions and improve
3. **Connect context across systems** — CRM, analytics, support, internal tools — unified, not siloed
4. **Make context queryable** — "What precedent exists for this?" should get useful answers

### Evaluating Agents (Ask These Questions)
- How much context does it have access to?
- How does it learn about my specific business?
- Can it remember decisions and improve over time?
- Does it connect to the systems where my actual context lives?

---

## Context Engineering (The Evolution from Prompt Engineering)

### The Shift
- **Prompt engineering** (2023) = Learning to ask really good questions
- **Context engineering** (now) = Being a librarian who decides what books someone has access to before they start reading

### How Context Windows Work
- A context window = a big sheet of paper passed to the LLM
- Measured in tokens (~¾ of an English word, ~4 characters)
- Everything goes in: your prompt, conversation history, retrieved docs, tool outputs
- **Limit:** When the window fills, older info gets pushed out

### What Goes Into Context
1. **Conversation history** — Prior prompts + outputs (how AI "remembers" within a chat, like the movie Memento)
2. **RAG (Retrieval-Augmented Generation)** — Find relevant docs, inject them into context. Like a librarian who finds exactly the 5 documents you need.
3. **Tool calling** — LLM signals which tool it wants; app invokes tool, puts results back in context. LLMs don't call tools directly — they request through the application layer.
4. **System messages** — Instructions, persona, rules, constraints
5. **Custom instructions** — Persistent user context injected into every conversation

### What Context Engineers Do
| Activity | Description |
|----------|-------------|
| **Curate** | Decide which documents, memories, APIs matter for each task |
| **Structure** | Layer system messages → tools → retrieved data → user prompt optimally |
| **Compress** | Summarize/chunk to stay under limits while preserving signal |
| **Evaluate** | Measure accuracy, watch for "context dilution" (irrelevant info distracting the model) |

**Key tradeoff:** More context = richer responses, but cost and latency rise linearly with window length.

---

## AI Memory Problem

### The Fundamental Issue
LLMs are like a friend who knows everything about history and science but can't remember your last conversation. Every new conversation = full brain reset to pre-training data.

**Current state:**
- No memory of previous conversations (limited cross-chat features emerging)
- Can't learn preferences over time
- No context about your business, role, or challenges
- Result: Constant re-explaining of the same context

### Current Workarounds (Hacks)
1. **Context window** — Stuffing relevant info into the prompt
2. **RAG** — Vector database + semantic search to find relevant docs and inject them
3. **Custom Instructions** — One-time setup that persists across conversations
4. **Cross-chat memory** — Emerging features in ChatGPT/Claude (limited)

### The Next Frontier: Real AI Memory
- AI systems that learn from every interaction
- Remember preferences, build understanding over time
- Carry context across all conversations and tasks
- Memory will be the defining characteristic separating useful AI from chatbots

---

## Custom Instructions (Practical Setup)

### Why They Matter
- Highest-ROI feature most people ignore
- Set up once → injected into every conversation automatically
- Eliminates constant re-explaining of role, company, style, preferences

### Three Templates to Steal

**1. The Voice & Audience Card**
```
Role & audience: I'm a [job/role] writing for [target audience].
Voice: [concise/direct/data-driven], no hype, no unnecessary jargon.
Structure: Lead with key takeaways, use clear H2 sections, make everything skimmable.
Constraints: Aim for ≤ [N] words unless specified. Define acronyms on first use. Cite sources.
```

**2. Clarify → Outline → Deliver**
```
If my request is ambiguous or missing key details (goal, audience, constraints, context), ask up to 3 clarifying questions — otherwise skip and proceed.
Show a 3-bullet "Approach" outlining your plan, then the full answer.
End with "Assumptions" (bulleted) and "Next steps" (2-3 concrete suggestions).
```

**3. Auto Follow-Ups Mode**
```
End every response with:
- "What I need from you": 1-2 targeted questions to improve next answer
- "Suggested next step": 1 concrete action you can take immediately
If I say "coach me," switch to asking one question at a time about my workflows/goals, then suggest 2 obvious + 2 creative ways to apply AI.
```

---

## Context Graphs (Future — Not Yet Practical)

### The Concept
A system of record for *decisions*, not just data. Captures:
- What inputs were considered
- What policies were evaluated
- What exceptions were granted, who approved, and why
- Decision traces that currently live scattered in Slack, calls, and people's heads

### Why Smart People Are Bullish
- Agents need insider context to handle gray areas
- Decision traces become encoded organizational knowledge
- Stops reliance on oral tradition

### Why Dharmesh Is Skeptical (For Now)
- Most companies are still struggling with **basic data unification**
- Agents themselves are very early, not widely deployed
- Asking companies to capture decision traces before they even have agents at scale = "installing a three-car garage when you don't own a single car"
- **Timeline:** Inevitable, but the "when" depends on adoption curve maturity

### Practical Takeaway
- Context graphs are a "not yet, but soon" opportunity
- Focus on getting your data unified and agents deployed first
- Keep this on your quarterly review radar
