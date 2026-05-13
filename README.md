# OpenClaw Skills

Reusable [OpenClaw](https://github.com/openclaw/openclaw) agent skill modules — structured, deterministic, and ready to drop into any OpenClaw workspace.

## Skills

| Skill | Purpose | Lines |
|---|---|---|
| **audience-intelligence-builder** | Build research-backed audience profiles. Two modes: --content (content audience) and --marketing (buyer persona). Triggers: audience profile, buyer persona, ICP, target audience, who am I writing for, who is my customer. | ~80 |
| **competitive-positioning-analyzer** | Analyze competitors' positioning, messaging, pricing, and marketing to find white space and advantages. Triggers: competitive analysis, competitor research, market positioning, battlecard, white space analysis. | ~90 |
| **growth-content-strategy** | Dharmesh Shah + Kieran Flanagan toolkit. Routes to reference modules by topic: AEO, AI adoption, GTM, content, agents, prompting. Triggers: AEO, AI growth, Dharmesh, Kieran, content strategy. | ~110 |
| **memory-capture** | Automatically parse, classify, and route brain dumps to the right workspace files. Use when the user says "remember this", "save this", "add to memory", "save all", "make sure to save", "things to remember", or drops a list of principles, names, insights, book references, ideas, or actionable items to capture. Also triggers when the user shares something at the end of a conversation that should be preserved across sessions. Routes each item to the correct file automatically — no manual decisions needed. | ~30 |
| **refactor-for-determinism** | >- | ~270 |

## Usage

Copy any skill directory into your OpenClaw workspace's `skills/` folder:

```bash
cp -r refactor-for-determinism ~/.openclaw/workspace/skills/
```

Each skill has a `SKILL.md` with frontmatter that OpenClaw reads for automatic triggering. See the [OpenClaw docs](https://docs.openclaw.ai) for details.

## Skill Structure

```
skill-name/
├── SKILL.md          # Instructions + frontmatter (required)
├── references/       # Context loaded on demand
├── scripts/          # Deterministic/repeatable steps
└── assets/           # Templates, icons, fonts
```

## Philosophy

- **Deterministic steps belong in scripts, judgment stays in SKILL.md**
- **Progressive disclosure** — frontmatter always in context, body on trigger, references on demand
- **Description is the trigger** — the most important line in any skill
- **Explanatory over imperative** — "why" beats "MUST"

## License

MIT
