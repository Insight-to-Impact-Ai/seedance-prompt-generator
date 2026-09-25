# Seedance Prompt Generator

Turn a reference photo and a scene idea into a finished Seedance 2.0 video prompt, delivered as a page with a copy button.

## Use it in 3 steps

1. **Clone or download this repo** and open the folder in the Claude desktop app (or Claude Code).
2. **Send any message.** Claude asks you for a reference photo.
3. **Upload the photo** and describe your scene. Claude asks four quick questions, then gives you a link to the finished prompt. Click **Copy** on that page and paste it into Seedance 2.0 with the same images attached in the same order.

For a talking-head or lip-sync clip, attach your voice recording (.mp3) along with the photo. Claude switches to the clone generator automatically.

## Using it with ChatGPT Codex instead

The same repo works in OpenAI Codex (the CLI or the desktop app) through `AGENTS.md`.

1. Clone or download this repo and open the folder in Codex.
2. Send any message. Codex asks you for a reference photo. Attach it, or give it the file path.
3. Describe your scene. Codex asks the four questions in chat; answer them.
4. Codex writes the finished page to `output/<scene-name>.html`. Open that file in a browser and click **Copy**.

Codex cannot publish a web page, so the page is a local file instead of a link. Everything else is the same. Tested with Codex CLI 0.145 on `gpt-5.5`; if your default Codex model errors, run `codex -m gpt-5.5`.

## What's inside

- `.claude/skills/film-prompt-generator` — narrative and cinematic scenes
- `.claude/skills/clone-prompt` — talking-head and lip-sync clips from your own voice
- `.claude/skills/seedance-2-0-prompting-guide` — the base prompting rules both generators use
- `CLAUDE.md` — tells Claude how to run the flow the moment the folder is opened
