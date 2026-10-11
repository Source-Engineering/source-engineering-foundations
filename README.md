# Source Engineering -- Foundations

> The discipline's intellectual home. Definition, principles, terminology, scope and non-goals.

This repository holds the discipline's definition: what Source Engineering is, what it is not, the three principles it stands on, the open questions it is closing, and the explicit positioning against adjacent disciplines. Every other aspect repo derives its legitimacy from this one.

## What is in this repository

- `docs/00-manifesto.md` -- the canonical manifesto. The "why this exists" arc, the three principles, the COTS contract, the contributor principles, the open questions.
- `docs/05-positioning.md` -- the explicit positioning matrix against eleven adjacent disciplines (ML/alignment, prompt engineering, context engineering, CoT/X-of-Thought, model-side XAI, MLOps, agent frameworks, observability, RAG, OpenDEAM/ECF, trust-by-policy).
- `terminology.md` -- the discipline's working vocabulary. Terms like *COTS*, *hesitation factor*, *judgment gap*, *evidence-anchored*, *provenance-as-response*, and the layer names.

## Provenance

The content in this repository was developed following two essays:

- [Source Engineering: Grounding AI-based Decisions with Integrity (December 2025)](https://nuel.otchere.com/posts/2025/12/source-engineering-grounding-ai-based-decisions-with-integrity.html) -- introduces the five pillars and the hesitation factor.
- [Reframing the Five Pillars, One Year Later (October 2026)](https://nuel.otchere.com/posts/2026/10/reframing-the-five-pillars-one-year-later.html) -- reframes the five pillars into a four-layer stack and identifies the judgment gap.

The original monorepo home for this content is now retired. The discipline's primary working repository is [Source-Engineering/project-governance](https://github.com/Source-Engineering/project-governance), which holds the change process, the ROADMAP, and the WBS epics.

## How to engage

- **Read the manifesto first.** Start at `docs/00-manifesto.md`.
- **Then the positioning matrix.** `docs/05-positioning.md` answers "isn't this just X?" for every adjacent discipline.
- **Then the terminology.** `terminology.md` gives you the working vocabulary.
- **Propose changes** through the change process in [Source-Engineering/source-engineering-governance](https://github.com/Source-Engineering/source-engineering-governance).

## Organisation

The discipline is published as a set of repositories under the [Source-Engineering](https://github.com/Source-Engineering) GitHub organisation. One authoritative home per artefact:

| Repo | Owns |
|---|---|
| [Source-Engineering/.github](https://github.com/Source-Engineering/.github) | Org profile README |
| [Source-Engineering/project-governance](https://github.com/Source-Engineering/project-governance) | Change process, ADRs, RFCs, release policy |
| [Source-Engineering/source-engineering-foundations](https://github.com/Source-Engineering/source-engineering-foundations) (this repo) | Discipline definition, principles, terminology |
| [Source-Engineering/source-engineering-research](https://github.com/Source-Engineering/source-engineering-research) | Research agenda, hypotheses, experimental protocols |
| [Source-Engineering/source-engineering-model](https://github.com/Source-Engineering/source-engineering-model) | Canonical conceptual and data model |
| [Source-Engineering/source-engineering-specifications](https://github.com/Source-Engineering/source-engineering-specifications) | Normative technical requirements |
| [Source-Engineering/source-engineering-architecture](https://github.com/Source-Engineering/source-engineering-architecture) | Reference architecture, blueprint stack |
| [Source-Engineering/source-engineering-reference-implementation](https://github.com/Source-Engineering/source-engineering-reference-implementation) | Working reference code |
| [Source-Engineering/source-engineering-conformance](https://github.com/Source-Engineering/source-engineering-conformance) | Conformance test suite |
| [Source-Engineering/source-engineering-tools](https://github.com/Source-Engineering/source-engineering-tools) | Reusable software utilities |
| [Source-Engineering/source-engineering-case-studies](https://github.com/Source-Engineering/source-engineering-case-studies) | Evaluated demonstrations, case studies |
| [Source-Engineering/source-engineering-practice](https://github.com/Source-Engineering/source-engineering-practice) | Practitioner guidance |
| [Source-Engineering/source-engineering-education](https://github.com/Source-Engineering/source-engineering-education) | Curriculum and learning resources |

## Status

This is the foundations slice. The canonical manifesto and the positioning matrix are stable; updates follow the change process in the governance repo. The terminology is a working document and evolves with the discipline.

## License

Apache-2.0. See [LICENSE](LICENSE).
