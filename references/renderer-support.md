# Mermaid — Renderer Support & Version Notes

Which Mermaid version a renderer bundles determines **which diagram types will render**. This file is the "will it render?" check when you're writing a diagram for a target you didn't test it on.

## The 10-second check: the `info` diagram

Mermaid has a built-in (but undocumented on the main syntax page) diagram type, `info`, that renders the version of the bundled Mermaid. Paste it into a fence at the target platform:

```mermaid
info
```

It renders the bundled version (e.g. `Mermaid 12.1.0`; a `-tiny` suffix appears on reduced builds). GitHub documents this trick at "Checking your version of Mermaid" in their [Creating diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams) page.

**Rule of thumb:** if the diagram renders where you tested it but fails at the target, it's almost always a version floor, not a syntax error.

## Renderer matrix

| Renderer | How its Mermaid version is chosen | How to check | Notes |
|---|---|---|---|
| **GitHub** (READMEs, Issues, PRs, Wikis) | A pinned Mermaid build, updated on GitHub's schedule — lags npm | `info` fence in a **draft commit** (check before you push) | Stable types always render. Newer `-beta` types may fail on GitHub even when they render elsewhere — GitHub won't let *you* pin a version. |
| **Obsidian** (notes) | Mermaid bundled with Obsidian; updated with each Obsidian release | `info` fence in a note; or Help → About for the Obsidian version | Renders `architecture-beta`, `swimlane-beta`, etc. on recent builds. |
| **mermaid-cli / npm** (SVG/PNG exports, CI) | **You control it — pin it** | `npx -y @mermaid-js/mermaid-cli@12.1.0 --version` | Best option for reproducible exports. Pin the version that matches your diagram's floor. |
| **Mermaid Live Editor** (mermaid.live) | Always the latest release | — | Good place to test a new type before committing it to a target. |

## Type version floors

(Also in the 60-second catalog of `mermaid-reference.md`.)

**Stable — renders on any recent Mermaid:** flowchart/graph, sequenceDiagram, classDiagram, stateDiagram(-v2), erDiagram, userJourney, gantt, pie, quadrantChart, requirementDiagram, gitgraph, mindmap, timeline.

**Need ≥ v10.x:** sankey (v10.3.0), xychart (v10.9+), C4 (v10.x+, **experimental**), zenuml (v10.x+).

**Need ≥ v11.x:** packet (v11.0.0), radar (v11.6.0), venn (v11.12.3), ishikawa (v11.12.3), treeView (v11.14.0), wardley (v11.14.0), eventmodeling (v11.15.0), swimlanes (v11.16.0), cynefin (v11.16.0), railroad (v11.16.0), architecture (v11.1.0), block (v11.x), kanban (v11.x), treemap (v11.x).

**Need v12.0+:** usecase, agentflow.

## Rules of thumb

1. **Target unknown → draw in the stable subset** (flowchart, sequence, class, state, ERD, gantt, pie, quadrant, gitgraph, mindmap, timeline, journey). If the type is version-sensitive, check with `info` first.
2. **GitHub is a pinned consumer.** A diagram using a newer type may render on Obsidian or the Live Editor but fail on GitHub. Test new types in a draft commit.
3. **The `-beta` is part of the keyword.** `architecture-beta`, `swimlane-beta`, `venn-beta`, … — you don't strip it.
4. **C4 is experimental.** Syntax can change without notice; pin a Mermaid version for any C4 export you care about.
5. **Mermaid 12 changed the defaults** (ELK layout + new default themes replaced dagre + the old defaults). A valid v11 diagram renders on v12, but it may *look* different.
6. **When in doubt, pin and export via CLI.** `npx -y @mermaid-js/mermaid-cli@12.1.0 -i in.mmd -o out.svg` — the version after `@` is yours to control.
7. **`info` is a real diagram** — not just a GitHub trick. Use it in any Mermaid surface to document which version rendered something.

## Source of truth

- Per-type version tags: <https://mermaid.ai/open-source> (each syntax page tags newer types, e.g. "v11.12.3+")
- Release notes (what shipped when): <https://github.com/mermaid-js/mermaid/releases>
- GitHub rendering docs (incl. the `info` check): <https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams>
