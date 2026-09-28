# 📊 Nina`s Bench

Benchmark and compare your local LLMs and quants — **speed, quality, and a pick for the best one.**

A single-file web app: **no build step, no dependencies, no telemetry.** Open `ninas-bench.html` in any modern browser and go.

![Nina`s Bench](screenshots/hero.png)

## Quick start

1. Start a local model server:
   - **LM Studio** — Developer tab → *Start server* (default `http://localhost:1234/v1`)
   - **Ollama** — `ollama serve` (default `http://localhost:11434`)
2. Open `ninas-bench.html` in your browser (double-click is enough).
3. Click **Connect & load models**, then tick the models/quants you want to compare.
4. Click **Run benchmark** — then read the recommendation banner at the top of the results.

That's it. Everything else (settings, tasks, results) is saved locally in your browser.

## What it measures

| Metric | Meaning | Better |
| --- | --- | --- |
| **TTFT** (ms) | Time to first token — includes prompt processing and, on a cold server, model load time. Keep the warm-up pass on. | Lower |
| **Gen tok/s** | Output tokens per second during decoding. Server-reported when available, otherwise estimated (`est`). | Higher |
| **Prompt tok/s** | How fast the model digests your prompt (reported by some servers, e.g. Ollama). | Higher |
| **Score 1–5** | Quality — your manual ★ rating or the auto-judge model's grade. | Higher |

Runs execute **sequentially**, so models never contend for CPU/GPU — that's what makes the numbers comparable.

## Features

- **Head-to-head quants** — select several quants of the same base model and get a "best quant per family" recommendation.
- **Editable task suite** — the defaults cover a quick fact, a math trap, coding and instruction-following; add your own tasks any time.
- **Warm-up pass** — loads each model's weights once with a tiny prompt so cold-start doesn't pollute your TTFT numbers.
- **Judge model auto-scoring** — an optional second model grades every output 1–5 as strict JSON; manual ★ always overrides.
- **Charts & tables** — generation speed and TTFT bar charts, plus a sortable per-run table.
- **Outputs grid** — read the actual answers side by side, expand collapsed "thinking" from reasoning models, copy outputs.
- **Export** — CSV or JSON for spreadsheets and archiving.
- **Local-first privacy** — everything lives in `localStorage`; no data leaves your machine except to your own model server.

## Help system

Press <kbd>?</kbd> (or click **? Help**) for the built-in guide: getting started, server setup, metrics glossary, troubleshooting, data & privacy and more — with a table of contents, context `?` buttons on every section header, and keyboard shortcuts.

| Shortcut | Action |
| --- | --- |
| <kbd>?</kbd> | Open help |
| <kbd>Esc</kbd> | Close help |
| <kbd>A</kbd> / <kbd>N</kbd> | Select all / clear models |
| <kbd>R</kbd> | Run benchmark |
| <kbd>C</kbd> | Cancel (while running) |

Shortcuts pause while you're typing in a field.

## License

**Free to use — except for commercial use.** Copy, modify and share it for any non-commercial purpose; commercial use requires written permission from Nina. See [LICENSE.md](LICENSE.md).

## Repository layout

```
ninas-bench.html      ← the whole app (single file)
README.md             ← this file
LICENSE.md            ← license terms
screenshots/          ← screenshots used in the README and blog post
blog/ninas-bench.md   ← the launch blog post
```
