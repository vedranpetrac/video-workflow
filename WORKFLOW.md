# Promo and explainer videos with an AI agent

The agent builds every frame; you direct. Seven steps, each one saved as files in one folder, so any step can be redone without touching the others.

```
my-video/
  plan.md              scenes, voice lines, lengths
  script.json          the same, as data the scripts read
  assets/vo/           one voice file per line
  assets/music/        the score
  assets/footage/      picked stock clips + credits.json
  scenes/              HyperFrames compositions (HTML)
  scripts/             Python scenes for the heavy visuals
  out/                 renders, previews, the final mix
```

## 1. Plan

Ask for a plan, not a video. Scenes, what the voice says in each, how long each one is, and how people should feel at the end. Read it like a director and give notes in plain words until it's right. The plan becomes `script.json`.

## 2. Voice: ElevenLabs

One audio file per sentence, so a bad line is redone alone. Fetch lossless (`pcm_48000`) and keep it 24-bit. A light chain after it: EQ, gentle compression, a short room, a limiter with headroom. No pitch shifting; it smears the voice.
Free option: Kokoro, runs on your own machine.

## 3. Timeline

Each scene is as long as its voice line plus padding, never shorter than its minimum, then snapped to whole beats of the music's tempo. Every cut lands on a beat because the timeline is built from the beat grid, not fixed by hand later.

## 4. Music: ElevenLabs Music

Ask for the mood, the exact length and a strong beat on the cut points. Save the prompt next to the file so the score can be regenerated.
Free option: a track from the YouTube Audio Library, cut to length with a fade.

## 5. Picture: HyperFrames first, Python for the heavy parts

- **HyperFrames** for most scenes: titles, captions, lower thirds, UI walk-throughs, charts, code, transitions. A scene is an HTML page with seekable animation, so the agent writes it like a web page, checks single frames, and HyperFrames renders it to MP4 the same way every time. Its registry has ready blocks to start from; restyle them to the brand instead of using them as they are.
- **Python** (skia-python, NumPy, OpenCV, piped to ffmpeg) for what HTML is bad at: thousands of animated shapes, particle systems, brand patterns drawn from the logo geometry, colour grades on stock footage, bloom.
- **Blender** (Cycles) for real 3D models, rendered as image sequences and composited in.
- **Stock footage** from Pixabay, picked from a numbered contact sheet, graded to the brand. Keep the credits file.

## 6. Mix

Place each voice line at its scene's cue, duck the music under the voice, then measure loudness and apply one gain to -14 LUFS (two-pass loudnorm), which is where YouTube plays it. Export H.264 MP4. On an NVIDIA card, NVENC makes the final encode a lot faster.

## 7. Notes and the final render

Watch it and write what bugs you, one sentence at a time. Preview at 720p and re-render only the scene that changed, not the whole video. Expect five or six rounds.

When the notes are done, render the whole video once at full resolution, 1080p or 4K, and run the mix from step 6 on it. That file in `out/` is the one to publish. How long it takes depends on the computer and the resolution.

## Rules

- API keys live in `.env`, never in the chat, the code or the repo.
- Brand colours, fonts and shapes in one file the scenes import, so a change lands everywhere.
- Keep the licence or credit for every clip, track and font you didn't make.
