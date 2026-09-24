# Bug inventory

Recurring failure modes and the fix for each. Apply the stack for your scene type before the render.

## Duplicate camera (and the phone trap)

**Breaks:** "places the camera down" spawns a second camera object on the surface while the POV keeps existing. **Why:** "sets the camera down" + vlogger genre references pull training data of visible cameras; "his hands appear at the edges of the frame" renders hands handling an object.

Fix stack:
1. Drop named cultural references with visible-camera baggage (e.g. "Casey Neistat handheld vlog").
2. Use "first-person POV" or "found-footage logic."
3. Replace "camera" with "perspective" or "frame" in placement language. **Same trap for "phone" / "iPhone":** "the iPhone he holds in his right hand" spawns a phone. Write "the frame held in his right hand." The style descriptor (`iPhone main-camera look`, `phone-cam color science`) is fine — it describes LOOK, not OBJECT.
4. Drop "his hands appear at the edges of the frame" → "the perspective itself lowers smoothly onto the surface."
5. State the surface is empty in two or three places (ENVIRONMENT, LOGIC RULE, ACTION).
6. Do NOT add "no duplicate camera" / "no phone visible" to negatives — inverse priming.

## Visible podium

**Breaks:** "talking to a small crowd in a park" generates a lectern. **Why:** crowd-listening-to-speaker data has podiums.

Fix: reframe "crowd / listeners" → "casual meetup / informal circle / friends close to him"; state "nothing in front of him" in LOGIC RULE; he stands "freely" with "hands free for gestures"; add `no podium` to NEGATIVE PROMPT (justified third item).

## Frozen subject

**Breaks:** locked tripod → statue. **Why:** "locked tripod throughout" read as "everything locked."

Fix, in LOGIC RULE: "Natural head movement and hand gestures evolve organically with the speech, no static movement, no looping."

## Looping gesture

**Breaks:** the same wave or head tilt repeats three times. Fix, in LOGIC RULE: "Hand gestures evolve organically with the speech, no looping."

## Muffled audio

**Breaks:** lip-sync audio comes out muffled or hollow. **Why:** DELIVERY described audio character. Fix: DELIVERY is exactly `Lip-sync driven by @audio_1.` — nothing else, ever.

## Cool lighting when you want warm

Apply the lighting redundancy stack (`style-anchors.md`): FORMAT + ENVIRONMENT + STYLE ANCHOR + LOGIC RULE + optionally negatives.

## Surface is not empty

**Breaks:** placed camera → cluttered ledge (bottles, papers, other cameras). Fix: "the [surface] is empty — nothing on it" in ENVIRONMENT and LOGIC RULE. Three mentions beat one.

## Multi-person inconsistency

**Breaks:** 4–6+ figures → faces drift, swap, flicker. Fix: reduce to 3–4; push extras to middle ground / background in soft focus ("Other travelers move through the terminal behind him in the middle ground, in soft focus"); for partial-visibility second subjects, state the cut point in STYLE ANCHOR, LOGIC RULE and ACTION ("body and lower jaw visible, face cut off above the chin"); a smooth zoom-in concentrates focus on the main subject by the end.

## Stuffed shot

**Breaks:** 6+ scripted beats in 5–10s feels rushed and glitchy. Fix: ~5–6 beats max for 15s, fewer for shorter. Cut beats; trust the model.

## Camera won't lock ("cinematic priming")

**Breaks:** locked tripod described, but tracking/dolly/drift still appears. **Why:** "cinematic" + "walks through the frame" pulls cinematic walking data, which has camera motion.

Fix stack:
1. Drop "cinematic." Use "static," "documentary," "observational," "fly-on-the-wall."
2. FORMAT names "STATIC LOCKED" in caps.
3. STYLE ANCHOR enumerates what the camera does NOT do.
4. LOGIC RULE adds the non-following clause: "Subject enters from [side], walks past the static camera position, and exits on [other side] — the camera does NOT follow him."
5. Replace "walks through the frame" with "walks past the camera position and exits the frame."
6. NEGATIVE PROMPT adds `no camera movement`.

## Uncanny walk

**Breaks:** floating feet, wrong arm swing, jerky weight. **Why:** "natural walk" is too vague. Fix, in LOGIC RULE: "His walk is natural and grounded — relaxed gait, normal arm swing, weight shifting realistically, [pulling the suitcase smoothly behind him]."

## Plasticky face at distance

**Breaks:** waxy/generic face in wide shots. **Why:** detail allocation. Fix: pull in to medium close-up minimum; add "Ultra-detailed skin texture — visible pores, freckles, individual mustache hairs, real eye moisture" to STYLE ANCHOR; add "The realism IS the content" when face detail is the point; if a wide is unavoidable, zoom in midway so the close landing rescues the face.

## Reference bleed (multi-reference)

**Breaks:** `@image_3` tagged for composition also imposes its color grade or lighting. Fix: state what each reference contributes and what it does not — the scope-locked pattern in `references-and-scope.md`. Repeat in STYLE ANCHOR and LOGIC RULE for maximum lock.

## Already-in-pose keeps animating a transition

Harden LOGIC RULE: "He is FROZEN in the [crouched / seated] pose at frame zero — no standing, no lowering, no transition. The shot opens with him already settled in the pose."

---

# Feedback translation

| Creator says | Fix |
|---|---|
| "Sounds muffled" | Strip DELIVERY to `Lip-sync driven by @audio_1.` |
| "Lighting's wrong" | Lighting redundancy stack; name the time of day |
| "Wrong vibe" | Style anchor mismatch — switch families |
| "Camera's there twice" / "extra phone in frame" | Duplicate-camera stack, including the phone trap |
| "Why is there a podium" | Reframe to "casual meetup," add `no podium` |
| "Looks frozen" | Organic-movement clause in LOGIC RULE |
| "Same gesture on repeat" | Anti-loop clause in LOGIC RULE |
| "Camera isn't locked" | Cinematic-priming stack — drop "cinematic," add `no camera movement` |
| "Walk looks weird" | Name gait, arm swing, weight shift |
| "Face looks plastic" | Pull to medium close-up minimum; detail showcase cue |
| "Face changed mid-shot" | "as shown in @image_1" in WARDROBE and STYLE ANCHOR; stubborn cases use @image_1 as a literal start frame |
| "Too many things happening" | Cut beats — 5–6 max for 15s |
| "Doesn't look like the reference" | Say which references control which aspects; scope-lock |
| "Other reference is bleeding in" | `@image_X contributes ONLY [thing], never [other things]` |
| "Audio plays past the visuals" | Match generation length to audio length exactly |
| "Audio ends too early" | Add a closing visual beat for the silence |
| "Weird faces in the crowd" | Push extras to soft focus, reduce headcount |
| "I need negative space for text" | Left-third / lower-third composition lock |
| "He's transitioning, I want him already in pose" | FROZEN-at-frame-zero language |
| "Handheld too shaky" | Restraint cues — "subtle," "gentle," "steadicam-assisted feel" |
| "Zoom feels rushed" | Shorten the zoom range or extend the duration |
