---
name: clone-prompt
description: Turn a creator's reference image plus a script/transcript and a voice recording (.mp3) into a Seedance 2.0 / Higgsfield lip-synced AI clone prompt — talking heads, vlog selfies, iPhone-observer shots, multi-cut B-roll — delivered as a published page with a copy button. Use when the user says "clone prompt", "talking head prompt", "lip-sync prompt", "voice prompt", "script to seedance", "use my voice", "vlog selfie prompt", "b-roll prompt", or uploads an mp3 with a script or transcript. Reads the mp3's duration with ffprobe and matches the shot to it. Not for narrative film scenes with invented dialogue — that is /film-prompt-generator.
---

# Clone Prompt

A system for turning a creator's reference image and their own dialogue (or a no-dialogue concept) into single-shot or multi-cut Seedance prompts that work on the first or second try. Every rule here is something that broke or got disproved in real generations.

Different shot types need different rules. The biggest single mistake is treating all shots the same.

## Golden rules

1. **The dialogue is the creator's. You don't rewrite it.** "yo guys so basically I think this is crazy" is the line. Wrap it, don't fix it.
2. **The reference image carries the visuals. Trust it.** `SUBJECT: @image_1.` is enough. Don't describe face, build, hair, eyes — over-describing fights the reference.
3. **Pick one specific choice. Never give Seedance "or".** "A walnut side table," not "a console or side table." Indecision in the prompt becomes ambiguity in the output.
4. **Single continuous shots use prose flow, not timestamps.** Internal `0:00–0:02 / 0:02–0:05` brackets trick the model into cutting. One time bracket in the action header, then prose.
5. **Multi-cut B-roll uses time-bracketed beats explicitly.** Multiple brackets in one ACTION block = explicit cuts. A feature when you want it.
6. **The action header has its own format.** `[time bracket] — [camera angle / position only].` What happens goes in the prose.
7. **Aesthetic in STYLE ANCHOR. Choreography in ACTION.** "Frame locks in place," "subject walks forward" is blocking → ACTION. Lens, lighting feel, grade, camera identity → STYLE ANCHOR.
8. **Lean negative prompts.** Default: `No music, no captions.` Add one only for a known bug in this scene type. Stacking "no plastic skin, no waxy CGI, no AI uncanny" inverse-primes the model toward exactly those.
9. **DELIVERY references the audio file, never describes it.** `Lip-sync driven by @audio_1.` Adding "device mic, off-axis, ambient bleed" makes the model process the audio toward that vibe and muffles clean source. Non-dialogue: `No dialogue.`
10. **The pre-line beat and post-line beat sell talking heads.** A breath before, a held look after. Real comes from the silence around the line.
11. **"Cinematic" is loaded.** It pulls toward camera movement. For a static lock, drop it — use "static," "documentary," "observational."
12. **Detail allocation follows framing.** Wide shots spread the detail budget thin → plasticky faces. Pull in to medium close-up when the face must look real.

## The two shot families

**Family A — single continuous shot.** Talking heads, vlog selfies, oners, walk-throughs. Header: `0:00 to 0:[end] — [camera angle / position]. One continuous take.` Body: flowing prose, dialogue inline with the physical beat it lands on. LOGIC RULE includes "Single continuous shot. No cuts, no jumps, no zoom."

**Family B — multi-cut B-roll.** Montages, packing sequences, mirror sequences. One time-bracketed beat per cut, each with its own camera angle in the header. LOGIC RULE includes "[N]-cut b-roll structure — hard cuts at [timestamps]. All shots locked tripod, no zoom, no pan." Same-angle jump cuts: state "All shots are jump cuts from the SAME locked camera angle and composition — the camera does not move, only time progresses between cuts."

## The master template

Plain text. No markdown in the final output.

```
FORMAT: [duration]s / [single continuous shot OR N-cut b-roll] / [one-line concept]

SUBJECT: @image_1.

WARDROBE: [Match @image_1, plus anything not visible in the reference]

PROPS: [Only if specific named props — suitcase, mic, etc.]

ENVIRONMENT: [Specific setting + lighting + ambient sound]

STYLE ANCHOR: [Aesthetic only — lens, camera identity, grade, lighting style, realism cues. NOT choreography.]

DELIVERY: [Dialogue: "Lip-sync driven by @audio_1." Non-dialogue: "No dialogue."]

LOGIC RULE: [Continuity — shot count, camera behavior, anti-bug cues for this scene type]

NEGATIVE PROMPT: No music, no captions[, plus 1–2 surgical additions for a known bug]

---

ACTION:

[Action header per shot family]

[Prose for oners, beat-blocked for multi-cut]
```

## Tags

Use `@` not brackets — `@image_1`, `@audio_1`. Each tag has one clean job, stated explicitly: `@image_1` identity/wardrobe lock, `@image_2` a specific prop, `@image_3` composition/style. Be explicit about what to take and leave from each: "Composition and framing match @image_3 — color grade does NOT match @image_3, override to golden hour."

**Inspiration-only references** ("this is just for the vibe, don't mention it") are never tagged — extract the qualities and describe them directly in the prompt. Confirm with the creator whether each image is tagged or inspiration.

`@audio_1` appears only in DELIVERY (and the closing line of ACTION for oners). Never describe its character. Natural mid-sentence pauses in the recording can be matched with `...` in the written dialogue.

Full tag patterns, scope-locking and the reference-bleed fix: `references/references-and-scope.md`.

## Duration from the audio

The audio's length sets the generation length. **Measure it — don't guess:**

```
ffprobe -v error -show_entries format=duration -of default=nw=1:nk=1 "voice.mp3"
```

Round up to the next whole second; that is the FORMAT duration and the end of the action header's time bracket. If the audio is shorter than the shot you want, write a closing visual beat for the silence — held look, lingering half-smile, eyes on lens. Never dead air.

No recording yet? Plan from word count: 5–10 words → 5–6s · 11–17 → 7–8s · 18–25 → 10–11s · 26–33 → 13–14s · 34–42 → 15s max. Conversational pace ~2.5–2.7 words/s. Past ~42 words, push back: cut the line or split into two generations.

**Long scripts / transcripts.** When the creator hands you a whole script or a transcript longer than one generation, segment it at natural sentence breaks into chunks of ≤42 words (≤15s), one generation per chunk. Number them, give each its own prompt, and tell the creator the mp3 timestamps to trim each chunk from (each generation takes its own audio file as `@audio_1`). Keep SUBJECT / WARDROBE / ENVIRONMENT / STYLE ANCHOR byte-identical across chunks so the segments cut together; vary only the ACTION prose and, if wanted, the framing. Put all chunks on one page.

## Intake

1. **Confirm the dialogue** exactly as written. Echo it back if long.
2. **Measure the audio** with ffprobe (or plan from word count).
3. **Identify the shot family** — oner or multi-cut.
4. **Identify the style anchor** — locked studio, vlog selfie, iPhone observer, cinematic B-roll, static observational, found-footage frame-as-X. Blocks in `references/style-anchors.md`.
5. **Identify reference scope** for every image — tagged or inspiration-only; which aspects it controls.
6. **Pick decisive specifics** — one surface, one time of day, one gesture, one exit direction.
7. **Apply the realism stack** — pores, freckles, eye moisture, micro-movements. Positive cues only.
8. **Apply the bug stack for this scene type** proactively — `references/bug-inventory.md`.
9. **Match framing to face fidelity** — pull in when the face must look real.
10. **Check composition against post needs** — text overlay planned → left-third / lower-third negative space, without mentioning the text.
11. **Write the prompt in the master template.** Dialogue rules in `references/dialogue-and-composition.md`.

If something is ambiguous, pick and flag it. Ask one question if you must, never ten.

## Delivery

The deliverable is a published Artifact page with a copy button, never a code block. Use `references/page-template.html` (shared house style with `/film-prompt-generator`): keep CSS, JS and structure verbatim; columns become **Cast & wardrobe** · **Anchor & rules** · **Action**; the header chips show duration, family, audio length, word count. The raw plain-text prompt goes in `<script id="raw" type="text/plain">` exactly per the template above. For a long script, one shot-list-style block per chunk, each with its trim timestamps, and the copy button copies all chunks separated by a line of `=====`. Title: 2–4 words specific to the piece. `icon: "film"` on first publish.

In chat: link, the measured audio length and the duration you set, the family and anchor you chose, any decisive picks you made for them, and the one or two bugs you pre-empted.

## Iteration

Diagnose first, match to the bug inventory, fix the one spot. The creator-language → fix table is at the end of `references/bug-inventory.md`.

## Final principles

The creator's words are sacred; the creator's face is sacred — direct the performance around both, invent neither. Trust the references, trust the audio, trust the model on micro-detail. Bugs cluster by scene type — apply the relevant stack before the render, not after. Decisiveness wins. Less prose, more signal: STYLE ANCHOR is aesthetic, ACTION is choreography, LOGIC RULE is rules. Quotes trigger lip-sync; the audio file drives timing; micro-pauses use ellipses.

## References

- `references/style-anchors.md` — the six anchor blocks, diegetic vs operator camera motion, the lighting redundancy stack
- `references/bug-inventory.md` — every recurring failure, its fix stack, and the feedback translation table
- `references/dialogue-and-composition.md` — dialogue performance, detail allocation, text-overlay framing, crowds, already-in-pose vs entering-pose, the decisiveness table
- `references/references-and-scope.md` — multi-reference tagging, inspiration-only handling, scope-locked patterns
- `references/sample-prompts.md` — six complete prompts across the families
- `references/page-template.html` — the page skeleton
