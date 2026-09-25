# Seedance Prompt Generator

This repo turns a reference photo and a scene idea into a finished Seedance 2.0 video prompt. This file is for OpenAI Codex and any other agent that reads AGENTS.md. It mirrors CLAUDE.md.

## Skills in this repo

The skill files live in `.claude/skills/` (the same files are linked from `.agents/skills/`). Read them directly by path; do not depend on automatic skill discovery.

- `.claude/skills/film-prompt-generator/SKILL.md` — narrative and cinematic scenes (drama, action, comedy, thriller)
- `.claude/skills/clone-prompt/SKILL.md` — talking-head and lip-sync clips driven by the user's own voice recording (.mp3)
- `.claude/skills/seedance-2-0-prompting-guide/SKILL.md` — the base rules both generators depend on. Never skip it.

Each skill has a `references/` folder next to it. The SKILL.md says which reference to read when.

## Start-up behavior

When a user opens this repo and sends any message, do the following. Do not wait for a command.

1. **If no reference photo is attached yet, ask for one first.** Say, in one short line: "Upload a reference photo of the person (or character design sheet) to get started. If you have a voice recording (.mp3), attach that too." Ask nothing else until an image arrives. If the user gives a file path instead of an attachment, read the image at that path.

2. **Once an image arrives, pick the generator automatically:**
   - An `.mp3` was attached, or the user mentions a script, transcript, talking head, vlog, or "use my voice" → read and follow `.claude/skills/clone-prompt/SKILL.md`.
   - Otherwise → read and follow `.claude/skills/film-prompt-generator/SKILL.md`.
   Do not ask the user which one to use.

3. **Follow that skill's process exactly**, starting with reference mapping (`@image_1`, `@image_2`, …) and its intake questions. Read `.claude/skills/seedance-2-0-prompting-guide/SKILL.md` before writing any prompt.

4. **Deliver as a page with a copy button.** You do not have a publishing tool, so write the page to `output/<scene-name>.html` using the skill's `references/page-template.html`, then tell the user the file path and that they should open it in a browser and click Copy. Never deliver the prompt only as a code block in chat.

## Tool substitutions

The skills were written for Claude Code and name two tools you do not have. Substitute as follows:

- **`AskUserQuestion`** → ask all four intake questions in one plain chat message. Number the questions, letter the options (a, b, c, d), mark the recommended option, and give each option a one-line preview. Wait for the answers before writing anything.
- **Artifact publish** → write the HTML file to `output/` as described above. On a revision, overwrite the same file. A new scene gets a new file.

## Rules

- Default duration is 15 seconds if the user gives none. Flag it.
- Keep every reply short. The user wants the prompt, not commentary.
- On revision feedback, make the minimal fix and rewrite the same file.
- Never modify the files under `.claude/skills/`. They are the system, not the output.
