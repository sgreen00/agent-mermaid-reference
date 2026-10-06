# Mermaid Reference — Agent Skill

**Every Mermaid diagram type in one place — as a git repo and as a loadable agent skill.**

This skill gives agents (and humans) the ground truth for Mermaid syntax: all 33 built-in diagram types, each with its exact keyword, a minimal working example, key features, gotchas, and the Mermaid version it first became available in — plus **renderer version support** (GitHub, Obsidian, mermaid-cli, Live Editor) so diagrams render *where they'll live*, not just where you tested them.

## Why it exists

Mermaid syntax is easy to get subtly wrong (unquoted special characters, unbalanced `end`s, version-gated keywords like `architecture-beta`). This repo is a copy-pasteable reference so an agent can draw correctly on the first try — and so it can check whether the *target renderer's* bundled Mermaid is new enough for the type it picked.

## Repo layout

```
├── LICENSE                    MIT
├── README.md                  this file
├── SKILL.md                   the agent skill (frontmatter + workflow)
└── references/
    ├── mermaid-reference.md   the full type reference (catalog, 33 minimal examples, gotchas)
    └── renderer-support.md    per-renderer version notes + the 10-second `info` check
```

## Use it as an agent skill

Copy this repo into your agent's skill directory (e.g. `~/.agents/skills/mermaid-reference/`) and it's available as the **`mermaid-reference`** skill. It activates on "mermaid", "diagram", and any diagram-type name, and hands the agent the exact keyword + minimal example for the type it needs.

## Use it as a human reference

Open `references/mermaid-reference.md`. Start at the 60-second catalog (or the "Which one?" guide), jump to the type, copy the example.

## Renderer support at a glance

GitHub and Obsidian bundle **pinned** Mermaid versions — newer diagram types only render on renderers new enough. Check any renderer in 10 seconds:

```mermaid
info
```

Full matrix, version floors, and rules of thumb: `references/renderer-support.md`.

## License

MIT — copy, modify, distribute. See `LICENSE`.
