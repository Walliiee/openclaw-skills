---
name: refactor-for-determinism
description: Audit and improve OpenClaw skills — structure, clarity, determinism, description quality, and size. Use when asked to review a skill, improve a skill, refactor a skill, make a skill more reliable, check if a skill is well-structured, or when creating a new skill from scratch. Also use when the user says "skill audit", "clean up this skill", "why isn't this skill triggering", or asks about skill best practices.
---

# Skill Improver

Audit existing skills and make them more reliable, triggerable, and maintainable. Also usable when creating a new skill from scratch.

## When to Use

- Reviewing or improving an existing skill
- Creating a new skill
- Debugging why a skill isn't triggering or producing poor results
- Periodic skill hygiene (run across all skills in `skills/`)

---

## Skill Anatomy (the target structure)

```
skill-name/
├── SKILL.md          (required — instructions + frontmatter)
├── scripts/          (deterministic/repeatable steps)
├── references/       (docs loaded into context as needed)
└── assets/           (templates, icons, fonts used in output)
```

**Three-level loading:**
1. **Frontmatter** (name + description) — always in context (~100 words)
2. **SKILL.md body** — loaded when skill triggers (aim for <500 lines)
3. **Bundled resources** — read on demand (unlimited size, scripts execute without loading)

---

## Audit Checklist

Run through these in order. Each section produces a finding (pass / needs work / missing).

### 1. Description Quality

The `description` field in frontmatter is the primary trigger mechanism. Check:

- [ ] **Does it say what the skill does AND when to use it?** Both are required.
- [ ] **Does it include realistic trigger phrases?** Think about what the user would actually type. Include locale-specific variants if relevant.
- [ ] **Is it specific enough to avoid false triggers?** Near-miss queries (related but wrong skill) should NOT match.
- [ ] **Is it pushy enough?** Skills undertrigger more than they overtrigger. Err toward broader matching. Example — instead of "Create LinkedIn posts" write "Orchestrate LinkedIn post creation. Use when: creating a post, drafting content, writing an opslag, any mention of LinkedIn..."

**Test:** Read the description and ask: "If the user typed [X], would Fenrik reach for this skill?" Try 3 should-trigger and 2 should-not-trigger prompts mentally.

### 2. Structure & Size

- [ ] **SKILL.md exists** with valid YAML frontmatter (name + description)
- [ ] **Under 500 lines?** If over, identify what can move to `references/` with clear pointers
- [ ] **Progressive disclosure?** Large reference material should live in `references/`, not inline
- [ ] **No orphan files?** Every file in the skill directory should be referenced from SKILL.md or a script

### 3. Instruction Clarity

- [ ] **Explanatory over imperative?** "Why" beats "MUST". Explain the reasoning so the model can generalize. If you find yourself writing ALWAYS/NEVER in caps, reframe as explanation.
- [ ] **Examples included?** At least one worked example for the primary workflow
- [ ] **Output format defined?** If the skill produces artifacts, the expected format should be explicit
- [ ] **Edge cases addressed?** What happens when input is missing, ambiguous, or outside scope?

### 4. Determinism Separation

The core principle: **deterministic steps belong in scripts, judgment stays in SKILL.md.**

**Deterministic** (script candidates):
- Validation checks, linting, formatting
- File creation from templates
- Data collection / aggregation
- Version bumps, string replacements
- Git operations, build steps

**Non-deterministic** (keep in SKILL.md):
- Writing content, making creative choices
- Selecting an approach from alternatives
- Interpreting ambiguous input
- Review judgments

For each step in the workflow, ask: "Would two runs of this step produce the same output given the same input?" If yes → script candidate.

**Script rules:**
- One script per responsibility (no mega-scripts)
- Self-contained with clear error messages
- Validate inputs, exit non-zero on failure
- Use relative paths from the skill directory
- SKILL.md calls scripts explicitly — no hidden logic

### 5. Cross-Skill Coordination

- [ ] **Does this skill overlap with another?** If so, one should coordinate (like `linkedin-post-workflow` coordinating sub-skills) rather than duplicating logic.
- [ ] **Are pointers correct?** Verify every file path reference resolves to a real file.
- [ ] **External dependencies noted?** If the skill needs specific tools, APIs, or models, state them.

---

## Audit Output Format

After running the checklist, produce:

```
## Skill Audit: [skill-name]

### Summary
[1-2 sentence overall assessment]

### Findings
| Area | Status | Detail |
|------|--------|--------|
| Description | ✅/⚠️/❌ | [what's good or wrong] |
| Structure | ✅/⚠️/❌ | [what's good or wrong] |
| Clarity | ✅/⚠️/❌ | [what's good or wrong] |
| Determinism | ✅/⚠️/❌ | [what's good or wrong] |
| Coordination | ✅/⚠️/❌ | [what's good or wrong] |

### Recommended Changes
1. [Specific change with reasoning]
2. [...]

### Script Candidates
- scripts/[name] — [purpose, inputs, outputs]
  (currently done manually in SKILL.md lines X-Y)
```

Present findings to the user and **wait for approval before making changes.**

---

## Creating a New Skill

When building from scratch rather than auditing:

### 1. Capture Intent

- What should this skill enable Fenrik to do?
- When should it trigger? (exact phrases the user would use)
- What's the expected output?
- Does it overlap with any existing skill in `skills/`?

### 2. Draft SKILL.md

Write frontmatter (name + description) first — the description is the most important line in the file. Then draft the workflow. Keep it under 500 lines. Use the instruction style from the audit checklist (explanatory > imperative, examples > rules).

### 3. Identify Scripts

Before finalizing, run the determinism check (section 4 above) on every step. Extract script candidates immediately — don't ship a skill with "TODO: script this later."

### 4. Review

Run the full audit checklist on your own draft. Fix issues before presenting to the user.

---

## Common Mistakes

| Mistake | Why It Fails | Fix |
|---------|-------------|-----|
| Description is too vague | Skill never triggers | Add specific phrases and contexts |
| Description is too narrow | Skill only triggers on exact wording | Add variants, Danish phrases, casual phrasings |
| Giant SKILL.md (500+ lines) | Wastes context on every invocation | Move reference material to `references/` |
| Scripting judgment calls | Script outputs wrong answers confidently | Keep interpretation/creativity in SKILL.md |
| One mega-script | Hard to debug, hard to reuse | One script per responsibility |
| Silent script failures | Skill proceeds on bad state | Validate inputs, exit non-zero, print errors |
| Duplicating another skill's logic | Drift, inconsistency | Coordinate via skill calls or shared references |
| MUST/ALWAYS/NEVER overload | Model follows letter, misses spirit | Explain the reasoning instead |
| No examples | Model guesses at output format | Include at least one worked example |
| Orphan files | Wasted disk, confusing for maintenance | Every file referenced from SKILL.md or deleted |
