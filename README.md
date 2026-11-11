# Video workflow

How I make promo and explainer videos with an AI agent. The agent builds every frame, I direct. Seven steps: plan, voice, timeline, music, picture, mix and notes. Each step is saved as files in one folder, so any step can be redone without touching the others.

The full write-up, with the render times on my PC: [petrach.dev/toolbox/video-workflow](https://petrach.dev/toolbox/video-workflow).

## What's here

| File | What it is |
| --- | --- |
| [WORKFLOW.md](WORKFLOW.md) | The seven steps, the folder layout and the rules |
| [prompts.md](prompts.md) | Every prompt, in order, with free options |
| [script.example.json](script.example.json) | An example `script.json`: voice settings, tempo and scenes |
| [.env.example](.env.example) | The key the voice and music steps read |

## Start

You need Claude Code, [HyperFrames](https://github.com/heygen-com/hyperframes), and an [ElevenLabs](https://elevenlabs.io) account for voice and music (or the free options in `prompts.md`). The heavy scenes use Python and ffmpeg, and Blender is optional for 3D.

```
claude plugin marketplace add heygen-com/hyperframes
claude plugin install hyperframes@hyperframes
git clone https://github.com/vedranpetrac/video-workflow my-video
cd my-video
cp .env.example .env
```

Put your key in `.env`, open Claude Code in `my-video` and paste the first prompt from `prompts.md`:

```
Write a plan for a 30-second promo for my brand: scenes, voice lines, lengths. Don't make anything yet.
```

## Licence

MIT for the workflow, the prompts and the example. HyperFrames, ElevenLabs, stock clips and music keep their own terms. See [LICENSE](LICENSE).
