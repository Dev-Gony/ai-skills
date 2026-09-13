# AI Skills

A personal collection of reusable AI Skills for repeatable workflows, formatting rules, and productivity patterns.

## Repository structure

Each skill lives in its own top-level directory.

    ai-skills/
    |-- AGENTS.md
    |-- README.md
    `-- one-paste-output/
        |-- SKILL.md
        `-- agents/
            `-- openai.yaml

## Repository-wide rules

Repository-wide instructions are defined in `AGENTS.md`.

Key rules include:

- Do not use emojis, emoticons, decorative Unicode symbols, or pictographs in repository content.
- Keep wording concise and practical.
- Prefer copy-paste-friendly output.
- Never commit API keys, tokens, passwords, webhook URLs, or other secrets.

## Skills

### one-paste-output

Returns complete file contents in one copy-paste-ready block per file.

Use cases include requests such as:

- "Give me the full code."
- "Make it possible to copy and paste in one go."
- "Give me the complete file, not a patch."
- "Do not split the code block."

The skill also handles Markdown files that contain their own fenced code blocks by selecting a longer outer fence so the response does not break in the middle.

Path: `one-paste-output/`

## Adding a new skill

Use one directory per skill and include at least:

    skill-name/
    |-- SKILL.md
    `-- agents/
        `-- openai.yaml

Add `scripts/`, `references/`, or `assets/` only when they materially improve the skill.

## Security

Do not store credentials or secrets in this repository.

Use environment variables, GitHub Secrets, or another appropriate secret-management mechanism when a skill needs external credentials.
