# OpenClaw Skills

Reusable [OpenClaw](https://github.com/openclaw/openclaw) agent skill modules — structured, deterministic, and ready to drop into any OpenClaw workspace.

## Skills

| Skill | Purpose | Lines |
|---|---|---|
| **refactor-for-determinism** | Audit and improve OpenClaw skills for structure, clarity, determinism, and trigger quality | ~170 |
| **audience-intelligence-builder** | Build research-backed audience profiles — content mode (pain points, triggers, language) or marketing mode (buyer persona, JTBD, buying journey) | ~80 |
| **competitive-positioning-analyzer** | Systematic competitive analysis: positioning, messaging, pricing, features, white space identification | ~90 |
| **growth-content-strategy** | AI growth & marketing toolkit — Dharmesh Shah + Kieran Flanagan frameworks, mental models, and playbooks routed by task | ~140 |
| **memory-capture** | Parse, classify, and route brain dumps to the right workspace files automatically | ~50 |

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
