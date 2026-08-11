# debgo-ai-carbonara-no-framework

An agentic AI orchestration demo using a kitchen scenario. Simple enough to explain in thirty seconds. Interesting enough to watch.

## What it shows

A dispatcher receives a plain English order. It knows nothing about cooking. An expeditor -- powered by a local LLM -- reasons through the job, picks the right doers, and sequences them correctly. The doers execute their one job each and report back.

The LLM figures out the sequence. That is the agentic part.

## Roles

- **Dispatcher** -- takes the order, delivers the result, knows nothing about kitchens
- **Expeditor** -- agentic brain; reads the doer registry, thinks out loud, builds a plan
- **Doers** -- single-purpose workers: `boil_pasta`, `fry_guanciale`, `make_egg_sauce`, `grate_cheese`, `combine`

## Requirements

- [Ollama](https://ollama.com) running locally
- `qwen2.5-coder:3b` pulled (`ollama pull qwen2.5-coder:3b`)
- Python 3.14+
- `pip install ollama`

## Run it

```bash
python carbonara.py
```

## Live tuning

At the top of `carbonara.py`:

```python
MODEL       = "qwen2.5-coder:3b"
TEMPERATURE = 0.3
STREAM_DELAY = 0.0
```

Bump `TEMPERATURE` to `0.8` during the demo to show wilder, less predictable output.
On a faster computer, increase `STREAM_DELAY` to 0.02 adding drama on waiting.

## What you will see

```text
[DISPATCHER]  received order: "make me a carbonara"

[EXPEDITOR]   thinking about: "make me a carbonara"
              ... reasoning trace printed here ...

[DOER boil_pasta]    Boil 200g spaghetti to al dente
[DOER boil_pasta]    Spaghetti is al dente and drained, standing by.

[DOER fry_guanciale] Render guanciale until crisp
[DOER fry_guanciale] Guanciale is crisp, fat rendered into the pan.

... and so on through to combine ...

[DISPATCHER]  Your carbonara is ready -- silky, rich, no scrambled eggs.
```

## Philosophy

No frameworks. No orchestration libraries. The Expeditor is a prompt and a registry. The LLM does the reasoning. Python does the wiring.

---

**East Van AI** · AI for the rest of us! · Vancouver, BC, Canada

[github.com/east-van-ai](https://github.com/east-van-ai) · <east-van-ai@proton.me>

MIT License · Copyright (c) 2026 Go Nakamaru
