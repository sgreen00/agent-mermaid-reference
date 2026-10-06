---
name: mermaid-reference
description: |
  Reference for all 33 Mermaid diagram types + renderer version support. Use when creating, editing, or debugging any Mermaid diagram in any context — GitHub READMEs, Obsidian notes, docs, or CI exports. Triggers on "mermaid", "diagram", "flowchart", "sequence diagram", "class diagram", "state diagram", "ERD", "C4", "sankey", "gantt", "pie chart", "xy chart", "architecture diagram", "mindmap", "timeline", "packet", "kanban", "radar", "wardley", "cynefin", "treemap", "venn", "ishikawa", or any other diagram type the user asks for. Provides the exact keyword, a minimal working example, key features, and gotchas per type — plus how to check which Mermaid version the target renderer bundles so the diagram actually renders there.
---

# Mermaid Reference

Ground truth for Mermaid syntax: **33 built-in diagram types**, each with the exact keyword, a minimal working example, key features, and gotchas — plus **renderer version support** so a diagram renders where it will live (GitHub, Obsidian, CLI export), not just where it was tested.

## When to use this skill

- The user asks to **create / draw / reference** any Mermaid diagram.
- The user's diagram **fails to render** or looks wrong — fix it from the per-type gotchas.
- The user asks "how do I draw X in Mermaid?" — answer with the keyword + a minimal example.
- A diagram is heading to a **target renderer not yet verified** (GitHub README, Obsidian note, exported SVG).

## Workflow

1. **Identify the target renderer** — GitHub README? Obsidian note? mermaid-cli SVG export?
2. **Check that renderer's Mermaid version.** Ten seconds: paste the `info` fence into a draft at the target (it renders the bundled version). Rules of thumb and the full matrix live in `references/renderer-support.md`. A diagram type only renders on a Mermaid version new enough for it (see "First available" in the catalog).
3. **Pick the type** from the catalog in `references/mermaid-reference.md` (or use its "Which one?" quick guide).
4. **Copy the minimal example and adapt the text.** Honor the type's gotchas — above all, labels with special characters (`(`, `)`, `{`, `}`, `<`, `>`, `|`, `#`, spaces, commas) **must be quoted** in the node.
5. **Verify the render at the target.** On failure, work back from the gotcha list (unquoted special chars, unbalanced `subgraph`/`end`, unbalanced sequence activations, keyword version floor) — and re-check the version floor if it renders locally but not at the target.

## Files in this skill

- **`references/mermaid-reference.md`** — the full reference: 60-second catalog, "Which one?" guide, general styling, and all 33 types (keyword → example → features → gotchas → version floor).
- **`references/renderer-support.md`** — per-renderer version model, the `info` check, version floors per type, and rules of thumb for cross-renderer work.

## Combining with other skills

- For **diagram packages generated from agent-system code** (code inventory → pattern detection → diagram suite → risks), combine with the **agent-mermaid** skill: agent-mermaid decides *what* to draw (scope, framework, structure); this skill decides *how to write each diagram correctly* (exact syntax per type + renderer support).
