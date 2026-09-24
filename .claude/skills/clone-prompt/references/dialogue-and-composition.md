# Dialogue, detail, composition, crowds, pose, decisiveness

## Dialogue performance

**Inline with the beat.** Every line is paired with the physical beat it lands on, woven into the prose — not a transcript field, not a list:

> He says with a small head tilt, "Yeah that's scary right?"
> He continues into the body of the thought, head moving naturally with the rhythm of the speech: "Like this technology has come a far way..."

**Emotion tag before the line.** ✅ *he says calmly, "I knew you'd come back"* — ❌ *"I knew you'd come back" — said calmly.* The first is direction the model reads; the second is metadata it ignores.

**Natural pauses with `...`** when the recording has them: "One of the easiest ways to tell something is ai generated is the dialogue... specifically the flow of it." Keeps lip-sync alignment cleaner.

**Trust the model on micro-detail.** For 15s, two micro-expressions max — one at the open, one at the close. Don't choreograph every blink. Gestures generically: ✅ "There are natural conversational gestures as he speaks." ❌ "On 'every,' his right hand enters frame in a sweeping open-palm gesture; on 'single,' he counts on his fingers..." Over-direction reads frantic.

**Gesture during speech, not before.** ✅ "While he says the line, his hand lifts and he casually points toward the right." ❌ "He opens already pointing right, then says the line." Humans gesture while speaking.

**The pre-line and post-line beat.** A breath, a lean, a small knowing half-smile before; a held look, the smile lingering after. Close every oner with the held beat, then `Lip-sync driven by @audio_1.` as the last line of ACTION.

## Detail allocation

The detail budget is finite and spread across the frame. Wide → plasticky faces. Close → real faces, lost context. Match framing to what matters:
- Face must look real (selfie vlogs, talking heads, walk-pasts) → medium close-up to close; waist-up or chest-up minimum.
- Setting matters → wider is fine; accept softer faces.
- Showcase shots → "Ultra-detailed skin texture — visible pores, freckles, individual mustache hairs, real eye moisture. The realism IS the content."

## Composition framing for text overlays

When text will be added in post, leave usable negative space — and **never mention the text**; the model renders gibberish. Describe the composition instead.

Left-third / right-third: "@image_1 is positioned in the LEFT third of the frame; the right two thirds are open negative space (sea, sky, hillside, no subject)."

Lower-third / upper-third: "@image_1 occupies the lower third of the frame, the upper two thirds filled with open sea and clear summer sky for compositional negative space."

State it in STYLE ANCHOR (as aesthetic) and LOGIC RULE (as a frame-to-frame lock). If the model recenters anyway, go geometric: "his body fully contained within the leftmost third of the frame width — his right edge does not cross the one-third vertical line."

## Crowd and background consistency

- Reduce headcount: 5–6 close extras is consistency hell; 2–3 with one or two further back is manageable.
- Push extras to middle ground / background in soft focus: "Other travelers move through the terminal behind him in the middle ground, in soft focus." / "A few people in the distance, partially visible."
- Second subjects in dialogue scenes: partial visibility, cut point stated in STYLE ANCHOR, LOGIC RULE and ACTION — "body and lower jaw visible, face cut off above the chin." More reliable than a second consistent face.

## Starting state: already-in-pose vs entering-pose

**Already-in-pose** — better for short shots (3–6s), awkward transitions (crouching, lying, getting into a chair), still-coming-to-life moments: "@image_1 begins already crouched among the red flowers — no transition from standing. He gently picks one bloom..."

**Entering-pose** — better for longer shots with room for both, transitions with visual interest, setup-then-action: "@image_1 walks into the frame and slowly lowers into the chair, settling into the seated pose."

If already-in-pose keeps animating a transition: "He is FROZEN in the [pose] at frame zero — no standing, no lowering, no transition."

## Decisiveness

Never offer Seedance a multiple choice. Pick one and state it as if there's no other option.

| Indecisive | Decisive |
|---|---|
| "a console table or side table" | "a walnut side table" |
| "his left or right hand" | "his right hand" |
| "evening or night" | "9pm at night" |
| "a few people" | "three people" |
| "warm or golden tones" | "deep amber tones" |
| "natural daylight" | "morning light through a window" |
| "walks across the frame" | "enters from the left, exits on the right" |

If you genuinely don't know what the creator wants, ask them — but inside the prompt, never hedge.
