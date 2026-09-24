# Story patterns

Why a prompt reads as "a guy doing an activity" instead of a scene: the story lives in a backstory aside the viewer never sees. A prompt that works puts the story **in the frame**. Every scene, however short, has three visible beats:

1. **Setup** — who wants what, and the one thing in the way. Shown, not implied. A tray handed over with a name. A table between two men. A salt circle on the floor.
2. **Turn** — the moment the situation changes. A door opens, a line is spoken, a card appears behind an ear, the knocking stops.
3. **Payoff** — the last frame answers the setup. A line, a look, a reveal, a hold. Always end on a held image: *"Hold on his face as the frame settles."*

If you cannot name the turn in six words, the scene has no story yet. Go back to the intake answers and find it before writing a single shot.

## Story engines

Pick one. Say which in the reply. The pattern names are for your planning; they never appear in the prompt.

### The reversal
The scene sets up one reading, then flips it. A maid delivering a tray turns out to be the thief. The wardrobe change *is* the reveal: she peels off the collar and cuffs and the uniform reads as a cocktail dress. Plant the flip in the wardrobe, prop or environment from shot 1 so the payoff costs no new setup.
- Setup: she is what everyone assumes.
- Turn: the door closes, the demure face melts into focus.
- Payoff: the outfit reveal and one cool line to a stranger.

### The callback line
The same short line opens and closes the scene, and the second delivery means something different because of what happened between. *"Where are the weapons?"* asked across a table, then asked again standing over the man. Costs almost no runtime and gives a 15-second clip a shape.
- Setup: the line, flat and patient.
- Turn: the answer that starts the fight.
- Payoff: the line again, same tone, new power balance.

### The deadpan button
A build of unease, then a punchline delivered dry. A knocking that stops when he says "Hello?", a ball that rolls into frame from nowhere, a slammed door, and then to camera: *"Yup. Definitely haunted."* The sound design does the story work; the last line is the only joke.
- Setup: he tells us what he suspects.
- Turn: the evidence arrives, played straight.
- Payoff: one dry line to lens.

### The third party
The scene's real story belongs to someone who barely speaks. Two friends in a booth: one orders, the other is silently in love with the waitress, and the payoff is a two-word nudge: *"Ask her out."* Give the silent character a whole arc in expressions only. This turns any ordinary errand into a scene.
- Setup: the errand (ordering, waiting, walking).
- Turn: the hero notices the friend noticing.
- Payoff: the nudge, and the friend's flustered denial, and the errand completing on top of it.

### The rule that holds
A physical rule both characters obey, and the scene tests whether it holds. A salt circle the vampire cannot cross. A table between a cop and a boss. The whole scene is the pressure on that rule. It gives Seedance a spatial constraint it can actually render, and gives the viewer a question.
- Setup: the rule shown plainly in the first wide.
- Turn: the rule is threatened (a gust nearly kills the candle).
- Payoff: it holds, or it breaks, and the antagonist reacts.

### The slow crack
One locked shot, one face, one pressure that builds until it snaps. A chess stream that ends in a rage-quit, a coaster climb that drops into bliss. No cuts: the arc is the performance. Write the emotional stages in order and give each a physical tell (hand pressing the temple, nostrils flaring, headphones ripped off). An off-screen voice can be the second character.
- Setup: concentration, small tells.
- Turn: the result lands (a pop-up, a crest, a chime).
- Payoff: the snap, then the deflation, then an exit.

### The transformation montage
Opening state, a decision, then a fast sweep of one-second beats that all prove the change. Each beat needs a different location, wardrobe variant and one specific detail (a vendor waving, chopsticks lifting noodles). The perspective rule is what holds it together: after he picks up the camera, we *are* the camera and his extended arm is in every shot.
- Setup: the drained state, the unused object.
- Turn: he picks it up.
- Payoff: the last beat is quieter than the peak, still in motion.

## What every good prompt has that a weak one lacks

- **Named secondary subjects with distinct looks.** Not "three henchmen" but The Boss (gold chain, rings), Henchman 1 (shaved head, neck tattoos), Henchman 2 (beard, backwards cap, MP5). Distinct looks stop face-blending and let the shot list reference them by name. Untagged secondaries go under `SECONDARY SUBJECTS` as a list.
- **Lettered environments when the story moves.** (A) kitchen, (B) staircase, (C) hallway with the guard, (D) study. The shot list then walks the letters in order. A scene that moves through space has momentum for free.
- **Hero props with a job.** The prop is the plot: the Ace of Hearts, the domed cloche, the fortune cookies that get the waitress to the table, the salt circle. If a prop is only set dressing it goes in ENVIRONMENT, not HERO PROPS.
- **An emotional arc in the SUBJECT line.** "Starts drained, transforms into curious and alive." "Casual, then genuinely unnerved, lands on deadpan." Write the arc, not a mood.
- **Dialogue that is a plot event, not colour.** Every line either changes the situation or is the button. If a line could be cut with no loss, cut it. Two lines can carry a whole scene when one answers the other.
- **A RULES or LOGIC RULE field that states the story constraint.** "The woman places the card, never the magician." "@image_2 never speaks." "@image_1 stays inside the circle for the entire scene." Story rules belong next to the identity locks.
- **A last frame.** The final shot ends on a hold, a line, or a reveal. Never on a character simply leaving frame unless the leaving *is* the joke.

## Scene-building procedure

1. From the intake answers, write the turn in one sentence.
2. Choose the engine above that fits it.
3. Write setup, turn, payoff as three sentences. These three sentences are the "What happened" aside on the page.
4. Cast the secondary subjects the turn needs, each with three distinguishing features. Cast nobody the turn doesn't need.
5. List the hero props the turn needs. Give each a job.
6. If the story moves, letter the environments in the order it moves through them.
7. Only now plan shots. Each shot is one named beat from the three-sentence story. The turn gets its own shot. The payoff is the last shot and ends on a hold.
8. Write the dialogue last, and only where a line changes the situation.

## Failure modes this fixes

- **Activity, not scene.** A man runs and jumps. Fix: who is behind him, or what is ahead, and show it in one shot (a searchlight, a fire escape door, a hand reaching from the next roof).
- **A cast of one.** Drama needs someone to play against. If the user gives one reference, add an untagged secondary (a voice through headphones, a guard, a waitress) or a physical rule that stands in for the antagonist.
- **The story is in the aside.** If the payoff depends on facts the viewer never sees, move one of those facts into a prop, a line or a wardrobe detail on screen.
- **Ending on nothing.** The last shot fades or he walks off. Fix: a held face, a callback line, a reveal.
