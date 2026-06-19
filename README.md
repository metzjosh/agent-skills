# Agent Scripts

Shared agent instructions, skills, scripts, automations, and portable workflow
helpers for Josh/Otto workspaces.

This repo is the canonical place for:

- `AGENTS.md`: repo-level instructions for agents editing this toolkit.
- `skills/`: reusable workflow skills in the Agent Skills format.
- `scripts/`: dependency-light helpers used across projects.
- `automations/`: reusable automation prompts, runbooks, and templates.
- `cron/`: cron job examples, schedules, and recurring-task helpers.
- `hooks/`: local guardrails such as pre-commit validation.
- `docs/`: notes for publishing, syncing, and operating this toolkit.
- `skills.sh.json`: catalog grouping for skill browsers.

## Skills

Skills are the main routing layer. Each `skills/<name>/SKILL.md` starts with
YAML front matter:

```yaml
---
name: skill-name
description: "Short generic trigger phrase."
---
```

Rules:

- Keep descriptions short and generic; optimize for routing, not documentation.
- Keep skill bodies terse and operational.
- Prefer helper scripts under `skills/<name>/scripts/` when a workflow has
  repeatable commands.
- Keep longer context under `skills/<name>/references/`.
- Quote `description` in front matter.
- Validate after edits: `scripts/validate-skills`.

Current skills:

| Skill | Description |
|-------|-------------|
| [tee-time](./skills/tee-time/) | Golf tee time planning with weather-first recommendations |

## Scripts

Top-level `scripts/` is for helpers that are useful across multiple skills or
workspaces. Keep them portable: avoid repo-specific imports, hard-coded local
paths, and credential assumptions.

Current helpers:

- `scripts/validate-skills`: checks every `skills/*/SKILL.md` for required
  front matter and folder/name consistency.

## Automations

Use `automations/` for reusable prompts, runbooks, and templates that describe
agent-operated jobs. Use skill-local `scripts/` when executable code belongs to
one skill, and top-level `scripts/` only when the helper is shared.

## Cron

Use `cron/` for recurring-job examples and schedule notes. Cron entries should
document:

- schedule and timezone
- expected inputs and outputs
- required skill or script
- safety boundaries
- verification and failure reporting

## Installation

To install a skill:

```bash
hermes skills install <skill-url>
```

Or browse the [skills catalog](https://github.com/metzjosh/agent-scripts/tree/main/skills).

## Syncing

Treat this repo as canonical for shared agent workflows. When copying material
into another workspace, preserve the same folder boundaries and keep
repo-specific rules in that downstream repo.

## License

MIT
