# Skills

A collection of Claude Code skills — reusable slash-command prompts that extend Claude's capabilities within a project.

## Attribution

Three skills in this repo — **grill-me**, **write-a-prd**, and **prd-to-plan** — are derived from work by **[Matt Pocock](https://skills.sh/mattpocock)**, used with his blessing. The originals can be found at https://skills.sh/mattpocock. These have been adapted for use with the Claude Code skills specification.

## Skills

| Skill | Description |
|---|---|
| [grill-me](grill-me/SKILL.md) | Interview the user relentlessly about a plan or design until reaching shared understanding. _(Based on Matt Pocock's skill.)_ |
| [write-a-prd](write-a-prd/SKILL.md) | Create a PRD through user interview, codebase exploration, and module design. _(Based on Matt Pocock's skill.)_ |
| [prd-to-plan](prd-to-plan/SKILL.md) | Turn a PRD into a multi-phase implementation plan using tracer-bullet vertical slices. _(Based on Matt Pocock's skill.)_ |
| [reality-check](reality-check/SKILL.md) | Activate a brutally honest, skeptical architectural partner that stress-tests ideas and assumptions. |
| [review-changes](review-changes/SKILL.md) | Review the latest changes against the project's documented guidelines. |
| [repo-doc-maintainer](repo-doc-maintainer/SKILL.md) | Review recent changes and decide whether project-level documentation needs a high-level update. |
| [ship-check](ship-check/SKILL.md) | Run the standard post-change validation flow (review-changes + repo-doc-maintainer) before final handoff. |

## Structure

```
<skill-name>/
  SKILL.md   ← the skill definition
```

Each skill lives in its own directory at repo root and contains a single `SKILL.md` file with YAML frontmatter (`name`, `description`) followed by the skill prompt body.

## Usage

Install skills into your project via the Claude Code skills system or by copying the relevant `SKILL.md` into your project's skills directory.
