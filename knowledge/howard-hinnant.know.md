# Howard Hinnant: Captured Knowledge

**Interview Dates**: January 7, 2025 (remote huddle); October 26, 2025 (filmed, Sturbridge MA)
**Interviewers**: Vinnie Falco; Ray Nowosielski
**Duration**: ~1 hour; ~1.5 hours
**Topics Covered**: Library evaluation criteria, field experience, standardization bar, ABI stability, move semantics, Chrono, allocator proposals, hash proposals, exception safety, undefined behavior, committee process, mentorship, Boost as testing ground, Peter Dimov, Beman Dawes

## Executive Summary

Howard Hinnant is a career-spanning C++ library implementer (MetroWorks, Apple, Ripple) and former LWG chair (2005-2010). His perspective is grounded in having both implemented the standard library as a vendor and championed major proposals through WG21, most notably move semantics and unique_ptr.

Three dominant themes emerge from these interviews. First, **field experience is the single most important prerequisite for standardization**. Howard returns to this point repeatedly and with increasing force: implementation alone proves something *can* work; only independent field experience proves it *does* work. Beman Dawes created Boost specifically to solve this problem, and Howard views its role as a testing ground as still essential. Second, **standardization should target what was previously impossible or impractical**, not what is merely convenient. The standard library is large; adding something that's already easy to do without it wastes committee time and implementation resources. Third, **correctness must always outweigh performance**. Howard is deeply troubled by compilers that exploit undefined behavior to remove user code in the name of optimization, viewing this as a fundamental inversion of priorities.

Howard also provides valuable structural insight into WG21's limitations: it is a volunteer organization that lacks executive power, cannot mandate work, and has no formal mechanisms for retrospectives or institutional knowledge capture. He views these as real but not necessarily solvable problems inherent to the consensus model.

---

## Principles

Distilled, actionable knowledge that can be applied agentically.

### P1: Standardize What Was Previously Impossible or Impractical

> *"I like when I standardize, I prefer to make what was previously impossible or impractical, possible. Or if not that, to make something that is very difficult or hard to make it easy. But making the easy easier, I find very uninteresting and not worthwhile to standardize."*

**The Principle**: The most valuable standardization efforts make what was impossible or impractical become possible, or what was genuinely difficult become easy. Standardizing minor conveniences for things already easy to do is not worth the cost.

**Why It Matters**: The standard library is large and every addition carries permanent costs: committee time, vendor implementation burden, maintenance obligations, and the near-impossibility of removal. These costs are only justified when the benefit is proportionally large. Convenience wrappers around already-easy operations consume the same resources as transformative facilities.

**When to Apply**: Evaluating any library proposal for standardization. Ask: "Can programmers already do this today? If so, how difficult is it?"

**Red Flags**:
- The proposal makes something slightly more convenient that is already straightforward
- The problem can be solved with a few lines of user code
- The proposal cannot articulate what was previously impossible or impractical
- Motivation section focuses on syntactic sugar rather than enabling new capabilities

**Supporting Experiences**: E1, E7

<!-- METADATA
kind: principle
id: P1
source-type: explicit
category: belongs/library
applies-to: library
confidence: high
supported-by: [E1, E7]
related-principles: [P3, P4]
-->

---

### P2: Require Independent Field Experience Before Standardization

> *"Nothing should be standardized unless it has some positive field experience under its belt."*

> *"Standardizing a library without field experience is a huge risk. You don't know whether it's gonna work, no matter how great it's designed and the programmers think it is, when it hits the field, if nobody uses it or nobody likes it, it's not useful."*

**The Principle**: Require positive feedback from independent users outside the proposer's organization before standardizing a feature. Implementation alone is insufficient; real-world validation from unbiased users is required.

**Why It Matters**: Implementation proves something *can* work; field experience proves it *does* work in real-world conditions. The committee has repeatedly standardized features that seemed correct in theory but failed in practice. Beman Dawes created Boost specifically to solve this problem, and it was a major reason C++11 succeeded.

**When to Apply**: Evaluating any library proposal, especially those introducing new types or abstractions. Also applies when modifying existing designs significantly during standardization, which resets field experience to zero.

**Red Flags**:
- Implementation completed shortly before the vote
- All positive feedback comes from the proposer's company
- "Field experience" limited to the proposer's immediate team
- No evidence of use outside the original development context
- Significant design changes from the field-tested version during standardization

**Supporting Experiences**: E2, E4, E5, E8

<!-- METADATA
kind: principle
id: P2
source-type: explicit
category: evaluation/field-experience
applies-to: both
confidence: high
supported-by: [E2, E4, E5, E8]
related-principles: [P1, P12]
-->

---

### P3: Every Paper Must Justify Its Existence Against the Status Quo

> *"What problem am I solving and if this paper's not accepted, how does the programmer solve this problem without this solution."*

**The Principle**: Every proposal must clearly answer two questions: What problem does this solve? And how must programmers cope today without it? If the answer to the second question is "easily," the proposal likely does not warrant standardization.

**Why It Matters**: The committee processes a large volume of papers. Without a rigorous filter on whether each proposal addresses a genuine gap, the standard accumulates features that provide marginal value while consuming permanent resources. This question also forces proposers to demonstrate understanding of the existing landscape.

**When to Apply**: First-pass evaluation of any proposal. This should be the opening question before examining design details.

**Red Flags**:
- Motivation section is vague about the actual pain point
- No comparison with existing approaches
- The "without this" answer is trivially implementable
- Proposal exists because the author wanted it, not because users need it

**Supporting Experiences**: E7

<!-- METADATA
kind: principle
id: P3
source-type: explicit
category: evaluation/motivation
applies-to: both
confidence: high
supported-by: [E7]
related-principles: [P1, P15]
-->

---

### P4: The Standard Library Must Outperform DIY

> *"If it is not as fast or faster than everybody can make it for themselves, then nobody will use the standard version. The standard version has to be better than everybody else's, otherwise nobody's gonna want to use it."*

**The Principle**: Standard library components must be at least as fast as competent hand-written alternatives. Users will abandon standard components that impose a performance penalty.

**Why It Matters**: This was the direct motivation for move semantics. Vector was the most fundamental data structure, but if the standard version was slower than what individual programmers could build, the entire premise of the standard library was undermined. Performance is a hard requirement, not a nice-to-have.

**When to Apply**: Evaluating library proposals that will replace or compete with existing user-written solutions. The standard version must be competitive on performance or provide other overwhelming advantages.

**Red Flags**:
- Benchmarks showing the proposed implementation is slower than common alternatives
- Design decisions that prioritize generality over performance without clear justification
- No performance analysis against existing practice
- Assumption that "correctness" excuses poor performance

**Supporting Experiences**: E1, E5

<!-- METADATA
kind: principle
id: P4
source-type: explicit
category: philosophy/library
applies-to: library
confidence: high
supported-by: [E1, E5]
related-principles: [P1, P5]
-->

---

### P5: Correctness Over Performance

> *"Performance is the 2nd most important goal when writing code, and the most important goal is correctness. And every once in a while, we seem to reverse those two and prefer performance over correctness."*

**The Principle**: Correctness must always be prioritized above performance. When the two conflict, correctness wins. Optimizations that can make correct programs incorrect are a violation of this hierarchy.

**Why It Matters**: Howard specifically targets compiler behavior around undefined behavior, where compilers remove user-written safety checks because the standard permits treating the protected-against condition as impossible. This turns correct-in-practice code into incorrect code purely for optimization. The hierarchy of correctness > performance should never be inverted, whether in library design, language rules, or compiler behavior.

**When to Apply**: Any design decision where performance and correctness trade off against each other. Also applies when evaluating whether to introduce undefined behavior for optimization opportunities.

**Red Flags**:
- Proposals that introduce UB to enable optimizations
- Designs where the "fast path" can silently produce wrong results
- Compiler behavior that removes user-written safety checks
- Arguments that "the programmer should know better" when the language could be safer

**Supporting Experiences**: E9

<!-- METADATA
kind: principle
id: P5
source-type: explicit
category: philosophy/tradeoffs
applies-to: both
confidence: high
supported-by: [E9]
related-principles: [P4, P6]
-->

---

### P6: Offer Layered APIs: Unchecked and Checked

> *"It's often good to have like a two-layer API, a low level layer that is unchecked. And then a safer layer, checked layer built on top of that, so that the mid-level programmer knows whether he's got this adversarial input or not and can choose the appropriate layer."*

**The Principle**: When a function must handle potentially adversarial input, provide both a fast unchecked layer and a safe checked layer built on top. Let the user choose the appropriate layer based on their trust model.

**Why It Matters**: A single API that always checks wastes performance when the caller knows inputs are valid. A single API that never checks creates vulnerabilities when inputs are adversarial. The layered approach satisfies both use cases without compromise, following the C++ philosophy of not paying for what you don't use.

**When to Apply**: Designing APIs that may process either trusted or untrusted input. Particularly relevant for parsers, validators, and any interface exposed to external data.

**Red Flags**:
- API that always validates even when the caller has already validated
- API that never validates, forcing all callers to validate externally
- No consideration of the trust boundary in the design
- Wide contract only, with no escape hatch for performance-sensitive paths

**Supporting Experiences**: *(No specific historical experience cited; derived from discussion with Vinnie Falco about adversarial input patterns)*

<!-- METADATA
kind: principle
id: P6
source-type: explicit
category: philosophy/library
applies-to: library
confidence: high
supported-by: []
related-principles: [P5, P4]
-->

---

### P7: Standardization Difficulty Is a Necessary Filter

> *"There needs to be roadblocks to getting things standardized. Otherwise, garbage accumulates in the standard and the standard degrades in quality. And so the bar should be very high to get a library or a language standardized."*

**The Principle**: The difficulty of getting something into the standard is a feature, not a bug. High barriers prevent low-quality or unnecessary additions from degrading the standard over time.

**Why It Matters**: Every addition to the standard is effectively permanent. The committee is poor at removing things once standardized. A high bar for entry is the primary defense against accumulation of poorly-designed or unnecessary features. Howard's move semantics took a decade, and he views that difficulty retrospectively as justified.

**When to Apply**: When frustrated by the pace of standardization or when tempted to lower the bar to get something through. The difficulty is the mechanism that maintains quality.

**Red Flags**:
- Arguments to lower the review bar because "we need this feature now"
- Proposals rushed through to meet a shipping deadline
- Acceptance of known deficiencies with promises to fix them later
- Pressure to standardize before field experience is established

**Supporting Experiences**: E1, E3, E4, E14

<!-- METADATA
kind: principle
id: P7
source-type: explicit
category: process/actual
applies-to: both
confidence: high
supported-by: [E1, E3, E4, E14]
related-principles: [P2, P13]
-->

---

### P8: ABI Breaks Must Be Weighed, Not Vetoed

> *"I lean towards being able to break it once in a while, otherwise if you're really rigid about ABI stability, then you just paint yourself into a corner eventually where you can't improve things."*

**The Principle**: Claims of ABI breakage should not serve as automatic vetoes. The benefit of the change must be weighed quantitatively against the cost of the break. Occasional ABI breaks are necessary to avoid permanent stagnation.

**Why It Matters**: Howard observed that ABI break claims function as "a very effective veto in the committee" that shuts down conversation without quantitative analysis. Yet the most important ABI break in recent history (ref-counted to SSO strings) was enormously beneficial despite being enormously costly. The lesson is that evaluation, not avoidance, is the correct response.

**When to Apply**: Any proposal where ABI breakage is cited as a concern. Demand quantitative analysis: What is the cost of the break? What is the cost of not making the change? How does the benefit compare?

**Red Flags**:
- ABI break cited as reason to reject without cost-benefit analysis
- Never-break-ABI policy applied rigidly to all situations
- Short-term ABI convenience creating long-term design debt
- Changes deferred indefinitely because of theoretical ABI concerns

**Supporting Experiences**: E6, E10

<!-- METADATA
kind: principle
id: P8
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E6, E10]
related-principles: [P13]
-->

---

### P9: Cross-Committee Proposals Require Established Relationships

> *"I was kind of a stranger. They didn't know who I was... so that was kind of doomed to fail."*

**The Principle**: Proposals that require cooperation across committee boundaries (e.g., C and C++ committees, or different working groups) will fail without pre-existing relationships and credibility in both groups.

**Why It Matters**: Howard's smarter allocator API required changes to the C standard's malloc/free interface. Despite the technical merit, he had no relationships in the C committee and was unknown there. The proposal never gained traction. Technical merit is necessary but insufficient; the proposer must also have standing in the relevant community.

**When to Apply**: Any proposal that touches multiple committees or requires coordinated changes across working groups. Invest in relationship-building before bringing the proposal.

**Red Flags**:
- Proposer has never attended the other committee's meetings
- No co-author from the other committee
- Proposal assumes cooperation that hasn't been negotiated
- Timeline doesn't account for cross-committee coordination overhead

**Supporting Experiences**: E11

<!-- METADATA
kind: principle
id: P9
source-type: tacit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E11]
related-principles: [P10]
-->

---

### P10: The Committee Lacks Executive Power

> *"The committee's a group of volunteers and not an organization... There's no one who can say, I want you to do this, and if you don't, you're fired."*

**The Principle**: WG21 is a volunteer body with no authority to direct work, prioritize features, or compel resolution of disputes. Important work can be abandoned simply because champions lose energy.

**Why It Matters**: The hash proposal died not because it was a bad idea but because both competing camps (Howard and Google) grew tired of arguing. Nobody could mandate resolution. This structural limitation means that features requiring sustained effort against resistance are disproportionately likely to fail, regardless of their value.

**When to Apply**: When evaluating why important features are missing from the standard, or when planning proposal strategy. Champions must have sufficient personal motivation to sustain multi-year efforts against resistance.

**Red Flags**:
- Feature champion showing signs of fatigue
- Competing proposals with no process to resolve the dispute
- Important feature with no dedicated champion
- Assumption that "the committee will prioritize this" when no one can make that happen

**Supporting Experiences**: E12

<!-- METADATA
kind: principle
id: P10
source-type: explicit
category: process/actual
applies-to: both
confidence: high
supported-by: [E12]
related-principles: [P9, P14]
-->

---

### P11: Powerful Tools Are Dangerous, Not Damning

> *"Any good tool is dangerous. I'm a big fan of pocket knives and kitchen knives and all that sort of stuff, but they can really help in the kitchen or they can chop your fingers off. You just know how to use them."*

**The Principle**: Features that are dangerous when misused but powerful when used correctly are valuable and belong in C++. Danger is not a sufficient argument against a feature; the question is whether the benefit justifies the risk and whether competent programmers can use it safely.

**Why It Matters**: This directly addresses the recurring debate over features like string_view. Howard's specific guidance for string_view in constructors: consume it entirely into owned memory before returning. The tool is safe when used with knowledge; the danger lies in ignorance, not in the tool itself.

**When to Apply**: Evaluating proposals that introduce potentially dangerous features. Ask whether competent users can use them safely and whether the benefits outweigh the risks.

**Red Flags**:
- Rejection of useful features purely because misuse is possible
- Conversely: proposals that provide no guidance on safe usage
- Features that are dangerous even for expert users
- No clear mental model for correct usage

**Supporting Experiences**: E13

<!-- METADATA
kind: principle
id: P11
source-type: tacit
category: philosophy/library
applies-to: both
confidence: high
supported-by: [E13]
related-principles: [P5, P6]
-->

---

### P12: Field Experience Reveals Better Names and Designs

> *"When you first write a library, you're not always sure how well it's gonna work in real life until you start using it a lot. And so it was over the course of several years that I decided Move Pointer was a bad name."*

**The Principle**: Real-world use over time reveals naming and design problems that are invisible at proposal time. Library authors should expect to iterate on names and interfaces based on field experience.

**Why It Matters**: Howard originally named unique_ptr as "move_ptr" and only realized the name was wrong after years of use. Peter Dimov's shared_ptr went from "better than everybody else's" to "even better than that" through years of field testing in Boost. This reinforces why field experience before standardization is essential - it catches problems that design review cannot.

**When to Apply**: When a proposal's naming or interface feels slightly off but nobody can articulate why. More time in the field may be needed. Also applies when evaluating whether a proposal has had sufficient iteration.

**Red Flags**:
- Names chosen without extended use in real code
- Interface designed entirely from first principles without iteration
- Resistance to renaming despite user confusion
- Proposal at first revision with no evidence of design evolution

**Supporting Experiences**: E5, E13

<!-- METADATA
kind: principle
id: P12
source-type: tacit
category: evaluation/field-experience
applies-to: library
confidence: high
supported-by: [E5, E13]
related-principles: [P2]
-->

---

### P13: It Is Easier to Add Than to Remove

> *"It is very hard once something gets into the standard, it's fairly difficult to take it out. We have a mechanism for doing that. We do do it, but it is difficult enough that we're not very good at it."*

> *"It's much easier to add things later."*

**The Principle**: Additions to the standard are effectively permanent. It is far safer to ship a minimal feature and add to it later than to ship a complete feature and need to remove parts.

**Why It Matters**: The LWG was explicitly risk-averse during Howard's tenure as chair, directing minimal scope for features like Chrono specifically because over-reaching risked permanent regret. Auto_ptr took years to deprecate and remove despite its well-known flaws. This asymmetry between ease of addition and difficulty of removal should fundamentally shape how proposals are scoped.

**When to Apply**: Scoping any proposal. When in doubt, start smaller. When there's pressure to include "everything we might need," resist.

**Red Flags**:
- Large proposals that try to solve every conceivable use case
- Features included "just in case" without demonstrated need
- Arguments like "we might as well add it while we're at it"
- Proposals where removing any piece would improve the whole

**Supporting Experiences**: E4, E13

<!-- METADATA
kind: principle
id: P13
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E4, E13]
related-principles: [P7, P8]
-->

---

### P14: The Committee Needs Formal Retrospectives and Knowledge Capture

> *"I think there's a need for that. And to the best of my knowledge, I don't think it exists at this time. But I'd love to see stuff like that in writing."*

**The Principle**: WG21 lacks formal mechanisms for evaluating its output quality, capturing lessons learned, conducting retrospectives, and onboarding new members with institutional knowledge. This gap should be filled.

**Why It Matters**: Howard describes a committee where mentorship is informal and accidental (Beman happened to mentor him), onboarding is "learn as you go," and there is no process for evaluating whether shipped features actually serve users. The committee has no formal metrics for success beyond "did we ship on time." Without retrospectives, the same mistakes recur across standardization cycles.

**When to Apply**: When evaluating committee process improvements, or when encountering repeated failure patterns that suggest institutional rather than individual causes.

**Red Flags**:
- Same type of failure recurring across different features
- New committee members repeating mistakes that experienced members would avoid
- No post-mortem when standardized features prove problematic
- Institutional knowledge lost when experienced members retire

**Supporting Experiences**: E15

<!-- METADATA
kind: principle
id: P14
source-type: explicit
category: process/actual
applies-to: both
confidence: high
supported-by: [E15]
related-principles: [P10]
-->

---

### P15: A Library Must Be Used to Have Value

> *"A library is good if lots of people use it. If a library does an amazing thing, whatever that thing is, but nobody uses it, there's no point in that library existing."*

**The Principle**: The ultimate measure of a library's value is adoption. Technical brilliance that nobody uses is worthless for standardization purposes.

**Why It Matters**: This is the demand-side complement to the supply-side question of field experience. A library may have a perfect design and flawless implementation, but if it doesn't attract users, it doesn't belong in the standard. Howard wants to see "GitHub projects showing people using it successfully and happily" as evidence of genuine demand.

**When to Apply**: Evaluating whether a proposal meets the bar for standardization. Look for evidence of actual usage, not just theoretical appeal.

**Red Flags**:
- Implementation exists but has negligible download/usage statistics
- Library is technically impressive but addresses a niche no one is in
- Proposer cannot point to external users
- All "users" are within the proposer's organization

**Supporting Experiences**: E2, E5

<!-- METADATA
kind: principle
id: P15
source-type: explicit
category: evaluation/library
applies-to: library
confidence: high
supported-by: [E2, E5]
related-principles: [P1, P2, P3]
-->

---

## Experiences

Relatable stories that illustrate and support the principles.

### E1: Move Semantics - A Decade to Standardize

**Context**: In 2001, Howard was the standard library implementer for MetroWorks. Vector was the most fundamental container but was too slow because every reallocation required deep copies. Howard identified that unnecessary heap allocations were the bottleneck and conceived of "move semantics" to eliminate them.

**What Happened**: Howard began work on the move semantics proposal in 2001. It required changes to both the language (rvalue references) and the library (move constructors, unique_ptr, etc.). He spent the next decade attending meetings, arguing for the proposal, and refining it. The effort crossed working group boundaries - as LWG chair, he had to go to EWG to push the language changes. Specific examples showed 10x to 100x performance improvements for operations like inserting vectors into vectors.

**The Outcome**: Success. Move semantics was standardized in C++11 and fundamentally changed how C++ programs manage resources. Howard notes: "I'm glad I didn't know that going into it. If I'd known how much work it would be to standardize it, I probably never would've started the effort."

**The Lesson**: The difficulty of standardization, while grueling, serves as quality control. Not knowing the difficulty was actually an advantage - it allowed Howard to "sprint forward with it and work on it for the love of working on it." Champions of important features need sustained personal motivation that can survive a decade of resistance.

> *"I was 20 years younger than I am now when I started that project. And so I think the fact that I didn't know how hard it would be was an advantage to myself."*

**Supports Principles**: P1, P4, P7

<!-- METADATA
kind: experience
id: E1
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [move-semantics, rvalue-references, unique-ptr, vector]
supports: [P1, P4, P7]
-->

---

### E2: Boost Libraries Drive C++11 Success

**Context**: Beman Dawes created Boost around 2000 as a testing ground for C++ libraries before standardization. He foresaw that standardizing libraries without field experience was risky and that the community needed a place to validate designs through actual use.

**What Happened**: Over roughly a decade, multiple libraries were developed, reviewed, and battle-tested in Boost. By the time C++11 was being assembled, shared_ptr, threads, regex, unordered containers, type_traits, and other Boost libraries had accumulated years of field experience. The long gap between C++03 and C++11 (eight years) allowed this field experience to accumulate. Howard estimates this volume of standardization was partly because of the unusually long development period.

**The Outcome**: Success. C++11 incorporated multiple Boost libraries and "very much invigorated, reinvigorated the language as a whole." Committee meeting attendance began growing. Howard considers C++11 to be "a very big impact on the industry."

**The Lesson**: Boost's role as a testing ground was essential to C++11's success. The field experience accumulated in Boost gave the committee confidence to standardize at scale. This validates Beman's original vision and the principle that field experience before standardization is critical.

> *"I would say that Boost was a giant success for the 2011 standard."*

**Supports Principles**: P2, P15

<!-- METADATA
kind: experience
id: E2
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [shared-ptr, threads, regex, unordered-containers, type-traits, chrono]
supports: [P2, P15]
-->

---

### E3: Concepts Failed for C++11

**Context**: There was a "something of a saga" effort to standardize concepts for C++11. Two camps had fundamentally different visions for what the language feature should look like.

**What Happened**: Howard, as LWG chair, was focused on libraries and only heard "through the walls" about the concepts debate in EWG. But the outcome was clear: a "huge effort" was invested, two camps formed, and consensus could not be reached. Neither side could convince the other, and the committee could not direct resolution.

**The Outcome**: Failure for C++11. Nothing was standardized. Concepts eventually arrived much later, in C++20.

**The Lesson**: Even universally recognized important features can fail if the committee cannot form consensus. The volunteer nature of the committee means there is no arbiter to break deadlocks. Important features can be delayed by nearly a decade due to design disagreements.

> *"I simply know that they failed to reach a consensus, and the result was that nothing in that department got standardized in 2011."*

**Supports Principles**: P7, P10

<!-- METADATA
kind: experience
id: E3
source-type: explicit
category: history/failures
applies-to: language
outcome: failure
features: [concepts]
supports: [P7, P10]
-->

---

### E4: Chrono - The Bare Minimum Done Right

**Context**: C++11 needed timing services to support threading (sleeping, timed mutex waits). Jeff Garland's Boost.DateTime had extensive field experience, but the committee was risk-averse about standardizing a full date/time library. Howard and Jeff were directed to standardize only the bare minimum.

**What Happened**: The LWG gave "marching orders" to standardize only durations, time points, and a few clocks - no calendaring, no leap seconds. While working on this subset, Howard realized that duration units could be related through templates instead of inheritance (a key departure from DateTime). This was too large a change for Boost.DateTime, so it became its own library. Beman suggested putting it in a nested namespace, and "Chrono" was chosen as the name. Significantly, when they altered the Boost library's design for standardization, they acknowledged this brought field experience "down to zero, which is risky."

**The Outcome**: Success. Chrono shipped in C++11 with minimal scope and was later expanded enormously (calendars, time zones, leap seconds in C++20). The conservative initial scope proved wise.

**The Lesson**: Shipping the minimum viable feature with room to grow later is safer than over-reaching. The committee's risk aversion, while frustrating at the time, produced a better outcome. Significantly altering a field-tested design resets field experience, and the committee was right to be cautious about that.

> *"The majority of the LWG really did not want to standardize something and regret it later. It's much easier to add things later, and it's very difficult to take things out of the standard."*

**Supports Principles**: P2, P7, P13

<!-- METADATA
kind: experience
id: E4
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [chrono, datetime, threading]
supports: [P2, P7, P13]
-->

---

### E5: Peter Dimov's shared_ptr - The Gold Standard

**Context**: Before standardization, everyone was writing their own shared pointer implementations because shared ownership is a universal need in any program of significant size.

**What Happened**: Peter Dimov created a shared_ptr implementation in Boost that was "just better than everybody else's." It was harder to get wrong, could do more things, and was "just bulletproof." Over several years of field testing in Boost, Dimov made it "from better than everybody else's to even better than that." By the time C++11 standardization arrived, it was a "shoe-in." Howard believes it may have been standardized without any changes at all, besides wordsmithing. Remarkably, Dimov achieved this without ever attending a committee meeting in person.

**The Outcome**: Success. Shared_ptr is one of the most widely used standard library components and is often cited as the exemplar of the Boost-to-standard pipeline.

**The Lesson**: Superior quality combined with extensive field experience makes standardization almost inevitable. Peter Dimov is described as "the only person I can think of who has succeeded in standardizing things without ever showing up to a meeting" - testament to how overwhelming quality and field experience can overcome even the committee's strong bias toward in-person advocacy.

> *"Peter Dimov is one of the, is the only person I can think of who has succeeded in standardizing things without ever showing up to a meeting."*

**Supports Principles**: P2, P4, P12, P15

<!-- METADATA
kind: experience
id: E5
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [shared-ptr]
supports: [P2, P4, P12, P15]
-->

---

### E6: Ref-Counted to SSO String ABI Break

**Context**: GCC's std::string implementation used reference counting. The industry was moving toward Short String Optimization (SSO), which was faster for the common case. Switching required breaking ABI.

**What Happened**: The transition was a "huge ABI break" that "hit GCC the hardest." It took GCC "years and years to transition its users from one design to the other." The cost was "very, very high." But Howard believes "the benefit was equally high. Or higher."

**The Outcome**: Success. Howard states: "The community is today better off than when it was before the ABI break."

**The Lesson**: This is the canonical example of an ABI break that was worth the enormous cost. It demonstrates that rigid ABI preservation can prevent important improvements, and that the correct approach is quantitative cost-benefit analysis, not blanket rejection of ABI breaks.

> *"In my opinion, that's a case where there was an ABI break. It was a huge ABI break. And yet we still did it, and I'm glad we did. It was still worth it."*

**Supports Principles**: P8

<!-- METADATA
kind: experience
id: E6
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [string, sso, abi]
supports: [P8]
-->

---

### E7: std::exchange - Convenience Without Necessity

**Context**: std::exchange was proposed as a standard library utility function.

**What Happened**: Howard evaluated it against his standard: What problem does this solve? How hard is it to do without this? His conclusion was that std::exchange "doesn't really do much" and "offers a slight convenience." When asked how hard it would be to do what std::exchange does without it, he answered simply: "It'd be easy."

**The Outcome**: Mixed. std::exchange was standardized despite Howard's opposition. "I didn't vote for it."

**The Lesson**: This is Howard's concrete example of a feature that passed his "making the easy easier" threshold - a convenience wrapper that does not make the previously impossible possible or the difficult easy. Whether this was the right call is debatable, but it illustrates how his evaluation framework applies in practice.

> *"Do we, if standard exchange weren't there, how hard would it be to do what standard exchange does? It'd be easy."*

**Supports Principles**: P1, P3

<!-- METADATA
kind: experience
id: E7
source-type: explicit
category: history/decisions
applies-to: library
outcome: mixed
features: [exchange]
supports: [P1, P3]
-->

---

### E8: The Last-Minute Implementation Vote

**Context**: A library proposal came up for vote without substantial field experience.

**What Happened**: The proposers wrote an implementation "mere hours before the vote" and announced at the vote that their proposal was now "implemented." This announcement swayed the committee to vote in favor.

**The Outcome**: Failure. Howard describes it as "just yet another example of our collective failure." He adds: "I won't bother to go down the list of libraries where this strategy has failed us in the past."

**The Lesson**: An implementation created at the last minute cannot provide the field experience needed to validate a design. The committee should not be swayed by the mere existence of code. Implementation is a necessary but insufficient condition; the real question is always "What has been the field experience?"

> *"I should quit asking 'Has it been implemented?' The correct question is: What has been the field experience?"*

**Supports Principles**: P2

<!-- METADATA
kind: experience
id: E8
source-type: tacit
category: history/failures
applies-to: library
outcome: failure
features: [unspecified-library-feature]
supports: [P2]
-->

---

### E9: Compilers Removing User Code for UB Optimization

**Context**: Signed integer overflow is undefined behavior in C++, even though all hardware implements it as two's complement wrap-around.

**What Happened**: Programmers write overflow checks that test for signed integer overflow. But because signed overflow is UB, compilers reason that "this can't happen" and remove the check entirely. The result is that user-written safety code is silently deleted by the optimizer. Howard describes "infamous cases" where this caused real problems.

**The Outcome**: Failure. Howard views this as "performance over correctness" and considers it deeply problematic. He notes the committee may be softening its stance with concepts like "erroneous behavior" but the problem is ongoing.

**The Lesson**: When hardware has well-defined behavior that programmers rely on, declaring it undefined in the standard creates a trap. Compilers exploiting UB to remove user code inverts the correctness-performance hierarchy. The committee's historically permissive stance toward UB is slowly being recognized as a problem.

> *"It makes correct code incorrect. In the name of making the code faster."*

**Supports Principles**: P5

<!-- METADATA
kind: experience
id: E9
source-type: explicit
category: history/failures
applies-to: language
outcome: failure
features: [undefined-behavior, signed-integer-overflow]
supports: [P5]
-->

---

### E10: Apple Forced Template Instantiation Creates ABI Fragility

**Context**: While at Apple, Howard had a policy of keeping as much of the standard library as possible out of the dynamic library (dylib). By keeping code in headers and templates rather than explicitly instantiating into the dylib, he minimized the ABI surface that could never be changed.

**What Happened**: Apple managers overruled this policy. They wanted explicit instantiation of templates like vector into the dylib to make compilation and linking faster. Howard argued the ABI fragility outweighed the compile-time benefit, but was overruled.

**The Outcome**: Failure. libc++ now has "some extra fragility on its ABI that can't be broken" because of this decision. The short-term compilation speed benefit created a permanent constraint.

**The Lesson**: ABI surface area should be minimized proactively. Once code is baked into a shared library, it becomes an ABI contract that is extremely difficult to change. Management decisions driven by short-term metrics (compile speed) can create long-term technical debt that is effectively permanent.

> *"My managers forced me to explicitly instantiate things like vector into the dylib."*

**Supports Principles**: P8

<!-- METADATA
kind: experience
id: E10
source-type: explicit
category: history/failures
applies-to: library
outcome: failure
features: [abi, libc++, dylib]
supports: [P8]
-->

---

### E11: Smarter Allocator Proposal Dies at the C Committee

**Context**: Around 2010, Howard wanted to improve the allocator model so containers like vector could ask the allocator "how much memory did you actually give me?" and "can you expand this in place?" This would eliminate waste from alignment rounding and avoid unnecessary reallocations.

**What Happened**: Howard realized the proposal needed C committee cooperation because all C++ allocators ultimately build on malloc/free. He attempted to bring the proposal to the C committee but "did not regularly attend the C meeting and so I was kind of a stranger. They didn't know who I was." The C committee showed no interest.

**The Outcome**: Failure. The proposal never gained traction. Howard describes it as "kind of doomed to fail" from the start due to lack of relationships.

**The Lesson**: Technical merit is necessary but insufficient for cross-committee proposals. The proposer must have standing and relationships in both communities. Starting from zero credibility in a committee is an almost insurmountable handicap.

> *"I was kind of a stranger. They didn't know who I was... so that was kind of doomed to fail."*

**Supports Principles**: P9

<!-- METADATA
kind: experience
id: E11
source-type: explicit
category: history/failures
applies-to: library
outcome: failure
features: [allocators, malloc, memory-management]
supports: [P9]
-->

---

### E12: Hash Proposal Abandoned by Both Sides

**Context**: Howard (with Vinnie Falco as co-author) proposed a hash framework that would allow hashing multiple objects with a single hash function, maintaining the integrity of the hash algorithm. This addressed a real problem: boost::hash_combine hashes two things and then hashes the hashes, producing what Howard considers "garbage in, garbage out."

**What Happened**: Google simultaneously became interested in the same problem and produced their own proposal. There was "pretty intense disagreement over details on how to accomplish it, what exactly the API should be like." The two sides argued until both Howard and Google "were tired of arguing, and we both just dropped it."

**The Outcome**: Failure. Despite universal recognition that better hashing was needed and that it's a vocabulary problem requiring standardization, nothing was standardized. The feature was abandoned.

**The Lesson**: The committee's lack of executive power means that when two competing proposals reach an impasse, there is no mechanism to force resolution. Important features can simply be abandoned when champions lose energy, regardless of community need.

> *"The basic reason is because the committee's a group of volunteers and not an organization... There's no one who can say, I want you to do this, and if you don't, you're fired."*

**Supports Principles**: P10

<!-- METADATA
kind: experience
id: E12
source-type: explicit
category: history/failures
applies-to: library
outcome: failure
features: [hash, hash-combine]
supports: [P10]
-->

---

### E13: Auto Pointer to Unique Pointer Evolution

**Context**: C++98 had auto_ptr, a smart pointer with unique ownership semantics. Because C++98 had no move semantics, auto_ptr's copy constructor had to modify the source - "very strange copy semantics" that made it error-prone in generic code. A poison pill was designed to prevent putting auto_ptr in a vector, but it didn't work for built-in arrays.

**What Happened**: Move semantics enabled a replacement: unique_ptr, which refuses to copy but can move. It was part of the original move semantics proposal, initially named "move_ptr." Over "the course of several years," Howard decided the original name was terrible and renamed it to unique_ptr. Auto_ptr was deprecated and eventually removed from the standard, though this took many years.

**The Outcome**: Success. Unique_ptr is now one of the most fundamental C++ tools. But the path illustrates both the power of field experience in revealing better designs and the difficulty of removing things from the standard.

**The Lesson**: Field experience revealed both a better design (unique ownership via move instead of mutating copy) and a better name (unique_ptr instead of move_ptr). The years-long removal of auto_ptr confirms that extraction from the standard is painful even for universally acknowledged design failures.

> *"That goes back to field experience. When you first write a library, you're not always sure how well it's gonna work in real life until you start using it a lot."*

**Supports Principles**: P12, P13

<!-- METADATA
kind: experience
id: E13
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [unique-ptr, auto-ptr, move-semantics]
supports: [P12, P13]
-->

---

### E14: Thread Cancellation Dropped from C++11

**Context**: C++ threading was being modeled partly on POSIX threads (pthreads), which includes cancellation. But pthreads cancellation is an "order to stop" - the thread stops instantly. In C++, instant termination would skip destructors, causing memory leaks and resource corruption.

**What Happened**: One camp wanted pthreads-style cancellation (immediate stop). The other camp, including Howard, wanted cooperative cancellation (a request to stop that lets the thread run destructors and clean up). The distinction was "never communicated strongly enough or appropriately enough or clearly enough" to reach consensus. Cancellation was removed from C++11 threading entirely. Howard believes it may have returned around C++20.

**The Outcome**: Failure for C++11. Howard describes it as "a poor move that made 2011 threads less good than they could have been." The camp wanting cancellation also suffered from lack of field experience with C++-style cooperative cancellation.

**The Lesson**: Insufficient field experience combined with communication failures can kill important features. The lack of a C++-specific implementation with field experience left the cooperative cancellation camp unable to demonstrate that their approach worked, even though pthreads-style cancellation was clearly incompatible with C++ resource management.

> *"Somehow it seemed to me that that was never communicated strongly enough or appropriately enough, or clearly enough that we were able to reach a consensus."*

**Supports Principles**: P2, P7

<!-- METADATA
kind: experience
id: E14
source-type: explicit
category: history/failures
applies-to: library
outcome: failure
features: [threads, cancellation, pthreads]
supports: [P2, P7]
-->

---

### E15: Beman Dawes - Mentorship and the First Lesson

**Context**: Howard attended his first WG21 meeting in 1998 or 1999, having just fully implemented vector<bool> for MetroWorks. At that first meeting, he discovered that a defect report had been filed against vector<bool> - the standard was only months old and already had a major design bug.

**What Happened**: Howard's reaction was blunt: "I thought you guys knew what you were doing." He said it out loud. Beman Dawes "taught me my first lesson at standardization: don't be an asshole." Beman was kind about it - "he just gave me a look and says, you know, we're here to fix the problems." Beman went on to become Howard's mentor, guiding him through LWG, helping him become chair in 2005, and advising on the right way to do things. This mentorship was entirely informal - there was "no formal" mentoring program.

**The Outcome**: Success for Howard personally. Beman's mentorship shaped his entire committee career. But there is no system to replicate this. Howard notes that onboarding at WG21 is essentially "learn as you go along" - "there was no general recognition of new people on the committee" beyond introductions.

**The Lesson**: Informal mentorship is the only mechanism for transferring institutional knowledge in WG21, and it depends entirely on personal relationships. There are no formal retrospectives, no written institutional knowledge, and no structured onboarding. Howard explicitly states he'd "love to see stuff like that in writing."

> *"Beman Dawes taught me my first lesson at standardization: don't be an asshole."*

**Supports Principles**: P14

<!-- METADATA
kind: experience
id: E15
source-type: explicit
category: process/actual
applies-to: both
outcome: mixed
features: [vector-bool, mentorship, onboarding]
supports: [P14]
-->

---

## Evaluation Checklists

Actionable checklists derived from principles, for evaluating proposals.

### When Reviewing Library Proposals

- [ ] Does this make the previously impossible or impractical become possible or easy? (P1)
- [ ] Or does it merely make the already-easy slightly easier? (P1)
- [ ] Is there documented field experience from users outside the proposer's organization? (P2)
- [ ] Has the implementation existed for a significant period before this proposal? (P2)
- [ ] What problem does this solve, and how do programmers cope without it today? (P3)
- [ ] Is the standard version at least as fast as hand-written alternatives? (P4)
- [ ] Does the design prioritize correctness over performance in all cases? (P5)
- [ ] For APIs handling potentially adversarial input, is there both a checked and unchecked path? (P6)
- [ ] Is the proposal scoped minimally, with room to add later? (P13)
- [ ] Can the proposer point to external projects using this successfully? (P15)

**Questions to Ask**:
1. "What has been the field experience with this implementation?" (P2)
2. "Who outside your organization has used this, and what was their feedback?" (P2)
3. "If this proposal is rejected, what does the programmer do instead, and how hard is that?" (P3)
4. "How does this perform against existing practice?" (P4)
5. "What is the minimal version of this that would be useful?" (P13)
6. "How long has this implementation been available for public use?" (P2, P12)

<!-- METADATA
kind: checklist
category: evaluation/library
applies-to: library
proposal-type: feature
derived-from: [P1, P2, P3, P4, P5, P6, P13, P15]
-->

---

### When Evaluating ABI Impact

- [ ] Has a quantitative cost-benefit analysis been performed? (P8)
- [ ] Is the ABI concern being used as a blanket veto without analysis? (P8)
- [ ] Can the ABI surface be minimized (headers/templates vs dylib instantiation)? (P8)
- [ ] What is the long-term cost of not making this change? (P8)
- [ ] Is there precedent for similar ABI breaks succeeding? (E6)

**Questions to Ask**:
1. "What is the specific cost of this ABI break, in concrete terms?"
2. "What is the cost of never making this change?"
3. "Can the ABI surface be restructured to avoid the break while keeping the improvement?"

<!-- METADATA
kind: checklist
category: evaluation/library
applies-to: both
proposal-type: feature
derived-from: [P8]
-->

---

### When Evaluating Cross-Committee Proposals

- [ ] Does the proposer have established relationships in all relevant committees? (P9)
- [ ] Is there a co-author from each committee involved? (P9)
- [ ] Has the cross-committee coordination been negotiated in advance? (P9)
- [ ] Does the timeline account for multi-committee review cycles? (P9)

**Questions to Ask**:
1. "Have you presented this to the other committee? What was their response?"
2. "Who in the other committee is championing this?"

<!-- METADATA
kind: checklist
category: process/navigation
applies-to: both
proposal-type: feature
derived-from: [P9]
-->

---

### When Evaluating Committee Process Health

- [ ] Is there a formal retrospective process for shipped features? (P14)
- [ ] Are new members receiving structured onboarding beyond introductions? (P14)
- [ ] Is institutional knowledge being captured in writing? (P14)
- [ ] Are metrics being tracked for feature adoption and user satisfaction? (P14)
- [ ] Is the standardization cadence allowing sufficient implementation time? (P10)

<!-- METADATA
kind: checklist
category: process/actual
applies-to: both
proposal-type: wording-cleanup
derived-from: [P10, P14]
-->

---

## Open Questions

1. What is Howard's "list of libraries where this strategy has failed us in the past"? He mentioned it but declined to enumerate. (Ref: E8)
2. What constitutes "sufficient" field experience? Is there a minimum time threshold, user count, or diversity of use cases? (Ref: P2)
3. Howard mentioned the 3-year cadence might be too fast for implementers. What is the optimal cadence, and what evidence would answer this? (Ref: E2)
4. Howard expressed concern about feature adoption lag. What specific features have had the longest time-to-adoption, and why? (Ref: P14)
5. How did the concepts debate eventually resolve between C++11 and C++20? What changed to make consensus possible? (Ref: E3)
6. Howard mentioned "erroneous behavior" as a softening of the UB stance. What is the current committee position, and how has it evolved? (Ref: E9)
7. What specific allocator API improvements did Howard propose circa 2010? The papers are "back there" but Howard couldn't recall details. (Ref: E11)
8. Howard noted Peter Dimov's Variant2 (always-has-a-value) gained popularity. What does this say about the standard variant's design compromise? (Mentioned in transcript but Howard lacked direct involvement)
9. Howard was the sole standard library implementer at both MetroWorks and Apple. How common is this "team of one" pattern among vendors, and what are its implications for implementation quality?
10. Howard mentioned that the 3-year cadence may mean proposals submitted after the beginning of a cycle miss that ship. What is the effective "proposal window" for each standard?

---

## Raw Transcript Reference

- Transcript 1: `inputs/howard-hinnant.md` - Remote huddle interview, January 7, 2025 (~1 hour)
- Transcript 2: `inputs/howard-hinnant-2.md` - Filmed interview, October 26, 2025, Sturbridge MA (~1.5 hours)
