# Sean Parent: Captured Knowledge

**Interview Date**: December 10, 2025 (filmed, San Jose CA)
**Interviewer**: Ray Nowosielski
**Duration**: ~46 minutes
**Topics Covered**: C++ ubiquity, Boost's historical role, C++98-to-C++11 gap, Boost licensing and commercial adoption, open source in industry, Alex Stepanov and generic programming, meta programming, Boost Graph Library, Doug Gregor and concepts/Swift, "Tragedy of C++" thesis, standard library complexity, macro vs micro performance, memory safety, Rust and Swift as competitors, committee decision-making, regular types, university connections, Dave Abrahams, Dave Sankel, Beman Libraries

## Executive Summary

Sean Parent is a senior principal scientist at Adobe with a career spanning Apple (system software, QuickDraw GX, 68K-to-PowerPC transition), Google (Chrome OS), and decades at Adobe (Photoshop, research labs). He managed Adobe's Software Technology Lab alongside Alex Stepanov, spearheaded Adobe's adoption of Boost as its first allowed open source dependency, and co-drove the creation of the Boost Software License with Dave Abrahams.

Three dominant themes emerge from this interview. First, **C++ is over-optimizing in the small while leaving macro performance untouched**. Sean argues the standard obsesses over squeezing individual cycles from function calls while providing no standard access to GPUs or SIMD units, which represent over 99% of modern hardware performance. This misallocation of committee effort is, in his view, one of C++'s fatal flaws. Second, **growing complexity is an existential threat**. The standard library's std::pair requires roughly 2000 lines of code - an implementation that should serve as an example of how to write code but instead demonstrates complexity beyond what reasonable developers can digest. Third, **the committee's refusal to document goals and decision rationale** produces inconsistent outcomes: similar decisions are made in isolation and may yield different answers at different times. Sean identifies this as the committee's biggest structural problem.

Sean sees Boost as having both historical significance (keeping C++ alive during the C++98-to-C++11 gap, providing the field-tested libraries that powered C++11) and future potential. He argues Boost could again pioneer a major pivot - this time toward memory safety, SIMD, and GPU support - by building libraries that demonstrate what language-level safety features would enable, thereby creating pressure for language evolution.

---

## Principles

Distilled, actionable knowledge that can be applied agentically.

### P1: The Standard Over-Optimizes in the Small While Ignoring Macro Performance

> *"The standards kind of over-turned to optimizing in the small and not optimizing in the large. So there's a lot of complexity that goes into the language to try to squeeze individual cycles out of function calls when you're leaving more than 99% of the performance on the table."*

**The Principle**: The C++ standard invests enormous complexity in micro-optimizations (eliminating individual cycles from function calls) while providing no standard access to GPUs, SIMD units, or system thread pools - where the vast majority of modern hardware performance resides.

**Why It Matters**: If C++ is the language used for performance, but the standard only addresses 0.25% of the machine's capability, the language's core value proposition is hollow. Developers choosing C++ for performance discover they must leave the standard entirely to access the hardware that matters. Meanwhile, the micro-optimization complexity makes the language harder to use without proportional benefit.

**When to Apply**: Evaluating any proposal that adds language or library complexity for micro-optimization. Ask: does this address where actual performance lives on modern hardware, or does it squeeze cycles from the fraction the standard already covers?

**Red Flags**:
- Proposals adding complexity to save cycles in single-threaded CPU code
- No standard SIMD or GPU proposal on the agenda
- Threading proposals that encourage spinning up threads rather than using a system thread pool
- Performance arguments that ignore the GPU/SIMD gap entirely

**Supporting Experiences**: E5, E6

<!-- METADATA
kind: principle
id: P1
source-type: explicit
category: philosophy/tradeoffs
applies-to: both
confidence: high
supported-by: [E5, E6]
related-principles: [P2, P3]
-->

---

### P2: The Standard Library Should Exemplify How Developers Write Code

> *"The standard library, in my opinion, should be an example of how developers should write their code. And so if your example for how to write a pair of two values is 2000 lines of code, the complexity is more than most reasonable developers can digest."*

**The Principle**: The standard library serves as the canonical example of how to write C++ code. When standard library implementations are so complex that competent developers cannot understand them, the library fails its pedagogical role and signals that the language has a complexity problem.

**Why It Matters**: Developers learn idioms and patterns by reading standard library code. If std::pair - the simplest possible composite type - requires roughly 2000 lines of implementation, the implicit message is that writing correct C++ is beyond ordinary developers. This drives talent away from the language and reinforces the perception that C++ is irredeemably complex.

**When to Apply**: Evaluating library designs and language features. If a simple concept requires disproportionately complex implementation in the standard library, this signals that language-level support is needed to reduce the complexity.

**Red Flags**:
- Standard library implementations of simple types that run to hundreds or thousands of lines
- Features that are straightforward to describe but require heroic template machinery to implement
- Library code that even experienced developers struggle to read
- Proposals that add more template machinery rather than seeking language simplification

**Supporting Experiences**: E5

<!-- METADATA
kind: principle
id: P2
source-type: explicit
category: philosophy/library
applies-to: library
confidence: high
supported-by: [E5]
related-principles: [P1, P3, P5]
-->

---

### P3: Growing Complexity Is C++'s Existential Risk

> *"The tragedy ending is it continues on what I view as kind of its current path of growing complexity and ignoring the landscape of modern hardware and modern security concerns... it becomes something that the industry just slowly migrates away from. It becomes COBOL."*

**The Principle**: Unchecked growth in language and library complexity, combined with failure to address modern hardware and security concerns, risks reducing C++ to a legacy-only language within decades.

**Why It Matters**: Sean's "Tragedy of C++" thesis frames this as a Shakespearean arc: the same ambition that made C++ dominant (expressiveness, zero-overhead abstractions) becomes the flaw that undoes it. The language will not disappear - "30, 50 years from now, you'll still be able to make a great career writing C++ code" - but it may no longer be what developers choose for new projects. The industry slowly migrates away, not through dramatic rejection but through gradual attrition.

**When to Apply**: Evaluating any proposal that adds complexity to the language. Ask: does this reduce overall complexity (by absorbing library hacks into the language) or increase it? Also applies when evaluating whether the committee is addressing the right problems at the right scale.

**Red Flags**:
- Proposals that add complexity without simplifying existing patterns
- Committee focus on niche optimizations while ignoring hardware and safety gaps
- No roadmap for complexity reduction
- Arguments that "C++ programmers can handle the complexity" without evidence

**Supporting Experiences**: E5, E6, E7, E9

<!-- METADATA
kind: principle
id: P3
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E5, E6, E7, E9]
related-principles: [P1, P2, P8]
-->

---

### P4: The Committee Must Document Goals and Decision Rationale

> *"I think the biggest problem with the standards committee is an unwillingness to specify what the goals are and basically what the rules are for the standards committee. So every decision that the standards committee tends to make tends to almost be made in isolation. And they don't then document the rationale for that decision. And so when a similar decision is made, they maybe come up with a different answer."*

**The Principle**: The committee must establish and document explicit design goals, and must record the rationale behind each major decision. Without this, decisions are made in isolation and similar questions receive inconsistent answers across time.

**Why It Matters**: Inconsistent decisions produce an inconsistent language. When there is no documented rationale, new committee members cannot learn from past reasoning, and the committee cannot hold itself accountable to its own precedent. Sean gives the example of regularity: even a basic rule like "all new types should be regular" is not enforced because it was never formally established as a goal.

**When to Apply**: Evaluating committee process, proposal consistency, and design coherence. When a proposal contradicts a prior decision, ask whether documented rationale exists for either decision. When a proposal introduces a new type, ask whether it follows the same design principles as existing types.

**Red Flags**:
- No documented rationale for why a similar past proposal was accepted or rejected
- New types that violate conventions established by existing standard types
- Design decisions that contradict recent committee positions without acknowledging the change
- "We've always done it this way" without documentation of what "this way" is

**Supporting Experiences**: E8

<!-- METADATA
kind: principle
id: P4
source-type: explicit
category: process/actual
applies-to: both
confidence: high
supported-by: [E8]
related-principles: [P11]
-->

---

### P5: Library Complexity Should Be Pushed Into the Language

> *"I would love to see more of that complexity pushed into the language level... a type function... the syntax within C++ to write a type function looks nothing like how you would write a function for values. And that's only because type functions were developed kind of accidentally exploiting the template mechanism."*

**The Principle**: When Boost libraries demonstrate useful patterns that require complex template machinery, the correct long-term response is to absorb that complexity into the language as first-class features, not to accept the library-level complexity as permanent.

**Why It Matters**: Variadic templates and lambda expressions both started as library hacks in Boost and were later absorbed into the language proper, enormously simplifying their use. But many patterns remain stuck at the library level - type functions, for example, still require template specialization syntax that bears no resemblance to value-level functions. Each such gap represents avoidable complexity that makes the language harder to teach and use.

**When to Apply**: When evaluating whether a capability should remain a library feature or be promoted to a language feature. If the library implementation is complex but the concept is simple, language support is likely warranted.

**Red Flags**:
- Library features that require deep template meta-programming for simple concepts
- Patterns that every library author needs but that have no direct language support
- Syntax for a common operation that looks nothing like the analogous operation in a different domain
- "Just use Boost.MPL" as the answer to a fundamental expressiveness gap

**Supporting Experiences**: E5, E10, E11

<!-- METADATA
kind: principle
id: P5
source-type: explicit
category: philosophy/coherence
applies-to: both
confidence: high
supported-by: [E5, E10, E11]
related-principles: [P2, P3, P6]
-->

---

### P6: Boost Can Pioneer Industry-Shaping Pivots

> *"Boost could help in a pivot for the language in the same way... that boost had such a major impact on C++ 11 and where the language was going in that timeframe."*

**The Principle**: Boost has demonstrated the ability to shape the direction of C++ by building libraries that prove out new paradigms before standardization. This role is not exhausted; Boost could again pioneer a major pivot toward safety, SIMD, and GPU support.

**Why It Matters**: The Boost-to-standard pipeline was the engine behind C++11's success. Sean argues this same mechanism could address C++'s current existential risks: if Boost libraries demonstrated that safety features, standard SIMD, and GPU support are feasible and valuable, this would create pressure for language-level changes. The precedent exists; it requires will and direction.

**When to Apply**: When evaluating Boost's strategic direction or when considering where the C++ ecosystem should invest effort. Also applies when assessing whether a problem should be solved at the library level first to build evidence for language changes.

**Red Flags**:
- Boost investing primarily in incremental convenience libraries rather than paradigm-shifting ones
- No Boost effort on safety, SIMD, or GPU support
- Committee making language decisions without library-level proof of concept
- Ecosystem treating Boost as purely legacy

**Supporting Experiences**: E1, E4, E9, E12

<!-- METADATA
kind: principle
id: P6
source-type: explicit
category: belongs/ecosystem
applies-to: both
confidence: high
supported-by: [E1, E4, E9, E12]
related-principles: [P5, P8, P9]
-->

---

### P7: Commercial Adoption Requires a Single, Liberal License

> *"Look, you need one license. This is ridiculous. It has a serious impact on your adoption within industry."*

**The Principle**: Open source projects seeking commercial adoption must have a single, clearly-written, commercially-friendly license. Multiple licenses, ambiguous terms, or requirements that burden commercial users will cause legal departments to reject adoption regardless of technical merit.

**Why It Matters**: Sean's direct experience at Adobe showed that Boost's early state - over a hundred individual contributor licenses - required enormous legal effort to vet. Legal departments default to "no" because their job is to mitigate risk. Every additional license, every ambiguous clause, and every commercial burden (credit requirements, copyleft provisions) adds risk that legal will reject. The Boost Software License's creation was directly driven by this commercial adoption need.

**When to Apply**: Any open source project seeking industry adoption. Also applies when evaluating whether an open source dependency is viable for commercial use.

**Red Flags**:
- Multiple licenses within a single project
- No indemnification or origin statement in the license
- Requirements for product-level credit or attribution display
- Copyleft/viral license terms
- License language drafted without legal review

**Supporting Experiences**: E2, E3, E4

<!-- METADATA
kind: principle
id: P7
source-type: explicit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E2, E3, E4]
related-principles: [P6]
-->

---

### P8: Memory Safety Is an Existential Threat the Committee Has Not Addressed

> *"Every major security agency in the world has issued guidance to stop using both C and C++ as languages... the standards committee has not adequately addressed that issue or taken a hard pivot on it. There was one fairly strong proposal to bring memory safety to C++, and that was shot down."*

**The Principle**: The C++ community faces an existential threat from the global push away from memory-unsafe languages. The committee's failure to meaningfully address memory safety, including rejecting a strong safety proposal, accelerates the timeline for C++ becoming a legacy-only language.

**Why It Matters**: This is not a theoretical concern. Government security agencies worldwide have issued formal guidance against C and C++. Competing languages (Rust, Swift) offer memory safety as a core feature. If C++ does not pivot toward safety, the "tragedy ending" is that the industry gradually migrates away. Sean believes C++ is still "set up better than most languages to make a pivot" but sees no indication the committee is choosing that direction.

**When to Apply**: Evaluating any proposal related to safety, undefined behavior, or language evolution strategy. Also applies when assessing whether the committee's priorities align with industry needs.

**Red Flags**:
- Safety proposals rejected without a counter-proposal
- Committee focus on features unrelated to the safety crisis
- Arguments that safety is "not C++'s job"
- No committee roadmap for addressing government guidance against C++

**Supporting Experiences**: E9

<!-- METADATA
kind: principle
id: P8
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E9]
related-principles: [P3, P6, P12]
-->

---

### P9: University Connections Inject Essential Research DNA

> *"A lot of what I see that was driven in the early days of boost came out of universities... getting that young research focused DNA re-injected into the project... people who are looking at these big problems with fresh eyes."*

**The Principle**: Boost's most impactful work came from university research teams. Re-establishing strong connections with universities is essential for tackling the hard, paradigm-shifting problems (safety, SIMD, GPU) that incremental industry work will not solve.

**Why It Matters**: Andrew Lumsdaine's team at Indiana University produced Doug Gregor, Jeremy Siek, and the Boost Graph Library. This academic pipeline brought both theoretical rigor and willingness to tackle fundamental problems. Sean argues that industry contributors tend toward incremental improvements, while the big pivots Boost needs require the "fresh eyes" and research orientation that universities provide. He specifically names Jeremy Siek and Hartmut Kaiser (HPX) as potential connections.

**When to Apply**: When evaluating Boost's organizational strategy, recruiting efforts, or research direction. Also applies when assessing whether a technical problem requires fundamental research rather than incremental engineering.

**Red Flags**:
- No academic collaborators on paradigm-shifting Boost projects
- All contributors from industry with incremental focus
- Hard problems being addressed with engineering workarounds rather than research
- No connection to CS departments working on relevant problems

**Supporting Experiences**: E10

<!-- METADATA
kind: principle
id: P9
source-type: explicit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E10]
related-principles: [P6]
-->

---

### P10: Political Deadlocks Kill Important Features When No One Can Break the Tie

> *"There was a competing proposal. He was out of Andrew Lumsdaine's team and there was a competing proposal from Stroustrup's team, and they couldn't reach consensus on the two. The end result was both of them got pulled from the standards and neither went in."*

**The Principle**: When competing proposals for an important feature reach political deadlock, the ISO consensus model provides no mechanism to break the tie. The result is that neither proposal advances, and the feature is lost for years or decades.

**Why It Matters**: Doug Gregor's concepts proposal was technically sound and had a working implementation, but a competing proposal from Stroustrup's team created an impasse. The committee pulled both. Concepts did not arrive until C++20 - nearly a decade later. Gregor, who had invested years of personal effort, left C++ and proved his design's value in Swift. The committee lost both the feature and the contributor.

**When to Apply**: When evaluating competing proposals for the same feature space. Also applies when assessing committee dynamics and the risk of deadlock.

**Red Flags**:
- Two competing proposals with entrenched camps and no clear path to consensus
- Champions showing signs of fatigue or disengagement
- Political dynamics overriding technical evaluation
- No structured process for resolving design disagreements

**Supporting Experiences**: E7

<!-- METADATA
kind: principle
id: P10
source-type: explicit
category: process/politics
applies-to: both
confidence: high
supported-by: [E7]
related-principles: [P4]
-->

---

### P11: All New Standard Types Should Be Regular

> *"Even what I would consider basic things like saying all new types within the language should be regular doesn't happen and doesn't get held up."*

**The Principle**: Every new type introduced into the standard should satisfy the requirements of regularity (copies are equal, assignment makes equal, equality is reflexive/symmetric/transitive). This should be an enforced design rule, not an optional aspiration.

**Why It Matters**: Regularity is a foundational concept from generic programming that ensures types compose predictably. When standard types violate regularity, generic algorithms cannot rely on consistent semantics, and users encounter surprising behavior. Sean identifies the failure to enforce this basic rule as symptomatic of the committee's larger failure to document and enforce design principles.

**When to Apply**: Evaluating any proposal that introduces new types. The first question should be: is this type regular? If not, there must be a compelling justification.

**Red Flags**:
- New types where copy does not produce equality
- Types with assignment that does not establish equality
- No discussion of regularity in the proposal
- Proposal authors unaware of or dismissive of regularity requirements

**Supporting Experiences**: E8

<!-- METADATA
kind: principle
id: P11
source-type: explicit
category: philosophy/library
applies-to: both
confidence: high
supported-by: [E8]
related-principles: [P4]
-->

---

### P12: Libraries Should Demonstrate Safety Guarantees to Drive Language Change

> *"If they started to structure the libraries to say, look, if we had safety features in the language then libraries structured in this fashion would be conformant... If they could demonstrate that and then come up with language proposals... I think that could have huge influence."*

**The Principle**: The most effective way to drive language-level safety features is to first build libraries that demonstrate what would be possible with those features - showing that real code can be structured to avoid aliasing, unsafe casting, and other hazards - and then propose the language features that would make such guarantees enforceable.

**Why It Matters**: This is the same strategy that made C++11 succeed: Boost libraries demonstrated what was possible, then language features (variadic templates, lambdas) made it native. Sean argues the same approach should be applied to safety. Rather than proposing abstract safety features, build libraries that work today but could be *proven safe* if the language provided the right guarantees. This creates concrete, demonstrable evidence for what the language needs.

**When to Apply**: When planning strategy for getting safety features into C++. Also applies more broadly to any language feature proposal: demonstrate the value at the library level first.

**Red Flags**:
- Language feature proposals with no library-level proof of concept
- Safety proposals that are purely theoretical with no working code
- Libraries that require unsafe constructs when they could be structured to avoid them
- No effort to show what language features would make existing libraries provably safe

**Supporting Experiences**: E1, E9

<!-- METADATA
kind: principle
id: P12
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E1, E9]
related-principles: [P5, P6, P8]
-->

---

## Experiences

Relatable stories that illustrate and support the principles.

### E1: Boost Kept C++ Alive During the Standards Gap

**Context**: After C++98, the next major standard was C++03 - which was merely a defect-fix release. The next real language update, C++11, did not arrive until thirteen years after C++98. During this enormous gap, C++ risked stagnation and irrelevance.

**What Happened**: Boost appeared during this gap and became a growing collection of high-quality open source libraries. These libraries "built off some of the ideas that Alex Stepanov laid down with the standard template library" and were "written by a group of people who kind of find ways to exploit aspects of the language and turn that into interesting and useful libraries." Boost both kept the language vibrant during the gap and became the foundation for C++11's features.

**The Outcome**: Success. C++11 was "a huge step up in the language." Variadic templates, lambda expressions, and many library features originated in or were validated through Boost. Sean states C++ "would've greatly diminished during that time period, just from stagnation" without Boost.

**The Lesson**: An ecosystem of high-quality libraries can keep a language alive and relevant even when the standard is stagnant. Boost's role was not just to provide libraries but to maintain community energy and prove out new paradigms. This precedent is directly relevant to Sean's argument that Boost could again pioneer a major pivot.

> *"I think C++ in some sense would've greatly diminished during that time period. Just from stagnation."*

**Supports Principles**: P6, P12

<!-- METADATA
kind: experience
id: E1
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [boost, c++11, variadic-templates, lambda-expressions]
supports: [P6, P12]
-->

---

### E2: Over 100 Licenses Nearly Blocked Adobe's Boost Adoption

**Context**: Sean was managing Adobe's Software Technology Lab when Boost first appeared. He wanted to use Boost libraries within Adobe products, but Adobe had strict legal requirements for any external code.

**What Happened**: "Boost didn't have a single license. So contributors to Boost were putting their code under their own license, which means that there were over a hundred licenses inside of the Boost Libraries." Sean had to get every one of these licenses vetted by Adobe's legal department. This was an enormous effort, and legal departments at companies defaulted to "no" because "their job is to mitigate risk."

**The Outcome**: Success, eventually. Sean successfully got the licenses vetted, and Boost became "the first open source libraries that were allowed to be used within the company." But the effort was disproportionate and would have been unnecessary with a single license.

**The Lesson**: Multiple licenses within a single project create an adoption barrier that scales with the number of licenses, not the size of the project. Even when every individual license is acceptable, the sheer volume of legal review required can block adoption. This directly motivated Sean's push for the Boost Software License.

> *"I had to get that all vetted by our legal department here before we could get sign off."*

**Supports Principles**: P7

<!-- METADATA
kind: experience
id: E2
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [boost-license, open-source-adoption]
supports: [P7]
-->

---

### E3: Sean and Dave Abrahams Create the Boost Software License

**Context**: Having experienced the pain of 100+ licenses firsthand, Sean pushed Dave Abrahams to establish a single license for Boost, arguing "it has a serious impact on your adoption within industry."

**What Happened**: Dave agreed but wasn't satisfied with existing commercially-friendly licenses (Berkeley standard license, MIT license) - "he wasn't quite happy with the terminology." He contracted with a lawyer to draft a new license specifically for Boost. Sean ran the draft past Adobe Legal and fed their input back to Dave "to make sure that it was acceptable for Adobe to use." The resulting Boost Software License was designed to be maximally commercially friendly: no credit requirements in the product, no copyleft provisions, clear origin statements.

**The Outcome**: Success. The Boost Software License became one of the most commercially-friendly open source licenses, removing a major barrier to industry adoption.

**The Lesson**: Effective licensing requires input from both the open source community and commercial legal departments. Sean's role as intermediary between Dave (community side) and Adobe Legal (commercial side) produced a license that satisfied both parties. The key design choices were all about minimizing commercial burden: no scrolling credits, no copyleft, clear indemnification.

> *"You don't want something that says, oh, every time you launch Photoshop, you need to see scrolling credits of every single library that went in before you can use the product."*

**Supports Principles**: P7

<!-- METADATA
kind: experience
id: E3
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [boost-software-license, open-source-licensing]
supports: [P7]
-->

---

### E4: Open Source Viewed as "Communist" in the Early Days

**Context**: When open source first appeared on the scene, it was perceived as fundamentally anti-commercial. Many licenses were "viral" - including an open source library in a product required open-sourcing the product itself.

**What Happened**: "It was viewed as being very anti-commercial use and so, you know, anti-corporation and it was kind of the communist view of open source software." Viral licenses meant legal departments refused to allow any open source into commercial products. Even non-viral licenses were rejected because legal departments lacked processes for evaluating them. "There wasn't a process at companies to do that. And so it meant you had to sit down with legal and try to make an argument."

**The Outcome**: Mixed. Sean credits Boost as "one of the projects that started to change that perception" because it met a real need, had a liberal license, was open for commercial use, and focused on language standardization, which gave companies a reason to contribute.

**The Lesson**: Boost helped shift the industry's perception of open source from "communist threat" to "valuable collaboration tool." The key was aligning open source contribution with corporate interests: contributing to Boost contributed to the C++ standard, which benefited every C++ shop. This alignment of incentives was essential for legitimizing open source in corporate environments.

> *"Anybody who's working in tech has signed an agreement with their company that says that whatever they produce at whatever hours they produce it is owned by the company."*

**Supports Principles**: P6, P7

<!-- METADATA
kind: experience
id: E4
source-type: explicit
category: history/successes
applies-to: both
outcome: mixed
features: [open-source, licensing, corporate-adoption]
supports: [P6, P7]
-->

---

### E5: std::pair at 2000 Lines of Code

**Context**: Sean's "Tragedy of C++" keynote at C++ North 2022 examined C++'s growing complexity problem. He needed a concrete example that would resonate with the audience.

**What Happened**: Sean showed the implementation of std::pair in the standard library. "You would think would be trivial implementation" - it is just a pair of two values. But the actual implementation "is something close to 2000 lines of code. It's ridiculous." This complexity exists because the language lacks the expressive power to implement even simple types simply; the library must use extensive template machinery to handle all the edge cases that the language does not address natively.

**The Outcome**: Failure. Sean presents this as a damning indictment: "If your example for how to write a pair of two values is 2000 lines of code, the complexity is more than most reasonable developers can digest."

**The Lesson**: When the simplest possible standard library type requires thousands of lines of implementation, the problem is not with the library author but with the language's expressiveness. The fix is language evolution that absorbs the complexity, not acceptance of library-level heroics as normal.

> *"The standard library, in my opinion, should be an example of how developers should write their code."*

**Supports Principles**: P1, P2, P3, P5

<!-- METADATA
kind: experience
id: E5
source-type: explicit
category: history/failures
applies-to: both
outcome: failure
features: [std-pair, template-complexity]
supports: [P1, P2, P3, P5]
-->

---

### E6: C++ Accesses Only 0.25% of the Machine

**Context**: C++ is chosen for performance-critical applications, yet the standard provides no way to access the majority of modern hardware's compute capability.

**What Happened**: Sean calculated that "if you're looking at just single threaded C++ running on a CPU, you're only able to use about 0.25% of the machine because most of the performance of the machine is locked up in the GPU and in the SIMD units." Furthermore, the standard threading model "encourages developers to spin up threads" when "you really don't want more threads executing on your hardware than you have cores on the machine." There is no standard access to system thread pools.

**The Outcome**: Failure. Sean notes a minimal SIMD library is "slated for C++ 26, something like that" but describes the overall situation as leaving "more than 99% of the performance on the table."

**The Lesson**: The standard's focus on micro-optimization (eliminating copies, enabling move semantics, constexpr everything) is misallocated effort when the macro performance problem - no standard GPU/SIMD access - remains unaddressed. This is not a niche concern; it affects every performance-sensitive C++ application.

> *"You're counting cycles when you should be counting in big buckets."*

**Supports Principles**: P1, P3

<!-- METADATA
kind: experience
id: E6
source-type: explicit
category: history/failures
applies-to: both
outcome: failure
features: [gpu, simd, threading, performance]
supports: [P1, P3]
-->

---

### E7: Doug Gregor's Concepts Rejected, Became Swift Protocols

**Context**: Doug Gregor, working out of Andrew Lumsdaine's team at Indiana University, designed and implemented "concept C++" for the C++ standard. He had invested years of personal effort and had a working implementation.

**What Happened**: "There was a competing proposal from Stroustrup's team, and they couldn't reach consensus on the two." The decision was "a very political decision." Both proposals were pulled from the standard - "neither went in." Gregor, having invested so much personal effort, "was looking for something outside of C++ to go do." He went to Apple and implemented his concepts design as Swift protocols. Sean believes Gregor wanted "to prove that his work was of high value. And I think he did that in Swift."

**The Outcome**: Failure for C++. Concepts did not arrive in C++ until C++20, roughly a decade later. The C++ community lost both the feature and one of its most talented contributors to Swift. "Within the community, it was a big political issue."

**The Lesson**: Political deadlocks in the committee have consequences beyond delay. Talented contributors who invest years in a design and see it killed by politics may leave the ecosystem entirely. The committee's inability to resolve competing proposals cost C++ both a decade of concepts support and Doug Gregor's ongoing contributions.

> *"I think he, you know, part of what he wanted to go do was prove that his work was of high value. And I think he did that in Swift."*

**Supports Principles**: P10

<!-- METADATA
kind: experience
id: E7
source-type: explicit
category: history/failures
applies-to: language
outcome: failure
features: [concepts, swift-protocols]
supports: [P10]
-->

---

### E8: The Committee's Undocumented Decision-Making

**Context**: Asked who is to blame for the "tragedy of C++," Sean pointed not at any individual but at the standards committee as a whole.

**What Happened**: Sean identified the committee's "unwillingness to specify what the goals are and basically what the rules are" as its biggest problem. "Every decision that the standards committee tends to make tends to almost be made in isolation. And they don't then document the rationale for that decision." The concrete example he gave: "Even what I would consider basic things like saying all new types within the language should be regular doesn't happen." Bjarne Stroustrup may advocate for such rules, "but Bjarne is not a dictator" - the ISO structure gives each country one vote, and even a hundred US members only get one vote collectively.

**The Outcome**: Failure. The result is "a lot of the inconsistency in the language, a lot of the warts in the language and a lot of the complexity."

**The Lesson**: A standards body that does not document its own design principles and decision rationale will produce an inconsistent standard. The ISO consensus model, while democratic, provides no mechanism for enforcing design coherence. This must be addressed through explicit, documented design goals that proposals are evaluated against.

> *"And so when a similar decision is made, they maybe come up with a different answer. And I think that's the reason for a lot of the inconsistency in the language."*

**Supports Principles**: P4, P11

<!-- METADATA
kind: experience
id: E8
source-type: explicit
category: process/actual
applies-to: both
outcome: failure
features: [committee-process, decision-rationale, regular-types]
supports: [P4, P11]
-->

---

### E9: The Memory Safety Proposal Shot Down

**Context**: Global security agencies have issued guidance against C and C++ as memory-unsafe languages. Rust and Swift offer safety as core features. C++ faces growing pressure to address this.

**What Happened**: "There was one fairly strong proposal to bring memory safety to C++, and that was shot down." Sean describes this in the context of the "tragedy" thesis: C++ is failing to pivot on safety even as the industry demands it. He believes C++ "could pivot" and is "still set up better than most languages to make a pivot" but sees "no indication that that's the direction that the standard is choosing to go."

**The Outcome**: Failure. The committee rejected the proposal without (in Sean's telling) establishing an alternative path. The safety gap remains unaddressed.

**The Lesson**: Rejecting a safety proposal without a counter-proposal or roadmap is not a neutral decision - it is an active choice to leave the safety gap open. Combined with government guidance and competitive pressure from Rust and Swift, this accelerates the timeline for C++ becoming a legacy language.

> *"The standards committee has not adequately addressed that issue or taken a hard pivot on it."*

**Supports Principles**: P3, P6, P8, P12

<!-- METADATA
kind: experience
id: E9
source-type: explicit
category: history/failures
applies-to: both
outcome: failure
features: [memory-safety, safe-cpp]
supports: [P3, P6, P8, P12]
-->

---

### E10: Boost Graph Library as the STL Extension Exemplar

**Context**: Alex Stepanov created STL with the vision that it "should be an example of how you should write code" - not just a container/algorithm library, but a paradigm for structuring software.

**What Happened**: Jeremy Siek, Doug Gregor, and Andrew Lumsdaine (all from Indiana University) created the Boost Graph Library, which applied STL's generic programming approach to graph data structures and algorithms. Sean describes it as "the one example that we have of using what Alex did with STL and generic programming as an example of doing something in a different, slightly different domain." He calls it "just a phenomenal piece of work" and "a stellar example."

**The Outcome**: Success. The Boost Graph Library demonstrated that STL's approach could generalize beyond sequences. However, Alex Stepanov himself views the meta-programming machinery required to make it work as "a hack" - "generic programming has nothing to do with meta programming."

**The Lesson**: The Boost Graph Library validates Stepanov's vision but also reveals the gap between what generic programming *should* look like and what C++ forces it to look like. The library's excellence was achieved despite the language's limitations, not because of them. This reinforces the principle that library-level complexity should ultimately be absorbed by the language.

> *"Alex always had this vision that his work on STL should be an example of how you should write code."*

**Supports Principles**: P5, P9

<!-- METADATA
kind: experience
id: E10
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [boost-graph-library, generic-programming, stl]
supports: [P5, P9]
-->

---

### E11: Alex Stepanov's Meta Programming Was a Hack

**Context**: Meta programming - using templates to write programs that the compiler uses to write your program - became one of Boost's defining characteristics. But its origin was accidental.

**What Happened**: Alex Stepanov "started this notion of meta programming in order to implement STL. But he will tell you, generic programming has nothing to do with meta programming. It was a hack so he could implement generic programming, and it kind of became the thing in Boost." The Boost Meta Programming Library (MPL) formalized this hack, and meta programming became synonymous with Boost in many developers' minds. Sean notes this "just brings a lot of complexity and noise" and "shouldn't really be the thing that's held up as this is the thing that people should be using from Boost."

**The Outcome**: Mixed. Meta programming enabled powerful libraries (boost::function, boost::any, which are now in the standard) but also became a source of the complexity that gives Boost its intimidating reputation. Bjarne Stroustrup "seems conflicted" about Boost in part because of this over-pivot on meta programming.

**The Lesson**: When a workaround becomes institutionalized, it obscures the original goal. Meta programming was a means to implement generic programming in a language that lacked first-class support for it. The correct response was always to push for language-level support, but the hack became the identity. This is the pattern that P5 (push library complexity into the language) aims to prevent.

> *"Generic programming has nothing to do with meta programming. It was a hack so he could implement generic programming."*

**Supports Principles**: P5

<!-- METADATA
kind: experience
id: E11
source-type: explicit
category: history/decisions
applies-to: both
outcome: mixed
features: [meta-programming, mpl, generic-programming]
supports: [P5]
-->

---

### E12: Beman Libraries as Boost's Standards-Focused Successor

**Context**: Dave Sankel, whom Sean hired from Bloomberg and groomed to manage Adobe's tech foundations research lab, started the Beman Libraries project.

**What Happened**: Beman Libraries is "kind of a successor to Boost, this time a little more focused on vetting libraries for standardization as opposed to building out libraries as a separate way of gaining experience." The key difference from Boost's original charter: "The idea is to start from a standards proposal and then build out the library and gain some experience to improve the standardization effort." Boost's original model was to build libraries independently and then turn successful ones into standards proposals. Beman inverts this: start with the proposal, then build the library to validate it.

**The Outcome**: Too early to evaluate. The project is new.

**The Lesson**: The Beman Libraries represent an evolution of the Boost model, addressing a perceived inefficiency: Boost libraries sometimes accumulated features and complexity that were unnecessary for standardization. Starting from the proposal ensures the library stays focused on what the standard actually needs. Whether this inverted model produces the same quality of field experience remains to be seen.

> *"Start from a standards proposal and then build out the library and gain some experience to improve the standardization effort."*

**Supports Principles**: P6

<!-- METADATA
kind: experience
id: E12
source-type: explicit
category: history/decisions
applies-to: library
outcome: mixed
features: [beman-libraries, standardization-process]
supports: [P6]
-->

---

### E13: Boost Viewed as "Legacy to Remove" at Companies

**Context**: Many Boost libraries have been standardized as part of C++11 and later standards. Companies that adopted Boost now face migration pressure.

**What Happened**: "If you talk to a lot of companies right now, they will say one issue that they have is now that large portions of boost have been standardized, they would like to be able to migrate to the standard versions. And in some cases that can be very hard. And so boost becomes almost synonymous within some organizations as legacy stuff that must be removed." Sean pushes back: "That's not completely true. There are large portions of Boost that are not standardized and are incredibly useful."

**The Outcome**: Mixed. Boost's success in getting libraries standardized created a perception problem: the project is seen as legacy rather than living. This perception threatens Boost's ability to play the future-shaping role Sean envisions.

**The Lesson**: The Boost-to-standard pipeline has a paradoxical side effect: success breeds the perception of obsolescence. Projects that serve as proving grounds for standardization must actively demonstrate ongoing relevance beyond what has already been standardized, or they risk being dismissed as legacy.

> *"Boost becomes almost synonymous within some organizations as legacy stuff that must be removed."*

**Supports Principles**: P6

<!-- METADATA
kind: experience
id: E13
source-type: explicit
category: history/decisions
applies-to: library
outcome: mixed
features: [boost, migration, standardization]
supports: [P6]
-->

---

### E14: Dave Abrahams - The Specification Gap Finder

**Context**: Sean hired Dave Abrahams to join Adobe's reformed Software Technology Lab after years of mutual attempts to hire each other.

**What Happened**: Sean describes Abrahams' distinctive capability: "Dave Abrahams is incredibly detail oriented. He has a really good eye for making sure that language is precise and that things are well specified and that there aren't any gaps in the specification. That's kind of his superpower." Abrahams is also credited with "the guarantees for exception handling," which Sean calls "a very important contribution to generic programming." He also worked on the Swift standard library and Swift UI at Apple, and co-created the Boost Software License.

**The Outcome**: Success. Abrahams' ability to find specification gaps makes him uniquely valuable for review: "He's a good person to run a presentation by or run a paper by, 'cause he will find the holes quite quickly."

**The Lesson**: The ability to find specification gaps is a rare and valuable skill in the standards community. When reviewing proposals or library designs, having someone with this skill in the review loop catches problems that design-level and implementation-level review miss.

> *"He will find the holes quite quickly."*

**Supports Principles**: P4

<!-- METADATA
kind: experience
id: E14
source-type: tacit
category: groups/lewg
applies-to: both
outcome: success
features: [specification-review, exception-safety]
supports: [P4]
-->

---

## Evaluation Checklists

Actionable checklists derived from principles, for evaluating proposals.

### When Reviewing Proposals for Performance Impact

- [ ] Does this proposal address performance at the macro level (GPU, SIMD, thread pools) or only micro level (individual cycles)? (P1)
- [ ] Does the proposed implementation exemplify how developers should write code, or does it require heroic template machinery? (P2)
- [ ] Does this proposal reduce overall language complexity or add to it? (P3)
- [ ] If the proposal adds complexity for micro-optimization, is there a proportional benefit? (P1)
- [ ] Could this library-level complexity be eliminated by a language feature? (P5)

**Questions to Ask**:
1. "What percentage of modern hardware performance does this proposal help access?" (P1)
2. "Can a competent developer read and understand this implementation?" (P2)
3. "Is there a simpler way to achieve this if the language provided better support?" (P5)

<!-- METADATA
kind: checklist
category: evaluation/library
applies-to: both
proposal-type: feature
derived-from: [P1, P2, P3, P5]
-->

---

### When Evaluating Committee Design Consistency

- [ ] Is there documented rationale for how similar past decisions were made? (P4)
- [ ] Does the proposed type satisfy regularity requirements? If not, is there a compelling justification? (P11)
- [ ] Is this decision consistent with the committee's stated design goals? (P4)
- [ ] Are the design principles being applied the same ones used for analogous features? (P4)

**Questions to Ask**:
1. "What was the rationale when the committee made a similar decision previously?" (P4)
2. "Is this type regular? If not, why not?" (P11)
3. "What documented design principle supports this choice?" (P4)

<!-- METADATA
kind: checklist
category: process/actual
applies-to: both
proposal-type: feature
derived-from: [P4, P11]
-->

---

### When Evaluating Boost Strategic Direction

- [ ] Is Boost investing in paradigm-shifting work (safety, SIMD, GPU) or only incremental convenience? (P6)
- [ ] Are there active university collaborations bringing research DNA into the project? (P9)
- [ ] Are libraries being structured to demonstrate what language-level safety features would enable? (P12)
- [ ] Is there a clear narrative for Boost's relevance beyond what has already been standardized? (E13)
- [ ] Is the licensing clear, single, and commercially friendly? (P7)

**Questions to Ask**:
1. "What would this library look like if the language had safety guarantees?" (P12)
2. "Which university research groups are involved in this effort?" (P9)
3. "How does this advance C++ beyond where it is today, not just make existing things slightly easier?" (P6)

<!-- METADATA
kind: checklist
category: belongs/ecosystem
applies-to: both
proposal-type: feature
derived-from: [P6, P7, P9, P12]
-->

---

### When Evaluating Memory Safety Proposals

- [ ] Does the proposal provide a concrete path toward safety, not just mitigation? (P8)
- [ ] Is there library-level evidence that the proposed safety model works in practice? (P12)
- [ ] Does rejection of this proposal come with an alternative roadmap? (P8)
- [ ] Does the proposal address the government guidance against C/C++? (P8)
- [ ] Does this reduce complexity or add to it? (P3)

**Questions to Ask**:
1. "If we reject this safety proposal, what is our alternative path?" (P8)
2. "Can existing libraries be restructured to demonstrate this safety model works?" (P12)
3. "What is the timeline for C++ to address the safety gap before the industry moves on?" (P3, P8)

<!-- METADATA
kind: checklist
category: evaluation/language
applies-to: both
proposal-type: feature
derived-from: [P3, P8, P12]
-->

---

## Open Questions

1. What specific memory safety proposal was "shot down" by the committee? What were the stated reasons for rejection, and was any alternative path proposed? (Ref: E9, P8)
2. Sean claims C++ accesses only 0.25% of the machine. What is the basis for this calculation? Does it hold across different workload types (servers, embedded, desktop)? (Ref: E6, P1)
3. How exactly does the Beman Libraries' inverted model (start from proposal, build library) compare in practice to Boost's original model (build library, then propose)? Does starting from the proposal produce sufficient field experience? (Ref: E12)
4. Sean mentions Rust "has not proven itself out at scale" and has "significant gaps for commercial products." What specific gaps is he referring to? (Ref: P3, P8)
5. What are the specific language features that would allow type functions to be written with the same syntax as value functions? Are there proposals in flight? (Ref: P5, E11)
6. Sean says Bjarne "seems conflicted" about Boost. What is the current relationship between Bjarne and the Boost community? Has Boost's meta-programming reputation evolved? (Ref: E11)
7. Which companies currently view Boost as "legacy stuff that must be removed"? What would change this perception? (Ref: E13)
8. Sean names Jeremy Siek and Hartmut Kaiser as potential university connections for Boost's future. Have any such collaborations materialized? (Ref: P9)
9. Sean mentions Dave Sankel is "a hard no with us" but cannot explain why on camera. What is the context? (Ref: transcript summary)
10. How has the committee's approach to political deadlocks changed since the concepts failure? Is there now a process for resolving competing proposals? (Ref: P10, E7)

---

## Raw Transcript Reference

- Transcript: `inputs/sean-parent.md` - Filmed interview, December 10, 2025, San Jose CA (~46 minutes)
