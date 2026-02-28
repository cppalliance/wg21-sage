# WG21 Merged Knowledge

**Source Files**: `knowledge/abrahams-gregor.know.md`, `knowledge/dave-abrahams.know.md`, `knowledge/howard-hinnant.know.md`, `knowledge/matheus-izvekov.know.md`, `knowledge/sean-parent.know.md`
**Source Count**: 5
**Merge Date**: 2026-02-27
**Threshold**: Principles appearing in 2+ sources

---

## Merged Principles

### M1: Political Fragility Kills Proposals

Consensus without a tiebreaker is structurally fragile. Competing proposals fracture politically. One defection after approval kills years of work. No one can compel resolution; champions simply tire and leave.

**Sources**: Abrahams-Gregor, Hinnant, Parent

**Examples of**:
- Boost required library proposals to converge on a single vision before review, preventing political fracture
- Move semantics survived a decade because Howard Hinnant maintained sole championing without competing proposals
- `std::jthread` added cooperative cancellation cleanly once the C++11-era competing-camps problem was gone

**Counterexamples**:
- Concepts killed in 2009 when Bjarne withdrew support after the design was voted into the draft standard
- Hash proposals abandoned when Howard and Google reached an impasse that no one could break
- Thread cancellation dropped from C++11 because competing camps (immediate vs. cooperative) could not reach consensus

<!-- METADATA
kind: merged-principle
id: M1
source-count: 3
sources: [Abrahams-Gregor:P6, Abrahams-Gregor:P10, Hinnant:P10, Parent:P10]
category: process/politics
applies-to: both
confidence: high
-->

---

### M2: Standardize Proven Practice

Standardize proven practice. Require field experience from independent users outside the proposer's organization. A last-minute implementation is not field experience. A library nobody uses has no value.

**Sources**: Abrahams-Gregor, Abrahams, Hinnant

**Examples of**:
- `std::shared_ptr` standardized after years of Boost field testing by thousands of independent users
- `std::chrono` derived from Boost.DateTime with years of real-world deployment before C++11
- Move semantics iterated for a decade with real implementation experience before standardization

**Counterexamples**:
- A library proposal implemented hours before the committee vote, swaying the outcome
- `std::regex` standardized without competitive implementation experience
- Concepts designed in committee without independent user validation prior to the C++0x vote

<!-- METADATA
kind: merged-principle
id: M2
source-count: 3
sources: [Abrahams-Gregor:P1, Abrahams-Gregor:P3, Abrahams:P2, Hinnant:P2, Hinnant:P12, Hinnant:P15]
category: evaluation/field-experience
applies-to: both
confidence: high
-->

---

### M3: Complexity Threatens C++

Complexity that only grows kills a language. C++ requires expertise merely to use it. Features accumulate; nothing is removed. The trajectory ends at COBOL.

**Sources**: Abrahams, Parent

**Examples of**:
- Swift discarded C-style for-loops during its instability period; C++ cannot remove anything
- Rust attracts new systems programmers partly because its ownership model is simpler to learn than C++ RAII plus move semantics plus smart pointers
- `auto_ptr` took years to deprecate and remove despite universally acknowledged flaws

**Counterexamples**:
- `std::pair` requires ~2000 lines of implementation for a pair of two values
- No evolution principles constrain feature addition; both Abrahams and Google failed to establish them in WG21
- The committee rejected a strong memory safety proposal without a counter-proposal or roadmap

<!-- METADATA
kind: merged-principle
id: M3
source-count: 2
sources: [Abrahams:P15, Parent:P3]
category: philosophy/evolution
applies-to: both
confidence: high
-->

---

### M4: Consensus Collaboration Produces Great Things

Experts collaborating without ego exceed individual capability. Arguments serve understanding, not dominance. This requires leadership that moderates rather than advocates.

**Sources**: Abrahams-Gregor, Abrahams

**Examples of**:
- Boost's golden-age peer review culture produced `shared_ptr`, `function`, and `tuple` through pure consensus
- Exception safety adopted into C++98 entirely through persuasion across national bodies, without a formal vote
- Beman Dawes' inclusive LWG leadership invited contributions regardless of formal committee membership

**Counterexamples**:
- Committee decisions driven by organizational affiliation rather than argument quality
- The Concepts unification process where political tensions overrode collaborative discovery
- Review managers who advocate for outcomes rather than moderating the consensus signal

<!-- METADATA
kind: merged-principle
id: M4
source-count: 2
sources: [Abrahams-Gregor:P7, Abrahams:P3]
category: philosophy/coherence
applies-to: both
confidence: high
-->

---

### M5: Implementation Validates Design

Implementation is the minimum credible evidence. A live demo outperforms any paper. Feedback from compiler and library maintainers outweighs committee speculation.

**Sources**: Abrahams-Gregor, Izvekov

**Examples of**:
- Doug Gregor's live Concepts demo at Mont-Tremblant opened delegates' eyes to what the feature enabled
- Louis Dionne's negative implementation experience with trivial relocation in libc++ influenced committee votes
- Clang compiled Boost in 18 months, proving the compiler implementation was sound

**Counterexamples**:
- Bjarne's original Concepts proposal lacked an implementation and implied behavior no one could demonstrate
- Template template parameter matching approved without partial ordering specification, causing years of broken compilers
- Features advancing through committee without implementation feedback from any major vendor

<!-- METADATA
kind: merged-principle
id: M5
source-count: 2
sources: [Abrahams-Gregor:P4, Abrahams-Gregor:P12, Izvekov:P12]
category: evaluation/field-experience
applies-to: both
confidence: high
-->

---

### M6: Innovation Requires External Incubation

Innovation needs a sandbox outside the standard. Designs must iterate through real use before stabilization. Premature standardization locks in mistakes. Boost proved this for C++11; Swift proved it again.

**Sources**: Abrahams-Gregor, Parent

**Examples of**:
- Boost incubated `shared_ptr`, `function`, `tuple`, and `chrono` for years before C++11 standardization
- Swift's deliberate source instability allowed removing C-style for-loops and redesigning access control
- Swift and Rust adopted Boost's peer-review model directly for their own evolution processes

**Counterexamples**:
- Concepts went from committee approval to draft standard without extended real-world shakeout
- The C++ committee after Boost's decline resorts to "off the cuff design" lacking real-user validation
- Thread cancellation proposed for C++11 without any C++-specific cooperative-cancellation implementation experience

<!-- METADATA
kind: merged-principle
id: M6
source-count: 2
sources: [Abrahams-Gregor:P2, Abrahams-Gregor:P9, Parent:P6]
category: belongs/ecosystem
applies-to: both
confidence: high
-->

---

### M7: Institutional Knowledge Degrades Without Capture

Rationale not written down is rationale lost. Knowledge degrades at every process transition. The committee has no retrospectives, no formal onboarding, no written institutional memory.

**Sources**: Hinnant, Izvekov

**Examples of**:
- Boost's peer review process captured community consensus and stated reasons for each library decision
- Swift Evolution proposals include rationale sections with alternatives considered
- Exception safety guarantees documented by Dave Abrahams became a permanent reference for C++98

**Counterexamples**:
- Linear algebra rationale from years of SG6 deliberation arrived at EWG invisible to reviewers
- Template specification expertise concentrated in retired members with no written knowledge transfer
- New committee members learn process through trial and error with no structured onboarding

<!-- METADATA
kind: merged-principle
id: M7
source-count: 2
sources: [Hinnant:P14, Izvekov:P8]
category: process/actual
applies-to: both
confidence: high
-->

---

### M8: Library Complexity Belongs in the Language

When a simple concept requires a complex implementation, the language is missing a feature. `std::pair` at 2000 lines is a language deficiency. `std::move` as a template instantiated everywhere is a tax on every translation unit.

**Sources**: Izvekov, Parent

**Examples of**:
- Variadic templates absorbed Boost.Preprocessor hacks into a clean language feature
- Lambda expressions replaced `boost::bind` and `boost::lambda` with direct language support
- C++11 rvalue references replaced library-level `auto_ptr` workarounds with a proper language mechanism

**Counterexamples**:
- `std::pair` requiring ~2000 lines of template machinery for a pair of two values
- `std::move` and `std::forward` implemented as library templates despite universal use in every translation unit
- Type functions still written through template specialization syntax bearing no resemblance to value functions

<!-- METADATA
kind: merged-principle
id: M8
source-count: 2
sources: [Izvekov:P4, Izvekov:P5, Parent:P2, Parent:P5]
category: philosophy/coherence
applies-to: both
confidence: high
-->

---

### M9: Permissive Licensing Maximizes Adoption

One license. Maximally permissive. No copyleft, no credit requirements, no strings. Legal departments default to "no"; every friction point is an adoption that never happens.

**Sources**: Abrahams, Parent

**Examples of**:
- The Boost Software License enabled Boost to appear in startup screens of programs worldwide
- Sean Parent got Adobe to adopt Boost only after vetting a single commercially-friendly license with Adobe Legal
- MIT and BSD licenses enabled broad industry adoption of foundational open source infrastructure

**Counterexamples**:
- Boost's original state of 100+ individual contributor licenses required enormous legal effort at every adopter
- Viral copyleft licenses that legal departments reject regardless of technical merit
- Projects with ambiguous licensing terms that trigger corporate legal review cycles before any code ships

<!-- METADATA
kind: merged-principle
id: M9
source-count: 2
sources: [Abrahams:P10, Parent:P7]
category: process/navigation
applies-to: library
confidence: high
-->

---

### M10: Standardize What Was Previously Impossible

Standardize what was impossible. Make the difficult easy. Do not standardize the already-easy. A library's value is enabling domain experts to stay in their domain.

**Sources**: Abrahams, Hinnant

**Examples of**:
- Move semantics made safe, efficient resource transfer possible where only unsafe `auto_ptr` hacks existed
- The STL eliminated the need for domain experts to write their own binary search, which they got wrong repeatedly
- `std::chrono` provided portable time manipulation that was previously platform-specific and error-prone

**Counterexamples**:
- `std::exchange` standardized despite doing little that a few lines of user code could not accomplish
- Proposals whose motivation describes syntactic sugar rather than enabling new capabilities
- Libraries addressing problems that domain experts already solve adequately without standard support

<!-- METADATA
kind: merged-principle
id: M10
source-count: 2
sources: [Abrahams:P1, Hinnant:P1, Hinnant:P3]
category: belongs/library
applies-to: library
confidence: high
-->

---

### M11: Without Agreed Principles, Decisions Drift

Without documented design principles, every decision is ad hoc. Similar questions receive different answers. The language becomes the sum of political victories, not a coherent design.

**Sources**: Abrahams, Parent

**Examples of**:
- Swift Evolution process documents goals and rationale for every accepted proposal
- Boost's peer review process recorded consensus decisions with stated reasons for each library
- Exception safety theory provided a documented framework against which library correctness could be evaluated

**Counterexamples**:
- Dave Abrahams failed to get WG21 to agree on evolution principles; Google's identical attempt also failed
- "All new types should be regular" is not enforced because it was never established as a documented rule
- Inconsistent decisions on similar questions across different meetings because no precedent was recorded

<!-- METADATA
kind: merged-principle
id: M11
source-count: 2
sources: [Abrahams:P11, Parent:P4]
category: process/actual
applies-to: both
confidence: high
-->

---

## Source Concordance

| Merged | Title                                            | Sources                                                              |
|--------|--------------------------------------------------|----------------------------------------------------------------------|
| M1     | Political Fragility Kills Proposals              | Abrahams-Gregor:P6,P10, Hinnant:P10, Parent:P10                     |
| M2     | Standardize Proven Practice                      | Abrahams-Gregor:P1,P3, Abrahams:P2, Hinnant:P2,P12,P15             |
| M3     | Complexity Threatens C++                         | Abrahams:P15, Parent:P3                                              |
| M4     | Consensus Collaboration Produces Great Things    | Abrahams-Gregor:P7, Abrahams:P3                                     |
| M5     | Implementation Validates Design                  | Abrahams-Gregor:P4,P12, Izvekov:P12                                 |
| M6     | Innovation Requires External Incubation          | Abrahams-Gregor:P2,P9, Parent:P6                                    |
| M7     | Institutional Knowledge Degrades Without Capture | Hinnant:P14, Izvekov:P8                                             |
| M8     | Library Complexity Belongs in the Language        | Izvekov:P4,P5, Parent:P2,P5                                         |
| M9     | Permissive Licensing Maximizes Adoption           | Abrahams:P10, Parent:P7                                              |
| M10    | Standardize What Was Previously Impossible       | Abrahams:P1, Hinnant:P1,P3                                          |
| M11    | Without Agreed Principles, Decisions Drift       | Abrahams:P11, Parent:P4                                              |
