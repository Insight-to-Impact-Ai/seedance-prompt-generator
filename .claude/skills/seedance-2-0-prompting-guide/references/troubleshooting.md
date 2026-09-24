# Troubleshooting and Iteration

## Common failure modes and fixes

| Problem | Diagnosis | Fix |
|---|---|---|
| Shots feel rushed or glitchy | Too many actions per shot | Cut actions. Split shots if needed. |
| User says "too much" / "chill" | Over-stuffed shots | Cut just the bloated part. Don't rewrite everything. |
| Characters duplicating | No anti-duplication rule | Add LOGIC RULE. Describe characters as distinct. |
| Dialogue feels cringe | Too long, on-the-nose | Cut 50%. Use contractions. |
| Wrong prop keeps generating | Model isn't locking on | Add NEGATIVE PROMPT. Repeat the constraint. |
| Emotional scene flat | Abstract writing | Write physical detail: "chest heaving, tears mixing with sweat, knuckles white." |
| POV shots show the camera | Missing POV rule | Add LOGIC RULE: "Camera IS the device, never visible in frame." |
| iPhone vlog looks too cinematic | Default cinematic DOF | Add: "Everything in focus front to back. NO shallow DOF." |
| Smart glasses POV has fisheye | Default action-cam distortion | Add: "No fisheye, no lens distortion, clean natural human POV." |
| Subject stops walking in a walking vlog | No continuous movement rule | Add: "Walks forward continuously for the full duration." |
| Audio feels overproduced for POV | Default studio-quality audio | Add: "Audio captured by device mic — natural, slightly muffled." |
| Object enters wrong part of frame | Camera framing not locked | Explicitly direct: "Camera tilts DOWN and focuses on the bottom of the stairs. Object enters from the side at floor level." |
| Environment too dark to see | "Black void" / "pitch black" language | Change to "dim but visible" |
| Ending feels forced | Default "cut to black" or dramatic push-in | Ask user preference. Default to a natural settle unless the user requests a dramatic ending. |

## Iteration loop

When the user gives feedback:

1. **Read what they ACTUALLY said.** Not what you assume.
2. **Make the minimal change.** Don't rewrite untouched sections.
3. **Translate their intent.** "Too dramatic" = lower intensity. "More emotion" = more physical detail. "Chill" = fewer actions per shot. "Too much dialogue" = cut lines.
4. **Match their energy.** Casual user = casual reply. Technical user = surgical reply.
5. **When they clarify a problem, fix the ONE spot that's broken.** If they say "the ball keeps entering from the wrong place" — fix that shot description, not the whole prompt.
6. **Never unilaterally restructure.** Ask one short clarifying question if truly ambiguous.

## Feedback translation guide

| User says | Means |
|---|---|
| "Too much" / "chill" | Too many actions per shot — cut actions |
| "Too dramatic" | Dial down intensity — softer performance, no push-ins, no cut-to-black |
| "More emotion" | Add physical detail to the performance |
| "Less dialogue" | Cut half the lines |
| "Format it nicely" | Reach for the master template, clean structure |
| "Not a comedy" | Serious tone — remove jokes, surreal beats, deadpan endings |
| "Be realistic" | Respect the clock — fewer actions/lines for the duration |
| "Why is [X] happening?" | That's the ONE spot to fix — don't touch anything else |
| "I already fixed [X]" | Don't touch that section — only fix what remains |
