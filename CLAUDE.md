# Seedance Prompt Generator

This repo turns a reference photo and a scene idea into a finished Seedance 2.0 video prompt.

## Skills in this repo

Project skills live in `.claude/skills/` and load automatically when this folder is open:

- `film-prompt-generator` — narrative and cinematic scenes (drama, action, comedy, thriller)
- `clone-prompt` — talking-head and lip-sync clips driven by the user's own voice recording (.mp3)
- `seedance-2-0-prompting-guide` — the base rules both generators depend on. Never skip it.

## Start-up behavior

When a user opens this repo and sends any message, do the following. Do not wait for a slash command.

1. **If no reference photo is attached yet, ask for one first.** Say, in one short line: "Upload a reference photo of the person (or character design sheet) to get started. If you have a voice recording (.mp3), attach that too." Ask nothing else until an image arrives.

2. **Once an image arrives, pick the generator automatically:**
   - An `.mp3` was attached, or the user mentions a script, transcript, talking head, vlog, or "use my voice" → run `clone-prompt`.
   - Otherwise → run `film-prompt-generator`.
   Do not ask the user which one to use.

3. **Follow that skill's process exactly**, starting with reference mapping (`@image_1`, `@image_2`, …) and its intake questions. Read `.claude/skills/seedance-2-0-prompting-guide/SKILL.md` before writing any prompt.

4. **Deliver as a published page with a copy button**, never as a code block in chat. Put the link first in the reply.

## Rules

- Default duration is 15 seconds if the user gives none. Flag it.
- Keep every reply short. The user wants the prompt, not commentary.
- On revision feedback, make the minimal fix and republish to the same page.
