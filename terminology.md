# Source Engineering -- Terminology

> The discipline's working vocabulary. Terms are defined as the discipline uses them; adjacent disciplines may use the same words differently, and the notes flag the distinction.

This document is canonical. New terms are added as the discipline grows; obsolete terms are marked deprecated and retained for one release.

## A

### Audit trail

The persistent record of who saw what response, when, with what evidence, and what they did with it. Part of Layer 4 of the discipline's four-layer stack. The audit trail is the substrate the discipline uses to support appeals, re-runs, and cross-domain comparison.

## B

### Blueprint (architecture blueprint)

A versioned architectural specification that floors one or more layers of the stack. Blueprints are the discipline's way of saying "this is what it looks like to ship Layer N as a coherent unit." Each blueprint is named with a version (v0.1, v0.2, ...).

## C

### Chain of Orchestrable and Traceable Sources (COTS)

The structured, machine-readable bundle that every Source Engineering response carries. The COTS has five named parts: Inputs, Context, Decisions, Evidence, Validation. The COTS is the unit of accountability for the discipline. If a response does not carry a COTS, it is not a Source Engineering response. See `docs/00-manifesto.md` for the full prose.

### Conformance

The property of an implementation that satisfies the discipline's specifications. Conformance is verified by the validation harness in `source-engineering-conformance` and is signalled by a badge.

## D

### Decision basis

The subset of a COTS that links a decision to its supporting evidence, its counterevidence, the context in which it was made, the constraints it was subject to, and any known gaps. See `source-engineering-research/protocols/legal-summarization-evaluation.md` for an example.

### Domain (high-stakes domain)

A vertical where a confidently wrong decision carries a cost the user is not willing to absorb through latency. Examples: legal review, medical triage, financial transaction routing, regulatory reporting. Source Engineering's case studies are organised by domain.

## E

### Evidence

The structured record of what the model considered, with provenance, in a COTS. Evidence is what the user can examine, re-run, and challenge. Evidence is not the model's chain-of-thought (which may be self-consistent and still wrong); evidence is the input-to-decision trail.

### Evidence-anchored

The property of a reasoning trace that ties every material claim to inspectable sources with explicit provenance. A response is evidence-anchored when a reviewer can reconstruct the declared basis for the decision from the COTS alone. The discipline's third principle, *Judgment is separate from evidence*, depends on the trace being evidence-anchored rather than self-consistent.

## H

### Hesitation factor

The reluctance to act on a model's answer because the user cannot verify its reasoning in time. The discipline exists to close the hesitation factor. The 2025 essay introduced the term; the 2026 reframing identified that the hesitation factor is smaller at the model layer but remains open at the judgment layer.

## J

### Judgment gap

The gap between a structurally valid answer (the model returned a decision that fits every declared option) and the right answer (the decision is correct for the situation). Source Engineering's claim is that closing the hesitation factor requires closing the judgment gap, and that closing the judgment gap requires the judgment layer to be a first-class surface. The 2026 reframing essay names this.

## L

### Layer

One of the four named layers of the discipline's stack: Typed Model (Layer 1), Runtime Validation (Layer 2), Business Guardrails (Layer 3), Audit Trail (Layer 4). Each layer has an interface, an owner, and a contract. See `source-engineering-architecture` for the full layer specification.

## P

### Pillar

One of the five named claims introduced in the 2025 essay: Data Provenance, Contextual Signature Mapping, Chain of Evidence, Explainability Anchoring, Human Validation Points. The 2026 reframing mapped the five pillars into the four layers; the pillars remain the language of the foundations, the layers are the language of the architecture.

### Provenance-as-response

The property of a response that carries the metadata of every input that shaped it as part of the answer itself, not in a separate dashboard. The discipline's first principle.

## R

### Re-run

The operation of repeating a decision given the same COTS, on a different model or a different version of the same model, to test for consistency. A re-run that produces a different decision against the same COTS is a conformance failure or a model-side bug, depending on the model contract.

## S

### Stack (four-layer stack)

The composition of the discipline into four named layers: Typed Model -> Runtime Validation -> Business Guardrails -> Audit Trail. Each layer hands a COTS-shaped artefact to the layer above. The stack is the discipline's shipping shape; the pillars are the discipline's intellectual shape.

## T

### Trace

A record of the steps the model took to produce a response. Traces can be operator-facing (LangSmith, Langfuse, Honeycomb) or user-facing (Source Engineering's claim). The discipline requires the trace to be evidence-anchored and exposed to the user, not merely produced for the operator.

### Typed question

A question that declares its answer shape in advance. The TypeSafe AI Jev model is the discipline's reference example of a model that accepts typed questions and returns calibrated probabilistic decisions. Typed questions are Layer 1's interface.

## V

### Validation

The subset of a COTS that captures the feedback surfaces exposed back to the user for the response. Validation is the discipline's fifth COTS component; it ties the response to the user's ability to challenge it.

## Deprecated terms

- *Trust-by-policy* -- still in use as the name of the failure mode the discipline is designed to prevent; not a term of art within the discipline.

## Related documents

- `docs/00-manifesto.md` -- the manifesto that names the three principles
- `docs/05-positioning.md` -- the positioning matrix that distinguishes Source Engineering from adjacent disciplines
- `source-engineering-model` -- the canonical conceptual model (forthcoming in P2)
- `source-engineering-architecture` -- the four-layer stack specification (forthcoming in P2)
