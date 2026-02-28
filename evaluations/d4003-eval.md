# Evaluation: P4003R0 "Coroutines for I/O"

**Model**: `rules/WG21_EVAL_GENERAL.md`
**Paper**: P4003R0 (D4003, 2026-02-22)
**Authors**: Vinnie Falco, Steve Gerbino, Mungo Gill
**Target audience**: LEWG
**Evaluated**: 2026-02-27

---

## Gate

**Paper scope:** A coroutine-native I/O execution model using C++20 language features, proposing the IoAwaitable protocol with two concepts, a type-erased executor, frame allocator propagation, and launch functions for asynchronous byte-oriented I/O.

**Model scope:** This model evaluates C++ standardization proposals against principles of proven practice, political viability, design coherence, implementation validation, complexity control, institutional knowledge, and ecosystem fit derived from experienced WG21 practitioners.

**Overlap:** 11 of 11 principles apply to this paper's subject matter.

**Result:** PASS - proceed to evaluation.

---

## Scoring

| #  | Criterion                                        | Score    |        |
|----|--------------------------------------------------|----------|--------|
| 1  | Political Fragility Kills Proposals              | 1        | ⚠️     |
| 2  | Standardize Proven Practice                      | 1        | ⚠️     |
| 3  | Complexity Threatens C++                         | 2        | ✅     |
| 4  | Consensus Collaboration Produces Great Things    | 1        | ⚠️     |
| 5  | Implementation Validates Design                  | 2        | ✅     |
| 6  | Innovation Requires External Incubation          | 2        | ✅     |
| 7  | Institutional Knowledge Degrades Without Capture | 2        | ✅     |
| 8  | Library Complexity Belongs in the Language        | 1        | ⚠️     |
| 9  | Permissive Licensing Maximizes Adoption           | 1        | ⚠️     |
| 10 | Standardize What Was Previously Impossible       | 2        | ✅     |
| 11 | Without Agreed Principles, Decisions Drift       | 2        | ✅     |
|    | **TOTAL**                                        | **17/22** |        |

Scoring: ✅ = 2 (compliant), ⚠️ = 1 (partial), ❌ = 0 (non-compliant)

**Passing threshold**: 14 / 22

**Result: PASS** (17/22)

---

## Executive Summary

P4003R0 is one of the strongest R0 papers this model has seen on implementation-first design. The paper is explicitly a "research report drawn from working code" - a complete coroutine-only networking library spanning sockets, timers, TLS, DNS, and HTTP across three platforms (Windows, Linux, macOS). The IoAwaitable protocol it describes is minimal: two concepts, one struct, one type-erased executor. The paper documents rationale exhaustively, including alternatives considered and rejected (allocator_arg_t, promise-template await_suspend). Every design decision traces to implementation experience. The paper scores full marks on implementation validation, external incubation, knowledge capture, complexity awareness, enabling previously-impossible capabilities, and principled design.

The paper's vulnerabilities are political and social. It enters a space where SG4 has already reached consensus that networking should use sender/receiver, and asks the committee to reconsider. All implementations (Capy, Corosio, Boost.Http) originate from a single organization (C++ Alliance). While respected WG21 contributors (Peter Dimov, Mateusz Pusz) provided feedback, the core design was not shaped by cross-organizational collaboration. Independent adoption outside the proposer's organization is not documented. These factors create political fragility - the paper asks a committee that has already committed to one direction to evaluate a fundamentally different approach, without demonstrating that the broader community has converged on its design.

The recommendation is positive with caveats. The paper's technical merits are substantial, but its path through the committee depends on political dynamics that no amount of implementation quality can fully resolve. The paper would benefit from documented independent adoption, cross-organizational co-authorship, and explicit engagement with the sender/receiver community to reduce political risk.

---

## Criterion-by-Criterion Analysis

### 1. Political Fragility Kills Proposals — ⚠️

**Score: 1/2**

> Consensus without a tiebreaker is structurally fragile. Competing proposals fracture politically. One defection after approval kills years of work. No one can compel resolution; champions simply tire and leave.

**Evidence from paper:** The paper enters a politically charged arena. SG4 polled at Kona (November 2023) on P2762R2 with consensus that "Networking should support only a sender/receiver model" (SF:5, F:5, N:1, A:0, SA:1). The paper acknowledges this directly and asks for straw polls that the coroutine-native approach is "distinct" and "warrants consideration" despite the Kona poll. The paper is positioned as a third option alongside the Networking TS executor model and sender/receiver.

Within its own camp, the proposal has converged on a single design vision. The three co-authors present a unified IoAwaitable protocol without internal competing alternatives. Companion papers P4007R0 and P4014R0 address the sender/receiver relationship.

**Notes:** The proposal itself is politically unified, but it asks the committee to reopen a decided question. The existing consensus for sender/receiver means a single defection from the paper's supporters - or simply continued commitment to the existing direction - could prevent the approach from being considered. The straw polls are carefully worded to avoid direct confrontation, but the structural political risk is real.

---

### 2. Standardize Proven Practice — ⚠️

**Score: 1/2**

> Standardize proven practice. Require field experience from independent users outside the proposer's organization. A last-minute implementation is not field experience. A library nobody uses has no value.

**Evidence from paper:** The paper is built on working code:

- **Capy** (github.com/cppalliance/capy): implements the IoAwaitable protocol
- **Corosio** (github.com/cppalliance/corosio): sockets, timers, TLS, DNS on multiple platforms
- **Boost.Http** (github.com/cppalliance/http): HTTP library built on Capy with type-erased streams
- Performance benchmarks: recycling frame allocator 3.1x faster than std::allocator (MSVC), 1.55x (Apple Clang)
- Self-contained Compiler Explorer demonstration
- The paper states "Both libraries are in active use"

All three implementations originate from C++ Alliance. The paper does not document independent users outside the proposer's organization. "In active use" is stated without specifics on adoption breadth. Mohammad Nejati, Michael Vandeberg, and Klemens Morgenstern assisted with implementation (per Acknowledgements), but they appear to be collaborators rather than independent adopters.

**Notes:** The implementation is genuine and predates the proposal. The paper is not a "last-minute implementation" - it describes a complete networking stack tested across platforms. But the field experience requirement calls for independent users outside the proposer's organization, and the paper does not demonstrate this. The score would rise to 2 with documented independent adoption.

---

### 3. Complexity Threatens C++ — ✅

**Score: 2/2**

> Complexity that only grows kills a language. C++ requires expertise merely to use it. Features accumulate; nothing is removed. The trajectory ends at COBOL.

**Evidence from paper:** The paper demonstrates strong complexity awareness throughout:

- The IoAwaitable protocol is described as minimal: "two concepts, a type-erased executor, and a thread-local write-through cache"
- "We could not find anything to remove from it without losing function"
- `task<T>` has one template parameter, enabling separate compilation and ABI stability
- Section 5.2 provides a direct comparison showing how allocator_arg_t infects every coroutine signature while IoAwaitable keeps route handlers clean
- Section 6.4 shows application developers write pure business logic without infrastructure noise
- The executor_ref is just two pointers
- The paper explicitly compares narrow C++ abstractions (iterators, allocators, RAII) with the IoAwaitable approach

The paper replaces complex existing patterns (callback hell, viral allocator parameters) with simpler alternatives. The complexity cost of the protocol itself is bounded and justified by the capability enabled.

**Notes:** The paper is among the strongest R0 papers on complexity justification. Every added mechanism (TLS propagation, two-call syntax, executor_ref) is explained as the minimal mechanism that works, with rejected alternatives shown to impose higher complexity.

---

### 4. Consensus Collaboration Produces Great Things — ⚠️

**Score: 1/2**

> Experts collaborating without ego exceed individual capability. Arguments serve understanding, not dominance. This requires leadership that moderates rather than advocates.

**Evidence from paper:** The paper has three co-authors (Falco, Gerbino, Gill), all from C++ Alliance. The Acknowledgements thank:

- Chris Kohlhoff (Boost.Asio - foundational prior art)
- Lewis Baker (foundational coroutine work)
- Peter Dimov and Mateusz Pusz (valuable feedback)
- Mohammad Nejati, Michael Vandeberg, Klemens Morgenstern (implementation assistance)

The design explicitly builds on Kohlhoff's executor model and credits it throughout. Companion papers (P4007, P4014) suggest broader ecosystem engagement. The paper positions itself constructively relative to sender/receiver rather than adversarially.

**Notes:** The feedback from Dimov and Pusz (both respected WG21 contributors from outside C++ Alliance) suggests some cross-organizational input. However, the core IoAwaitable protocol appears to be designed by the C++ Alliance team, with external contributors providing feedback rather than co-designing. Being R0, the paper has not yet been through committee review. The score could rise with evidence that committee feedback shaped subsequent revisions.

---

### 5. Implementation Validates Design — ✅

**Score: 2/2**

> Implementation is the minimum credible evidence. A live demo outperforms any paper. Feedback from compiler and library maintainers outweighs committee speculation.

**Evidence from paper:** The paper is explicitly structured as a research report from implementation:

- Three implementations: Capy (protocol), Corosio (networking), Boost.Http (application layer)
- Cross-platform: Windows (IOCP), Linux (epoll/io_uring), macOS (kqueue)
- Benchmarks: recycling frame allocator vs. mimalloc vs. std::allocator, with quantified results
- Self-contained Compiler Explorer demonstration
- Complete code examples drawn from working implementations
- Section 7 provides a non-normative reference implementation of the promise mixin
- Section 10 provides draft wording derived from implementation experience
- Appendix B provides a complete listing of `any_read_stream`

The paper's methodology is "use C++20 coroutines directly for I/O and observe what the language provides" - every design decision emerged from building the solution.

**Notes:** This is the paper's greatest strength. The implementation is not a proof-of-concept but a complete networking stack. The paper structure itself - reporting what was observed rather than speculating about what might work - is the gold standard for implementation-validated design.

---

### 6. Innovation Requires External Incubation — ✅

**Score: 2/2**

> Innovation needs a sandbox outside the standard. Designs must iterate through real use before stabilization. Premature standardization locks in mistakes. Boost proved this for C++11; Swift proved it again.

**Evidence from paper:** The IoAwaitable protocol was developed entirely outside the standard:

- Capy and Corosio libraries were built and used before this paper was written
- Boost.Http demonstrates that higher-level libraries can be built on the protocol
- The design iterated through real networking use cases (HTTP servers, TLS connections, DNS resolution)
- The incubation produced concrete lessons: TLS for frame allocators was chosen over allocator_arg_t after experiencing the ergonomic cost; the two-argument await_suspend was chosen after identifying the silent-mismatch problem with promise-template approaches
- The paper explicitly states: "Standards should follow implementations, not the reverse"

**Notes:** The paper embodies the incubation principle. Design decisions that might seem arbitrary in a committee paper (e.g., thread-local propagation vs. allocator_arg_t) are explained as the result of trying alternatives and observing which worked in practice.

---

### 7. Institutional Knowledge Degrades Without Capture — ✅

**Score: 2/2**

> Rationale not written down is rationale lost. Knowledge degrades at every process transition. The committee has no retrospectives, no formal onboarding, no written institutional memory.

**Evidence from paper:** The paper is exceptional on rationale documentation:

- Section 5.2: detailed comparison of allocator_arg_t approach vs. TLS, with side-by-side code examples showing ergonomic cost
- Section 5.5: direct responses to three anticipated TLS objections (hidden behavior, thread migration, implicit propagation/lifetime)
- Section 3.1: explains why the two-argument await_suspend was chosen over the promise-template alternative, with the specific failure mode (silent runtime errors)
- Section 4: explains why the term "executor" is used intentionally, honoring Kohlhoff's model
- Section 6: documents the type erasure benefit of coroutine frames, explaining why `task<T>` needs only one template parameter
- Appendix A: provides complete background for non-networking specialists
- Draft wording (Section 10) captures precise semantics
- Mermaid diagrams visualize data flow and protocol interactions

**Notes:** Future readers can reconstruct every design decision from the paper alone, without consulting the authors. This is the standard every WG21 paper should meet but few do.

---

### 8. Library Complexity Belongs in the Language — ⚠️

**Score: 1/2**

> When a simple concept requires a complex implementation, the language is missing a feature. `std::pair` at 2000 lines is a language deficiency. `std::move` as a template instantiated everywhere is a tax on every translation unit.

**Evidence from paper:** The paper builds entirely on existing C++20 language features (coroutines) without proposing new ones. It identifies that "for I/O, the basis is already in the language" and leverages coroutine_handle<> type erasure, promise_type, await_suspend, and compiler-managed state.

However, the paper explicitly acknowledges language-library boundary tensions:

- The thread-local frame allocator is necessary because `operator new` has a fixed signature - the allocator cannot arrive as a parameter without polluting every coroutine signature (Section 5.1-5.3)
- The two-call syntax `run_async(ex)(my_task())` is described as "unfortunate" - a consequence of C++17 evaluation order being the only mechanism that works
- The paper states these are pragmatic workarounds, not ideal solutions

**Notes:** The paper is transparent about where the language falls short. The TLS mechanism works but is a library-level workaround for a language timing constraint. The two-call syntax is acknowledged as an ergonomic compromise. These are real boundary tensions - the paper handles them pragmatically but does not fully resolve them.

---

### 9. Permissive Licensing Maximizes Adoption — ⚠️

**Score: 1/2**

> One license. Maximally permissive. No copyleft, no credit requirements, no strings. Legal departments default to "no"; every friction point is an adoption that never happens.

**Evidence from paper:** The reference implementations are publicly available on GitHub under the C++ Alliance organization:

- github.com/cppalliance/capy
- github.com/cppalliance/corosio
- github.com/cppalliance/http

C++ Alliance projects are known to use the Boost Software License. However, the paper itself does not explicitly state the license for any of these implementations.

**Notes:** The licensing is almost certainly BSL (the C++ Alliance's standard practice), which is the paradigmatic maximally-permissive license. The score is partial solely because the paper does not document the license explicitly. This is an easy fix in a future revision.

---

### 10. Standardize What Was Previously Impossible — ✅

**Score: 2/2**

> Standardize what was impossible. Make the difficult easy. Do not standardize the already-easy. A library's value is enabling domain experts to stay in their domain.

**Evidence from paper:** Standard C++ has no async I/O. The Networking TS was never adopted. The sender/receiver model (P2300) remains in progress. The paper enables something that is currently impossible in the standard:

- Coroutine-native async I/O with type-erased streams, separate compilation, and ABI stability
- A complete execution model for byte-oriented I/O (sockets, TLS, DNS, HTTP)
- Frame allocator customization without signature pollution
- Cooperative cancellation via std::stop_token propagated through coroutine chains

The paper argues this is a distinct approach from both the Networking TS and sender/receiver, providing capabilities neither offers in exactly this form. Application developers currently cannot write portable async I/O in standard C++.

**Notes:** This is not syntactic sugar. The paper enables domain experts (networking application developers) to write async I/O in standard C++, which they currently cannot do. The comparison to STL eliminating hand-written binary search is apt - networking is a domain where experts repeatedly get the concurrency, lifetime, and resource management wrong without library support.

---

### 11. Without Agreed Principles, Decisions Drift — ✅

**Score: 2/2**

> Without documented design principles, every decision is ad hoc. Similar questions receive different answers. The language becomes the sum of political victories, not a coherent design.

**Evidence from paper:** The paper explicitly states design principles and follows them consistently:

- Three priorities documented (Section 1): correctness first, ergonomics second, performance third
- The paper argues from the C++ principle that "the abstractions that succeed in C++ are narrow" - iterators for traversal, RAII for resource lifetime, allocators for memory strategy
- The design references Kohlhoff's executor model as established precedent
- Every design choice (two-argument await_suspend, TLS for frame allocators, type-erased executor_ref) is traced to stated principles
- The paper demonstrates consistency: similar questions (how to propagate executor? stop token? frame allocator?) receive the same answer (environment pointer via await_suspend for the first two; TLS for the third, with documented justification for why)

**Notes:** The paper is grounded in documented principles and applies them consistently. It also implicitly argues that the committee needs agreed-upon principles for async I/O - the Kona poll chose sender/receiver without considering the coroutine-native approach because no such principles constrained the decision space.

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
