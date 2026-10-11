# Source Engineering -- Manifesto

> A discipline for grounding AI-based decisions with integrity.

This is the canonical manifesto. It supersedes the legacy `MANIFESTO.md` at the repo root, which carried a small cardinal-rule debt (em-dashes that violated the GitHub D-004 rule) and has been retired. The prose below is the same discipline, expressed under the canonical naming and convention set.

## Why this exists

Large language models produce confident answers. Confidence is not the same as justification. In high-stakes domains (legal, medical, financial, regulatory), a structurally valid answer can be the wrong answer. The gap between "the model answered" and "I can act on the answer" is the **hesitation factor**.

Source Engineering is the discipline that closes the hesitation factor by treating model reasoning as **evidence-anchored**, not merely produced. The discipline is not a replacement for the model; it is the engineering surface around the model that turns a response into something a person can audit, challenge, and trust on the merits rather than on faith.

The original framing essay (December 2025) named the **five pillars**: data provenance, contextual signature mapping, chain of evidence, explainability anchoring, and human validation points. The one-year-later essay (October 2026) reframed the pillars into a **four-layer stack** (typed model, runtime validation, business guardrails, audit trail) and identified the remaining gap as the **judgment gap**: a model can return a structurally valid answer that is the wrong answer for the business.

The discipline exists to close both gaps.

## The three principles

### 1. Provenance is a property of the response

Every input that shaped an output (prompt, retrieval chunk, system setting, prior turn, calibrated parameter) is logged at the time of the call and surfaces with the response. Not as an afterthought. Not in a separate dashboard. As part of the answer itself. If the user cannot see what shaped the answer, the user cannot trust the answer.

### 2. Context is a runtime signal

Context engineering (temperature, top-p, prompt cache state, tool budget, retrieval depth) is a public interface, not a hidden knob. The user sees what the model sees. The user can adjust it. The user can ask *why it was set this way*. A model operator that hides its context from the user is asking the user to trust the operator, not the model. Source Engineering rejects that.

### 3. Judgment is separate from evidence

A model can return a decision that fits every declared option and still be the wrong decision for the situation. The evidence chain proves what the model considered; the judgment layer decides whether the decision holds for this user, this moment, this stake. The two must be separable surfaces, exposed to the same reviewer, so the reviewer can ask "did you consider the right things?" and "given what you considered, is this the right call?" as separate questions.

## What this discipline is not

Source Engineering is often confused with adjacent disciplines. The boundaries matter because each adjacent field optimizes a different surface, and conflating them hides the gap the discipline is closing.

- **Not prompt engineering.** Prompt engineering optimizes the question. Source Engineering optimizes the auditability of the answer. A perfectly prompted system can still be un-auditable; an auditable system can use plain prompts.
- **Not chain-of-thought alone.** CoT can produce plausible traces. Source Engineering requires the trace to be evidence-anchored to the inputs, not merely self-consistent. A CoT that loops inside its own reasoning is not a chain of evidence.
- **Not model-side explainability.** Model-side explainability explains weights and activations (SHAP, attention maps, neuron analyses). Source Engineering explains the journey from input to decision in domain terms the user can act on.
- **Not trust-by-policy.** "Trust the provider" is not engineering. Source Engineering earns trust by surfacing enough for the user to verify, not by asking the user to assume.
- **Not MLOps.** MLOps owns the training and deployment pipeline. Source Engineering owns the response surface, the audit trail, and the evidence chain at the call site. MLOps ends where the model is deployed; Source Engineering begins where the model is called.

For the full positioning matrix (with OpenDEAM, ECF, agent frameworks, and retrieval-augmented generation), see [`docs/05-positioning.md`](05-positioning.md).

## The chain of orchestrable and traceable sources (COTS)

A Source Engineering response carries a **COTS** -- a structured, machine-readable bundle containing:

- **Inputs**: every data point that shaped the response, with provenance metadata
- **Context**: the runtime parameters set for this call, with their rationale
- **Decisions**: every decision point the workflow took, with the option set and the rationale
- **Evidence**: the chain linking each output to its supporting data and reasoning step
- **Validation**: the feedback surfaces exposed back to the user for this response

The COTS is the contract. If a response does not carry one, it is not a Source Engineering response. The COTS is the unit of accountability: every audit, every appeal, every re-run, every cross-domain comparison works against the COTS, not against the response alone.

The COTS schema is versioned (current target: v0.1 in Slice 1 of the roadmap). The formal JSON / YAML / TOML schema is captured in `docs/framework/cots-schema.md` once Slice 1 lands; this manifesto holds the prose.

## Working principles for contributors

- **No silent pillars.** Every claim in this discipline must trace to a working artifact or an explicitly labeled open question. The discipline grows by closing questions, not by accumulating epics.
- **Reversible commitments.** Every interface proposal is a proposal until it ships. Once it ships, downgrades get a CR. Nothing in the discipline is irreversible; every change is a branch, a CR, a review, a merge.
- **Domain first.** Architectures that work for one high-stakes domain do not assume others. Each domain writes its own COTS profile. The shared skeleton is the discipline; the per-domain profile is the implementation.
- **Human in the loop, but not in the way.** Feedback surfaces are designed to be evidence-aware and latency-tolerating, not to require a human at every step. Humans are reviewers, not gatekeepers of every call.

## Open questions (carried forward from the 2026 reframing)

- **Calibration drift across customer segments.** How the runtime layer surfaces per-segment drift without leaking segment identity. Slice 4 in the roadmap.
- **Latency vs. auditability.** The cost of carrying a full COTS at every call, and where amortization is possible (caching, batched audit, asynchronous persistence). Slice 4.
- **Judgment gap closure.** What does it take for the judgment layer to be a first-class surface, not a post-hoc annotation? Slice 5 / Slice 6.
- **Legal-document summarization prototype.** The in-progress validation domain; results feed back into the framework's evidence schemas. Slice 3.

The discipline grows where these questions get answered. The roadmap records which slice answers which question; the kanban board records the day-to-day work.

## Anchors

- December 2025 essay: [Source Engineering: Grounding AI-based Decisions with Integrity](https://nuel.otchere.com/posts/2025/12/source-engineering-grounding-ai-based-decisions-with-integrity.html)
- October 2026 essay: [Reframing the Five Pillars, One Year Later](https://nuel.otchere.com/posts/2026/10/reframing-the-five-pillars-one-year-later.html)
- Repository: https://github.com/Source-Engineering
- Roadmap: [`ROADMAP.md`](https://github.com/Source-Engineering/project-governance/blob/main/ROADMAP.md)
