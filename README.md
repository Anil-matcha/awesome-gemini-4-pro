<div align="center">

# Awesome Gemini 4 Pro

**Use cases, prompts, evaluation notes, and evidence tracking for the rumored next Gemini Pro model.**

[![License: MIT](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-unreleased%20%2F%20tracked-f59e0b)](docs/evidence-ledger.md)
[![Google AI](https://img.shields.io/badge/Google%20AI-official%20docs-4285F4)](https://ai.google.dev/gemini-api/docs/models)
[![Current baseline](https://img.shields.io/badge/current%20baseline-Gemini%203.8%20Flash-34A853)](https://ai.google.dev/gemini-api/docs/latest-model)

</div>

This is an independent, evidence-led collection of practical workflows for **Gemini 4 Pro**: coding agents, multimodal analysis, research, structured generation, visual prototyping, tool use, evaluations, and safety checks.

> [!WARNING]
> **Status snapshot — September 19, 2026:** Google’s public Gemini API catalog and DeepMind model pages do not list a callable Gemini 4 Pro model. There is no official Gemini 4 Pro model ID, model card, price, context limit, or launch date to document. Community posts and Arena screenshots speculate that an unusually capable model shown as <code>gemini-3.8-flash</code> may be a Gemini 4 Pro checkpoint. That identity claim is unconfirmed. This repository labels it as a **community signal**, not a fact.

The goal is to make the discussion useful without turning a rumor into an API tutorial. Every case states what is known, what is inferred, how to reproduce the workflow with an available Gemini model, and what evidence would be needed to upgrade the claim.

## Related Projects

- [awesome-gpt-6-astra](https://github.com/Anil-matcha/awesome-gpt-6-astra) — companion use cases, prompts, evaluations, and safety notes for GPT-6 Astra.
- [awesome-gemini-4-carbon](https://github.com/Anil-matcha/awesome-gemini-4-carbon) — Source-linked tracker for Google's Gemini 4 Carbon: cyber and coding benchmarks, pricing, restricted-access status.
- [awesome-claude-fable-5](https://github.com/Anil-matcha/awesome-claude-fable-5) — predecessor Claude frontier-model use-case archive.
- [awesome-claude-fable-5-1](https://github.com/Anil-matcha/awesome-claude-fable-5-1) — companion launch-evidence and use-case collection for Claude Fable 5.1.
- [Awesome-Gemini-Omni-API-Prompts](https://github.com/Anil-matcha/Awesome-Gemini-Omni-API-Prompts) — prompts and API examples for Gemini Omni media workflows.
- [awesome-ai-video-models](https://github.com/Anil-matcha/awesome-ai-video-models) — broader video-model comparison for the multimodal and 3D workflows tracked here.
- [awesome-ai-image-models](https://github.com/Anil-matcha/awesome-ai-image-models) — image-model comparison for visual-generation and editing workflows.
- [awesome-generative-ai-apps](https://github.com/Anil-matcha/awesome-generative-ai-apps) — production-ready AI SaaS templates for turning model workflows into applications.
- [Gemini API documentation](https://ai.google.dev/gemini-api/docs) — Google’s official developer documentation.

## Quick status

| Question | Evidence-led answer | Source |
|---|---|---|
| Is Gemini 4 Pro publicly released? | **Not confirmed.** It is not listed in the public Gemini API model catalog or the DeepMind model index. | [Gemini API models](https://ai.google.dev/gemini-api/docs/models), [DeepMind models](https://deepmind.google/models/gemini/) |
| Is there an official API identifier? | **No published Gemini 4 Pro identifier.** Do not send <code>gemini-4-pro</code> to an API and assume it works. | [Gemini API models](https://ai.google.dev/gemini-api/docs/models) |
| What is the community alias claim? | Some Arena observers claim that a model displayed as <code>gemini-3.8-flash</code> may be an unreleased Gemini 4 Pro checkpoint. | [X trend shared for this tracker](https://x.com/i/trending/2100554063016518107), [reported X discussion](https://officechai.com/ai/gemini-4-0-pro-arena/) |
| What is the official Pro baseline? | Gemini 3.1 Pro is a preview model for complex tasks, advanced coding, long-context, multimodal understanding, and algorithmic development. | [Gemini 3.1 Pro](https://deepmind.google/models/gemini/pro/), [model card](https://deepmind.google/models/model-cards/gemini-3-1-pro/) |
| What is the official fast baseline? | Gemini 3.8 Flash is listed as a stable model for long-horizon software engineering, autonomous agents, and complex enterprise workflows. | [Gemini 3.8 Flash](https://ai.google.dev/gemini-api/docs/latest-model) |
| What context/output numbers can be quoted safely? | The Gemini 3.1 Pro model card lists up to 1M input tokens and 64K output tokens. Those numbers are **not** Gemini 4 Pro specifications. | [Gemini 3.1 Pro model card](https://deepmind.google/models/model-cards/gemini-3-1-pro/) |

## How to read this repository

The evidence labels are intentionally strict:

- **Official** — published by Google in model documentation, an API reference, a model card, or a Google product announcement.
- **Integration** — published by a vendor or platform that exposes a Google model, with the exact surface named.
- **Community** — a public user report, demo, screenshot, or social post. Useful for hypotheses; not proof of model identity or general performance.
- **Evaluation** — a reproducible benchmark or test with a stated harness, date, and configuration.
- **Derived** — a workflow inferred from documented capabilities. It is a useful starting point, not a measurement.
- **Unverified** — a claim that lacks an official model identity, methodology, or independent reproduction.

Use the current official models to reproduce the workflows today. If Google later publishes Gemini 4 Pro, update the identity, model ID, pricing, limits, and evidence labels before treating any case as a Gemini 4 Pro result.

## Read first

1. **Do not invent an endpoint.** There is no verified Gemini 4 Pro API model string in the sources reviewed here.
2. **Record the surface.** Gemini app, AI Studio, Gemini API, Vertex AI, Arena, and a third-party wrapper are not interchangeable evaluation environments.
3. **Separate capability from identity.** An impressive output from <code>gemini-3.8-flash</code> may show what that endpoint did; it does not prove the endpoint is an unreleased Pro checkpoint.
4. **Keep a human approval boundary.** Tool calls, browser actions, code changes, purchases, messages, deletion, permissions, and production deployments must be controlled by the surrounding application.
5. **Capture evidence.** Save the prompt, model label, exact model ID if available, settings, files, tool schema, output, latency, cost, and reviewer decision.

## Reproducible API baseline

The following example uses an official model that is available in the Gemini API. Set <code>GEMINI_MODEL</code> to <code>gemini-3.8-flash</code> or <code>gemini-3.1-pro-preview</code> depending on the workflow. This is a baseline harness for the use cases below; it is not a Gemini 4 Pro access path.

Install the current Google GenAI SDK:

    pip install google-genai

Run a text or multimodal prompt:

    import os
    from google import genai

    client = genai.Client(api_key=os.environ["GEMINI_API_KEY"])
    model = os.getenv("GEMINI_MODEL", "gemini-3.8-flash")

    response = client.models.generate_content(
        model=model,
        contents=(
            "Act as a careful engineering reviewer. "
            "State assumptions, distinguish evidence from inference, "
            "and finish with a verification checklist."
        ),
    )

    print(response.text)

The syntax above follows Google’s [GenerateContent API examples](https://ai.google.dev/api/generate-content). Check the [current model catalog](https://ai.google.dev/gemini-api/docs/models) before selecting a model in a production application.

## Menu

| Section | Cases |
|---|---|
| [💻 Coding and software engineering](#-coding-and-software-engineering) | 1–3 |
| [🧰 Agents, tools, and research](#-agents-tools-and-research) | 4–6 |
| [🎨 Visual, structured, and multimodal work](#-visual-structured-and-multimodal-work) | 7–10 |
| [🧪 Evaluation and release tracking](#-evaluation-and-release-tracking) | 11–13 |
| [🛡️ Safety and practical limits](#-safety-and-practical-limits) | 14–15 |
| [📘 Prompt patterns](docs/coding-agent-use-cases.md) | Reusable templates |
| [🧾 Evidence ledger](docs/evidence-ledger.md) | Source and status history |

The cases are designed to be reproducible with a published Gemini model today. Claims about Gemini 4 Pro are marked explicitly when they depend on unverified community evidence.

## 💻 Coding and software engineering

### Case 1: Long-horizon repository work

**Use a strong Gemini model when a task crosses architecture, code, tests, tools, and several verification loops.**

Give the agent an outcome, repository context, allowed tools, constraints, and a definition of done. Ask it to inventory first, make a plan, implement in small changes, and verify each meaningful step.

Prompt pattern:

    Goal:
    <the outcome that must be true when the task is complete>

    Repository:
    <stack, entry points, relevant files, interfaces, and known constraints>

    Allowed tools:
    <read, search, test, edit, browser, or other tools; state what each may change>

    Definition of done:
    <tests, screenshots, logs, metrics, or reviewer checks>

    Work in stages. Inspect before editing. Keep an evidence log.
    Separate confirmed findings from hypotheses. Stop before irreversible actions.

**Verification:** run focused tests first, then the project-wide checks; attach changed files, command output, and unresolved risks.

**Evidence:** Official / Derived — Gemini 3.8 Flash is documented for long-horizon software engineering; Gemini 3.1 Pro is documented for advanced coding and algorithmic development. These are adjacent-model capabilities, not Gemini 4 Pro measurements.

### Case 2: Large-context code and document review

**Use multimodal context when the answer depends on a code repository plus design files, PDFs, screenshots, audio, or video.**

Ask for file-backed findings. Require the model to cite the file, symbol, page, timestamp, or image region supporting each claim. Ask it to distinguish a confirmed defect from a suspected issue and to propose the smallest safe change.

Prompt nudge:

    Review the supplied repository and media before proposing edits.
    Every finding must cite a file, symbol, page, timestamp, or visible region.
    Return:
    1. confirmed issues ordered by severity,
    2. hypotheses that need verification,
    3. reproduction steps,
    4. a minimal patch plan,
    5. tests that would prove the fix.
    Do not change files until the review is complete.

**Verification:** sample-check citations against the original files, then run the proposed reproduction steps. For visual findings, save before/after screenshots.

**Evidence:** Official / Derived — the Gemini 3.1 Pro model card describes text, image, video, audio, PDF, and code-repository understanding, with up to 1M input tokens.

### Case 3: Plan–build–review relay

**Use the highest-capability model for architecture and review, and a faster model for routine execution when the work can be checked mechanically.**

A practical relay:

1. Plan: identify interfaces, risks, acceptance criteria, and the smallest safe implementation.
2. Build: execute bounded tasks with tests and a change log.
3. Review: inspect the diff, test evidence, edge cases, and rollback path.

Keep the model names and prompts in the run record. Never describe the relay as a benchmark unless the task set, costs, latency, and grading method are published.

**Evidence:** Derived — based on the documented difference between the official Pro and Flash surfaces. It is a routing pattern, not a claim that Gemini 4 Pro exists.

## 🧰 Agents, tools, and research

### Case 4: Search-grounded research with custom tools

**Combine current web grounding with a small, typed business-tool surface.**

The research loop should be explicit:

1. Gather sources.
2. Extract claims and dates.
3. Reconcile conflicts.
4. Call only the tools needed to test or transform those claims.
5. Write an answer with citations, assumptions, and open questions.

Tool contract checklist:

- narrow JSON schemas;
- authorization and tenant checks inside the tool;
- timeouts and idempotency;
- dry-run or proposal mode before side effects;
- visible logs and a human approval step for consequential actions.

Google documents combining built-in tools such as Search with custom function calling for Gemini 3 models in the [tool-combination guide](https://ai.google.dev/gemini-api/docs/tool-combination).

**Evidence:** Official / Derived — the workflow is documented for current Gemini 3 models, not a Gemini 4 Pro endpoint.

### Case 5: Multimodal incident or field-report triage

**Turn mixed evidence into a structured investigation packet.**

Supply logs, screenshots, a short screen recording, an audio note, and the relevant runbook. Ask the model to produce:

- an event timeline;
- observations tied to the supplied evidence;
- competing root-cause hypotheses;
- missing data and the next safest diagnostic;
- a proposed fix with rollback steps;
- a concise handoff for a human operator.

Do not let the model silently treat a screenshot or transcript as authoritative. Require confidence and source references for every important conclusion.

**Evidence:** Official / Derived — Gemini 3.1 Pro’s model card lists text, image, video, audio, and PDF inputs. The incident workflow is a proposed application pattern.

### Case 6: Bounded browser and computer-use QA

**Use a model to inspect a test environment, reproduce a user journey, and report UI failures.**

Start with a disposable account and a test tenant. Give the agent a narrow goal, visible stop conditions, and a tool wrapper that blocks purchases, messages, deletion, permission changes, and production navigation by default.

Prompt pattern:

    Test only the staging tenant.
    Navigate to the checkout form, enter the supplied test values,
    and stop before submitting payment.
    Capture screenshots at each state.
    Report the first divergence from the expected flow.
    Do not create accounts, send messages, delete data, or change permissions.

**Verification:** replay the run from a clean state; compare screenshots; inspect action logs; have a human approve any change suggested by the agent.

**Evidence:** Derived — a safe harness pattern around multimodal and agentic capabilities. It is not evidence that an unreleased Gemini 4 Pro has computer-use access.

## 🎨 Visual, structured, and multimodal work

### Case 7: SVG and interface generation

**Treat the viral Arena SVG demos as a hypothesis to test, not as proof of model identity.**

Several public posts reported unusually polished SVG outputs from a model shown in Arena as <code>gemini-3.8-flash</code>, including a pelican-riding-a-bicycle example. The reports are useful because the task is easy to save, render, and compare, but they do not establish that the hidden model was Gemini 4 Pro.

Prompt pattern:

    Create one self-contained SVG, viewBox 0 0 1200 800.
    Draw a pelican riding a bicycle in a clean editorial illustration style.
    Use semantic groups, accessible text labels, deterministic geometry,
    no external assets, no filters that require network access,
    and include a short design note after the SVG.
    Return valid XML only for the SVG portion.

**Verification:** parse the XML, render it in two SVG engines, check the viewBox and text, compare file size, and record the exact model surface and label.

**Evidence:** Community / Unverified — [X trend](https://x.com/i/trending/2100554063016518107) and [reported Arena discussion](https://officechai.com/ai/gemini-4-0-pro-arena/). Do not cite this case as an official Gemini 4 Pro capability.

### Case 8: Voxel and 3D scene prototyping

**Use a text-to-code prompt to explore a scene, then validate it in a real renderer.**

Community posts also showed a voxel pagoda-style 3D demo attributed to the same disputed Arena identity. A useful reproduction does not ask whether the demo “looks impressive”; it measures whether the output runs, uses deterministic assets, and satisfies a small scene specification.

Prompt pattern:

    Build a self-contained Three.js scene with a voxel pagoda,
    three levels, a ground plane, a controllable orbit camera,
    deterministic colors, and no external network dependencies.
    Return the complete runnable HTML.
    Add a smoke-test checklist for loading, camera control, and object count.

**Verification:** run in a sandbox, capture a screenshot, check console errors, count scene objects, and test on a cold load with network disabled.

**Evidence:** Community / Unverified — public Arena demos reported by X users and summarized in the [Arena discussion report](https://officechai.com/ai/gemini-4-0-pro-arena/).

### Case 9: Structured JSON under a hard schema

**Prefer a strict schema, bounded output, and validation over “infinite output” demonstrations.**

Use JSON mode or structured output where the API supports it. Define required fields, maximum array lengths, allowed enums, and a checksum or summary field. Validate the response before using it.

Prompt pattern:

    Return an array of exactly 25 planets.
    Each item must contain id, name, mass_kg, radius_km, and evidence.
    mass_kg and radius_km must be numbers.
    evidence must be one of: observed, simulated, unknown.
    Do not invent an external citation. If a value is unknown, use null.

**Verification:** parse the response, validate against the schema, reject extra keys, and measure truncation and retry rate.

**Evidence:** Official / Derived — Google documents controlled JSON generation for current Gemini models. A community “256K output ceiling” claim is listed in the evidence ledger as unverified and is not a recommended production pattern.

### Case 10: Video, audio, and PDF understanding

**Convert long media into an evidence-linked brief.**

Ask for segment timestamps, speaker or scene changes, quoted phrases limited to what is needed, and an uncertainty column. For PDFs, require page numbers and preserve tables separately from prose.

A good output schema:

| Field | Meaning |
|---|---|
| <code>claim</code> | one concise observation |
| <code>source</code> | page, timestamp, frame, or file name |
| <code>confidence</code> | high, medium, or low |
| <code>action</code> | the next review or operation |
| <code>open_question</code> | what remains unresolved |

**Verification:** sample at least one source pointer per section and compare the summary against the original media.

**Evidence:** Official / Derived — the Gemini 3.1 Pro model card documents multimodal input; the use case is a reviewable workflow, not a Gemini 4 Pro result.

## 🧪 Evaluation and release tracking

### Case 11: Candidate-identity evaluation harness

**Compare behavior without pretending that an alias reveals the hidden model.**

For every run, record:

- requested model string and displayed label;
- surface: API, AI Studio, app, Arena, or wrapper;
- date and timezone;
- prompt and attached files;
- generation settings and tool access;
- output, latency, errors, and estimated cost;
- evaluator rubric and score;
- whether the result was independently reproduced.

Compare official baselines such as <code>gemini-3.8-flash</code> and <code>gemini-3.1-pro-preview</code> on the same task set. If an Arena alias is available, store it as <code>observed_label</code>, not <code>official_model_id</code>.

**Evidence:** Evaluation / Derived — a measurement protocol. It does not assign an identity to an anonymous model.

### Case 12: Small, honest benchmark suite

Use a compact task set that reflects real work:

| Track | Example task | Primary metric |
|---|---|---|
| Coding | fix a seeded bug and add a regression test | tests passing, review score |
| Long context | find conflicts across a repository and policy PDF | citation precision, recall |
| Multimodal | extract timed observations from a short video | source-pointer accuracy |
| Structured output | emit records under a strict schema | valid-first-pass rate |
| SVG/UI | generate and render a deterministic artifact | render validity, rubric score |
| Agents | use one read-only tool and one proposal tool | task success, unsafe actions |

Publish the harness, task fixtures, grading rubric, and failure cases. Never compare numbers from different surfaces as if they were one benchmark.

### Case 13: Release-watch evidence ledger

Watch for these upgrade signals:

1. a Google-owned model page naming Gemini 4 Pro;
2. an official API catalog entry with a stable or preview model ID;
3. a model card with context, modalities, evaluations, and limitations;
4. official pricing and availability;
5. an independent reproduction that names the exact surface and configuration.

When one appears, update [docs/evidence-ledger.md](docs/evidence-ledger.md), then revise the status table and examples. Keep older community claims in the history instead of silently rewriting them.

## 🛡️ Safety and practical limits

### Case 14: Prompt-injection and tool-boundary evaluation

Test the model and the harness together. Include untrusted text in a webpage, PDF, image, or tool result that attempts to override the task. Measure whether the agent:

- treats retrieved content as data rather than instructions;
- asks for approval at the correct boundary;
- refuses unauthorized tool arguments;
- logs the attempted injection;
- preserves the original task and source precedence rules.

The tool wrapper must enforce the boundary. A prompt saying “do not delete files” is not a substitute for a tool that cannot delete files.

### Case 15: Production-readiness checklist

Before deploying any Gemini workflow:

- name the exact model ID and surface;
- set timeouts, budgets, and retry limits;
- validate structured outputs;
- isolate secrets and private files;
- redact sensitive data where possible;
- use least-privilege tools;
- require approval for irreversible actions;
- log inputs, outputs, tool calls, and reviewer decisions;
- define rollback and incident response;
- rerun the evaluation suite after model or prompt changes.

No benchmark score or viral demo removes the need for domain review in legal, medical, financial, security, employment, or production operations.

## Contributing

Contributions are welcome when they add a concrete workflow, prompt, integration, evaluation, or correction.

Please include:

- a direct source link;
- the evidence label;
- model name, exact ID, and surface;
- publication or observation date;
- the prompt, tool contract, benchmark method, or reproduction steps;
- costs, limits, safety boundaries, and failure modes when relevant.

Do not submit guessed model IDs, invented prices, private transcripts, secrets, exploit chains, or unattributed benchmark numbers. See [CONTRIBUTING.md](CONTRIBUTING.md) and the [use-case template](docs/use-case-template.md).

## Acknowledgements and correction policy

This repository is an independent community collection and is not affiliated with or endorsed by Google. It follows the evidence-led structure of the Anil-matcha GPT-6 Astra and Claude Fable collections.

If Google publishes Gemini 4 Pro, or if a cited community claim is corrected, open an issue with the source and the exact passage to update. Keep the correction visible in the evidence ledger.

## Sources

- [Gemini API models](https://ai.google.dev/gemini-api/docs/models)
- [What’s new in Gemini 3.8 Flash](https://ai.google.dev/gemini-api/docs/latest-model)
- [Gemini 3.1 Pro model page](https://deepmind.google/models/gemini/pro/)
- [Gemini 3.1 Pro model card](https://deepmind.google/models/model-cards/gemini-3-1-pro/)
- [GenerateContent API](https://ai.google.dev/api/generate-content)
- [Combining built-in tools and function calling](https://ai.google.dev/gemini-api/docs/tool-combination)
- [X trend shared for this tracker](https://x.com/i/trending/2100554063016518107)
- [Reported Arena discussion](https://officechai.com/ai/gemini-4-0-pro-arena/)
