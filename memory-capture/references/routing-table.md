# Routing Table — memory-capture

Maps each input type to target file(s). Apply this table during the Classify step.

## Input Types → Target Files

| Input type | Classification signal | Target file(s) |
|---|---|---|
| Product/business principle | Rule for building or shipping things (NIHS, ha styr på basics, ship ugly) | `products/PRODUCT-PLAN.md` (Building Philosophy section) + daily log |
| Life/personal principle | Rule for living or operating (above-average lower floor, 80/20) | `reference/thinking-framework.md` (Part 1) + daily log |
| Original professional model | The user's own frameworks and mental models | `reference/thinking-framework.md` (Part 2) + daily log |
| Person reference | Name + why relevant | `memory/YYYY-MM-DD.md` (daily log only). Add to `MEMORY.md` only if a new session needs this from day 1 |
| Book/source insight | Insight attributed to a book or source | Route the insight itself (product or life principle), attribute source inline in that file |
| Actionable todo | Something to do in future | `tasks/current.md` |
| Startup-critical fact | Fact a brand-new session needs on day 1 (infra, active projects, preferences) | `MEMORY.md` + daily log |
| Everything | All items regardless of type | `memory/YYYY-MM-DD.md` — ALWAYS, no exceptions |

## Format Reference

### products/PRODUCT-PLAN.md (Building Philosophy) / reference/thinking-framework.md
```
## [Principle Name]

[1-2 sentence explanation of what it means.]

**Source:** [book/person/context if applicable]
**Apply:** [one-line trigger — when to use this principle]
```

### tasks/current.md (canonical task list)
```
- [ ] **[Item name]** — [brief context]
  - Added: YYYY-MM-DD
```

### MEMORY.md (startup-critical only)
- Max 1-2 lines. Link to source file if more detail needed.
- Only add if a new session genuinely needs this from day 1.

### Daily log (`memory/YYYY-MM-DD.md`)
MUST follow this exact structure for AI navigability:

```markdown
# Memory — YYYY-MM-DD (Weekday)

## Decisions
- **[Decision name]** — [What was decided and why]

## What Happened
- [Time/Event] — [Concise summary]

## Key Lessons
1. **[Lesson]** — [What broke/what worked]. Fix: [if applicable].

## Quick Wins
- [Win] — [What got done easily]

## Carry Forward
- [ ] **[Task]** — [Context + priority]. Deadline: [if any].
```

Rules:
- ALWAYS include all 5 section headers, even if empty (write "None today.")
- This structure lets me scan quickly: Decisions first, then events, then learnings, then wins, then tasks
- Write here regardless of where else you route
- Keep entries scannable — I need to find things fast in future sessions

**AI Optimization Check — apply to EVERY item before writing:**
1. **Structure over prose** — Is this a bullet point, not a paragraph?
2. **Pointers over copies** — Does this reference a source instead of duplicating?
3. **Machine-readable** — Are section headers consistent? Is metadata present?
4. **Valid references** — Do all links/paths resolve?
5. **Executable** — Can a future AI agent act on this without asking questions?

If any check fails, rewrite the item before saving.

## Domain-Specific Destinations

These override the general routing above when the item clearly belongs to one of these domains:

| Input type | Classification signal | Target file |
|---|---|---|
| Quote | Inspiring/memorable quote worth keeping | `learning/quotes-pool.md` |
| Forecast | Probability estimate on a future event | `learning/forecast-tracker.md` |
| Learning Q&A | Answer to a learning question, quiz result | `learning/learning-and-interview-readiness.md` (Question Log section) |
| CV/job fact | Work experience, skill, achievement, cert | `skills/cv-builder/cv-master-data.json` |
| Interview prep | Prep note, answer framework, company research | `./interview-prep/` |
| Study note | Content related to active certification/course | `study/` (relevant course folder) |

All of these still go to the daily log as well.

## Deduplication Rule

Before writing to any target file, check if the item (or a near-identical version) already exists there.
- If yes: skip the write, note "already exists" in the confirm output.
- If no: write it.

## Ambiguity Rule

If an item could be a product principle OR a life principle — flag it for the user's decision.
Do not guess. Output: "⚠️ [item] — could be product or life principle. Which file?"
