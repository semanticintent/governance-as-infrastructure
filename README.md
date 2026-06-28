# Governance-as-Infrastructure: From Audit to Runtime

<!-- DOI: concept ("all versions") DOI — always resolves to the latest release -->
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21010922.svg)](https://doi.org/10.5281/zenodo.21010922)
[![ORCID](https://img.shields.io/badge/ORCID-0009--0006--2011--3258-brightgreen?logo=orcid)](https://orcid.org/0009-0006-2011-3258)

**Author:** Michael Shatny ([ORCID](https://orcid.org/0009-0006-2011-3258))

Governance is traditionally a document, a review, or an audit — applied *after* a system has produced something to govern. This paper proposes it can be compiled into runtime infrastructure: a **Governed Constraint Set** that operates before any artifact exists and *gates* execution on it. Where Methodology-as-Infrastructure compiles *how to think* and Intent-as-Infrastructure compiles *what to reach into*, **Governance-as-Infrastructure compiles *what must be true*** — with the human reserved at the moment of formalization, before any agent runs.

## Read the Paper

- [Governance-as-Infrastructure: From Audit to Runtime](docs/governance-as-infrastructure.md)

## Key Argument

| Governance-as-Audit | Governance-as-Infrastructure |
|---|---|
| Applied *after* the artifact exists | Operates *before* any artifact exists |
| Prose policy, dashboards, post-hoc review | Explicit, machine-checkable Governed Constraint Set |
| Findings are advisory | The gate blocks execution |
| Unknowns discovered in incidents | Unresolvable residue surfaced up front |
| Remediation — late, expensive, reactive | Design — early, cheap, proactive |

## The Four Required Properties

For a system to qualify as Governance-as-Infrastructure, all four must hold:

1. **Pre-execution** — operates before any artifact exists or any agent is invoked (design, not audit; upstream of even Policy-as-Code, which gates *deployed* artifacts)
2. **Constraint-formalized** — governance compiled into an explicit, machine-checkable **Governed Constraint Set**, not prose policy or tribal knowledge
3. **Residue-sovereign** — the Governed Constraint Set, *including the unresolvable residue*, is a human-readable, git-trackable, provable artifact; the residue is surfaced, never silently auto-resolved
4. **Human-as-primitive at formalization** — human judgment is reserved at the moment of formalization, by design, and **execution gates on it** — nothing proceeds past unacknowledged residue

A system with audit logs and dashboards that resolves ambiguity silently and gates nothing is *Governance-as-Audit*, not GaI. The four-property test is the diagnostic.

## Evidence Base

- **The CAL publishing pipeline** — a production system (`semantic-cal-case-studies`) that researches, authors, validates, compiles, and deploys analytical artifacts in a single agentic session. Its three pre-deploy gates (audit · fact verification · author DOI judgment) form a Governed Constraint Set satisfying all four properties. The **UC-236 incident** ("cited ≠ correct") is the documented event that turned implicit governance into an explicit, gating constraint set; the dividend was a sustained run of zero post-publish corrections.
- **Phoenix Runtime** — seven-agent legacy modernization pipeline; the A-06 Validator + `phoenix gate --approve` wire governance into the run.
- **RECALL** — sovereign provenance: every artifact embeds its source and authorship, making the constraint set git-trackable and provable.

## The Paradigm Progression

| Paradigm | What it encodes | Human role |
|---|---|---|
| Infrastructure-as-Code | Server provisioning | Designs config |
| Policy-as-Code | Compliance rules on deployed artifacts | Sets thresholds |
| Methodology-as-Infrastructure | Analytical framework | Receives output |
| Intent-as-Infrastructure | Workflow intent | First-class primitive at the *moment of consequence* |
| **Governance-as-Infrastructure** | **What must be true before execution** | **First-class primitive at the *moment of formalization*** |

## The Two Lineages

GaI sits where two progressions converge — one of disciplines, one of infrastructure paradigms:

```
Discipline axis:       TDD  →  DDD  →  BDD  →  GDD
Infrastructure axis:   IaC  →  PaC  →  MaI  →  IaI  →  GaI
```

Both terminate, upstream, at governance. **GDD is the discipline (the verb); GaI is the infrastructure (the noun).** GDD's ICR cycle *produces* the Governed Constraint Set; GaI is the claim that the Set *is* a gating runtime. Same primitive, two axes.

## Related Work

- [Governance-Driven Design (GDD)](https://doi.org/10.5281/zenodo.20938777) — the discipline GaI is the infrastructure counterpart of
- [Intent-as-Infrastructure: When the Compiler Is Claude](https://doi.org/10.5281/zenodo.20681523) — the preceding paradigm in the progression
- [Methodology-as-Infrastructure: From Framework to Runtime](https://doi.org/10.5281/zenodo.18946631) — the first paradigm in the progression
- [The Synthesis Gate: What Makes a Workflow Agentic](https://doi.org/10.5281/zenodo.20684283) — the human-judgment node, at the moment of consequence
- [Semantic Intent as Single Source of Truth](https://doi.org/10.5281/zenodo.17114972) — governance as a primitive, established before the term trended

## License

MIT
