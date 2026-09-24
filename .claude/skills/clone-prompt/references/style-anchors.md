# Style anchors

The most common shot types, with the rules that actually work. Paste the block, adapt the bracketed parts.

## Locked studio talking head

Sit-down podcast-style, locked tripod, controlled lighting.

```
STYLE ANCHOR: Locked studio talking head, podcast / YouTube creator aesthetic. Cinematic prosumer camera (Sony A7S3-style), locked tripod, no camera movement. Medium close-up framing — head, shoulders, [mic if visible]. Slight shallow DOF on background only — face fully sharp, background warmly blurred. [Lighting description specific to scene]. Photorealistic — natural human skin of @image_1 with visible pores, freckles, real eye moisture, subtle natural micro-movements.
```

LOGIC RULE add (fights the frozen-subject bug): "Natural head movement and hand gestures evolve organically with the speech, no static movement, no looping." Camera locks; subject still moves.

## Vlog selfie — he's holding the phone

The frame IS the iPhone he holds. Found-footage logic.

```
STYLE ANCHOR: Vlog selfie aesthetic, found-footage logic. The frame the viewer sees through IS the iPhone he is holding pointed at his face — not a separate object. iPhone front camera look, no fisheye, no extreme distortion. Selfie framing — head and shoulders, slight upward angle. Full DOF — everything sharp, phone-cam color science. Photorealistic — natural human skin of @image_1 with visible pores, freckles, real eye moisture, subtle natural micro-movements.
```

LOGIC RULE add: "The frame the viewer sees through IS the iPhone he is holding — there is no separate, second, or duplicate camera or recording device visible at any point. The phone is never visible in frame, only the natural sway of his arm holding it."

## iPhone observer — someone else filming

Talking-to-a-group shots, candid documentary B-roll.

```
STYLE ANCHOR: iPhone footage aesthetic, found-footage logic. The frame the viewer sees through IS the iPhone held by someone outside the [gathering] — not a separate object. iPhone wide lens look, no fisheye, no extreme distortion. [Opens at medium shot, then smooth digital zoom-in to medium close-up if you want a zoom]. Slight natural handheld sway throughout. Full DOF — everything sharp, phone-cam color science. Photorealistic.
```

## Cinematic B-roll — locked tripod, mild movement OK

```
STYLE ANCHOR: Cinematic [vlog/B-roll] aesthetic, locked tripod, no camera movement. [Framing — wide, slight low angle, etc.]. [Color grade]. Photorealistic, natural human skin of @image_1 with visible pores, freckles, real eye moisture. Full DOF — everything sharp, no shallow depth-of-field, no blur.
```

## Static observational B-roll — rigidly locked

Walk-pasts, side profiles, fly-on-the-wall. Use when "cinematic" is fighting the lock.

```
STYLE ANCHOR: Static locked tripod shot, documentary observation aesthetic. The camera is rigidly fixed on a tripod and does not move, pan, zoom, dolly, or track at any point during the entire shot. [Framing]. The frame composition is fixed throughout. [Color grade]. Photorealistic, natural human skin of @image_1 with visible pores, freckles, real eye moisture. Full DOF.
```

LOGIC RULE add: "The camera is LOCKED — it does not move, pan, zoom, dolly, track, tilt, or follow the subject at any point. The frame composition is fixed throughout the entire [N] seconds. Subject enters the frame from [side], walks past the static camera position, and exits the frame on [other side] — the camera does NOT follow him."

NEGATIVE PROMPT: add `no camera movement` — a justified third item.

## Found-footage "frame as X"

Only when the action requires the character to interact with the frame as a device: placing the camera on a tripod ("the perspective lowers onto the tripod"), a mirror ("his face fills the frame as he leans in"), a handheld selfie ("the frame sways with his stride"), a physical pan. For multi-cut B-roll where the camera is just choosing angles, use standard spatial language instead — "camera positioned directly in front of @image_1, eye-level, medium close-up." The model understands positions natively; it doesn't need to philosophize about what the frame is.

## Diegetic camera motion — the subject moves the camera

Different from operator motion. The motion lives in the ACTION prose as the character physically turning the camera:

> "He physically pans the camera off himself toward the window, the pan revealing the blue sky and clouds."

LOGIC RULE can still lock everything else: "The pan is the only camera movement; before and after the pan, the camera is held relatively steady with natural handheld sway only."

## Operator camera motion — zoom-outs, dolly-backs, push-ins

Stable cinematic: "Cinematic camera with smooth slow zoom-out across the entire shot. Stable, deliberate camera motion only — no shake, no handheld."

Handheld pull-back: "Handheld camera with subtle natural sway, smooth handheld zoom-out across the entire shot. Subtle handheld micro-movement throughout, organic operator feel — gentle, never shaky, never vlog-style."

Match zoom range to duration: a 4s shot handles medium close-up → medium; extreme close-up → medium-wide in 4s feels rushed. Shorten the range or extend the duration.

The handheld trap: "handheld" alone pulls toward vlog shake. Always pair with restraint — "subtle," "gentle," "barely perceptible," "steadicam-assisted feel." The goal is alive, not shaky.

## Lighting — the redundancy stack

A single mention loses to the setting's default prior (bedroom = neutral daylight, airport = cool overcast). To force a lighting state, repeat it across fields:

1. **FORMAT** names it: `... GOLDEN HOUR bedroom`
2. **ENVIRONMENT** specifies the source: "Low orange sun pouring through a window on one side, casting STRONG warm amber and orange light directly onto the bed. Visible angled patches of golden-orange sunlight stretching diagonally across the bedspread. Deep amber glow saturating the scene, natural shadow falloff on the unlit side."
3. **STYLE ANCHOR** repeats the palette: "STRONG golden-hour lighting throughout — rich amber, orange, and honey tones dominate. Warm color temperature, directional low sunlight casting visible warm light shapes on surfaces."
4. **LOGIC RULE** locks it across cuts: "Lighting is strongly warm/golden across all cuts — never cool, never neutral."
5. **NEGATIVE PROMPT** if needed: `no cool lighting, no neutral daylight` — breaks the two-item discipline; stubborn lighting justifies it.

Lighting reference images: describe what's literally in them — window-shaped light patches on a wall, strong directional sun from one side, deep amber not soft yellow. The model needs the *what* of the light, not the *feel*.
