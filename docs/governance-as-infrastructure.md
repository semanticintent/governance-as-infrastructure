# Governance-as-Infrastructure: From Audit to Runtime

**Author:** Michael Shatny ([ORCID: 0009-0006-2011-3258](https://orcid.org/0009-0006-2011-3258))
**DOI:** [10.5281/zenodo.21010922](https://doi.org/10.5281/zenodo.21010922) (concept DOI — always resolves to the latest version)
**License:** MIT

---

## Abstract

Where Methodology-as-Infrastructure (MaI) compiles *how to think* into deterministic runtimes, and Intent-as-Infrastructure (IaI) compiles *what to reach into* with an intelligent compiler and the human reserved at the moment of consequence, **Governance-as-Infrastructure (GaI) compiles *what must be true* into a pre-execution layer, with the human reserved at the moment of formalization** — before any artifact exists.

This paper proposes that governance, traditionally a document, a review, or an audit applied after a system has produced something, can be compiled into runtime infrastructure: a **Governed Constraint Set** that is pre-execution, formalized, sovereign, and gating. Four properties are required — Pre-execution, Constraint-formalized, Residue-sovereign, and Human-as-primitive-at-formalization. A system that has audit logs and oversight dashboards but resolves ambiguity silently and blocks nothing is *Governance-as-Audit*, not GaI. The CAL publishing pipeline — a production system that researches, authors, validates, compiles, and deploys analytical artifacts — serves as the primary case study, including the incident (UC-236) that turned its implicit governance into an explicit, gating constraint set. GaI is positioned as the upstream completion of the `-as-Infrastructure` progression (IaC → PaC → MaI → IaI → GaI), and as the infrastructure counterpart to Governance-Driven Design (GDD): GDD is the discipline that produces a Governed Constraint Set; GaI is the claim that the Set is infrastructure.

---

## 1. The Problem: Governance Arrives After the Artifact Exists

The default posture of software governance is remediation. Compliance layers, audit trails, oversight dashboards, and review boards are applied *after* something has been built — a feature, a schema, a decision, an analysis. The artifact exists first; governance inspects it second.

This was tolerable when the gap between "designed" and "in production" was measured in weeks. A wrong assumption made during design had time to surface in review, in QA, in staging, before it reached a user. The audit ran in the slack between commitment and consequence.

AI-first delivery removes the slack. Agents generate code, schemas, analyses, and decisions at a pace that compresses the design-to-production gap toward zero. An agent executes on whatever intent it can infer, and it does so fast enough that the cost of a misunderstood assumption compounds before anyone has reviewed anything. Governance applied after the artifact exists is, in this regime, governance applied after the damage is done.

The instinctive response — *add more audit* — does not address the structural problem. It addresses it later and more expensively. More dashboards do not move the moment of governance earlier; they enrich the record of a decision already made. The question that audit cannot answer, because it arrives too late to ask it, is the one that matters most in AI-first delivery:

> **Do we know what *correct* means here — before any agent runs — and can we prove it?**

A discipline exists for asking that question: Governance-Driven Design (GDD) [1]. What follows is the claim that the *answer* to that question — the formalized definition of correctness, the explicit constraint set, the surfaced residue — is not merely a document the discipline produces. It is **infrastructure**: a runtime layer that gates execution, in the same sense that Methodology-as-Infrastructure made an analytical framework a runtime [2], and Intent-as-Infrastructure made workflow intent a runtime [3].

---

## 2. The Concept: Governance-as-Infrastructure

### 2.1 Definition

**Governance-as-Infrastructure (GaI)** is a paradigm in which the governance layer of a delivery system is compiled into an executable, sovereign artifact — the **Governed Constraint Set** — that operates *before* any output artifact is produced and *gates* execution on it.

Governance, in this framing, is not a property of the organization that surrounds a system. It is a property of the system itself: a formalized, machine-checkable statement of what must hold true, what must not be violated, and what remains unresolved and requires human judgment before execution proceeds. The Governed Constraint Set is to governance what the compiled runtime is to methodology in MaI, and what the sovereign finding record is to intent in IaI — the artifact that makes the abstraction operational rather than aspirational.

### 2.2 The Four Required Properties

For a system to qualify as Governance-as-Infrastructure, all four properties must hold.

**1. Pre-execution.** The governance layer operates before any output artifact exists and before any agent is invoked. This is the defining distinction from both classical audit (which inspects artifacts that already exist) and Policy-as-Code (which gates *deployed* configurations). GaI moves governance to the earliest possible moment — the formalization of what correctness means — which is the only moment early enough to catch a misunderstood assumption before a fast, autonomous agent acts on it.

**2. Constraint-formalized.** Governance is compiled into an explicit, machine-checkable Governed Constraint Set: what the system must hold true, what it must not violate. It is not prose policy, not a dashboard, not tribal knowledge held in a reviewer's head. The act of formalization is itself the governance act — it converts implicit, inconsistent expectations into an explicit object that can be stress-tested for internal conflict.

**3. Residue-sovereign.** The Governed Constraint Set — *including the unresolvable residue* — is a sovereign artifact: human-readable, git-trackable, and provable. The **residue** is the set of constraints that genuinely require human judgment: where business rules are undefined, where constraints conflict, where the domain has not been fully examined. In GaI the residue is a first-class output, surfaced explicitly, never silently auto-resolved. A system that encounters ambiguity and resolves it invisibly inside a scoring function fails this property: it has hidden the residue, not surfaced it.

**4. Human-as-primitive at formalization.** Human judgment is reserved at the moment of formalization — by design, not as an optional approval step — and execution gates on it. Nothing proceeds past unacknowledged residue. This is the property that situates GaI in the human-as-primitive lineage of IaI, but moves the human further upstream: IaI reserves the human at the *moment of consequence* (when ambiguity surfaces during execution); GaI reserves the human at the *moment of formalization* (when the constraint set is declared, before any artifact exists).

### 2.3 Relationship to Methodology- and Intent-as-Infrastructure

GaI is the third paradigm in a progression, and it is best understood by where it places the definition of "correct" and where it places the human.

| Paradigm | What it encodes | Human role |
|---|---|---|
| Infrastructure-as-Code | Server provisioning | Designs config |
| Policy-as-Code | Compliance rules on deployed artifacts | Sets thresholds |
| Methodology-as-Infrastructure | Analytical framework | Receives output |
| Intent-as-Infrastructure | Workflow intent | First-class primitive at the *moment of consequence* |
| **Governance-as-Infrastructure** | **What must be true before execution** | **First-class primitive at the *moment of formalization*** |

The progression is one of increasing upstreamness. Each paradigm pins something — provisioning, policy, methodology, intent, governance — earlier in the lifecycle, and the human, where present, moves with it. GaI is the upstream terminus: there is no layer earlier than the definition of what correctness means, because every other layer presupposes it.

GaI does not violate MaI's determinism requirement or supersede IaI's intelligent compiler. It composes with them. A GaI system may use an MaI runtime to execute its analysis and an IaI compiler to generate its artifacts; what makes it GaI is that a Governed Constraint Set gates both, before either runs.

### 2.4 Relationship to Governance-Driven Design (GDD)

GaI and GDD describe the same primitive from two sides.

**GDD is the discipline** — the practice of governance-first design, operationalized through the Iterative Constraint Refinement (ICR) cycle: formalize, stress, check, surface, gate, converge [1]. GDD answers *how a person or team works*.

**GaI is the infrastructure** — the claim that the artifact GDD's ICR cycle produces, the Governed Constraint Set, *is* a runtime layer. GaI answers *what governance becomes once it is executable*.

The bridge is direct: the ICR cycle of GDD produces the Governed Constraint Set; GaI is the proposition that the Governed Constraint Set is infrastructure. One cannot be derived from the other by relabeling, because they make different claims — GDD makes a methodological claim (this is how to surface assumptions before they become expensive); GaI makes an architectural claim (this surfaced, formalized object is a gating runtime, with qualifying properties). They cite each other; neither is redundant.

---

## 3. The Mechanism: The Governed Constraint Set

The Governed Constraint Set is produced by the ICR cycle and is the unit of infrastructure in GaI. Its structure is what makes it gating rather than advisory.

A constraint set holds three categories of statement:

- **What must hold true** — invariants the system commits to.
- **What must not be violated** — prohibitions the system enforces.
- **What remains unresolved** — the residue, requiring human judgment before execution proceeds.

The first two are checkable by machine. The third is the governance act. The exit condition of the cycle is not that all constraints are resolved — many will not be — but that all unresolved residue is **explicitly acknowledged, with an owner**. An organization that proceeds with full awareness of its unresolved constraints occupies a fundamentally different position than one that proceeds without knowing they exist. The difference between those two positions is the value GaI delivers, and it is delivered *before* execution, not discovered after.

The gate is the operational consequence. In a GaI system, execution does not proceed past unacknowledged residue. The gate is wired into the pipeline — it stops the run — rather than printed beside it as a recommendation. This is the property that distinguishes GaI from a governance *report*: a report informs; a gate blocks.

---

## 4. Case Study: The CAL Publishing Pipeline

### 4.1 The Pipeline as a Governance Runtime

The CAL publishing pipeline (`semantic-cal-case-studies`) is a production system that takes a structural analysis — a cascade event worth examining — and produces a live, citable, DOI-archived case study in a single agentic session. Its arc:

```
Scope → Research → Brief (JSON) → Audit (0/0/0)
  → Generate HTML → Verify facts → Deploy → Index → Promote
```

Each step is AI-executed. The human makes one decision, at the end: publish or not. The pipeline is fast, the sources are cited, the HTML compiles, deployment takes seconds. The instinct is to let it run.

GaI asks the prior question: what does *correct* mean here, and can it be proven before publication? That question was not formalized at the outset. An incident formalized it.

### 4.2 The Founding Incident (UC-236)

Case UC-236 shipped with three factual errors. A statistic attributed to one game belonged to another; a "zero" was in fact a "two"; a third figure was cited accurately from a source that was itself stale. Every prior check had passed: the model had cited its sources accurately, the sources existed, the citations matched, the audit returned 0/0/0, the HTML compiled.

None of those constraints caught the errors, because the operative constraint had never been made explicit. The pipeline's implicit definition of "correct" was *"every claim is supported by a cited source."* The incident revealed that this constraint and a different one — *"every claim is true"* — had been silently treated as identical. **Cited is not correct.** A model can cite accurately and still misread; a cited source can be stale or wrong.

This is the failure mode GaI exists to prevent: an assumption made too late, surfaced only by the cost of being wrong.

### 4.3 The Governed Constraint Set in Production

The response was not more audit. It was formalization. The pipeline's implicit constraints were made explicit, stress-tested for the conditions that would break each, and checked for internal conflict. Three conflicts surfaced — most importantly, that "cited" and "correct" were distinct constraints previously collapsed into one. The unresolvable residue was named: *are AI-cited facts verified against their sources, or merely cited?* — a question that cannot be answered from audit output, compile success, or citation count.

The residue produced infrastructure. Three gates are now wired into the pipeline before deployment:

1. **Structural + semantic audit (0/0/0)** — nothing proceeds with warnings.
2. **Explicit fact verification** — claim by claim, against cited sources. This gate did not exist before UC-236; it exists because of it.
3. **Author editorial gate** — the one constraint a machine cannot resolve: *does this thesis earn a permanent DOI?* Human, by design, before publication.

These three constitute a Governed Constraint Set that satisfies all four GaI properties: it operates pre-execution (before deploy), it is formalized (explicit, checkable), the residue is sovereign (the editorial gate is a named, permanent human decision), and execution gates on it (a run does not publish past an unverified claim or an unacknowledged thesis judgment).

### 4.4 The Dividend

After the constraint set was made explicit, cases shipped end-to-end — research, brief, audit, verify, generate, deploy, index, promote — with zero post-publish corrections across a sustained run. The pipeline did not get faster. The constraint set got explicit. Speed was never the bottleneck; the undefined definition of correctness was. This is the empirical signature of GaI: not a slower system, but a system whose governance moved upstream of its output, so that what gets built is what was actually meant.

---

## 5. Discussion

### 5.1 When Does a System Qualify as GaI?

The four-property test is the diagnostic. It separates GaI from two neighbors that resemble it.

*Governance-as-Audit* has dashboards, logs, and review, but applies them to artifacts that already exist, resolves ambiguity silently, and gates nothing. It fails Pre-execution and, usually, Residue-sovereign and Gating. It is the default posture, and it is not GaI.

*Policy-as-Code* formalizes compliance rules and can gate — but it gates *deployed* configurations against fixed thresholds. It is upstream of deployment, not upstream of the artifact's existence, and it does not surface a residue of decisions requiring human judgment; it encodes decisions already made. It is a genuine ancestor of GaI in the progression, but it pins a later layer.

A system is GaI only if the definition of correctness is formalized, the residue is sovereign, and execution gates on human-acknowledged residue, before any artifact exists. The CAL pipeline qualifies. A compliance dashboard does not.

### 5.2 Governance as the Most Upstream Layer

GaI's claim that governance is the *most upstream* layer of infrastructure is not a fashionable repositioning of a trending word. In the present author's work, governance has been a primitive since the first Semantic Intent pattern — Semantic Intent as Single Source of Truth, with immutability governance [4] — established before "AI governance" became a common term. GaI is the continuation of that through-line: the same primitive, now claimed as runtime infrastructure rather than as a source-of-truth discipline. The provenance matters because the most common objection to a governance framing is that governance is merely the current preoccupation of the field. The reply is that the primitive predates the preoccupation.

The deeper reason governance is upstream is structural. Every other layer — provisioning, policy, methodology, intent — presupposes a definition of what correctness means. When a machine executes inferred intent before any human review, no check downstream of that definition is early enough to catch a wrong assumption. The layer that defines correctness before anything is built is, necessarily, the first layer. GaI names it.

### 5.3 Limits

GaI does not claim that governance can be fully automated; the opposite is its central commitment. The most valuable output of the cycle is precisely the residue that a machine cannot resolve. GaI does not claim to prevent all error — a human can acknowledge a residue and still decide wrongly; the claim is narrower and stronger: that the decision is surfaced, owned, and made before execution, rather than discovered after. And GaI does not claim novelty of the governance impulse — it claims a specific architectural form for it: pre-execution, formalized, sovereign, gating. The contribution is the form and its qualifying test, not the impulse.

---

## 6. Conclusion

For decades, governance has been something added to a system after the system produced something to govern. Governance-as-Infrastructure inverts that posture. In AI-first delivery, where the gap between designed and in-production collapses toward zero, governance is the most upstream layer of infrastructure there is: the runtime that decides whether an artifact should exist at all, before it does, with the human reserved at the one moment a machine cannot stand in for — deciding what correct means.

The progression is complete on both axes. Methodology became a runtime. Intent became a runtime. And governance — the discipline named by Governance-Driven Design, the artifact named the Governed Constraint Set — is the runtime that comes first. The gate is not beside the pipeline. The gate is the pipeline's first instruction.

---

## References

[1] Shatny, M. (2026). *Governance-Driven Design (GDD): Formalizing Intent Before the Machine Runs.* Zenodo. Concept DOI: 10.5281/zenodo.20938777

[2] Shatny, M. (2026). *Methodology-as-Infrastructure: From Framework to Runtime.* Zenodo. DOI: 10.5281/zenodo.18946630

[3] Shatny, M. (2026). *Intent-as-Infrastructure: When the Compiler Is Claude.* Zenodo. DOI: 10.5281/zenodo.20681523

[4] Shatny, M. (2025). *Semantic Intent as Single Source of Truth.* Zenodo. DOI: 10.5281/zenodo.17114971

[5] Shatny, M. (2026). *The Synthesis Gate: What Makes a Workflow Agentic.* Zenodo. DOI: 10.5281/zenodo.20684283

[6] Shatny, M. (2026). *CAL — Cascade Analysis Language.* Zenodo. DOI: 10.5281/zenodo.18905193

---

## Appendix A: The Two Lineages

GaI sits at the convergence of two progressions the author has been building in parallel — one a lineage of *disciplines* (how a practitioner works), the other a lineage of *infrastructure paradigms* (what the discipline becomes when executable).

```
Discipline axis:       TDD  →  DDD  →  BDD  →  GDD
                       (implementation → domain → behaviour → governance)

Infrastructure axis:   IaC  →  PaC  →  MaI  →  IaI  →  GaI
                       (provisioning → policy → methodology → intent → governance)
```

Both terminate, upstream, at governance. The discipline axis ends at GDD; the infrastructure axis ends at GaI. They are the same terminus viewed from two angles — the verb and the noun of a single primitive. Governance-Driven Design is how it is practiced; Governance-as-Infrastructure is what it is once it runs. The convergence is not a coincidence of naming. It is the structural fact that, in AI-first delivery, the definition of correctness is both the last discipline to be adopted and the first layer to execute.
