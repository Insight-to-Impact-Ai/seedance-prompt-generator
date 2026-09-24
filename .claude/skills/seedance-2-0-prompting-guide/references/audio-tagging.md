# Audio Tagging — When the User Uploads Pre-Generated Audio

This is critical and changes how the shot is written.

## If a user attaches an audio file (song, voiceover, dialogue track)

1. Tag it as `@audio_1` in the MUSIC field, or inline in the shot if it's voice.
2. **Do NOT transcribe the audio content into the shot description.** The model syncs lip movement to the audio itself.
3. Keep the shot description minimal — describe the PERFORMANCE, not the lyrics or words.

**Example — singing scene with attached song:**

```
MUSIC: @audio_1

SHOT 1 — 0:00 to 0:15, MCU to MS, 50mm, slow pull-back.
Opens tight on @image_1 performing @audio_1 passionately on stage. Camera slowly pulls back, revealing the crowd.
```

Don't write "He sings 'We will rock you'" or describe lyric beats. The audio drives the performance.

## Hybrid case — audio has only the user's dialogue, but other characters respond

When the attached audio contains only @image_1's voice but the scene needs another character to speak back, transcribe ONLY the response character's lines. Mark the user's lines with `@audio_1`.

```
@image_1 speaks @audio_1 "Excuse me, do you guys have Rolexes?"
@image_2 replies: "Are you wearing those recording glasses?"
@image_1 replies @audio_1 "Yeah, I'm recording."
```

## Audio realism for POV scenes

When the scene is POV through a real-world device (phone, smart glasses, vlog camera), add: "All audio sounds like it was captured by the device's microphone — natural, slightly muffled, no studio polish." Otherwise the generated audio feels bass-boosted and wrong for the format.
