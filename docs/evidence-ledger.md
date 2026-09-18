# Gemini 4 Pro evidence ledger

This ledger keeps official facts, adjacent-model capabilities, and community speculation separate. Dates are observation dates for this repository, not claims about when Google changed a product.

## Current ledger

| Date | Source | Signal | Label | Confidence | Supports | Does not support |
|---|---|---|---|---|---|---|
| 2026-09-19 | [Gemini API model catalog](https://ai.google.dev/gemini-api/docs/models) | The public catalog lists Gemini 3.8 Flash, Gemini 3.1 Pro Preview, and other Gemini 3 models; no Gemini 4 Pro ID is listed. | Official | High | Current API availability and model naming | The identity of an anonymous Arena model |
| 2026-09-19 | [Google DeepMind Gemini models](https://deepmind.google/models/gemini/) | The public model page presents Gemini 3.8 Flash and Gemini 3.1 Pro; it does not present a Gemini 4 Pro product page. | Official | High | Current public product status | Future release timing |
| 2026-09-19 | [Gemini 3.1 Pro model card](https://deepmind.google/models/model-cards/gemini-3-1-pro/) | Gemini 3.1 Pro is natively multimodal, with text, image, video, audio, PDF, and code-repository understanding; it lists up to 1M input tokens and 64K output tokens. | Official | High | A reproducible Pro baseline and multimodal use cases | Gemini 4 Pro specifications |
| 2026-09-19 | [Gemini 3.8 Flash documentation](https://ai.google.dev/gemini-api/docs/latest-model) | Google documents long-horizon software engineering, autonomous agents, enterprise workflows, an API ID, and pricing for Gemini 3.8 Flash. | Official | High | A reproducible fast baseline | That 3.8 Flash is secretly Gemini 4 Pro |
| 2026-09-19 | [X trend shared for this tracker](https://x.com/i/trending/2100554063016518107) | A live discussion collects posts speculating about an Arena model label and Gemini 4 Pro. | Community | Low | The existence of active public interest | Model identity, specs, or release status |
| 2026-09-17 | [Reported Arena discussion](https://officechai.com/ai/gemini-4-0-pro-arena/) | X users reported that an Arena model displayed as <code>gemini-3.8-flash</code> produced strong SVG/3D outputs; the article also repeats an unverified long-output claim. | Community / Unverified | Low | Reproducible hypotheses for SVG, 3D, and output-stress tests | Official Gemini 4 Pro identity, benchmark scores, or pricing |

## Evidence rules

Upgrade a claim from community signal to official only when a Google-owned source provides the model name or an unambiguous official identifier. A screenshot, arena alias, metadata label, output style, or third-party route is not sufficient on its own.

Upgrade a performance claim only when the task, prompt, model surface, settings, tool access, date, grading method, and failure cases are available. Prefer independent reproduction over repeated posts.

If a source disappears or changes, preserve the old row and add a correction row. Do not silently rewrite history.

## Pending questions

- Will Google publish a model page or model card named Gemini 4 Pro?
- Will the public API catalog expose a Gemini 4 model ID?
- Is the Arena <code>gemini-3.8-flash</code> label an ordinary Gemini 3.8 Flash endpoint, an experiment, or an unreleased checkpoint?
- Do the reported SVG, 3D, and long-output behaviors reproduce outside Arena?
- What will the official context window, modalities, pricing, safety report, and availability be if a Gemini 4 model launches?
