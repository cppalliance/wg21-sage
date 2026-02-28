# Matheus Izvekov: Captured Knowledge

**Interview Date**: January 7, 2025
**Interviewer**: Vinnie Falco
**Duration**: ~1 hour 10 minutes
**Topics Covered**: Template implementation, compiler ontology vs. standardese, overload resolution, committee process, standard bugs taxonomy, P3310 template template parameter matching, trivial relocation, implementation burden, vocabulary types, knowledge loss in process transitions, Numerics Study Group (SG6)

## Executive Summary

Matheus Izvekov is a Clang compiler developer (formerly at Bloomberg) specializing in templates, overload resolution, and template argument deduction. He is one of the few active WG21 participants with deep expertise in the template and overload resolution areas of the language specification, domains whose original architects have largely retired from active committee work.

Three dominant themes emerge from this interview. First, **there is a significant translation gap between compiler implementation knowledge and standardese**. Matheus describes his own difficulty converting deep compiler understanding into standard wording, calling it a difference in "ontology" between Clang's internal model and the standard's specification model. This gap means that the people best positioned to fix template-related defects in the specification are not necessarily the people best positioned to write the wording. Second, **the committee's feature throughput exceeds implementers' capacity to absorb it**. Matheus notes that standard library implementation teams are understaffed and that approved features like linear algebra may take years to ship, suggesting the committee should throttle its output to match implementation capacity. Third, **institutional knowledge degrades at every process transition** - from study groups to EWG to CWG - because oral rationale and satisfactorily-answered objections are not captured in papers, and transcripts are not publicly accessible.

Matheus also provides a valuable first-person account of presenting highly technical template papers to a committee audience where few members share his depth of expertise. He frames this not as a committee deficiency but as a natural consequence of C++'s complexity, and notes that the trust people place in recognized experts is a reasonable mechanism even when it means voting on material one does not fully understand.

---

## Principles

Distilled, actionable knowledge that can be applied agentically.

### P1: Standard Bugs Come in Two Kinds With Different Fix Paths

> *"There's like two kinds of major bugs in the standard. There's editorial bugs - the standard was worded wrong, people wanted it to say something and then the standard said something else. And then there are problems in the wording where it looks obviously wrong, but you can't make the case that people didn't want to say that."*

**The Principle**: Defects in the C++ standard fall into two distinct categories requiring different remediation processes: editorial bugs (wording fails to express known intent) and design-level bugs (wording appears wrong but original intent is unclear). The fix path differs dramatically.

**Why It Matters**: Editorial bugs can be fixed efficiently through CWG directly, sometimes without even requiring a paper, and applied as a DR. Design-level bugs require the full process: a paper, EWG review, technical vote, plenary, and CWG wording. Misclassifying a design-level bug as editorial (or vice versa) wastes time or produces inadequate fixes. Understanding this taxonomy helps paper authors choose the right process path and set realistic timelines.

**When to Apply**: When encountering a defect in the standard, or when writing a paper to fix one. Determine which category the bug falls into before choosing a process strategy.

**Red Flags**:
- Attempting to fix a design-level bug through the editorial process
- Treating an editorial fix as requiring full EWG review
- Assuming all standard defects follow the same remediation path
- Paper author frustrated by "bureaucratic overhead" on a bug that genuinely requires design review

**Supporting Experiences**: E1

<!-- METADATA
kind: principle
id: P1
source-type: explicit
category: process/formal
applies-to: language
confidence: high
supported-by: [E1]
related-principles: [P2]
-->

---

### P2: Language Proposals Must Go Through Evolution Before Core

> *"Sometimes features went through core and now we learned hard lessons. People sometimes bring that up as an example why things have to go through EWG first."*

**The Principle**: Language proposals must receive directional approval from EWG before proceeding to CWG for wording. Skipping this step risks approving features with incomplete specifications that compilers cannot implement correctly.

**Why It Matters**: The canonical historical example is the relaxed template template parameter matching feature, which went straight to CWG, was applied retroactively as a DR, and then proved to have fundamentally incomplete specification around partial ordering. This caused years of broken compiler implementations and workarounds. The committee has since corrected this - the current norm is that anything that even faintly resembles a feature goes through EWG first, which Matheus notes is occasionally overcorrective.

**When to Apply**: When routing a language paper through the committee process. Even defect reports with design implications should go through EWG.

**Red Flags**:
- Paper going directly to CWG without EWG review
- "It's just a bug fix" used to justify skipping evolution review
- Core wording changes that have design implications not reviewed by EWG
- DR applied retroactively without considering interaction with other features

**Supporting Experiences**: E2

<!-- METADATA
kind: principle
id: P2
source-type: explicit
category: process/actual
applies-to: language
confidence: high
supported-by: [E2]
related-principles: [P1, P9]
-->

---

### P3: Compiler Ontology Differs From Standardese Ontology

> *"The wording falls very short. Everything the compiler does is not exactly described, and has a different ontology than what the compiler does. There's difficulty in translation - the standardese ontology versus the clang ontology."*

**The Principle**: The internal model that compilers use to implement language features differs structurally from the model the standard uses to specify them. Experts in compiler implementation are not automatically experts in standard wording, and vice versa.

**Why It Matters**: The people best positioned to understand the correct behavior of complex language features (compiler implementers) face a translation burden when writing standard wording. Matheus describes writing wording that didn't express what he thought it meant, discovering the mismatch only upon review. This gap means that wording experts and implementation experts must collaborate, but they are often overloaded and available only during scheduled sessions.

**When to Apply**: When a paper author has deep implementation expertise but limited wording experience. When reviewing papers from compiler implementers. When scheduling CWG sessions for highly technical papers.

**Red Flags**:
- Paper author describes implementation behavior but wording specifies something different
- Wording that looks correct to language lawyers but produces surprising implementation requirements
- Compiler implementer working on wording without CWG expert collaboration
- Long delays between wording review sessions causing context loss

**Supporting Experiences**: E3

<!-- METADATA
kind: principle
id: P3
source-type: explicit
category: wording/pitfalls
applies-to: language
confidence: high
supported-by: [E3]
related-principles: [P9]
-->

---

### P4: Foundational Utilities Are Better as Language Features Than Library Templates

> *"A lot of basic language things like std::move are used everywhere but implemented in terms of templates. They cause a lot of overhead in code bases because templates are expensive. A lot of these things, simple enough and used a bunch, would probably be more efficient to make language features instead of library features."*

**The Principle**: Widely-used foundational utilities (std::move, std::forward, atomic operations) that are currently implemented as library templates would serve users better as language features. Language-level implementation is cheaper for the compiler, produces better error diagnostics, and eliminates unnecessary template instantiation overhead.

**Why It Matters**: Templates are expensive for compilers to process. Facilities like std::move and std::forward are used pervasively, meaning their template overhead is multiplied across every translation unit. As language features, they could be implemented more efficiently by the compiler with better user-facing error messages. Matheus fears the committee will resist making future foundational features (like wrapping/non-wrapping integer arithmetic) into language features because of a bias that "everything should be library."

**When to Apply**: When evaluating proposals for foundational, pervasive utilities. When the utility is simple enough that a language feature would be straightforward and the usage frequency justifies the compiler investment.

**Red Flags**:
- Foundational utility implemented as a template that every translation unit instantiates
- Proposal for a pervasive facility that defaults to "library" without considering language-level alternatives
- Error messages from template-based utilities that are incomprehensible to users
- Compile-time overhead from template instantiation of trivial operations

**Supporting Experiences**: E4

<!-- METADATA
kind: principle
id: P4
source-type: explicit
category: philosophy/tradeoffs
applies-to: both
confidence: medium
supported-by: [E4]
related-principles: [P5, P6]
-->

---

### P5: Templates Are Expensive and Should Be Used Judiciously

> *"Templates are really expensive on the compiler. When I was a user, I tended to write way more templates than I do now. Now I'm more mindful of that - having code bases that compile fast and are easy to understand when a problem happens."*

**The Principle**: Template instantiation is computationally expensive for compilers, and this cost is often invisible to users. Code that compiles fast and produces comprehensible errors when something goes wrong should be preferred over heavily-templatized designs when the genericity is not essential.

**Why It Matters**: Matheus went from being a heavy template user to a judicious one after gaining compiler implementation experience. The cost of templates is not just compilation time but also diagnostic quality - template errors are notoriously difficult to decipher. This perspective from inside the compiler is rarely available to language users or even to committee members evaluating proposals.

**When to Apply**: When designing library APIs that use templates, or when evaluating proposals with heavy template usage. Consider whether the template is providing essential genericity or merely syntactic convenience.

**Red Flags**:
- Templates used for minor convenience rather than essential genericity
- Library designs where compile-time cost scales poorly with usage
- No consideration of diagnostic quality in template-heavy designs
- Assumption that "more generic is always better"

**Supporting Experiences**: E4

<!-- METADATA
kind: principle
id: P5
source-type: tacit
category: philosophy/library
applies-to: both
confidence: high
supported-by: [E4]
related-principles: [P4, P6]
-->

---

### P6: Overload Resolution Is Too Complex for Anyone to Fully Understand

> *"The rules for overload resolution are really complicated and no one really understands them fully, not even in the committee - all the implications of some of the exceptions we allow. Successor languages to C++ are avoiding overload resolution, making the cases where they allow it more restricted."*

**The Principle**: C++ overload resolution rules are so complex that no individual fully understands all their implications, including committee experts. Users should avoid writing code that relies heavily on overload resolution subtleties, and the committee should be cautious about adding further exceptions or special cases.

**Why It Matters**: While overload resolution rarely causes runtime safety issues, it can produce surprising results when code relies on exception cases. Successor languages to C++ have recognized this and are restricting or avoiding overload resolution entirely. This suggests the complexity is not just an implementation challenge but a fundamental usability problem.

**When to Apply**: When designing APIs that rely on overload resolution for correctness. When evaluating proposals that add new overload resolution rules or exceptions. When writing user code that depends on subtle overload distinctions.

**Red Flags**:
- Proposal adding new special cases to overload resolution
- API design where correctness depends on subtle overload ranking
- Code that produces different results depending on which overload is selected in non-obvious ways
- Assumption that committee members fully understand overload resolution implications

**Supporting Experiences**: *(General observation from compiler implementation experience; no single story cited)*

<!-- METADATA
kind: principle
id: P6
source-type: tacit
category: philosophy/language
applies-to: language
confidence: high
supported-by: []
related-principles: [P5, P10]
-->

---

### P7: The Committee Creates More Work Than Implementers Can Absorb

> *"We have approved the linear algebra feature into the C++ standard library, but barely anyone right now is working on C++ standard library implementation. Linear algebra is a crazy amount of work for not having anyone to do it."*

**The Principle**: The committee's feature approval rate exceeds the implementation capacity of compiler and library vendors. Features approved today may not be implementable for years, and the committee should throttle its output to match what implementers can realistically absorb.

**Why It Matters**: Matheus observes from personal relationships that standard library implementation teams are understaffed. Approving large features like linear algebra when there are insufficient implementers means users will wait years for the feature to become available. The committee would be more productive holding features and shipping them when implementation capacity exists, rather than creating a growing backlog.

**When to Apply**: When evaluating whether to advance a large proposal. When planning the committee's work schedule for a standard cycle. When assessing the gap between "standardized" and "available to users."

**Red Flags**:
- Large features approved with no assessment of implementation capacity
- Growing gap between features standardized and features implemented
- Implementation teams unable to keep pace with approved features
- Assumption that approval equals availability

**Supporting Experiences**: E6

<!-- METADATA
kind: principle
id: P7
source-type: explicit
category: process/timing
applies-to: both
confidence: high
supported-by: [E6]
related-principles: [P8]
-->

---

### P8: Knowledge Degrades at Every Process Transition

> *"A lot of times I need to figure out why something in the paper or some idea was considered, and you cannot find that on the paper. Sometimes if you go to the WG21 wiki and find the transcripts you find that information, but sometimes not even then, and you have to ask the author."*

**The Principle**: Institutional knowledge about proposal rationale degrades at every process transition - from study groups to EWG to CWG. Oral rationale, satisfactorily-answered objections, and design alternatives considered are largely lost because they are not recorded in the paper itself.

**Why It Matters**: Papers typically address objections that had measurable impact on consensus (e.g., "come back after addressing these concerns"), but if a question was asked, received a satisfactory answer, and the paper proceeded, that exchange exists only in session transcripts. Transcripts are not publicly accessible. A large feature like linear algebra that spent years in the Numerics Study Group (SG6) may arrive at EWG with most of its rationale already discussed and resolved - but invisible to anyone who wasn't in those earlier sessions.

**When to Apply**: When reviewing a paper that has been through multiple working groups. When trying to understand why a design decision was made. When evaluating whether objections have been adequately addressed.

**Red Flags**:
- Paper arriving at EWG or CWG with thin rationale after extensive study group work
- Important design decisions with no recorded justification
- Reviewers raising questions that were already resolved in earlier sessions
- Assumption that the paper contains all relevant context

**Supporting Experiences**: E7

<!-- METADATA
kind: principle
id: P8
source-type: explicit
category: process/actual
applies-to: both
confidence: high
supported-by: [E7]
related-principles: [P2, P9]
-->

---

### P9: Simultaneous Sessions Separate Core Expertise From Evolution Decisions

> *"CWG has some people that are fully dedicated to CWG, they're almost never in other rooms, but they have evolutionary concerns. A lot of papers maybe go through EWG too quickly - they would have gone in better shape to core if some of these people were able to attend EWG sessions."*

**The Principle**: Because CWG and EWG sessions run simultaneously, wording experts with valuable evolutionary insights cannot participate in EWG deliberations. This structural separation means papers may pass EWG without the benefit of core expertise, arriving at CWG in worse shape than necessary.

**Why It Matters**: CWG members sometimes find issues in papers that EWG approved - issues that the paper title didn't suggest and that EWG reviewers didn't catch. Since many CWG members are volunteers donating their time, it is unreasonable to demand they attend both sessions. This is a structural problem with no easy solution, but awareness of it should inform how papers are reviewed and routed.

**When to Apply**: When scheduling papers for EWG review. When a paper has significant wording implications that would benefit from CWG input before the formal EWG vote.

**Red Flags**:
- Highly technical language paper passing EWG without any CWG member present
- CWG sending papers back to EWG for issues that could have been caught earlier
- Paper authors surprised by CWG objections on points not raised in EWG
- No mechanism for informal CWG input before formal EWG vote

**Supporting Experiences**: E3

<!-- METADATA
kind: principle
id: P9
source-type: explicit
category: groups/ewg
applies-to: language
confidence: high
supported-by: [E3]
related-principles: [P2, P3]
-->

---

### P10: C++ Concepts Do Not Provide True Template Type-Checking

> *"How easily you can write a template that's not really correct for all inputs, all types you can use it with, and how it wouldn't really be feasible to improve the language where that's not an issue anymore. Concepts don't really give you that - they help a little bit, but they're not a real solution."*

**The Principle**: C++20 concepts improve template usability but do not provide true type-checking for templates. It remains easy to write templates that are incorrect for some valid inputs, and the language offers no feasible path to full template type safety. The C++11 concept design might have provided this, but that design space is now closed.

**Why It Matters**: Users expect that if their code compiles, it is at least type-correct. Templates violate this expectation because the compiler cannot check template bodies against all possible instantiations. Concepts constrain what types can be passed to a template, but they do not verify that the template body is correct for all types satisfying the constraints. This fundamental limitation should be understood by anyone designing template-heavy APIs or evaluating template-related proposals.

**When to Apply**: When evaluating proposals that rely on concepts for correctness guarantees. When designing template APIs. When assessing whether a template library needs additional testing or validation beyond what concepts provide.

**Red Flags**:
- Assumption that concept-constrained templates are automatically correct for all satisfying types
- Template library tested only with a handful of types
- Reliance on concepts as a substitute for comprehensive testing
- Proposals claiming concepts "solve" the template type-safety problem

**Supporting Experiences**: *(General observation from compiler implementation experience; no single story cited)*

<!-- METADATA
kind: principle
id: P10
source-type: tacit
category: philosophy/language
applies-to: language
confidence: high
supported-by: []
related-principles: [P5, P6]
-->

---

### P11: First-Time Authors Should Calibrate Expectations About Committee Expertise

> *"I was like a lot of my interactions were with Richard Smith, which was one of the biggest C++ language experts, and he kind of colored my view a little bit. That made me realize I have to be more careful about assuming that just because I presented my paper and almost everyone voted for it, it was understood."*

**The Principle**: New paper authors should not assume the broader committee shares the depth of expertise of their immediate collaborators. A near-consensus vote does not necessarily indicate deep understanding of the material - it may reflect trust in the author's recognized expertise, which is a reasonable mechanism given C++'s complexity.

**Why It Matters**: Matheus frames this as a calibration problem for newcomers, not a committee deficiency. It is unreasonable to expect a committee of volunteers to be experts in every area of a language as complex as C++. People sometimes vote following the lead of someone they trust as an expert - and Matheus considers this trust-based voting better than the alternatives. But authors must still ensure their papers communicate clearly to non-experts, because CWG will later find issues that EWG's trust-based vote did not surface.

**When to Apply**: When presenting a paper for the first time. When interpreting vote results on highly technical material. When deciding how much explanatory material to include in a paper.

**Red Flags**:
- Near-unanimous vote on highly complex material with minimal discussion
- Author assuming that vote results reflect deep understanding
- Paper written for expert peers when the audience is broader
- Surprise when CWG raises issues that EWG "approved"

**Supporting Experiences**: E3

<!-- METADATA
kind: principle
id: P11
source-type: tacit
category: process/navigation
applies-to: language
confidence: high
supported-by: [E3]
related-principles: [P9]
-->

---

### P12: Implementation Experience From Trusted Maintainers Carries Weight

> *"Louis, who is the libc++ maintainer, came up and made a presentation showing his experience implementing it in libc++, and he had a lot of negative impressions. I do trust his opinion a lot on that stuff. His presentation had an impact on my vote."*

**The Principle**: Practical implementation experience from recognized compiler or library maintainers carries significant weight in committee deliberations and should be actively sought before advancing proposals with complex implementation requirements.

**Why It Matters**: In the trivial relocation debate, Louis Dionne's firsthand negative experience implementing a competing proposal in libc++ influenced votes, including Matheus's. This is the implementation analog of field experience for libraries - it provides evidence that cannot be obtained from reading the paper alone. Maintainers who have attempted implementation can identify problems that paper review cannot surface.

**When to Apply**: When evaluating proposals with significant implementation complexity. When deciding whether a feature is ready to advance. When implementation feedback contradicts the paper's claims.

**Red Flags**:
- Advancing a feature without implementation feedback from major compiler/library vendors
- Dismissing negative implementation experience as "that's just one implementation"
- Paper claiming implementation is straightforward when no implementer has confirmed this
- No implementation attempted before committee vote

**Supporting Experiences**: E5

<!-- METADATA
kind: principle
id: P12
source-type: tacit
category: evaluation/field-experience
applies-to: both
confidence: high
supported-by: [E5]
related-principles: [P7]
-->

---

## Experiences

Relatable stories that illustrate and support the principles.

### E1: N4148 - The Trivially Copyable Bug

**Context**: Around 2014, Matheus was writing a wrapper type and wanted to guarantee that if the wrapped type was trivially copyable, the wrapper would be too. During research on the std-proposals mailing list, he discovered a flaw in the standard's definition: types with deleted or inaccessible copy/move constructors and destructors could still be considered trivially copyable.

**What Happened**: Matheus wrote N4148 ("Disallowing Inaccessible Operators from Trivially Copyable") to fix this specific issue. However, the broader wrapper problem - guaranteeing that a wrapper preserves the trivial copyability of its inner type without performance regressions - remains unsolved. The paper addressed a small subset of the problem. Because Matheus could not attend committee meetings at the time, someone else carried the paper over the finish line.

**The Outcome**: Success. The fix was merged into C++17. But this was a design-level bug, not an editorial one - it required the full process (EWG review, technical vote, plenary, CWG) and could not be fixed through the editorial path alone.

**The Lesson**: Even "simple" standard defects may require the full committee process when original intent is unclear. Authors who cannot attend meetings need champions willing to present and defend their papers.

> *"Building off my work in following papers, someone else carried it over the finish line because I couldn't attend meetings at the time."*

**Supports Principles**: P1

<!-- METADATA
kind: experience
id: E1
source-type: explicit
category: history/successes
applies-to: language
outcome: success
features: [trivially-copyable, wrappers]
supports: [P1]
-->

---

### E2: P3310 - The Template Template Parameter Matching Blunder

**Context**: Before C++17, template template parameters had to match the argument template's signature exactly. James Touton proposed relaxing these rules so that if the template argument would work for the parameter in all uses, the match would be accepted - a theoretically correct extension.

**What Happened**: The proposal went straight to CWG without passing through EWG, and was applied retroactively as a defect report. When compiler implementers began implementing it, they discovered the specification completely lacked wording for how partial ordering should work with the relaxed matching rules. Compilers implemented broken workarounds. Clang put the feature behind a flag disabled by default, which prevented Clang from claiming C++17 conformance for years. Matheus eventually developed a correct solution at Bloomberg, gained deployment experience with it, and wrote P3310 to standardize the fix. James Touton later joined as co-author, contributing wording.

**The Outcome**: Mixed. The original feature was a blunder - not James Touton's fault, as it was backed by the committee at the time - that caused years of implementation pain. Matheus's fix (P3310) resolved the specification gap, but the damage from the incomplete original was long-lasting.

**The Lesson**: Skipping EWG review for language features, even ones that appear to be straightforward extensions, risks approving incomplete specifications. This historical blunder is now regularly cited as justification for the current norm that all language changes must go through EWG.

> *"People started implementing that on the compilers and realized the specification is really lacking, because we allow this extension, then a bunch of code relies on partial ordering, but the paper completely lacked any wording explaining how partial ordering works with that new feature."*

**Supports Principles**: P2, P12

<!-- METADATA
kind: experience
id: E2
source-type: explicit
category: history/failures
applies-to: language
outcome: mixed
features: [template-template-parameters, partial-ordering]
supports: [P2, P12]
-->

---

### E3: First EWG Presentation at St. Louis

**Context**: Matheus's first in-person WG21 meeting was in St. Louis in mid-2024. He presented his first paper to EWG - a long, well-explained paper on a highly technical template topic.

**What Happened**: The paper received near-consensus in EWG, with roughly 30 people voting and almost no opposition. But Matheus later realized the votes were not all high-quality - not everyone who voted deeply understood the material. When the paper reached CWG, reviewers found issues not suggested by the paper's title, including slightly related changes that people questioned whether EWG had really intended to approve. Some initial misunderstandings surfaced during the CWG session, requiring Matheus to come back a second time.

**The Outcome**: Mixed. The paper progressed but was delayed. Matheus attributes the miscalibration to his own expectations, not a committee failure. His prior interactions with Richard Smith, one of the foremost C++ language experts, had led him to overestimate the broader committee's depth of template expertise.

**The Lesson**: A near-unanimous vote on complex material may reflect trust in the author rather than deep understanding - and that trust is a reasonable mechanism, not a failure. But authors must still ensure their papers are accessible to non-experts, because downstream review (in CWG) will surface issues that trust-based EWG voting did not catch.

> *"Almost basically unanimous consensus, but that didn't mean people really understood what was going on there, and they had some difficulty later because of that."*

**Supports Principles**: P9, P11

<!-- METADATA
kind: experience
id: E3
source-type: explicit
category: process/actual
applies-to: language
outcome: mixed
features: [template-argument-deduction, partial-ordering]
supports: [P9, P11]
-->

---

### E4: The Wording Collaboration Bottleneck

**Context**: Matheus's papers address deeply technical template specification issues - areas where the original authors have retired or become inactive. His expertise is in compiler implementation, not in writing standardese.

**What Happened**: Wording experts in CWG (such as Jens Maurer) can help translate compiler-implementation knowledge into correct standard wording, but they are overloaded with other work. Matheus only receives wording feedback when his paper is scheduled for a CWG session. Between sessions - often months apart - he works on other problems, and by the time his paper comes back, the wording context is no longer fresh. This creates a cycle of slow iteration where each wording review requires re-establishing context.

**The Outcome**: Mixed. Papers progress but slowly. The gap between sessions is unhelpful for maintaining momentum on complex wording problems.

**The Lesson**: The committee has a structural bottleneck where the people who understand template behavior (compiler implementers) and the people who can write correct standardese (CWG wording experts) have limited overlap and limited interaction time. This bottleneck is especially severe for areas where the original specification authors are no longer active.

> *"There are only times really that those aspects of my paper get any help from those people - when my paper is going to be seen in a session. And then several months later, I have to come back, and things are not as fresh in my memory anymore."*

**Supports Principles**: P3

<!-- METADATA
kind: experience
id: E4
source-type: explicit
category: process/actual
applies-to: language
outcome: mixed
features: [template-specification, standardese]
supports: [P3]
-->

---

### E5: Trivial Relocation - Implementation Experience Tips the Scale

**Context**: Two competing proposals for trivial relocation were before the committee: Arthur O'Dwyer's approach (closer to existing industry practice) and Pablo Halpern's approach (more radical, aiming to avoid requiring type authors to opt in).

**What Happened**: Matheus found problems with both proposals. Arthur's paper didn't include a type-theoretically correct mechanism for the language to determine whether a type is trivially relocatable. Pablo's paper had unanswered questions and unfamiliar design choices. Louis Dionne, the libc++ maintainer, presented his experience implementing one of the approaches in libc++ and reported significant negative impressions. Matheus trusts Louis's judgment on implementation matters, and this presentation directly influenced his vote against Pablo's paper.

**The Outcome**: Mixed. Pablo's proposal was pulled from C++26. The feature remains unresolved.

**The Lesson**: Implementation experience from trusted library and compiler maintainers provides evidence that paper review alone cannot generate. When a recognized implementer reports negative experience, the committee takes it seriously - and should.

> *"Louis, who is the libc++ maintainer, came up and made a presentation showing his experience implementing it in libc++, and he had a lot of negative impressions. I do trust his opinion a lot on that stuff."*

**Supports Principles**: P12

<!-- METADATA
kind: experience
id: E5
source-type: explicit
category: history/decisions
applies-to: language
outcome: mixed
features: [trivial-relocation]
supports: [P12]
-->

---

### E6: Linear Algebra and the Implementation Capacity Gap

**Context**: The C++ standard library approved a linear algebra feature. Matheus, while not following the paper's progress through the process, observed the outcome from his position as a compiler/library-adjacent developer.

**What Happened**: Matheus notes that "barely anyone right now" is working on C++ standard library implementation, and linear algebra represents a massive amount of implementation work. He observes that users will likely wait five or more years for the feature to be available, and suggests the committee would have been more productive holding such features until implementation capacity was available rather than creating a growing backlog.

**The Outcome**: Too early to assess. The feature is standardized but implementation timeline is uncertain.

**The Lesson**: Standardization without implementation capacity creates a gap between what the standard promises and what users can access. The committee should factor implementation capacity into its scheduling decisions.

> *"Linear algebra is a crazy amount of work for not having anyone to do it. I would severely throttle down the amount of features coming in because people don't have time to implement them. You're probably only going to get them in five years."*

**Supports Principles**: P7

<!-- METADATA
kind: experience
id: E6
source-type: explicit
category: process/timing
applies-to: library
outcome: mixed
features: [linear-algebra, stdla]
supports: [P7]
-->

---

### E7: Knowledge Loss Across SG6, EWG, and CWG Transitions

**Context**: In discussing how the linear algebra proposal moved through the committee, the conversation revealed a general pattern of knowledge loss at process transitions.

**What Happened**: Matheus explains that a large feature like linear algebra spent years in the Numerics Study Group (SG6). By the time it reached EWG, much of the foundational rationale had already been debated and resolved - but none of that context was in the paper, because the authors considered those questions settled. If a reviewer at EWG didn't ask a particular question, the answer wouldn't appear anywhere. Even for questions that were asked, if the answer was satisfactory and the paper proceeded, the exchange would only be captured in session transcripts, which are not publicly accessible. Published papers typically address only objections that had measurable impact on consensus.

**The Outcome**: Mixed. The feature progressed, but the rationale trail is incomplete for anyone trying to reconstruct it later.

**The Lesson**: The committee's multi-stage process inherently degrades institutional knowledge at each transition. This is not entirely fixable - requiring volunteer authors to document every objection and answer would be counterproductive. But awareness of this pattern should inform how reviewers approach papers that have been through extensive prior review, and raises separate questions about the transparency of committee deliberations.

> *"A lot of discussions about that were probably lost in the transition from the study group to the evolution group. If people didn't really press hard on a question, the authors probably wouldn't even try to clarify it on the paper."*

**Supports Principles**: P8

<!-- METADATA
kind: experience
id: E7
source-type: explicit
category: process/actual
applies-to: both
outcome: mixed
features: [linear-algebra, process-transitions]
supports: [P8]
-->

---

### E8: Filling the Template Expertise Void

**Context**: The areas of the C++ specification dealing with template argument deduction, partial ordering, and partial template specialization were mostly specified before C++11. The experts who originally worked on them have largely retired or become very inactive in WG21.

**What Happened**: Matheus, through his work on Clang's template implementation, found himself as one of the few active committee participants with deep knowledge in these areas. He has been working on fixing long-standing specification problems in template deduction and partial ordering, but faces the dual challenge of being an implementation expert (not a wording expert) in an area where few colleagues can provide substantive review.

**The Outcome**: Ongoing. Matheus's papers are in flight but progress slowly due to the wording bottleneck and scheduling constraints.

**The Lesson**: When domain expertise concentrates in a single active participant, the committee has a bus-factor problem. Areas whose original architects have left active service become increasingly difficult to maintain and improve, especially when the specification and implementation ontologies diverge.

> *"The people that worked on that kind of stuff kind of retired or became very inactive a long time ago, and I'm kind of trying to fill that void."*

**Supports Principles**: P3, P9

<!-- METADATA
kind: experience
id: E8
source-type: explicit
category: process/actual
applies-to: language
outcome: mixed
features: [template-argument-deduction, partial-ordering, partial-specialization]
supports: [P3, P9]
-->

---

### E9: No Mentorship - Learning the Process Alone

**Context**: Matheus first engaged with WG21 in 2014 through his trivially copyable paper, and became more active when he joined Bloomberg and began attending meetings.

**What Happened**: Matheus states plainly that no one ever sat down with him to explain how the committee process works. There was no structured mentorship. He learned incrementally - a little from the 2014 paper experience, more as he started attending meetings and navigating the process for his own papers. The learning was entirely self-directed.

**The Outcome**: Mixed. Matheus eventually learned the process, but through trial and error rather than guidance.

**The Lesson**: The committee's lack of formal onboarding or mentorship means newcomers must invest significant time learning the process through experience. This raises the barrier to entry for new participants who lack the benefit of an informal mentor relationship.

> *"No one came to me to try to explain all those kinds of things at once. That kind of mentorship never happened to me. I always tried to figure out stuff on my own."*

**Supports Principles**: P11

<!-- METADATA
kind: experience
id: E9
source-type: explicit
category: process/actual
applies-to: both
outcome: mixed
features: [onboarding, mentorship]
supports: [P11]
-->

---

## Evaluation Checklists

Actionable checklists derived from principles, for evaluating proposals.

### When Reviewing Language Proposals

- [ ] Has this proposal gone through EWG before reaching CWG? (P2)
- [ ] Does the wording correctly express the intended behavior, or is there a compiler-vs-standardese ontology gap? (P3)
- [ ] Has the proposal been reviewed by at least one CWG wording expert before formal EWG vote? (P9)
- [ ] Are there implementation reports from compiler vendors? (P12)
- [ ] Does the proposal add new overload resolution rules or special cases? If so, are the implications fully analyzed? (P6)
- [ ] If this is a foundational utility, has a language-level alternative been considered versus a library template? (P4)
- [ ] Does the proposal interact with template argument deduction or partial ordering? If so, has an expert in those areas reviewed it? (P3, P10)

**Questions to Ask**:
1. "Has any compiler implemented this? What was the experience?" (P12)
2. "Does the wording match what the compiler would actually need to do?" (P3)
3. "Were there CWG members present during the EWG review?" (P9)
4. "What overload resolution interactions does this create?" (P6)
5. "Is this a defect fix or a design change? What process path does it require?" (P1)

<!-- METADATA
kind: checklist
category: evaluation/language
applies-to: language
proposal-type: feature
derived-from: [P1, P2, P3, P4, P6, P9, P10, P12]
-->

---

### When Assessing Committee Throughput and Scheduling

- [ ] Is there sufficient implementation capacity to deliver approved features within a reasonable timeframe? (P7)
- [ ] Are defect report papers being deprioritized inappropriately during shipping cycles? (P7)
- [ ] Is rationale from study group deliberations captured before the paper transitions to EWG? (P8)
- [ ] Are session transcripts available for papers with thin rationale sections? (P8)
- [ ] Does the paper's rationale section reflect only objections with consensus impact, or does it include broader context? (P8)

**Questions to Ask**:
1. "Who will implement this, and when?" (P7)
2. "What was discussed in the study group that isn't in this paper?" (P8)
3. "Is this being deprioritized because it's a DR, and is that appropriate?" (P7)

<!-- METADATA
kind: checklist
category: process/timing
applies-to: both
proposal-type: feature
derived-from: [P7, P8]
-->

---

### When Evaluating Template-Related Proposals

- [ ] Does this interact with partial ordering? Is the interaction fully specified? (P2, P10)
- [ ] Has a compiler implementer reviewed the wording for ontology alignment? (P3)
- [ ] Is the template usage essential for genericity, or could a simpler mechanism suffice? (P5)
- [ ] Are concepts being relied upon for correctness guarantees they cannot provide? (P10)
- [ ] What is the compile-time cost of the proposed template usage? (P5)

**Questions to Ask**:
1. "Has this been implemented in a compiler? Did the wording match what the implementer expected?" (P3, P12)
2. "What happens for types that satisfy the concept constraints but weren't tested?" (P10)
3. "What is the template instantiation overhead for typical usage?" (P5)

<!-- METADATA
kind: checklist
category: evaluation/language
applies-to: language
proposal-type: feature
derived-from: [P2, P3, P5, P10, P12]
-->

---

## Open Questions

1. What are the specific "tons of little issues" that still prevent writing a C++ wrapper that guarantees no performance regression relative to the wrapped type? Matheus mentioned this remains unsolved. (Ref: E1)
2. What was the C++11 concept design that might have provided true template type-checking, and why is that design space now considered closed? (Ref: P10)
3. Which successor languages to C++ is Matheus referring to when he says they are "avoiding overload resolution" or making it more restricted? What specific restrictions have they adopted? (Ref: P6)
4. What is Eric Niebler's current position on customization point objects (CPOs), and why did they fall out of favor for standardization? Matheus couldn't recall the details. (Ref: transcript discussion of ADL avoidance)
5. What specific features besides std::move and std::forward does Matheus believe should transition from library templates to language features? He mentioned wrapping/non-wrapping integer arithmetic as a future concern. (Ref: P4)
6. What is the current state of implementation staffing across major standard library vendors (libc++, libstdc++, MSVC STL)? Matheus claims severe understaffing but did not provide specifics. (Ref: P7)
7. How many active WG21 participants have deep expertise in template argument deduction and partial ordering? Is the bus-factor problem as severe as Matheus suggests? (Ref: E8)
8. What is the committee's current stance on the EWG overcorrection - requiring full EWG review for anything that "smells faintly" like a feature? Is this being reassessed? (Ref: P2)

---

## Raw Transcript Reference

- Transcript: `inputs/matheus-izvekov.md` - Remote huddle interview, January 7, 2025 (~1 hour 10 minutes)
- Corrections: `inputs/matheus-izvekov-corrections.md` - Interviewee feedback applied to this document
