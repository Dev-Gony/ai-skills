# Repository Instructions

These instructions apply to the entire repository unless a more deeply nested `AGENTS.md` provides more specific rules.

## Output and Writing Rules

- Do not use emojis, emoticons, decorative Unicode symbols, or pictographs in any generated or modified repository content.
- Do not add emojis or emoticons to Markdown files, source code, comments, examples, commit messages, pull request text, or generated documentation.
- Use plain text headings and labels instead of decorative symbols.
- Keep wording concise and practical. Avoid unnecessary repetition and filler.
- Prefer copy-paste-friendly output when providing file contents.
- When presenting a complete file, provide the entire file as one continuous block rather than splitting it into multiple fragments.

## Skill Repository Rules

- Keep one skill per top-level skill directory.
- Every skill must contain `SKILL.md`.
- Every skill must contain `agents/openai.yaml` for UI metadata.
- Keep `SKILL.md` focused on reusable instructions rather than long background explanations.
- Add `scripts/`, `references/`, or `assets/` only when they materially improve the skill.
- Never commit API keys, access tokens, passwords, webhook URLs, or other secrets.

## Change Discipline

- Preserve existing working behavior unless the task explicitly requires a change.
- Prefer small, reviewable changes.
- Check existing repository instructions before editing files.
- If instructions conflict, follow the higher-priority instruction source and the more specific in-scope `AGENTS.md` where applicable.
