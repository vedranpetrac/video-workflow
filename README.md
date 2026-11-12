# Video workflow

How I make promo and explainer videos with an AI coding agent such as Claude Code, with HyperFrames for most scenes. The agent builds every frame, I direct. Seven steps: plan, voice, timeline, music, picture, mix, and notes with the final render. Each step is saved as files in one folder, so any step can be redone without touching the others.

The full write-up, step by step: [petrach.dev/toolbox/video-workflow](https://petrach.dev/toolbox/video-workflow). You can also give that link to your agent and let it walk you through the steps.

## What's here

| File | What it is |
| --- | --- |
| [WORKFLOW.md](WORKFLOW.md) | The seven steps, the final render, the folder layout and the rules |
| [prompts.md](prompts.md) | Every prompt, in order, with free options |
| [script.example.json](script.example.json) | An example `script.json`: voice settings, tempo and scenes |
| [.env.example](.env.example) | The key the voice and music steps read |

## Start

Nothing here has to be paid. You need an AI coding agent that can work in a folder (I use Claude Code, but a free agent or another model provider works too), [HyperFrames](https://github.com/heygen-com/hyperframes), and an [ElevenLabs](https://elevenlabs.io) account for voice and music or the free options in `prompts.md`. The heavy scenes use Python and ffmpeg, and Blender is optional for 3D.

The first two commands install HyperFrames as a Claude Code plugin; the [HyperFrames docs](https://hyperframes.heygen.com/introduction) cover other agents.

```
claude plugin marketplace add heygen-com/hyperframes
claude plugin install hyperframes@hyperframes
git clone https://github.com/vedranpetrac/video-workflow my-video
cd my-video
cp .env.example .env
```

Put your key in `.env`, open your agent in `my-video` and paste the first prompt from `prompts.md`:

```
Write a plan for a 30-second promo for my brand: scenes, voice lines, lengths. Don't make anything yet.
```

## Licence

MIT for the workflow, the prompts and the example. HyperFrames, ElevenLabs, stock clips and music keep their own terms. See [LICENSE](LICENSE).
