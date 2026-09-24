# Rule library

Exact wording that has held up in Seedance renders. Adapt names and specifics; keep the structure. Place these as their own labelled fields in the prompt between `STYLE` and `LOGIC RULE`.

## Standing locks — in every prompt's LOGIC RULE

```
Only one @image_1 visible in frame at any time. No duplicates, no split screen, no side-by-side figures, no multi-panel or contact-sheet layout, no white studio backdrop — this is a single live-action scene, not a character sheet. @image_1 wears his black rectangular glasses in every shot[, including mid-air] — they never come off, never slip, never change shape. His head stays shaved and bald throughout, with no hair growth. Same wardrobe across all shots.
```

Adapt the identity locks (glasses, shaved head) to whatever the reference actually shows. If there is a second tagged subject, add "and only one @image_2".

Negative prompt companions: `no on-screen text or titles, no smiling` (when the sheet smiles), `no crowd`, `no other people`.

## MOVEMENT RULE — running, parkour, fights, chases

```
MOVEMENT RULE: @image_1 travels left to right in every shot — screen direction never reverses. His momentum carries across every cut: he is already at full speed when each shot begins, never returns to a standing start, never stops, never hesitates, never resets his stride. Real human body weight and real gravity — he is heavy on every landing and absorbs it through bent knees and hips. The gap jump uses a single-foot takeoff at a full run, never a two-footed hop. The landing resolves into a diagonal shoulder roll across the back, not a head-over-heels somersault, and he comes out of it onto his feet without pushing off the ground with his hands. Arms drive in natural opposition to his legs at all times. His dress shoes lose a little grip on the wet gravel — fast, but not weightless.
```

Negative prompt companions: `no slow motion, no speed ramping, no wire work, no floating or hovering at the top of the jump, no superhero landing pose, no impossible distance or height, no parkour flips or somersaults`.

Geography clause for LOGIC RULE: "The rooftop geography stays consistent: Roof B is lower than Roof A and stays lower, and he only ever descends, never climbs back up."

## PERFORMANCE RULE — crying, held emotion

```
PERFORMANCE RULE: Slow and small throughout — he never sobs. The crying builds in order and skips no step: jaw tightens, chin trembles once, breath catches high in the chest, eyes fill and hold for a long beat, then the first tear falls. Three tears across the whole film, no more. No wailing, no heaving shoulders, no hand over the face, no shaking, no collapse. He blinks slowly and holds still for long stretches. Tears run and he never wipes them away. The line is delivered quietly and slowly with a clear pause in the middle, steady at first and cracking on the repeat.
```

Camera companion in STYLE: "Locked-off camera throughout — no push-ins, no handheld, no camera movement of any kind. Straight cuts only, no dissolves or fades. The stillness is the point."

Music companion: "Strings never enter." Sparse piano notes spaced too far apart to be a melody; the last seconds room tone and breathing only.

Negative prompt companions: `no sobbing or wailing out loud, no shaking shoulders, no camera movement, no push-in, no dissolves or fades, no cut to black, no swelling orchestral score, no warm golden-hour light` (for the drained present).

If the render comes back too composed, the fix is one shot: let the breath catch twice instead of once.

## WEIGHT RULE — carrying a body, a limp animal, anything heavy

```
WEIGHT RULE: In SHOT 3 and SHOT 4, @image_2 is completely limp and completely still. She is dead weight in his arms — heavy, unresisting, sagging slightly where the blanket is not supported. She never shifts, settles, breathes, twitches or moves in any way, and neither does the tail. @image_1 carries her low and braced against his chest with both forearms under her, the way a person carries something heavy they do not want to put down. His posture shows the weight — shoulders down, back straight, arms tight.
```

Negative prompt companions: `no breathing or rising chest under the blanket, no wagging or twitching tail`.

## TIME AND LIGHT RULE — flashbacks

```
TIME AND LIGHT RULE: The light is what tells the two times apart, not a filter or an effect. The flashback is flooded with warm honey-gold late afternoon sun through the window, dust floating in the beam. The present-day shots are the same room under flat grey overcast light with the sun gone and the window dull. Same furniture, same angles, same room — only the light has changed. No colour filters, no vignette, no dissolves.
```

Alternative when the flashback is a different place: describe it as the visual opposite of the present in every way (sterile white and clinical green vs drained grey kitchen) so the cut reads as another time instantly. Label the flashback shot `FLASHBACK` in its header. Give it the fewest seconds — a memory intrudes, it doesn't linger. Place it before the line, not last, unless the user wants to end on the memory.

## Constraining a secondary subject

Give it its own labelled field so the constraint is impossible to miss.

Animal that must read as dead:
```
THE DOG: Rosie is never seen alive and never seen whole. In the flashback she is completely covered by the white sheet. The only part of her visible anywhere in the film is the feathered golden tail hanging out from under the edge of the sheet, perfectly still. No face, no eyes, no body, no movement.
```
With a live reference (`@image_2`) and a warm opening shot: "@image_2 is alive and visible only in SHOT 1. From SHOT 3 onward she is wrapped completely in the white blanket with only her feathered tail uncovered."

Antagonist that should stay off screen:
```
THE PURSUER: A police helicopter, never fully visible in frame — represented only by its sweeping searchlight beam, the shadows it throws, and rotor noise. No reference image, no pursuing characters on foot.
```

Untagged human secondary: describe in prose under SECONDARY SUBJECTS with the differences from `@image_1` stated (broader, darker-haired, no glasses) — the anti-blend rule.

## Design-sheet wardrobe extraction

Write the wardrobe field from the sheet, item by item, then "Identical in every shot." Deconstructing it for story (jacket off, tie loose, sleeves up) is allowed when the story motivates it — say so in the reply. One physical detail tied to the story is worth adding: "the left shoulder of the polo darkened in a damp patch where he has been holding her against it."
