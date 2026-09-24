---
name: film-prompt-generator
description: Turn a scene idea plus character reference images into a finished Seedance 2.0 film prompt, delivered as a published page with a copy button. Use for any narrative or cinematic scene — drama, action, grief, comedy, thriller, parkour, a "007 scene", a "sad scene where the dog dies" — when the user says "film prompt", "seedance film prompt", "film prompt generator", "write me a scene", "make a prompt for this scene", "create a prompt for a [genre] clip", or uploads a character design sheet and describes a scene. Not for talking-head / lip-sync clone prompts driven by a voice file — that is /clone-prompt.
---

# Film Prompt Generator

The workflow layer on top of `seedance-2-0-prompting-guide`. That skill holds the rules of the format; this one holds the process: intake questions, a story with a visible setup, turn and payoff, one complete physical or emotional arc per shot, the extended rule fields, and a published page with a copy button.

**Always load the base guide first:** read `.claude/skills/seedance-2-0-prompting-guide/SKILL.md` (relative to the repo root). Everything below assumes its template, formatting rules, shot-count math, and checklist.

**Then read `references/story-patterns.md`.** The single most common failure of this generator is a prompt that is an activity, not a scene: a man runs and jumps, a man cries, and nothing happens *to* anyone. That file is how to stop it.

## The process, in order

### 1. Map the references

Every uploaded image gets an `@image_N` tag in upload order. Announce the mapping at the top of the reply before anything else (`@image_1 = the man, @image_2 = the old dog`). Read each image.

**Character design sheets** (turnaround grids, multi-panel sheets) are the normal input here. From the sheet, extract and lock:
- Identity: ethnicity, age, build, hair (or shaved), glasses, distinguishing features
- Wardrobe **exactly as shown** — the guide's rule: new reference wardrobe replaces any previous wardrobe. Don't carry a suit from the last prompt into a polo-shirt reference.
- For an animal: breed, age markers, coat colour, distinctive features (greyed muzzle, feathered tail)

Every prompt built from a design sheet carries the anti-sheet rule (see `references/rule-library.md`): no multi-panel layout, no white studio backdrop, no side-by-side duplicates, no on-screen text — "a single live-action scene, not a character sheet."

If the reference smiles broadly and the scene is serious, direct the performance off the smile explicitly.

### 2. Ask the four intake questions — always

Use `AskUserQuestion` with all four questions in one call, each with 3–4 concrete options and a preview, options tailored to the genre the user named. Do this even when the brief seems complete. Patterns and ready-made option sets are in `references/intake-questions.md`.

1. **Setting** — where, and what the space gives you visually
2. **The turn** — the moment the scene changes: what happens, and to whom. Every option must name a second party or a physical rule, because a cast of one has no turn
3. **Shot count** — from the guide's table, with the recommended one marked
4. **Dialogue** — none, one line, a callback line (same line opens and closes), or an exchange

Duration: if the user didn't state one, default to **15s** and flag it in the reply.

### 3. Build the story — on screen, not in an aside

Follow the scene-building procedure in `references/story-patterns.md`:

1. Write the turn in one sentence. If you can't, the intake answers aren't enough yet; pick the most concrete reading and say so.
2. Choose a story engine (reversal, callback line, deadpan button, third party, rule that holds, slow crack, transformation) and name it in the reply.
3. Write **setup, turn, payoff** as three sentences. This is the "What happened" aside on the page, and it is also the spine of the shot list.
4. Cast only the secondary subjects the turn needs, each with three distinguishing features, listed by name under `SECONDARY SUBJECTS`. A scene with one reference image still needs someone or something to play against: an untagged secondary, an off-screen voice, or a physical rule.
5. List the hero props the turn needs and give each a job. A prop with no job goes in `ENVIRONMENT`.
6. If the story moves, letter the environments (A), (B), (C) in the order it moves through them and tag each shot with its letter.

The viewer must be able to reconstruct the story from what is in frame. If a payoff depends on a fact the viewer never sees, move that fact into a prop, a line, or a wardrobe detail on screen. Sad scenes still hinge on one domestic specific (the bowl filled that morning); action scenes still hinge on a coherent route (roof A → roof B one metre lower → service landing, always descending). But the specific has to be visible.

### 4. Plan the shots

- **Each shot is one beat from the three-sentence story.** The turn always gets its own shot. The payoff is always the last shot and ends on a hold: a face, a line, a reveal. Never end on a character simply leaving frame unless the leaving is the point.
- **One complete arc per shot.** A gap jump needs run-up, flight, landing and recovery in one unbroken shot; a cry needs jaw, chin, breath, eyes, tear in one unbroken shot. Never cut mid-movement.
- **Name each shot** for the beat it contains (the keys · the garage · the empty podium · the side door · the taillights). If you can't name it, it's filler — cut or merge it.
- **Geography is coherent and directional.** Screen direction locked in action; one location separated only by light in drama.
- **Timecodes are whole seconds and add up.** Give the turn and the hero move the most seconds; give an intruding flashback the fewest.
- **Deviate from the user's chosen shot count only when the movement needs the room**, and say so in the reply with the alternative offered.

### 5. Add the extended rule fields

The base template has `LOGIC RULE`. This skill adds named rule fields when the scene calls for them — exact wording in `references/rule-library.md`:

| Field | When |
|---|---|
| `MOVEMENT RULE` | Any running, parkour, fight, chase — screen direction, momentum across cuts, real weight, single-foot takeoff, shoulder roll |
| `PERFORMANCE RULE` | Any crying or held emotion — the ordered build, a tear count, no sobbing, never wipes the face |
| `WEIGHT RULE` | Carrying a body, a limp animal, anything heavy — dead weight, never shifts or breathes |
| `TIME AND LIGHT RULE` | Any flashback — the light tells the time, not a filter; straight cuts only |
| `THE DOG` / `THE PURSUER` | A secondary subject that must be constrained hard — alive only in shot N, only the tail visible, never fully in frame |

**Story constraints go in `LOGIC RULE` too**, next to the identity locks: "The Husband and the Wife never share a frame." "The Stranger never crosses the yellow line." "@image_2 never speaks." A story rule the model can't see is a story rule it will break.

Plus the standing locks in every prompt: only one `@image_N` in frame, glasses stay on including mid-air, head stays shaved, wardrobe identical across shots, anti-sheet rule.

**Negative prompt** always bans the defaults that make AI footage look fake for that genre: action — slow motion, speed ramping, wire work, apex hovering, superhero landing; drama — push-ins, dissolves, cut to black, swelling strings, sobbing, shaking shoulders.

### 6. Write the dialogue

Dialogue is a plot event, not colour: every line either changes the situation or is the button. One line unless the user chose otherwise. Oblique and specific beats theatrical: "He said to bring it round. He didn't say where." / "He was here first." / "I filled your bowl this morning. I forgot." The two patterns that land hardest are a habitual phrase arriving too late, and a callback line whose second delivery means something new. Two short sentences with a stated pause; steady on the first, cracking on the second. Emotion direction goes before the line, inline in the prose. Never a speech.

### 7. Build the page — every time

The deliverable is a published Artifact page, never a code block. Copy `references/page-template.html`, keep its CSS, JS and structure verbatim, and fill the slots:

- `<title>`: a 2–4 word name specific to this scene (The Valet, Last Bus, Carrying Rosie). A new scene is a new file and a new URL; a revision republishes the same file.
- Palette: two accent tokens drawn from the scene's own `COLOR LOGIC` (gold + steel for the casino, honey + dusk for the dog). Neutrals get a bias toward the accent. Type stays constant: Instrument Serif / Archivo / JetBrains Mono.
- Header: eyebrow, title, one-sentence lede, reference-mapping chips, spec chips (duration, shots, references, dialogue lines, one scene-specific number such as "3 tears, total").
- Three columns: **Cast & wardrobe** · **World & rules** · **Shot list**, then the "What happened" aside (the three-sentence story) under the shots.
- The raw plain-text prompt goes in `<script id="raw" type="text/plain">` exactly as the guide's template — this is what the copy button copies. Styling never reaches the clipboard.
- Publish with `icon: "film"` on first publish; omit icon on republish.

### 8. Reply

Link first. Then, briefly: the story engine you chose and the three-sentence story, the line, the shots as a numbered list of one line each, the judgment calls you made and why (shot-count deviation, flashback placement, an unseen antagonist), and one to three things to watch in the render with the single-shot fix for each. Don't repeat the prompt text in chat.

## Iteration

Follow the base guide's iteration loop: read what they actually said, make the minimal change, fix the one broken spot, republish the same file. "Boring / AI-ish / random" means the shots are interchangeable beats — rebuild them as one continuous route, don't polish the prose. "Doesn't make sense / no story" means the turn is missing or is only in the aside — name the turn, give it a shot, and put the fact it depends on in frame. "Make it slow / not over-crying" means fewer tears, slower build, longer holds, a stated pause in the line. When the user reverses one of your rules (e.g. "I want a flashback of the dog"), their vision wins: build it the safe way (a sheet with only the tail showing) rather than arguing for the ban.

## References

- `references/story-patterns.md` — setup / turn / payoff, the seven story engines, what every good prompt has, the scene-building procedure. Read every time.
- `references/example-prompts.md` — three finished original prompts, one per engine, each with the three-sentence story it came from. Read the closest one before writing shots.
- `references/intake-questions.md` — the four-question pattern with option sets for action and drama
- `references/rule-library.md` — exact wording for every extended rule field and standing lock
- `references/page-template.html` — the page skeleton with slots; reuse verbatim
- `references/worked-examples.md` — Rooftop Gap Run and Carrying Rosie, the raw prompts the rule fields are calibrated to
