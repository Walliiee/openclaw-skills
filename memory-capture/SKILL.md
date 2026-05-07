---
name: memory-capture
description: Automatically parse, classify, and route brain dumps to the right workspace files. Use when the user says "remember this", "save this", "add to memory", "save all", "make sure to save", "things to remember", or drops a list of principles, names, insights, book references, ideas, or actionable items to capture. Also triggers when the user shares something at the end of a conversation that should be preserved across sessions. Routes each item to the correct file automatically — no manual decisions needed.
---

# memory-capture

## Workflow

### 1. Parse
Split input into individual items. One item = one thing to save.
Ignore filler words, conjunctions, and source attributions (handle those in the next step).

### 2. Classify
For each item, apply the routing table → `references/routing-table.md`.
Flag ambiguous items (product vs. life principle) instead of guessing.

### 3. Deduplicate
Before writing, check if the item already exists in the target file. Skip if duplicate. Note it in confirm output.

### 4. Write
Write each item to all target files using the format in `references/routing-table.md`.
**Always write to the daily log (`memory/YYYY-MM-DD.md`) regardless of other targets.**

### 5. Confirm
Output a compact summary — one line per item:
```
• [item] → [file(s)]
```
Flag duplicates (skipped) and ambiguous items (needs the user's decision) clearly.

## Reference
- Routing table + formats: `references/routing-table.md`
- Canonical example: `references/example-capture-2026-03-25.md`
