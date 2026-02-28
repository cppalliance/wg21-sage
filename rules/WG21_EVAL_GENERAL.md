# WG21 General Evaluation Model

This model evaluates C++ standardization proposals against principles of proven practice, political viability, design coherence, implementation validation, complexity control, institutional knowledge, and ecosystem fit derived from experienced WG21 practitioners.

**Source**: `knowledge/merged.know.md`
**Principles**: 11 scoring criteria
**Scope**: both
**Generated**: 2026-02-27

---

## Gate

Before evaluation, verify the paper falls within this model's scope.

Read the paper's title, abstract, and target audience. If the paper's subject matter overlaps with fewer than half the scoring criteria below, decline evaluation and produce the Gate: Scope Mismatch output instead.

### Gate Failure Output

```markdown
## Gate: Scope Mismatch

**Result:** DECLINED — This paper falls outside the model's evaluation scope.

**Paper scope:** [one sentence describing what the paper addresses]

**Model scope:** This model evaluates C++ standardization proposals against principles of proven practice, political viability, design coherence, implementation validation, complexity control, institutional knowledge, and ecosystem fit derived from experienced WG21 practitioners.

**Overlap:** [N] of 11 principles apply to this paper's subject matter.

**Recommendation:** [Suggest which kind of evaluation model would be appropriate, or suggest the user generate one from a knowledge file covering the paper's domain.]
```

---

## Scoring

For each criterion, assign a score of 0, 1, or 2.

| #  | Criterion                                        | Score | |
|----|--------------------------------------------------|-------|----|
| 1  | Political Fragility Kills Proposals              | 0-2   | |
| 2  | Standardize Proven Practice                      | 0-2   | |
| 3  | Complexity Threatens C++                         | 0-2   | |
| 4  | Consensus Collaboration Produces Great Things    | 0-2   | |
| 5  | Implementation Validates Design                  | 0-2   | |
| 6  | Innovation Requires External Incubation          | 0-2   | |
| 7  | Institutional Knowledge Degrades Without Capture | 0-2   | |
| 8  | Library Complexity Belongs in the Language        | 0-2   | |
| 9  | Permissive Licensing Maximizes Adoption           | 0-2   | |
| 10 | Standardize What Was Previously Impossible       | 0-2   | |
| 11 | Without Agreed Principles, Decisions Drift       | 0-2   | |
|    | **TOTAL**                                        | **X/22** | |

Scoring: ✅ = 2 (compliant), ⚠️ = 1 (partial), ❌ = 0 (non-compliant)

**Passing threshold**: 14 / 22

---

## Executive Summary

[2-3 paragraphs: key strengths, critical gaps, overall recommendation. Written after completing all per-criterion analysis.]

---

## Criterion-by-Criterion Analysis

### 1. Political Fragility Kills Proposals — [emoji]

**Score: X/2**

> Consensus without a tiebreaker is structurally fragile. Competing proposals fracture politically. One defection after approval kills years of work. No one can compel resolution; champions simply tire and leave.

**Compliant (2):** The proposal has converged on a single design vision without competing alternatives. The champion has built broad consensus across stakeholders. There is no unresolved political fracture that a single defection could exploit to kill the proposal.

**Partial (1):** The proposal acknowledges competing approaches and argues for one, but rival proposals or unreconciled design camps still exist. Political risk is recognized but not fully mitigated.

**Non-compliant (0):** Multiple competing proposals target the same problem space with no convergence. The proposal was approved by a narrow margin with vocal opposition. A single defection or withdrawal of support could derail the effort.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 2. Standardize Proven Practice — [emoji]

**Score: X/2**

> Standardize proven practice. Require field experience from independent users outside the proposer's organization. A last-minute implementation is not field experience. A library nobody uses has no value.

**Compliant (2):** The proposal documents years of field use by independent users. Multiple implementations exist with positive feedback from outside the proposer's organization, comparable to how `std::shared_ptr` and `std::chrono` were standardized after extensive Boost deployment.

**Partial (1):** An implementation exists and has some users, but feedback is limited to the proposer's organization or team. Field experience is recent rather than sustained over years.

**Non-compliant (0):** No implementation predates the proposal, or the implementation was created shortly before submission. No independent field experience is documented. The proposal resembles `std::regex` — standardized without competitive implementation experience.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 3. Complexity Threatens C++ — [emoji]

**Score: X/2**

> Complexity that only grows kills a language. C++ requires expertise merely to use it. Features accumulate; nothing is removed. The trajectory ends at COBOL.

**Compliant (2):** The proposal reduces net complexity or replaces existing complex patterns with simpler alternatives. It demonstrates that the feature does not impose new expertise requirements on users who do not use it. Complexity is bounded and justified by the capability enabled.

**Partial (1):** The proposal adds complexity but acknowledges the cost and argues the benefit outweighs it. The complexity impact is localized rather than pervasive.

**Non-compliant (0):** The proposal adds significant complexity without addressing the cumulative cost. It introduces new expertise requirements for broad categories of users. The feature interacts with existing features in ways that multiply complexity, as `std::pair` requiring ~2000 lines exemplifies.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 4. Consensus Collaboration Produces Great Things — [emoji]

**Score: X/2**

> Experts collaborating without ego exceed individual capability. Arguments serve understanding, not dominance. This requires leadership that moderates rather than advocates.

**Compliant (2):** The proposal demonstrates collaborative development across organizations and individuals. Design decisions reflect synthesis of multiple perspectives. The champion has moderated competing inputs rather than advocating a predetermined outcome, similar to Boost's golden-age peer review culture.

**Partial (1):** The proposal shows some collaborative input but is primarily the product of a single author or organization. Feedback from others is acknowledged but has not visibly shaped the design.

**Non-compliant (0):** The proposal appears driven by a single organization's agenda. Design decisions reflect advocacy rather than consensus discovery. Dissenting perspectives are dismissed rather than incorporated.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 5. Implementation Validates Design — [emoji]

**Score: X/2**

> Implementation is the minimum credible evidence. A live demo outperforms any paper. Feedback from compiler and library maintainers outweighs committee speculation.

**Compliant (2):** The proposal includes implementation experience from at least one major compiler or library vendor. Design decisions are informed by implementation feedback. The implementation has been tested against real-world code, as when Clang compiled Boost in 18 months to prove soundness.

**Partial (1):** A prototype implementation exists but has not been tested by compiler or library maintainers. Implementation feedback is limited to the proposer's own experience.

**Non-compliant (0):** No implementation exists, or the implementation was created solely to satisfy a committee requirement without genuine validation. The proposal advances through committee without implementation feedback from any major vendor, as with Bjarne's original Concepts proposal.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 6. Innovation Requires External Incubation — [emoji]

**Score: X/2**

> Innovation needs a sandbox outside the standard. Designs must iterate through real use before stabilization. Premature standardization locks in mistakes. Boost proved this for C++11; Swift proved it again.

**Compliant (2):** The proposed feature or library has been incubated outside the standard, iterating through real use and design revisions before being brought to committee. The incubation period allowed mistakes to be found and corrected, as Boost incubated `shared_ptr`, `function`, and `chrono` for years.

**Partial (1):** Some external incubation occurred, but the design has changed substantially since entering the committee process. The incubation period was brief relative to the feature's complexity.

**Non-compliant (0):** The design was created within the committee process without prior external incubation. The proposal went from committee approval to draft standard without extended real-world shakeout, as with C++0x Concepts.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 7. Institutional Knowledge Degrades Without Capture — [emoji]

**Score: X/2**

> Rationale not written down is rationale lost. Knowledge degrades at every process transition. The committee has no retrospectives, no formal onboarding, no written institutional memory.

**Compliant (2):** The proposal documents its rationale, records alternatives considered, and captures the reasoning behind design decisions. Future readers can understand why choices were made without consulting the authors, as Dave Abrahams' exception safety guarantees became a permanent reference.

**Partial (1):** Some rationale is documented, but key design decisions lack recorded reasoning. An alternatives section exists but is incomplete.

**Non-compliant (0):** The proposal contains no rationale for its design choices. Years of deliberation in subgroups are invisible to downstream reviewers. Critical reasoning exists only in the heads of participants, as with linear algebra rationale that arrived at EWG invisible to reviewers.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 8. Library Complexity Belongs in the Language — [emoji]

**Score: X/2**

> When a simple concept requires a complex implementation, the language is missing a feature. `std::pair` at 2000 lines is a language deficiency. `std::move` as a template instantiated everywhere is a tax on every translation unit.

**Compliant (2):** The proposal recognizes the boundary between language and library. If it is a library proposal, it does not work around a language deficiency that should be fixed first. If it is a language proposal, it absorbs complexity that currently burdens library implementers, as variadic templates absorbed Boost.Preprocessor hacks.

**Partial (1):** The proposal acknowledges a language-library boundary tension but does not fully resolve it. A library workaround is proposed with a note that a future language feature would be preferable.

**Non-compliant (0):** The proposal introduces or perpetuates library-level complexity that masks a missing language feature. The implementation requires disproportionate template machinery for a conceptually simple operation, as `std::pair` and `std::move` exemplify.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 9. Permissive Licensing Maximizes Adoption — [emoji]

**Score: X/2**

> One license. Maximally permissive. No copyleft, no credit requirements, no strings. Legal departments default to "no"; every friction point is an adoption that never happens.

**Compliant (2):** Any reference implementation or associated library uses a single, maximally permissive license (BSL, MIT, BSD, or equivalent). Corporate legal departments can approve adoption without negotiation, as the Boost Software License enabled Boost to appear in startup screens worldwide.

**Partial (1):** The licensing is mostly permissive but has minor friction points — multiple licenses, attribution requirements, or ambiguities that require legal review.

**Non-compliant (0):** The reference implementation uses copyleft or restrictive licensing. Licensing terms are ambiguous or require per-organization legal review. Corporate adoption is impeded by licensing friction regardless of technical merit.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 10. Standardize What Was Previously Impossible — [emoji]

**Score: X/2**

> Standardize what was impossible. Make the difficult easy. Do not standardize the already-easy. A library's value is enabling domain experts to stay in their domain.

**Compliant (2):** The proposal enables something that was previously impossible or prohibitively difficult in portable C++. It makes domain experts more effective by providing capabilities they cannot reasonably write themselves, as the STL eliminated repeated binary-search errors and `std::chrono` replaced platform-specific time manipulation.

**Partial (1):** The proposal simplifies something that is currently possible but difficult. The improvement is meaningful but does not cross the threshold from impossible to possible.

**Non-compliant (0):** The proposal standardizes something already easy to accomplish in a few lines of user code. Its motivation describes syntactic sugar rather than enabling new capabilities, as with `std::exchange`.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

### 11. Without Agreed Principles, Decisions Drift — [emoji]

**Score: X/2**

> Without documented design principles, every decision is ad hoc. Similar questions receive different answers. The language becomes the sum of political victories, not a coherent design.

**Compliant (2):** The proposal is grounded in documented design principles. It references established guidelines or precedent and demonstrates consistency with prior committee decisions on similar questions, as Swift Evolution proposals include goals and rationale for every accepted change.

**Partial (1):** The proposal implicitly follows design principles but does not explicitly state them or reference precedent. Consistency with prior decisions is present but not demonstrated.

**Non-compliant (0):** The proposal makes design choices without reference to any principles or precedent. Similar questions in the proposal receive different treatment without justification. The design reflects ad hoc decisions rather than coherent reasoning.

**Evidence from paper:** [evaluator fills in]

**Notes:** [evaluator fills in]

---

## Source Traceability

| #  | Criterion                                        | Source Principle |
|----|--------------------------------------------------|-----------------|
| 1  | Political Fragility Kills Proposals              | M1              |
| 2  | Standardize Proven Practice                      | M2              |
| 3  | Complexity Threatens C++                         | M3              |
| 4  | Consensus Collaboration Produces Great Things    | M4              |
| 5  | Implementation Validates Design                  | M5              |
| 6  | Innovation Requires External Incubation          | M6              |
| 7  | Institutional Knowledge Degrades Without Capture | M7              |
| 8  | Library Complexity Belongs in the Language        | M8              |
| 9  | Permissive Licensing Maximizes Adoption           | M9              |
| 10 | Standardize What Was Previously Impossible       | M10             |
| 11 | Without Agreed Principles, Decisions Drift       | M11             |
