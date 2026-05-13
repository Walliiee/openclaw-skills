---
name: refactor-for-determinism
description: >-
  Audit and improve OpenClaw skills. Use when reviewing, improving, or creating a skill; debugging why a skill doesn't trigger; "skill audit"; "clean up this skill"; "why isn't this skill triggering".
license: MIT
compatibility: skills-ref optional; validate step degrades gracefully without it
metadata: {"openclaw": {"emoji": "🔬"}}
---

# Skill Improver

Audit existing skills and make them more reliable, triggerable, and maintainable. Also usable when creating a new skill from scratch.

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
1. **Frontmatter** (`name` + `description`) — always in context (~100 tokens)
2. **SKILL.md body** — loaded when skill triggers (aim for <500 lines)
3. **Bundled resources** — read on demand (unlimited size, scripts execute without loading)

---

## Audit Checklist

Run through these in order. Each section produces a finding (pass / needs work / missing).

### 1. Description Quality

The `description` field in frontmatter is the primary trigger mechanism. Check:

- [ ] **Does it say what the skill does AND when to use it?** Both are required.
- [ ] **Does it include realistic trigger phrases?** Think about what the user would actually type. Include Danish variants if relevant.
- [ ] **Is it specific enough to avoid false triggers?** Near-miss queries (related but wrong skill) should NOT match.
- [ ] **Is it pushy enough?** Skills undertrigger more than they overtrigger. Err toward broader matching. Example — instead of "Create LinkedIn posts" write "Orchestrate LinkedIn post creation. Use when: creating a post, drafting content, writing an opslag, any mention of LinkedIn..."
- [ ] **Is it under 200 characters?** AgentSkills spec allows up to 1024, but OpenClaw injects descriptions into every system prompt. At 30 skills, a 400-char description burns ~12K tokens per turn. Trim ruthlessly: one sentence for *what*, one for *when*.
- [ ] **No XML tags in description?** Tags like `<example>` are explicitly forbidden by the spec and break frontmatter parsing.

**Token impact test:** Count description characters. Target: 100–200. Max: 250. If over, the OpenClaw cost per skill is `97 + name_length + description_length + location_length` characters per prompt. Run `scripts/measure.sh <skill-dir>` to get exact counts without guessing.

**Trigger test:** Read the description and ask: "If the user typed [X], would Fenrik reach for this skill?" Try 3 should-trigger and 2 should-not-trigger prompts mentally.

### 2. Structure & Size

- [ ] **SKILL.md exists** with valid YAML frontmatter (name + description)
- [ ] **Under 500 lines?** If over, identify what can move to `references/` with clear pointers. Run `scripts/measure.sh <skill-dir>` for line count.
- [ ] **Progressive disclosure enforced?** AgentSkills loads in 3 tiers:
  1. **Metadata** (`name` + `description`) — always in context, ~100 tokens. Keep descriptions tight.
  2. **Instructions** (SKILL.md body) — loaded on activation. Keep under 500 lines / <5000 tokens.
  3. **Resources** (`references/`, `scripts/`, `assets/`) — loaded on demand only. Move anything non-essential here.
- [ ] **No orphan files?** Every file in the skill directory should be referenced from SKILL.md or a script
- [ ] **File references one level deep?** Spec recommends `references/REFERENCE.md`, not `references/deep/nested/file.md`. Deep nesting wastes context on traversal.

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
- [ ] **Uses `{baseDir}` for sibling references?** The spec provides `{baseDir}` as the skill folder path. Use it instead of hardcoded relative paths like `../other-skill/` or bare filenames that assume CWD.
- [ ] **External dependencies noted?** If the skill needs specific tools, APIs, or models, state them.

### 6. Spec Compliance

Cross-check against the AgentSkills spec and OpenClaw extensions:

**Required frontmatter:**
- [ ] **`name`** — 1-64 chars, lowercase a-z, numbers, hyphens. No leading/trailing hyphen, no consecutive hyphens. Must match folder name. *Anthropic API surface additionally forbids XML tags and the reserved words `anthropic` and `claude`.*
- [ ] **`description`** — 1-1024 chars (but see Section 1 for length guidance). *Anthropic API surface additionally forbids XML tags.*

**Optional frontmatter (add if relevant):**
- [ ] **`license`** — License name or reference to a bundled license file. Confirmed agentskills.io spec field. Add when distributing publicly; safe to omit for private skills.
- [ ] **`compatibility`** — Max 500 chars. Human-readable environment requirements (runtime, packages, network, etc.). Confirmed agentskills.io spec field. Not used for runtime gating — use `metadata.openclaw.requires.*` for that.
- [ ] **`metadata`** — Per agentskills.io spec: a YAML map of string keys to values. For OpenClaw specifically: must be **single-line JSON** (`{"openclaw": {...}}`); YAML block syntax works with standard YAML parsers but may silently fail in OpenClaw's strict parser. For OpenClaw, use `metadata.openclaw` with:
  - `emoji` — for the macOS Skills UI.
  - `homepage` — URL shown in UI. (Also valid as top-level `homepage` field — both locations work.)
  - `os` — platform gate: array of `"darwin"`, `"linux"`, `"win32"`.
  - `skillKey` — overrides which config key is used for lookup.
  - `requires.bins` — all must exist on PATH.
  - `requires.env` — env vars that must be set.
  - `requires.config` — `openclaw.json` paths that must be truthy.
  - `requires.anyBins` — at least one must exist on PATH.
  - `primaryEnv` — ties to `skills.entries.<name>.apiKey`.
  - `install` — installer specs (brew/node/go/uv/download) for the UI.
  - `always: true` — skip all gates, always include.
- [ ] **`allowed-tools`** — Confirmed agentskills.io spec field. Space-separated pre-approved tools. Example: `Bash(git:*) Bash(jq:*) Read`. Experimental — support varies by runtime.

**OpenClaw-specific extensions to verify:**
- [ ] **`user-invocable`** — `false` hides it from slash commands.
- [ ] **`disable-model-invocation`** — `true` keeps instructions out of the agent prompt (still invocable as slash command).
- [ ] **`command-dispatch: tool`** + `command-tool` + `command-arg-mode` — for direct tool dispatch.

**Validation:**
- [ ] **Run `scripts/validate-frontmatter.sh <skill-dir>` or `skills-ref validate ./skill-name` if available.** Catches frontmatter syntax errors, naming violations, and field constraints before runtime.

**OpenClaw loading precedence (highest wins on name conflict):**
1. `<workspace>/skills`
2. `<workspace>/.agents/skills`
3. `~/.agents/skills`
4. `~/.openclaw/skills`
5. Bundled skills
6. `skills.load.extraDirs` (from openclaw.json)

When debugging "wrong skill version loading," check which source level is winning.

**Per-skill config overrides (`openclaw.json` → `skills.entries.<name>`):**
- `enabled: false` — disable the skill entirely
- `apiKey` — string or SecretRef; injected via `primaryEnv`
- `env` — key-value pairs injected only if not already set in process env
- `config` — arbitrary per-skill fields for skills that read their own config
- `allowBundled` — allowlist for bundled skills only

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
| Spec Compliance | ✅/⚠️/❌ | [what's good or wrong] |

### Recommended Changes
1. [Specific change with reasoning]
2. [...]

### Script Candidates
- scripts/[name] — [purpose, inputs, outputs]
  (currently done manually in SKILL.md lines X-Y)
```

Always show the full findings table before touching any files — the user may want to accept only some changes.

---

## Worked Example

**Target skill:** `notify-slack`
**Issue reported:** "skill never fires when I say anything about Slack"

**Description as found:**
> Send a Slack message using the workspace webhook.

---

### Summary
Functional but invisible — the description has no trigger phrases and omits the "when" clause entirely, so the skill never self-activates.

### Findings
| Area | Status | Detail |
|------|--------|--------|
| Description | ❌ | 50 chars, no trigger phrases, no "when" clause |
| Structure | ✅ | 42 lines, clean |
| Clarity | ⚠️ | No edge case for missing or invalid webhook |
| Determinism | ⚠️ | curl call inline in SKILL.md — no validation, no error output |
| Coordination | ✅ | No overlap with other skills |
| Spec Compliance | ⚠️ | Missing `license`, `requires.env: SLACK_WEBHOOK` |

### Recommended Changes
1. Replace description: `"Send Slack notifications and channel messages. Use when asked to notify Slack, post to a channel, alert the team, or when the user says 'ping Slack', 'drop a note in [channel]', 'let the team know'."` (194 chars)
2. Add `requires.env: SLACK_WEBHOOK` — skill should not load when unconfigured.
3. Move the curl call to `scripts/send.sh`; validate webhook URL and payload before sending.

### Script Candidates
- `scripts/send.sh` — accepts channel + message args, validates `SLACK_WEBHOOK` env var, sends via curl, exits non-zero on failure. Currently inline in SKILL.md with no validation.

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
| Missing `metadata.openclaw` | Skill loads everywhere regardless of env | Add `requires.bins`/`requires.env` gating; write as single-line JSON |
| `metadata` as YAML block | Silently ignored by strict parsers | Use single-line JSON: `{"openclaw": {...}}` |
| Not using `{baseDir}` | Relative paths break if CWD changes | Reference sibling files with `{baseDir}` |
| `name` contains reserved words | Spec violation on Anthropic API surface | Avoid `anthropic` and `claude` in skill names if using the Anthropic API |
| XML tags in `name` or `description` | Forbidden on Anthropic API surface | Remove all `<tag>` patterns before uploading to Anthropic |
| No `license` field | Unclear terms if distributing publicly | Add if publishing via agentskills.io; safe to skip for private skills |
| Skipping validation | Frontmatter errors caught at runtime | Run `scripts/validate-frontmatter.sh` or `skills-ref validate` |
