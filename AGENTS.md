# agent-scripts

Read this file before changing the repo.

## Structure

- Shared workflow material belongs in the most specific folder:
  `skills/`, `scripts/`, `automations/`, `cron/`, `hooks/`, or `docs/`.
- Shared skills live in `skills/<skill-name>/`.
- Each skill must have `SKILL.md` with YAML front matter containing `name` and a quoted `description`.
- Keep skill-specific helpers inside the owning skill folder, using `scripts/`, `references/`, `assets/`, or `agents/openai.yaml` as needed.
- Keep shared helpers in top-level `scripts/` only when more than one skill or workspace should use them.
- Keep recurring-job prompts and examples in `automations/` or `cron/`, not inside unrelated skill folders.
- Keep `skills.sh.json` updated when adding or removing public skills.

## Style

- Keep skill descriptions short and generic; optimize them for routing.
- Keep skill bodies operational and concise.
- Keep scripts dependency-light and portable.
- Do not include private credentials, account numbers, tokens, or local-only secrets.

## Validation

- Run `scripts/validate-skills` before publishing changes.
