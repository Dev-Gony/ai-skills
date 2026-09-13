---
name: one-paste-output
description: Produce complete copy-paste-ready file contents without fragmenting a file across multiple code blocks. Use when a user asks for a whole file, full code, one-copy output, copy-paste-ready content, or says not to split code blocks. Applies to source code, Markdown, YAML, JSON, configuration files, prompts, and similar text files.
---

# One Paste Output

## Core rule

When providing the contents of a file, make the result usable with one copy-and-paste action per file.

- Output the complete file, not only changed fragments, when the user asks for the full file or asks for copy-paste-ready output.
- Use exactly one fenced code block for each file.
- Do not leave any part of that file outside its code block.
- Put the filename as a plain heading immediately before the block when multiple files are returned.
- Do not split one file into several code blocks for commentary, examples, or sections.
- Preserve the file's intended contents exactly enough that the user can paste it directly into the target file.

## Nested fence handling

A Markdown file may itself contain fenced code blocks. Never let those inner fences terminate the outer response block.

Choose an outer backtick fence longer than every consecutive backtick sequence contained in the file.

Examples:

- If the file contains no triple-backtick fences, an ordinary triple-backtick outer fence is acceptable.
- If the file contains triple-backtick fences, wrap the entire file with four backticks.
- If the file contains four consecutive backticks, use five for the outer fence.

Keep inner fences unchanged. Do not remove valid Markdown code examples merely to simplify the response formatting.

## Multiple files

For multiple requested files, use this structure:

Filename A
[one complete fenced block containing all of Filename A]

Filename B
[one complete fenced block containing all of Filename B]

Each file must require only one copy operation.

## Modification requests

When the user asks to modify an existing file:

- If they ask for the full file, return the complete updated file.
- If they say they are confused by patches or partial snippets, default to the complete updated file.
- If they explicitly ask for only a patch, diff, changed function, or changed lines, honor that request instead.
- Do not use placeholders such as `...existing code...` in a complete-file response.

## Commentary

Keep commentary outside file blocks brief. Do not interrupt a file block with explanations.

If no explanation is needed, provide the filename and complete block directly.

## Validation before responding

Before sending the answer, verify:

1. Every requested file is present.
2. Each file appears in exactly one fenced block.
3. No requested file content appears before or after its block.
4. No placeholders omit unchanged content when a complete file was requested.
5. The outer fence cannot be closed by any fence inside the file.
6. The result can be copied directly into the destination file without reconstructing fragments.
