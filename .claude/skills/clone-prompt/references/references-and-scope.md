# References and scope

## Multi-reference tagging

Each tag has one clean, separate job, stated in the prompt:
- `@image_1` → identity / face / body / wardrobe lock
- `@image_2` → a specific prop (the suitcase, the mug, a cap with specific branding)
- `@image_3` → composition / style / scene reference

Be explicit about what to take and what to leave, or the model takes everything — including what you wanted to override. Especially critical when a style reference's lighting conflicts with what you want:

> "Composition and framing match @image_3 — color grade does NOT match @image_3, override to golden hour."

## Inspiration-only references

When the creator shows an image "just for inspiration / just for you / don't put that in the prompt," don't tag it. Extract the specific qualities (composition, grade, mood, prop shape, lighting feel) and bake them into the prompt as direct description.

> An H&M ad screenshot, "just for the color grade":
> ✅ STYLE ANCHOR: "Warm sun-bleached vintage summer film color palette — soft golden tones, slightly desaturated, subtle film grain feel."
> ❌ "Color grade matches @image_4."

The same image can be a real reference one chat and inspiration-only the next. Always confirm which.

## The scope-locked pattern

For references with a single job, lock the scope HARD with inclusive AND exclusive language. `@image_X contributes ONLY [thing]` + `never [other things]` beats positive-only description:

> "@image_2 informs ONLY the shape and form of the white pillow-balloon — its composition, framing, lighting, female subject, dress, color palette, and any other element do NOT carry over."

> "@image_2 contributes ONLY the wardrobe and outfit — never the face, body, or identity, which remain @image_1."

If a specific bleed keeps happening across renders, name that element in the exclusion list. For maximum lock, repeat the scope statement in both STYLE ANCHOR and LOGIC RULE.

## Audio

`@audio_1` in DELIVERY: `Lip-sync driven by @audio_1.` Never describe its character. If the recording has natural pauses, `...` in the written dialogue matches them; the audio drives timing regardless.

## Face drift across a shot

"Face changed mid-shot" → strengthen the reference: "as shown in @image_1" in WARDROBE and STYLE ANCHOR. For the most stubborn cases, use `@image_1` as a literal start frame.
