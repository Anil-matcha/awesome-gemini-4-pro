# Coding-agent use cases

This guide turns the repository’s coding cases into prompts that can be run against an official Gemini model today. Replace the model only after checking the current [Gemini API catalog](https://ai.google.dev/gemini-api/docs/models).

## 1. Repository audit before editing

    Goal:
    Review this repository for the highest-risk correctness, security, and
    maintainability issues. Do not edit files.

    Method:
    1. Inventory the repository and identify the runtime entry points.
    2. Trace the data flow for the requested feature.
    3. Inspect tests, configuration, dependency versions, and deployment files.
    4. Separate confirmed defects from hypotheses.

    Output:
    - finding ID and severity;
    - exact file and symbol;
    - evidence and reproduction steps;
    - impact;
    - smallest safe fix;
    - tests that would prove the fix;
    - residual uncertainty.

Use a read-only tool wrapper for the first pass. A large context window increases coverage, but it does not replace tests or human review.

## 2. Multi-file implementation with a verification loop

    Implement this change:
    <short outcome>

    Constraints:
    <compatibility, performance, security, and UX constraints>

    Before editing:
    - inspect the current implementation;
    - list files that will change;
    - identify likely regressions;
    - state assumptions that affect the design.

    During editing:
    - make the smallest coherent change;
    - keep interfaces backward compatible unless explicitly asked otherwise;
    - add or update regression tests;
    - do not modify secrets, production data, or unrelated formatting.

    Done means:
    - focused tests pass;
    - broader checks pass or their failures are explained;
    - the diff is summarized file by file;
    - rollback steps are documented.

## 3. Tool-calling agent with approval boundaries

Use a typed tool contract. The model may inspect and propose; the application decides whether a side effect is authorized.

    Tools:
    - list_records: read-only, tenant-scoped, max 100 records.
    - draft_change: creates a proposal only; never applies it.
    - apply_change: requires an approval token from the caller.

    Rules:
    - validate every argument server-side;
    - reject unknown fields;
    - log the user, model, tool, arguments, and result;
    - make retries idempotent;
    - stop if source instructions conflict with the system policy;
    - ask for approval before apply_change.

The tool wrapper is the security boundary. Prompt instructions are not an access-control system.

## 4. Long-context review with source pointers

For a repository, design deck, policy PDF, or incident recording:

    Read all supplied sources before answering.
    For every material claim, provide a source pointer:
    file and line, PDF page, video timestamp, audio timestamp, or image region.
    Return separate sections for:
    - confirmed observations;
    - inferred explanations;
    - contradictions;
    - missing evidence;
    - recommended next checks.

Sample-check at least one pointer from every section before relying on the result.

## 5. Evaluation harness

Store a run manifest next to every output:

    requested_model: gemini-3.8-flash
    displayed_label: gemini-3.8-flash
    surface: Gemini API
    observed_at: 2026-09-19T00:00:00+05:30
    generation_settings: <complete settings>
    tools: []
    files: []
    prompt_hash: <hash>
    output_hash: <hash>
    latency_ms: <number>
    estimated_cost_usd: <number or unknown>
    evaluator: <rubric and reviewer>
    reproduction: <yes or no>

If an anonymous Arena model is tested, set official_model_id to null and retain the displayed label separately. Never convert an alias into a guessed model ID.
