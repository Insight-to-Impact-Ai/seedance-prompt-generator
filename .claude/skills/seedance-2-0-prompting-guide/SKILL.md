---
name: seedance-2-0-prompting-guide
description: Write Seedance 2.0 / Higgsfield-style cinematic video prompts — shot-by-shot, any scene, any duration. Use when the user describes a scene they want generated as video, asks for a Seedance prompt, a video prompt, a shot list, or wants an existing video prompt fixed, shortened, or reformatted. Triggers on "seedance", "video prompt", "make a prompt for this scene", "shot by shot", "b-roll prompt", "POV vlog prompt", "turn this into a video prompt", or feedback like "too much", "chill", "be realistic", "too dramatic" on a prior video prompt.
---

# Seedance 2.0 Prompting Guide

A system for turning any scenario into a shot-by-shot cinematic prompt. Works for any scene, any duration, any shot count.

## Process

1. **Understand the scene.** Who's in it, where, what happens, emotional tone, duration, shot count.
2. **Ask only if you must.** Clarifying questions are fine for missing essentials (duration, number of characters, tone). Don't ask about things you can reasonably infer — make a choice and flag it.
3. **Pick the shot count.** Match pacing to emotional intent.
4. **Fill the master template.** Every section, every time, in order.
5. **Write the shots.** Each gets framing, lens, movement, and prose action.
6. **Apply the pre-delivery checklist** before delivering.

Your only job is to translate the user's vision into a precise, AI-readable cinematic prompt. Do not impose your own story ideas. If they give you something weird or sparse, lean in rather than second-guessing.

## The golden rule: respect the clock

**Short durations are tiny. Chill.**

- 5 seconds = one simple beat
- 10 seconds = two or three beats
- 15 seconds = three or four beats, max

If a shot describes 5 actions, it will glitch. If dialogue stuffs 3 lines into 2 seconds, it will feel rushed. Count actions. Count syllables. Be realistic.

When a user says **"too much"**, **"chill"**, or **"be realistic"** — that's the signal that actions or dialogue are overstuffed. Cut, don't rewrite.

## The master template

Plain text only. No markdown formatting in the final output.

```
FORMAT: [duration]s / [shot count] SHOTS / [one-line concept]

SUBJECT: @image_1. [Age, build, hair, distinguishing features, energy/personality]

SECONDARY SUBJECT: @image_2. [Same level of detail, if applicable]

WARDROBE @image_1: [Specific items, colors, accessories]
WARDROBE @image_2: [Same, if applicable]

HERO PROPS: [Named objects. Tag with @image_N if referenced.]

ENVIRONMENT: [Location, time of day, sensory detail. Label (A), (B), (C) if multiple.]

MOOD: [Emotional arc, not just a vibe]

MUSIC: [How the score evolves — or @audio_N if pre-generated audio is attached]

COLOR LOGIC: [Dominant palette + one accent/pop color]

STYLE: [Aesthetic reference + technical specs — DOF, grain, lighting]

LOGIC RULE: [Continuity rules, anti-duplication, prop consistency]

NEGATIVE PROMPT: [Optional — specific things to avoid]

---

SHOT 1 — 0:00 to 0:0X, [FRAMING], [LENS]mm, [MOVEMENT].
[Action in prose. Dialogue inline.]

SHOT 2 — 0:0X to 0:0Y, [FRAMING], [LENS]mm, [MOVEMENT].
[Action]
```

## Hard formatting rules

| Rule | Right | Wrong |
|---|---|---|
| Image tags | `@image_1` | `<<<image_1>>>`, `[image_1]`, `**image_1**` |
| Bold in output | Plain text | `**bold text**` |
| Shot metadata separator | Period + line break | `/` between metadata and action |
| Timestamps | Whole seconds (`0:00 to 0:02`) | Decimals (`0:01.5 to 0:03.2`) |
| Section dividers | `---` between metadata and shots | No divider / walls of text |
| Blank lines | One between shots | Everything stacked together |
| Character tags | Every character gets their own `@image_N` | Reusing `@image_1` for secondary people |

**Tagging rule:** `@image_N` tags are strictly for reference images the user uploaded. One reference image = one tag. If a character has no reference image, they don't get a tag — describe them in prose instead. See `references/reference-mapping.md`.

## Duration and shot count math

The model cannot coherently resolve more than about 2–3 distinct actions per second. Every shot needs room to breathe.

| Shots | Best Avg Shot Duration | Scenario Type |
|---|---|---|
| 1 (oner) | Full scene | Single continuous performance, vlog POV, emotional breakdown, one-take fight, musical number |
| 2–3 | 3s+ each | Slow atmospheric, moody reveal, contemplative |
| 4–6 | ~2–3s each | Standard narrative — setup, turn, resolution |
| 7–9 | ~1.5–2s each | Dialogue-driven, cinematic story |
| 10–14 | ~1–1.5s each | Fast montage, MTV cutting, vlog pacing |
| 15+ | <1s each | Rarely advisable — model struggles below 1s |

**Formula:** `avg shot duration = total duration ÷ shot count`. If the math gives less than 1 second per shot, cut shots or extend duration.

**Picking shot count by emotional intent:**
- Long held emotion (grief, ecstasy, tension) → fewer shots, longer each
- Energy and momentum (action, party, montage) → more shots, faster
- Single continuous performance (singing, fighting, speaking, vlogging) → 1 oner
- Narrative with beats (setup → conflict → climax) → match shot count to beats

## Writing mood, music, color, style

**MOOD — write an arc, not a vibe.**
- Weak: "Scary and tense."
- Strong: "Casual vlog banter sliding into genuine unease, landing on a deadpan punchline."

**MUSIC — describe evolution, or tag @audio_N.**
- Weak: "Dramatic music."
- Strong: "Sparse piano note under ambient room tone. Strings enter at the midpoint, building tension. A single sharp cello stab on the reveal."
- With audio attached: `MUSIC: @audio_1`

**COLOR LOGIC — dominant palette + one accent.**
- Weak: "Colorful."
- Strong: "Warm amber household light in the hallway. Basement staircase dim and cool-toned, but visible — not a black void."
- Watch out: don't say "pitch black" or "black void" unless you genuinely want nothing visible. If the scene needs a staircase or hallway where things still happen, use "dim but visible."

**STYLE — aesthetic + technical specs.** Always include an aesthetic reference (Ultra-Realistic, A24 restraint, found-footage, iPhone vlog), technical specs (DOF, grain, lighting, framing quirks), and what to avoid if relevant ("no fisheye", "no shallow DOF").

## Logic rules — prevent AI failures

| Failure | Rule |
|---|---|
| Duplicate characters | "Only one @image_1 visible in frame at any time." |
| Characters blend together | "@image_1 is visually distinct from the [other character] — different hair, build, face. No duplicates." |
| Wardrobe changes mid-scene | "Same wardrobe across all shots unless specified." |
| POV camera appears in frame | "POV — camera is [device]. The device is never visible in frame." |
| Props appear from nowhere | "The [prop] is produced at SHOT N with a visible motion." |
| Specific identity (card, book, logo) | "The [item] is always the same. No other, ever. Only ONE visible at a time." |
| Subject stops moving in a walking shot | "Walks forward continuously for the full duration." |
| Autofocus hunting in POV | "NO autofocus shifting. Focus stays locked on his face." |

## Dialogue rules

**Good dialogue:** short (1–2 lines per character per shot, max), broken (contractions, hesitations, em-dashes), real, in character.

**Bad dialogue:** long speeches, info-dumps, theatrical or on-the-nose lines, cringe brand mentions.

**When in doubt, cut the dialogue.** Silence plus a face beats a monologue.

**Inline only.** Dialogue lives inside the shot description in double quotes — no separate script format:

> @image_1 sits back, jaw tight. "I'm not doing this again." He stands.

**Dialogue math.** A spoken line takes about 2–3 seconds. If a 4-second shot has 3 lines, it's overstuffed. Count it out.

## Intake

1. **Check duration.** If not stated, ask or default and flag it.
2. **Check characters.** How many? Any reference images?
3. **Check tone.** Comedy, thriller, emotional, action, surreal?
4. **Check pacing.** Fast? Slow burn? Oner?
5. **Check for audio.** Pre-generated audio attached? If yes — use `@audio_N`, don't transcribe. See `references/audio-tagging.md`.
6. **Infer the rest.** Location, wardrobe, music, color — make cinematic choices. The user can correct.

Write the prompt. Deliver cleanly. Let the work speak.

## Pre-delivery checklist

- [ ] FORMAT line at top with duration / shot count / concept
- [ ] Every uploaded reference image is tagged with `@image_N`. Characters without reference images are described in prose (no tag).
- [ ] Wardrobe explicit (items, colors, accessories)
- [ ] Environment has sensory detail
- [ ] MOOD describes an emotional arc
- [ ] MUSIC describes evolution OR tags @audio_N
- [ ] COLOR LOGIC names dominant palette + accent
- [ ] STYLE names aesthetic + technical specs
- [ ] Shot lines use consistent format
- [ ] Each shot has breathing room (≤2–3 distinct actions per second)
- [ ] Total shot durations add up to the stated total duration
- [ ] No `**bold**` markdown
- [ ] No `/` separators in shot lines
- [ ] Dialogue is short and real
- [ ] Dialogue math checks out (2–3 seconds per line)
- [ ] Logic rules prevent known failure modes
- [ ] If POV, device is never in frame + device-specific look is specified
- [ ] If audio attached, @audio_N is tagged and lyrics/words are NOT transcribed
- [ ] Ending lands cleanly

## References

Read these when the scene calls for them:

- `references/camera-language.md` — framing, lens, and movement vocabulary. Read while writing shot lines.
- `references/pov-scenes.md` — POV rules for phone vlogs, smart glasses, camcorders, action cams. Read whenever the scene is shot through a real-world device.
- `references/audio-tagging.md` — how to handle pre-generated audio files, hybrid dialogue cases, POV audio realism.
- `references/reference-mapping.md` — how `@image_N` tags map to uploaded images.
- `references/troubleshooting.md` — common failure modes and fixes, the iteration loop, and the feedback translation guide. Read whenever the user gives feedback on an existing prompt.

## Final principles

**Translate, don't rewrite.** The user has a vision. Your job is precise, cinematic, AI-readable translation.

**Respect the clock.** Short durations are tiny. Count actions. Count words. Be realistic.

**Cut before you add.** A simple shot with rich atmosphere beats a busy shot every time.

**Specificity beats volume.** Three specific sensory details beat a paragraph of vague description.

**When audio is tagged, the shot description stays minimal.** Don't choreograph every lyric beat.

**The user is always right about their own vision.** Suggest, don't impose.
