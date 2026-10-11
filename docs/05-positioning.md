# Source Engineering -- Positioning

> Where Source Engineering sits, and what it is not.

This document is the explicit positioning matrix for the Source Engineering discipline. It is the second half of the manifesto and is the answer to "but isn't this just X?" where X is one of the adjacent disciplines the work is often confused with. The structure is: a positioning summary, a per-discipline comparison table, then per-discipline notes with the specific surface each adjacent field owns and the specific surface Source Engineering owns.

## Positioning summary

Source Engineering is a **discipline about the response**, not about the model, the prompt, the training pipeline, or the deployment. The discipline's claim is that the response is a software artifact in its own right, with its own engineering surface, and that this surface is currently under-engineered. The five pillars and the four-layer stack are the engineering surfaces the discipline proposes.

Concretely:

- If you are optimizing **the model** (training, fine-tuning, RLHF, distillation, quantization, evals), you are in ML / alignment work. Source Engineering is downstream of you.
- If you are optimizing **the prompt** (templates, structured outputs, tool definitions, function calling, context window packing), you are in prompt / context engineering. Source Engineering is downstream of you.
- If you are operating **the system around the model** (orchestration, retrieval, agents, observability, deployment, scaling), you are in MLOps / agent frameworks / platform engineering. Source Engineering consumes the COTS that this work produces.
- If you are **the human in front of the answer** (legal reviewer, medical practitioner, financial analyst, regulator), Source Engineering exists to make your review possible in a way the current surface does not.

Source Engineering is the layer that turns an answer into something a human reviewer can act on with the hesitation factor reduced. It is a *response-side* discipline, not a model-side or platform-side one.

## Comparison matrix

| Adjacent discipline | Owns | Does not own | Source Engineering differs because |
|---|---|---|---|
| **ML / alignment** | Model weights, training, fine-tuning, evals | Response surface, audit trail, evidence chain | The hesitation factor persists even after a well-aligned model; SE adds the response-side surface alignment cannot reach. |
| **Prompt engineering** | Question framing, prompt templates, structured outputs, tool calling | Audit trail, evidence chain, judgment surface | A perfectly prompted system can still be un-auditable. SE makes the answer auditable regardless of prompt quality. |
| **Context engineering** | Runtime parameters (temperature, top-p), prompt cache, tool budget, retrieval depth | Provenance-as-response, evidence-anchoring to inputs, user-visible context | SE treats context as a public interface and pairs it with provenance + evidence; context engineering alone surfaces the knobs but not the audit. |
| **CoT / X-of-Thought** | Reasoning traces, intermediate steps | Evidence linking to inputs, structured audit, judgment surface | CoT is a self-consistent trace; SE requires the trace to be evidence-anchored to inputs and exposed for review. |
| **Model-side explainability** (SHAP, attention, neuron analysis) | Weight-level, activation-level explanations | Domain-level explanation of the input-to-decision journey | SE explains in domain terms the user can act on; XAI explains in model terms. |
| **MLOps** | Training pipeline, deployment, monitoring, scaling | Response surface, COTS, audit trail | MLOps ends at deployment; SE begins at the call site. |
| **Agent frameworks** (LangChain, LlamaIndex, AutoGen) | Orchestration, tool use, multi-step workflows | Cross-provider COTS adapters, user-visible audit, evidence schema | Agent frameworks carry the trace internally; SE requires the trace to be a structured bundle exposed to the reviewer. |
| **Observability** (LangSmith, Langfuse, Honeycomb) | Operator-facing traces, debugging, performance | End-user-visible traces, evidence-anchored COTS, judgment surface | Observability surfaces traces to operators; SE surfaces them to the user and ties them to inputs. |
| **Retrieval-augmented generation** (RAG) | Retrieval, ranking, grounding | COTS schema, judgment separation, evidence-anchoring at the response level | RAG grounds the answer in retrieved documents; SE grounds the answer in a COTS that includes the retrieval plus the reasoning plus the user feedback surfaces. |
| **OpenDEAM / Enterprise Semantics / ECF** | Enterprise architecture, semantic frameworks, governance canon | AI-decision auditability, evidence chain at the call site | SE is a *consumer* of ECF-style semantic discipline and a *peer* of OpenDEAM at the architecture layer; SE does not duplicate either. |
| **Trust-by-policy** ("the provider vouches") | Compliance posture, contractual assurance | Engineered auditability, evidence chain, user-verifiable trace | SE rejects the premise; trust must be earned by surfacing, not asserted by policy. |

## Per-discipline notes

The matrix above is the lookup. The notes below give the load-bearing distinctions.

### vs. Context engineering

Context engineering in 2026 has matured into a first-class discipline (Anthropic prompt cache, OpenAI structured tools, Gemini thinkingBudget, runtime temperature). The pillars essay in 2025 anticipated this; the 2026 reframing essay names it. The two are not the same: context engineering gives the model operator the **knobs**; Source Engineering requires the knobs to be **surfaced to the user** as data points back to them, and the resulting response to be **evidence-anchored** rather than merely optimized. The open question the 2026 essay names is per-segment calibration drift -- that is a Source Engineering question (the audit surface), not a context engineering question (the knob surface).

### vs. Agent frameworks

Agent frameworks (LangChain, LlamaIndex, AutoGen, LangGraph, and the long tail) own orchestration. They carry internal traces. They do not, today, expose a COTS at the response level. Source Engineering's claim is that **a response without a COTS is not auditable**, regardless of how good the orchestration is. The future of agent frameworks is likely a COTS adapter per provider (this is a deferred slice in the roadmap), not a replacement for the discipline.

### vs. Observability

Observability tools (LangSmith, Langfuse, Arize Phoenix, Helicone, Honeycomb) are operator-facing. They make the engineer faster. Source Engineering's claim is that the **end user** also needs the trace, and tied to the inputs (not just the steps). The two are complementary: observability tools are the natural home for the operator-side view of the COTS; Source Engineering is the user-side view of the same data.

### vs. OpenDEAM / ECF / Enterprise Semantics

OpenDEAM, ECF (Enterprise Concepts Framework), and the broader Enterprise Semantics canon own the **architecture** and **semantics** layers of the enterprise. Source Engineering is a **consumer** of those: the COTS schema, the audit-trail layer, the evidence-anchoring rules all live within a discipline-aware architecture. The relationship is peer-level, not subordinate: SE does not duplicate the architecture work; SE does not need the architecture work to exist either -- it is independently shippable, but more powerful when paired. The deliberate scope-lock is that SE is **not** under the Enterprise-Semantics org; it is its own discipline org, and cross-references are explicit (CRs) rather than implicit (forks).

### vs. Trust-by-policy

The most common misread is "the provider vouches for the answer." Source Engineering rejects this premise at the architectural level. A trusted-by-policy response cannot be re-verified by the user; the user is asked to trust the provider's word. A Source Engineering response carries a COTS that the user can examine, re-run, and challenge. The discipline's value is precisely the refusal to substitute provider trust for user verification.

## Adjacent future work (deferred, not on the build path until a CR names them)

- Cross-provider COTS adapters (Anthropic Citations API, OpenAI Decisions API, Gemini Grounding with Google Search)
- A benchmark suite for evidence-anchored reasoning
- Visualization tools for the audit trail
- A COTS-to-ECF mapping (semantic interop with the Enterprise Concepts Framework)
- A formal differentiation CR vs. OpenDEAM, captured as a peer-discipline document

Each will land via its own CR. The discipline grows where these questions get answered; the kanban board at http://192.168.50.160:7000/board/13 records the day-to-day work.

## Anchors

- December 2025 essay: [Source Engineering: Grounding AI-based Decisions with Integrity](https://nuel.otchere.com/posts/2025/12/source-engineering-grounding-ai-based-decisions-with-integrity.html)
- October 2026 essay: [Reframing the Five Pillars, One Year Later](https://nuel.otchere.com/posts/2026/10/reframing-the-five-pillars-one-year-later.html)
- Manifesto: [`docs/00-manifesto.md`](00-manifesto.md)
- Repository: https://github.com/Source-Engineering
