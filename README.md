# AI Skills

A personal collection of reusable AI Skills for repeatable workflows, output conventions, and practical productivity patterns.

This repository is used to design, document, version, and improve Skills that can later be packaged and installed in ChatGPT.

## What this repository is for

The goal is to turn repeated instructions and workflows into reusable Skills instead of explaining the same preferences every time.

Examples include:

- enforcing consistent output formats
- making generated files easier to copy and paste
- standardizing beginner-friendly GitHub guidance
- defining repeatable automation project workflows
- storing practical AI usage patterns as reusable assets

The repository also serves as a portfolio of how AI workflows are designed, tested, and improved over time.

## Repository structure

Each Skill lives in its own top-level directory.

    ai-skills/
    |-- AGENTS.md
    |-- README.md
    `-- one-paste-output/
        |-- SKILL.md
        `-- agents/
            `-- openai.yaml

As more Skills are added, the repository will grow like this:

    ai-skills/
    |-- AGENTS.md
    |-- README.md
    |-- one-paste-output/
    |-- github-beginner-guide/
    |-- automation-project-coach/
    `-- ...

## Repository-wide rules

Repository-wide instructions are defined in `AGENTS.md`.

Key rules include:

- Do not use emojis, emoticons, decorative Unicode symbols, or pictographs in repository content.
- Keep wording concise and practical.
- Prefer copy-paste-friendly output.
- When returning a complete file, keep the entire file in one continuous block.
- Keep one Skill per top-level directory.
- Never commit API keys, access tokens, passwords, webhook URLs, or other secrets.

## Available Skills

### 1. one-paste-output

Status: completed and tested

Purpose:

Return complete file contents in one copy-paste-ready block per file.

Useful when a user asks for requests such as:

- "Give me the full code."
- "Make it possible to copy and paste in one go."
- "Give me the complete file, not a patch."
- "Do not split the code block."
- "Write the entire README.md so I can paste it at once."

Main behavior:

- returns the complete requested file instead of partial fragments
- uses one fenced block per file
- avoids placeholders such as `...existing code...`
- defaults to the full file when the user says patches are confusing
- supports multiple files while keeping each file separately copyable
- handles Markdown files that contain their own fenced code blocks by using a longer outer fence

Path: `one-paste-output/`

Core files:

    one-paste-output/
    |-- SKILL.md
    `-- agents/
        `-- openai.yaml

## How a Skill is organized

A basic Skill contains the following files:

    skill-name/
    |-- SKILL.md
    `-- agents/
        `-- openai.yaml

### SKILL.md

The main instruction file for the Skill.

It contains:

- the Skill name
- the description used to determine when the Skill should be selected
- detailed behavior and workflow instructions
- output requirements and validation rules

### agents/openai.yaml

Contains UI metadata used when the Skill is displayed in ChatGPT.

Optional directories may be added when necessary:

    scripts/
    references/
    assets/

Use these only when they materially improve the Skill.

## Development workflow

The basic workflow used in this repository is:

    Identify a repeated problem
            |
            v
    Define expected input and output
            |
            v
    Create the Skill structure
            |
            v
    Write and refine SKILL.md
            |
            v
    Validate the Skill
            |
            v
    Package as skill.zip
            |
            v
    Install in ChatGPT
            |
            v
    Test with real prompts
            |
            v
    Improve based on actual usage

GitHub is used as the source of truth for the Skill files, while packaged ZIP files are used for installation and testing.

## Installing a Skill in ChatGPT

A Skill is not automatically active in ChatGPT just because its source exists on GitHub.

Typical installation flow:

1. Prepare the Skill directory.
2. Validate the Skill.
3. Package the Skill as `skill.zip`.
4. Open the Skills interface in ChatGPT.
5. Upload or install the packaged Skill.
6. Test it in a new conversation.

For example, after installing `one-paste-output`, a prompt such as:

    README.md 전체 내용을 한 번에 복붙할 수 있게 작성해줘.
    중간에 코드블럭 나누지 마.

should trigger the Skill when the request matches its description.

## Adding a new Skill

When adding another Skill:

1. Define the repeated problem it solves.
2. Decide what requests should trigger it.
3. Define the expected input and output.
4. Create one top-level directory for the Skill.
5. Add `SKILL.md`.
6. Add `agents/openai.yaml`.
7. Add optional resources only when necessary.
8. Validate and package the Skill.
9. Test it with realistic prompts.
10. Document the Skill in this README.

Recommended structure:

    new-skill-name/
    |-- SKILL.md
    |-- agents/
    |   `-- openai.yaml
    |-- scripts/       optional
    |-- references/    optional
    `-- assets/        optional

## Planned Skills

Potential future Skills include:

### github-beginner-guide

Guide GitHub beginners with explicit step-by-step instructions such as where to click, what file to edit, how to commit changes, and how to verify the result.

### automation-project-coach

Guide automation projects through small testable stages instead of implementing everything at once.

Possible flow:

    minimum working test
    -> verify result
    -> add one feature
    -> test again
    -> isolate errors
    -> stabilize
    -> move to operational use

Additional Skills will be added when a repeated workflow or preference is worth turning into a reusable instruction set.

## Security

Do not store credentials or secrets in this repository.

Examples of values that must not be committed:

- API keys
- access tokens
- passwords
- Slack webhook URLs
- private authentication files
- personal credentials

Use environment variables, GitHub Secrets, or another appropriate secret-management mechanism when a Skill needs external credentials.

## Current status

The repository currently includes the first completed Skill:

- `one-paste-output`: created, validated, packaged, installed, and tested in ChatGPT

The next step is to add more Skills based on repeated real-world workflows rather than creating Skills only for demonstration purposes.
