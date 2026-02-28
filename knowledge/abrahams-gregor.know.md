# Dave Abrahams & Doug Gregor: Captured Knowledge

**Interview Date**: December 10, 2025
**Interviewers**: Filmed verite for documentary (Ray Nowosielski production)
**Participants**: Dave Abrahams, Doug Gregor, LuAnne Abrahams, Amy Gregor
**Duration**: ~1.5 hours
**Location**: San Jose, CA (Abrahams residence, dinner party)
**Topics Covered**: Boost origins and collaborative culture, the Concepts debacle (C++0x), committee politics, Clang development, Swift design lessons, field experience requirements, standards committee process, innovation sandboxes, Alex Stepanov's legacy, Boost as a unique open source project, backward compatibility, academia's hostility to C++

## Executive Summary

Dave Abrahams and Doug Gregor are co-architects of some of the most consequential developments in C++ and programming language design over the past 25 years. Both were early Boost contributors who shaped its collaborative culture, co-drove the Concepts proposal through WG21, built Clang, and designed core aspects of Swift. This dinner conversation - a reunion after years of personal estrangement - covers their shared trajectory from Boost's founding through the Concepts failure and into their post-committee careers.

Three dominant themes emerge. First, **innovation requires a sandbox separate from the standard**. Boost served this role for C++ by providing a space where smart people could experiment, get real user feedback, and iterate rapidly - something the committee's six-month cadence and high political stakes cannot support. Both Abrahams and Gregor view the committee's current lack of such a testing ground as a serious deficit. Second, **field experience from real users is irreplaceable**. Implementation proves a design *can* work; only pressure from actual users reveals whether it *does* work. This conviction, forged in the Boost peer-review process, was carried directly into Swift's evolution process. Third, **political fragility can destroy years of technical work**. The Concepts story - where a single co-author's last-minute withdrawal killed a proposal that had been voted into the draft standard - traumatized both participants and drove their departure from active committee work. Gregor's explicit lesson: "it's hard to personally invest in something that can go away on the whim of one person."

Gregor also contributes a key insight about the difference between library and language evolution: retrofitting an existing language with new paradigms is fundamentally harder than building from scratch, which informed his pivot from C++ committee work to building Clang and Swift.

---

## Principles

Distilled, actionable knowledge that can be applied agentically.

### P1: Standards Committees Should Enshrine Existing Practice, Not Invent

> *"Standards committees should not invent per se, they should take what is known to work well and enshrine it so everyone can build on it."*

**The Principle**: A standards committee's proper role is to codify what is already known to work well through real-world use, not to design new features from scratch during the standardization process.

**Why It Matters**: When the committee standardizes untested designs, the cost of failure is permanent. Features cannot be removed. The Concepts debacle illustrates the extreme case: even a technically sound design that had not been validated through real-world use was too fragile to survive committee politics. Abrahams notes that the committee "strays from that still quite often" and views it as a recurring source of failure.

**When to Apply**: Evaluating any proposal, but especially language features. Ask: "Has this been proven in practice outside the committee process?" If the answer is no, the proposal is inventing rather than enshrining.

**Red Flags**:
- The design is evolving significantly between committee meetings
- No implementation predates the proposal by meaningful time
- The proposal addresses a theoretical concern without demonstrated user demand
- Design decisions are being made in committee rooms rather than validated by use

**Supporting Experiences**: E1, E2, E6, E8

<!-- METADATA
kind: principle
id: P1
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E1, E2, E6, E8]
related-principles: [P2, P3, P9]
-->

---

### P2: Innovation Requires a Sandbox Outside the Standard

> *"The C++ committee of the time was not set up to innovate or try ideas like this."*

> *"With Boost not being the driving entity for the C++ standard, now they're missing that... the experimentation to build up what is the best practice before we get into the language. So it's a little bit more off the cuff design. Not as much trying it with real users."*

**The Principle**: Meaningful innovation in a language ecosystem requires an incubation space separate from the standards process - a place where designs can evolve rapidly through experimentation and user feedback without the political stakes and glacial pace of standardization.

**Why It Matters**: Boost served this role for C++ and was a major reason C++11 succeeded. The Boost peer-review culture - "here's the thing, please try it and tell me what can be better" - produced battle-tested libraries that could enter the standard with confidence. Without such a sandbox, the committee resorts to "off the cuff design" that lacks real-user validation. Gregor notes that Swift and Rust adopted nearly identical peer-review processes directly from the Boost model.

**When to Apply**: When assessing the health of a language ecosystem's evolution pipeline. Also when deciding whether to propose something directly to the committee versus incubating it externally first.

**Red Flags**:
- A proposal goes straight from author's desk to committee without external incubation
- The committee is the first venue where the design receives critical review
- There is no community of users who have iterated on the design outside the proposer's organization
- The language ecosystem lacks any equivalent of Boost's incubation role

**Supporting Experiences**: E1, E2, E6, E8

<!-- METADATA
kind: principle
id: P2
source-type: explicit
category: belongs/ecosystem
applies-to: both
confidence: high
supported-by: [E1, E2, E6, E8]
related-principles: [P1, P3, P9]
-->

---

### P3: Real Users Are the Only Reliable Validators of Design

> *"You have to get that feedback. 'Cause without that feedback loop, you can design yourself into something that doesn't make sense. Either it doesn't make sense for the user you built it for, or... you can't actually do that."*

> *"Users are the best at finding the weak points of your design."*

**The Principle**: Only feedback from real users exercising a design in production conditions can validate that a design actually works. Implementation without user feedback leads to designs that are internally consistent but practically broken.

**Why It Matters**: The Boost process demonstrated repeatedly that smart people collaborating on a design still need external pressure to find its weak points. Gregor distinguishes between having an implementation (which proves you *can* build it) and having user feedback (which proves it *works* for the people it's meant to serve). Abrahams adds that people now "show an implementation, but it hasn't been out in the world like evolving due to the pressure that you get from actual users."

**When to Apply**: Evaluating any proposal's readiness for standardization. Also during design iteration - the Boost ethos was to publish early and iterate based on feedback.

**Red Flags**:
- The only users are the design team itself
- Feedback is limited to code review rather than actual use
- The implementation exists but has never been handed to independent users
- Design changes are driven by committee discussion rather than user reports

**Supporting Experiences**: E1, E2, E5

<!-- METADATA
kind: principle
id: P3
source-type: explicit
category: evaluation/field-experience
applies-to: both
confidence: high
supported-by: [E1, E2, E5]
related-principles: [P1, P2]
-->

---

### P4: Implementability Is a Decisive Test for Language Features

> *"The more we looked at the things that Bjarne was saying should work, we kept concluding that there was no way to implement it. And implementability is a huge test in the committee. You need to be able to show that you can actually build this thing that you're gonna standardize."*

**The Principle**: A language feature that cannot be demonstrated through a working implementation should not be standardized, regardless of how appealing its design appears on paper. The ability to implement is not a secondary concern but a primary design constraint.

**Why It Matters**: The Concepts story provides a vivid illustration. Bjarne's original proposal seemed to imply things that could not be implemented. Gregor's six-month prototype in GCC proved their alternative *could* be built, which was persuasive - but the prototype nature of that implementation also became a concern when core language implementers worried about production quality. Both the positive case (demo wins support) and the negative case (implementability doubts erode support) validate this principle.

**When to Apply**: Evaluating any language feature proposal. If there is no working implementation, or if the implementation is a last-minute prototype, treat the design as unvalidated.

**Red Flags**:
- No implementation exists
- Implementation was rushed immediately before a vote
- Implementers express concern about production viability
- The specification implies behavior that no one has demonstrated working

**Supporting Experiences**: E4, E5, E6

<!-- METADATA
kind: principle
id: P4
source-type: explicit
category: evaluation/language
applies-to: language
confidence: high
supported-by: [E4, E5, E6]
related-principles: [P1, P3]
-->

---

### P5: Simplicity of Presentation Determines Committee Reception

> *"Simplicity is like totally key to getting anything through the committee."*

**The Principle**: When presenting to the committee, the way a feature is framed matters as much as its technical content. Proposals that look scary or imply hidden complexity will be rejected even if the underlying design is sound. Reframing the same design in simple, familiar terms can save it.

**Why It Matters**: Jeremy Siek saved Jaako's tuple proposal at the Santa Cruz committee meeting by recognizing that the meta-programming implications were frightening the implementers. By rewriting the specification in boring, simple terms - "it's just a typo" - he converted opposition into acceptance. Gregor credits this moment with probably helping "the Boost cause quite a lot" because the first proposals to succeed set the precedent for everything that followed.

**When to Apply**: Preparing any committee presentation or proposal paper. Also when reading the room during discussion - if reviewers seem overwhelmed, the problem may be presentation rather than design.

**Red Flags**:
- Reviewers' eyes glaze over during the presentation
- The specification reveals implementation complexity that users would never see
- The proposal uses unfamiliar jargon or advanced techniques when simpler framing exists
- The committee's concerns are about complexity rather than correctness

**Supporting Experiences**: E3

<!-- METADATA
kind: principle
id: P5
source-type: tacit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E3]
related-principles: [P10]
-->

---

### P6: One Person's Defection Can Destroy Years of Collaborative Work

> *"I knew how much effort it took to get there. And I knew it could disappear... on the whim of one person. One bad email chain."*

> *"It's hard to personally invest in something that can go away like that."*

**The Principle**: In a consensus-based committee, a single influential person withdrawing support from an already-approved feature can kill it, regardless of the years of collaborative work invested. This structural vulnerability makes large proposals inherently risky and can permanently discourage talented contributors.

**Why It Matters**: The Concepts proposal was co-authored by Gregor and Bjarne, voted into the draft standard, and merged into the 800-page document by the editor. Then Bjarne wrote a single message withdrawing support and demanding incompatible changes. The feature was ripped out entirely. This experience drove both Abrahams and Gregor away from active committee participation. Gregor explicitly identifies the moment he decided (perhaps subconsciously) that making big improvements to C++ was no longer viable.

**When to Apply**: When assessing whether to invest in a large committee proposal. When evaluating the political stability of a co-authorship arrangement. When designing governance processes for standards bodies.

**Red Flags**:
- A co-author has expressed reservations but signed off anyway
- One person holds disproportionate influence over a proposal's fate
- The proposal has been approved but key stakeholders show signs of buyer's remorse
- No formal mechanism exists to prevent unilateral withdrawal after approval

**Supporting Experiences**: E5, E6

<!-- METADATA
kind: principle
id: P6
source-type: explicit
category: process/politics
applies-to: both
confidence: high
supported-by: [E5, E6]
related-principles: [P7, P10]
-->

---

### P7: Consensus-Driven Collaboration Can Produce Great Things

> *"That process of getting the feedback and everybody working toward this goal was like another kind of validation for me that you can actually produce great things by consensus."*

> *"A whole bunch of smart people are helping you make your ideas work better. It's like no competition, it was just all focused on... we want to build the best thing that we know how to build."*

**The Principle**: When a group of motivated experts collaborates without competition, focused purely on building the best possible artifact, the results can exceed what any individual could achieve. The absence of ego and organizational rivalry is essential to this dynamic.

**Why It Matters**: Boost's early culture was one of pure collaborative discovery. Gregor describes offering up a library, receiving improvements from smart peers, and iterating - "that's the fun part." Every few months someone discovered a new C++ technique that let everyone rebuild things better. This culture produced libraries that became ubiquitous. The key ingredients were shared motivation, mutual respect, and focus on quality over credit.

**When to Apply**: When building or evaluating technical communities. When assessing whether a project's culture supports the kind of collaboration that produces great results.

**Red Flags**:
- Contributors are competing rather than collaborating
- Organizational affiliations drive technical positions
- Credit and ownership dominate over quality
- Feedback is adversarial rather than constructive

**Supporting Experiences**: E1, E2

<!-- METADATA
kind: principle
id: P7
source-type: explicit
category: philosophy/coherence
applies-to: both
confidence: high
supported-by: [E1, E2]
related-principles: [P6, P10]
-->

---

### P8: Retrofitting a Language Is Much Harder Than Building From Scratch

> *"It is much easier to build a system from scratch and keep a coherent... it is so much harder to take something that wasn't designed for it and to retrofit it with the ideas."*

**The Principle**: Adding a major new paradigm to an existing language is fundamentally harder than designing it into a new language from scratch. Backward compatibility constraints, existing idioms, and accumulated design debt all compound the difficulty.

**Why It Matters**: Gregor says their Concepts work "found ways to take the system that we built that we thought would work pretty well and actually make it work on existing code" and considers this an engineering achievement. But the difficulty of retrofitting generic programming concepts into C++ while maintaining backward compatibility was a major factor in the proposal's fragility. This experience directly informed the decision to build Swift from scratch rather than continuing to push C++ further.

**When to Apply**: When deciding whether to evolve an existing language versus create a new one. When estimating the difficulty of adding a paradigm-level feature to an established language.

**Red Flags**:
- A proposal requires pervasive changes to existing standard library sections
- Backward compatibility forces awkward compromises in the new design
- The new feature interacts poorly with existing features in unforeseen ways
- The implementation requires heroic engineering to maintain compatibility

**Supporting Experiences**: E4, E6, E7

<!-- METADATA
kind: principle
id: P8
source-type: explicit
category: philosophy/evolution
applies-to: language
confidence: high
supported-by: [E4, E6, E7]
related-principles: [P1, P11]
-->

---

### P9: Allow Deliberate Instability for Experimentation Before Stabilization

> *"One of the great things, Chris was brilliant in setting the direction for Swift to be unstable for a few years. So that we could discover what was working and what wasn't."*

> *"You need that experimentation."*

**The Principle**: A new language or major feature benefits from a deliberate period of instability where the design can evolve freely based on real usage. Premature stabilization locks in mistakes that would have been caught with more experimentation.

**Why It Matters**: Swift's early years of intentional source instability allowed the team to discover and fix design problems that would have been permanent in a standardized language. This stands in direct contrast to the Concepts experience, where the design went straight from committee approval to the draft standard without equivalent real-world shakeout. Abrahams and Gregor both view the lack of such an experimentation phase as a structural weakness of the C++ standardization process.

**When to Apply**: When introducing a major new feature or language. When designing the governance process for a new technical standard. When evaluating whether a feature is mature enough for permanent standardization.

**Red Flags**:
- A major feature is being standardized without an extended period of real-world use
- There is pressure to stabilize quickly for marketing or competitive reasons
- The design team has not had the opportunity to make breaking changes based on user feedback
- "We can fix it later" is offered as justification for known design weaknesses

**Supporting Experiences**: E6, E8

<!-- METADATA
kind: principle
id: P9
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E6, E8]
related-principles: [P1, P2, P3]
-->

---

### P10: Competing Proposals Must Be Unified Before Proceeding

> *"Now we have two competing proposals that are very different visions, and this is something we try to avoid in Boost... we try to build consensus, build toward one thing."*

**The Principle**: When two competing proposals exist for the same problem space, the committee must unify them into a single vision before proceeding. Allowing competing proposals to advance in parallel creates political fractures that can be exploited to kill both.

**Why It Matters**: The existence of two competing concepts proposals - Bjarne's and Indiana's - created a political dynamic that consumed years of effort. Gregor had to travel repeatedly to Texas A&M to negotiate a unified design with Bjarne. Even after achieving unity on paper, the underlying tensions remained and eventually destroyed the proposal. The Boost norm of "build toward one thing" exists precisely to prevent this failure mode.

**When to Apply**: When multiple proposals address the same problem space. When co-authors have fundamentally different visions for a feature's direction.

**Red Flags**:
- Two or more papers in the same space are advancing through the committee simultaneously
- Co-authors express fundamentally different motivations for the same feature
- "Unification" consists of surface-level compromise rather than genuine shared vision
- One party views the unified proposal as a tactical concession rather than genuine agreement

**Supporting Experiences**: E4, E5, E6

<!-- METADATA
kind: principle
id: P10
source-type: tacit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E4, E5, E6]
related-principles: [P6, P7]
-->

---

### P11: Backward Compatibility Is a Non-Negotiable Constraint

> *"One of the big things about C++ is backward compatibility. Existing code needs to work even if you change the language."*

**The Principle**: Any change to a standardized language must preserve backward compatibility with existing code. This constraint is not negotiable and must be treated as a first-order design requirement, not an afterthought.

**Why It Matters**: Gregor notes that the Concepts work managed to achieve backward compatibility, which he considers an engineering achievement. But this constraint also makes every language change dramatically harder and more expensive. The tension between innovation and compatibility is one of the fundamental challenges of evolving a mature standard.

**When to Apply**: Evaluating any language feature proposal. Assessing the scope and risk of proposed changes.

**Red Flags**:
- A proposal handwaves about backward compatibility
- Existing valid programs would change meaning silently
- The proposal requires an "opt-in" mechanism that fragments the language
- Backward compatibility was tested only on a narrow set of programs

**Supporting Experiences**: E4, E6

<!-- METADATA
kind: principle
id: P11
source-type: explicit
category: philosophy/evolution
applies-to: language
confidence: high
supported-by: [E4, E6]
related-principles: [P8]
-->

---

### P12: Working Demonstrations Outperform Paper Proposals

> *"No one is going to get how it changed things unless we actually had an implementation that we could show it and play with it. Because there's a difference... it's a different feel and it's hard to get that across."*

**The Principle**: A live demonstration of a working implementation is far more persuasive than any written proposal. The experience of using a feature cannot be conveyed through specification text alone.

**Why It Matters**: Gregor's live demo at Mont-Tremblant - just him with an editor, no slides - is something he considers one of the best presentations he ever gave. Multiple attendees told him it "opened their eyes" to what was possible. The flip side: Bjarne's proposal lacked a working implementation and was less convincing. However, the demo also created political fallout, illustrating that technical persuasion can be politically dangerous when it makes a competing proposal look weak.

**When to Apply**: When deciding how to present a proposal. When evaluating a proposal that exists only as text without a demonstration.

**Red Flags**:
- A proposal for a new programming paradigm or experience has no demo
- All evidence for the proposal's value is textual or theoretical
- The proposer resists requests to demonstrate the feature in action
- Committee members are asked to imagine the experience rather than witness it

**Supporting Experiences**: E5, E7

<!-- METADATA
kind: principle
id: P12
source-type: tacit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E5, E7]
related-principles: [P4, P5]
-->

---

## Experiences

Relatable stories that illustrate and support the principles.

### E1: Boost's Founding and Early Collaborative Culture

**Context**: Around 2000, Beman Dawes founded Boost with the explicit goal of incubating libraries that could eventually improve the C++ standard. C++ was struggling at the time - Java appeared to be taking over the world, and contributing to C++ "didn't look like a way to make a big dent in anything." Gregor joined as a student, drawn by the online community's enthusiasm for generic programming.

**What Happened**: The early Boost community operated without version control (tarballs on SourceForge), without formal structure, and without any sense that it would become significant. What it had was a group of motivated experts collaborating without competition. Gregor describes discovering Boost as finding "my people" - an online community that understood generic programming. Every few months someone discovered a new C++ technique, and everyone would rebuild their libraries to take advantage of it. The culture was "no competition, just all focused on building the best thing that we know how to build."

**The Outcome**: Success. Boost became ubiquitous - its license appearing in startup screens everywhere, its libraries compiled into every major operating system. Gregor now sees Boost dependencies routinely: "oh yeah, this depends on Boost. Of course it does."

**The Lesson**: When smart people collaborate without ego, focused purely on quality, and with a rapid feedback cycle, the results can far exceed anyone's expectations. The committee couldn't have produced this - it was the informal, outside-the-standard nature of Boost that enabled the innovation.

> *"A whole bunch of smart people are helping you make your ideas work better. It's like no competition, it was just all focused on... we want to build the best thing that we know how to build."*

> *"What is the secret sauce? I think a lot of it comes down to people... very smart people, they're collaborating. And it was a fun time for C++ the language because we were discovering ways to use it that hadn't been intended and hadn't been known before."*

**Supports Principles**: P1, P2, P3, P7

<!-- METADATA
kind: experience
id: E1
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [boost, generic-programming, collaborative-development]
supports: [P1, P2, P3, P7]
-->

---

### E2: TR1 - Boost's First Test of Committee Influence

**Context**: The C++ committee created a Library Technical Report process to build new standard libraries. This was Gregor's first committee meeting. He attended specifically because the committee was starting this TR process, and Boost libraries were candidates.

**What Happened**: Gregor's `function` library and Jaako's `tuple` library were among the first Boost libraries discussed for inclusion in the Technical Report. The process worked: libraries that had been incubated through Boost's peer review and field-tested by real users were evaluated by the committee and accepted. Gregor describes it as "a test for Boost in a sense - can this process work in a way that actually affects the standard?"

**The Outcome**: Success. The Technical Report included several Boost libraries, validating Beman's original vision that Boost could serve as an incubator for the standard library.

**The Lesson**: Boost's model of external incubation followed by committee standardization was effective. Libraries that arrived at the committee already proven through peer review and real-world use had a much smoother path to adoption.

> *"I feel like it was a test for Boost in a sense. Like can this process work in a way that actually affects the standard? And it did."*

**Supports Principles**: P1, P2, P3, P7

<!-- METADATA
kind: experience
id: E2
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [function, tuple, tr1]
supports: [P1, P2, P3, P7]
-->

---

### E3: The "It's Just a Typo" Story

**Context**: At the Santa Cruz committee meeting, the first two Boost libraries - Gregor's `function` and Jaako's `tuple` - were being considered for the Technical Report. Jaako's tuple proposal implied complex template meta-programming that the Boost community was comfortable with but that committee implementers found alarming.

**What Happened**: Jaako attempted to describe the meta-programming behind the tuple implementation. The committee members' eyes glazed over. Gregor watched the room turning against the proposal. Jeremy Siek read the room, intervened, and said "don't worry everyone, it's okay - it's just a typo. He actually meant to write it like this" and wrote down something "very boring and simple" that expressed the same interface without the scary internals. This reframing converted opposition into acceptance.

**The Outcome**: Success. The proposal was saved, and Gregor believes Jeremy "probably helped the Boost cause quite a lot" because succeeding with the first proposals set a precedent for everything that followed.

**The Lesson**: The committee's acceptance of a proposal depends heavily on how it is presented, not just what it contains. Implementation complexity that users will never see should be hidden from the specification. Reading the room and simplifying on the fly is a critical political skill.

> *"Jeremy correctly read the room as going sort of against Jaako's proposal and said, don't worry everyone, it's okay. It's just a typo."*

> *"Simplicity is like totally key to getting anything through the committee."*

**Supports Principles**: P5

<!-- METADATA
kind: experience
id: E3
source-type: explicit
category: process/navigation
applies-to: library
outcome: success
features: [tuple, template-metaprogramming]
supports: [P5]
-->

---

### E4: The Competing Concepts Proposals

**Context**: The Boost community and the C++ committee both wanted to add language support for generic programming (concepts). Bjarne brought a proposal at the Lillehammer meeting (~2005). The Indiana team - Gregor, Jeremy Siek, Jaako, Ron Garcia, and others at Andrew Lumsdaine's laboratory - had a fundamentally different vision grounded in generic programming theory.

**What Happened**: Bjarne's proposal seemed to start from syntactic sugar - making things look nice - rather than from the fundamental principles of generic programming. To Abrahams and others, "the fundamentals aren't there." The Indiana team developed an alternative proposal with a working implementation in GCC. This created a politically dangerous situation: two competing proposals from two of the most prominent groups in the C++ world. The committee spent three to four years trying to unify the visions, with Gregor traveling repeatedly to Texas A&M to negotiate with Bjarne.

**The Outcome**: Mixed. The collaboration produced a design that Gregor considers technically excellent - it bridged both visions and achieved backward compatibility. But the political cost was enormous, and the underlying tensions were never fully resolved.

**The Lesson**: Starting from fundamentals versus starting from syntax leads to very different designs. When prominent figures hold incompatible visions, the unification process consumes extraordinary effort and may leave unresolved tensions that surface later.

> *"We had very different ideas of how to approach it."*

> *"His proposal seemed to start with... the most sugary and palatable way to express these ideas. And to a lot of us it seemed like the fundamentals aren't there."*

**Supports Principles**: P4, P8, P10, P11

<!-- METADATA
kind: experience
id: E4
source-type: explicit
category: history/failures
applies-to: language
outcome: mixed
features: [concepts]
supports: [P4, P8, P10, P11]
-->

---

### E5: Doug's Live Concepts Demo at Mont-Tremblant

**Context**: Six months after the competing proposals appeared at Lillehammer, the committee met in Mont-Tremblant, Canada. The Indiana team had realized that "no one is going to get how it changed things unless we actually had an implementation that we could show and play with."

**What Happened**: Gregor gave a live demo - just him with an editor projecting on screen, no slides. He walked through the process of doing generic programming with their concepts implementation helping the programmer along the way, building up from a concrete algorithm to finding the abstractions. Multiple attendees said it "opened their eyes" to what was possible. But Bjarne "got extremely upset at this demonstration" - he felt disrespected because the working demo implicitly highlighted that his own proposal lacked an implementation. The Indiana team had to hold an emergency huddle to manage the political fallout, ultimately offering an apology even though "we all thought we hadn't done anything disrespectful."

**The Outcome**: Mixed. Technically, the demo was a landmark - Gregor considers it one of the best presentations he ever gave. Politically, it created a crisis that colored the entire multi-year collaboration that followed.

**The Lesson**: A working demonstration is the most powerful form of technical persuasion, but it can also be the most politically dangerous. When a demo implicitly diminishes a competing proposal from a powerful figure, the technical victory may be offset by political damage. Managing the human dynamics is as important as getting the technology right.

> *"I feel like that was one of the best presentations I've ever given. It was very, you know, just very chill with an editor. There were no slides. There was no big statements. Just like, here's the experience."*

> *"Bjarne got extremely upset at this demonstration... it was clear that he felt disrespected."*

**Supports Principles**: P4, P6, P10, P12

<!-- METADATA
kind: experience
id: E5
source-type: explicit
category: history/failures
applies-to: language
outcome: mixed
features: [concepts]
supports: [P4, P6, P10, P12]
-->

---

### E6: Bjarne's Last-Minute Withdrawal Kills Concepts

**Context**: After years of collaboration between Gregor and Bjarne, the unified Concepts proposal - covering both language changes and extensive standard library updates - was voted into the C++ draft standard around 2008. Pete Becker, the editor, merged over 100 pages of changes into the 800-page document. Additional features like range-based for had been designed on top of Concepts.

**What Happened**: Just before the Frankfurt committee meeting, Bjarne wrote a message to the committee saying he could no longer support the proposal. He demanded changes that were incompatible with the existing design - reverting toward his original vision. Abrahams characterizes it: "he had been pushed by reality about what was possible and what would work into this position that he just couldn't stand." Gregor made a "half-hearted attempt" to defend the design but knew immediately "there was no saving it." The feature was removed from the draft standard. Pete Becker had to unwind all the changes. Features built on top of Concepts, like range-based for, had to be redesigned without them.

**The Outcome**: Failure. Years of work by dozens of people were destroyed. Both Abrahams and Gregor describe this as "heartbreaking." Gregor decided - perhaps subconsciously - that making big improvements to C++ was no longer viable. Abrahams went to "a couple more meetings" but was already "looking elsewhere." Both pivoted away from committee work toward building Clang and Swift.

**The Lesson**: A consensus process with no mechanism to prevent unilateral withdrawal after approval is structurally fragile. The larger the investment in a proposal, the more devastating the loss when political support collapses. This fragility acts as a deterrent against ambitious proposals, which may explain why the committee now tends toward smaller, incremental changes.

> *"That one person could, after having signed off on this thing all the way through, then kill such a significant and useful thing... that sort of turned me off."*

> *"I knew how much effort it took to get there. And I knew it could disappear on the whim of one person. One bad email chain. And it's hard to personally invest in something that can go away like that."*

**Supports Principles**: P1, P2, P4, P6, P8, P9, P10, P11

<!-- METADATA
kind: experience
id: E6
source-type: explicit
category: history/failures
applies-to: language
outcome: failure
features: [concepts, range-for]
supports: [P1, P2, P4, P6, P8, P9, P10, P11]
-->

---

### E7: Clang Compiles Boost in 18 Months

**Context**: After the Concepts debacle, Gregor shifted from being a user of C++ to being an implementer. He wanted to build a new implementation of C++ that could "do a better job of evaluating that machine."

**What Happened**: Gregor led the development of Clang's C++ support, going from zero C++ capability to compiling Boost in approximately 18 months. "That was the gold standard benchmark" - because Boost "uses every single one" of the weird template tricks that only a faithful implementation of the standard would support. Abrahams considers the impact of Clang "easily as big as Boost itself."

**The Outcome**: Success. Clang became one of the most widely used C++ compilers and Gregor's work on it led to his role at Apple building Swift.

**The Lesson**: When you need to prove that something works, pick the hardest possible benchmark. Boost compilation was the acid test for C++ compilers precisely because it exercised the most obscure corners of the language. This is another manifestation of the principle that implementation validates design.

> *"We went from, it doesn't do any C++ to it compiles Boost in 18 months. And that was the gold standard benchmark."*

**Supports Principles**: P4, P8, P12

<!-- METADATA
kind: experience
id: E7
source-type: explicit
category: history/successes
applies-to: language
outcome: success
features: [clang, boost]
supports: [P4, P8, P12]
-->

---

### E8: Swift's Evolution Process Modeled on Boost

**Context**: When designing the governance process for Swift's evolution, Gregor asked Abrahams what they should do. Swift also had a deliberate period of source instability in its early years.

**What Happened**: Abrahams said: "Boost did it. Let's just do it again." The Swift evolution process was built as a near-exact replica of the Boost peer-review process: a review manager runs each review, there is a formal review period with community feedback, and then a decision is made on the final proposal. Gregor confirms: "the process is almost exactly the same." Additionally, Chris Lattner set the direction for Swift to be source-unstable for several years, allowing the team to discover and fix design problems through real usage.

**The Outcome**: Success. Swift's evolution process is widely regarded as well-functioning, and the instability period allowed major design improvements (like the removal of C-style for loops and the redesign of the access control model) that would have been impossible in a stabilized language.

**The Lesson**: Successful governance processes can be transplanted across communities. The Boost model of peer review with real user feedback is language-agnostic. Deliberate instability, while painful for early adopters, produces dramatically better long-term designs.

> *"I remember when you asked me what we should do about the process for Swift, and I was like, Boost did it. Let's just do it again."*

> *"One of the great things, Chris was brilliant in setting the direction for Swift to be unstable for a few years."*

**Supports Principles**: P1, P2, P3, P9

<!-- METADATA
kind: experience
id: E8
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [swift, boost, evolution-process]
supports: [P1, P2, P3, P9]
-->

---

### E9: Alex Stepanov's Sense of Failure

**Context**: Alex Stepanov, the inventor of generic programming and the STL, retired and asked visitors not to talk about programming. Abrahams and Gregor both visited him over the years.

**What Happened**: Despite having influenced an entire generation of programmers, Stepanov feels his "experiment was a failure." His vision was "large catalogs of reusable, well-documented generic components" - and this never materialized at the scale he envisioned. Even the Swift Standard Library couldn't approach this goal due to binary size constraints. Gregor describes visiting Stepanov and him eventually starting to talk about "programming and his legacy," which made Gregor sad because "he's influenced so many of us that have made an impact on the industry." Recently, Stepanov showed unexpected openness to giving a talk again when David Sankel asked.

**The Outcome**: Mixed. Stepanov's influence is vast and undeniable - Boost, Clang, Swift, and modern C++ all carry his intellectual DNA. But by his own measure, the vision remains unfulfilled.

**The Lesson**: Visionaries often judge themselves by the gap between their vision and reality, while the rest of the world judges them by how much they moved the needle. Impact that seems indirect or incomplete to the originator may be transformative when viewed from the outside.

> *"He feels like his experiment was a failure. His vision was large catalogs of reusable, well-documented generic components."*

> *"He's influenced so many of us that have made an impact on the industry."*

**Supports Principles**: P7

<!-- METADATA
kind: experience
id: E9
source-type: tacit
category: history/regrets
applies-to: both
outcome: mixed
features: [stl, generic-programming]
supports: [P7]
-->

---

### E10: Academia's Hostility to C++ and Bjarne's Isolation

**Context**: Abrahams sets the stage for the Concepts story by explaining Bjarne Stroustrup's career-long position.

**What Happened**: Bjarne does not have a Turing Award despite C++ being more influential than languages whose creators did receive one (Niklaus Wirth for Pascal). Two factors explain this: (1) Academia hates C++ because it is "unclean and inelegant" - it grew organically from C, lacks a formal theoretical foundation, and bears no resemblance to the mathematically pure functional languages that academics prefer. (2) As a result, Bjarne has spent much of his career feeling "under assault from all sides" and not recognized for his contribution - which sometimes leads him to misidentify allies as adversaries.

**The Outcome**: This context is essential for understanding why Bjarne reacted so strongly to the competing Concepts proposal and ultimately withdrew support. His sensitivity was not arbitrary - it was shaped by decades of feeling besieged.

**The Lesson**: Understanding a key stakeholder's broader context - their career frustrations, their sense of recognition, their history of conflict - is essential for navigating committee politics. Technical disagreements do not occur in a vacuum; they are colored by the personal histories of the participants.

> *"Bjarne for a lot of his career has felt like under assault from all sides. And not recognized for his contribution. And sometimes I think he doesn't realize who his allies are."*

> *"C++ is an extremely practical language. It started with C and was grown organically. For academics who like pure functional programming that looks like a direct expression of mathematics, C++ is nothing like that."*

**Supports Principles**: P6, P10

<!-- METADATA
kind: experience
id: E10
source-type: explicit
category: groups/ewg
applies-to: both
outcome: mixed
features: [c++, concepts, committee-politics]
supports: [P6, P10]
-->

---

### E11: Boost as a Unique Open Source Project

**Context**: Amy Gregor asked whether other groups had tried to do what Boost did. Abrahams reflected on Boost's uniqueness.

**What Happened**: Abrahams realized that Boost was a "completely unique" open source project: one that existed specifically to support another project (the C++ standard). It was not a product in itself - it was an incubation pipeline for the standard library. This grassroots origin (Beman started it outside the committee, not as a committee subgroup) was key to its effectiveness, because the standard needed to be stable while Boost could move fast. Gregor observes that modern languages (Swift, Rust, Python) have adopted nearly identical peer-review processes, but they don't need a separate Boost-like entity because they have lighter-weight governance structures. The C++ committee's uniquely heavy ISO process is what created the need for Boost in the first place.

**The Outcome**: The insight explains both why Boost was necessary and why it hasn't been replicated: most modern languages have internalized the Boost model into their standard evolution process.

**The Lesson**: When a standards process is too rigid for innovation, the ecosystem will self-organize to fill the gap. The specific form of that self-organization depends on the governance structure. Heavy ISO processes create the need for external incubators; lighter-weight processes can incorporate experimentation directly.

> *"The idea that we existed to support some other project, the project of C++. That's a completely unique thing."*

> *"I wonder if partly this hasn't been replicated because most languages don't have the same kind of international standards committee of many, many people making decisions for them."*

**Supports Principles**: P2, P9

<!-- METADATA
kind: experience
id: E11
source-type: tacit
category: history/successes
applies-to: both
outcome: success
features: [boost, open-source, standards-process]
supports: [P2, P9]
-->

---

### E12: The Pivot from Libraries to Language Features

**Context**: The Boost community started by building libraries. Over time, they realized the language itself needed to change to support their library-building activities.

**What Happened**: Gregor describes an "interesting inflection point" where Boost contributors pivoted from writing libraries to writing language proposals. Abrahams worked on move semantics. Gregor worked on variadic templates. Eventually they arrived at the "grand goal" of Concepts - a massive language change to support generic programming natively. This pivot changed the nature of the work: library proposals could be validated through Boost's existing incubation process, but language proposals had no equivalent sandbox. The six-month committee cycle and the impossibility of shipping a modified C++ compiler to real users meant the feedback loop that made Boost successful was broken.

**The Outcome**: Mixed. Individual language features (move semantics, variadic templates) succeeded. The grand goal of Concepts failed. The pivot exposed a fundamental gap: the ecosystem had an incubation process for libraries but not for language features.

**The Lesson**: The processes that work for library evolution do not automatically work for language evolution. Language changes require compiler modifications, which raises the bar for experimentation dramatically. This asymmetry means language proposals are inherently riskier and less validated than library proposals.

> *"Many of us that were involved in Boost and on the committee, we pivoted. We started writing language proposals... And we had this grand goal of, well, let's do generic programming, this massive task."*

**Supports Principles**: P1, P2, P4

<!-- METADATA
kind: experience
id: E12
source-type: implicit
category: history/evolution
applies-to: both
outcome: mixed
features: [move-semantics, variadic-templates, concepts]
supports: [P1, P2, P4]
-->

---

## Evaluation Checklists

Actionable checklists derived from principles, for evaluating proposals.

### When Reviewing Language Proposals

- [ ] Has this been proven through real-world use outside the committee process? (P1)
- [ ] Is there a working implementation that predates this proposal? (P4)
- [ ] Has the implementation been used by people outside the proposer's organization? (P3)
- [ ] Is the proposal enshrining existing practice or inventing something new? (P1)
- [ ] Does the proposal maintain full backward compatibility with existing code? (P11)
- [ ] Have implementers confirmed they can build this in production quality? (P4)
- [ ] Is there a single unified vision, or are there competing proposals? (P10)
- [ ] Has there been a deliberate experimentation period before standardization? (P9)

**Questions to Ask**:
1. "Has this been incubated outside the committee? Where?" (P2)
2. "Who has used this implementation, and what problems did they find?" (P3)
3. "If we standardize this and discover a design flaw, what is our recourse?" (P9)
4. "Do all co-authors genuinely agree on the direction, or is this a political compromise?" (P10)
5. "Can you demo this live?" (P12)

<!-- METADATA
kind: checklist
category: evaluation/language
applies-to: language
proposal-type: feature
derived-from: [P1, P3, P4, P9, P10, P11, P12]
-->

---

### When Reviewing Library Proposals

- [ ] Has this been field-tested by independent users? (P3)
- [ ] Is this enshrining existing practice or designing something new? (P1)
- [ ] Was the library incubated through a process with peer review and user feedback? (P2)
- [ ] Can the proposal articulate what was previously impossible or impractical? (P1)
- [ ] Is the presentation accessible to committee members who are not domain experts? (P5)
- [ ] Are there competing proposals that need to be unified first? (P10)

**Questions to Ask**:
1. "How long has this library been available for public use?" (P3)
2. "Who outside your organization has used this, and what was their feedback?" (P3)
3. "Was this incubated in Boost or an equivalent community?" (P2)
4. "If I'm an implementer unfamiliar with the domain, can I understand this specification?" (P5)

<!-- METADATA
kind: checklist
category: evaluation/library
applies-to: library
proposal-type: feature
derived-from: [P1, P2, P3, P5, P10]
-->

---

### When Navigating Committee Politics

- [ ] Have you identified all key stakeholders and their concerns? (P6, P10)
- [ ] Do you understand the personal and career context of potential opponents? (E10)
- [ ] Is your presentation framed in the simplest possible terms? (P5)
- [ ] Do you have a working demonstration, and have you considered whether it might embarrass someone? (P12, E5)
- [ ] Are all co-authors genuinely aligned, not just tactically cooperating? (P10)
- [ ] Is there a fallback plan if a key supporter withdraws? (P6)

**Questions to Ask**:
1. "Does anyone feel their work is being diminished by this proposal?"
2. "Have we achieved genuine consensus or merely suppressed disagreement?"
3. "If the most influential person in the room changes their mind tomorrow, does this survive?"

<!-- METADATA
kind: checklist
category: process/politics
applies-to: both
proposal-type: feature
derived-from: [P5, P6, P10, P12]
-->

---

## Open Questions

1. What specifically was the technical change Bjarne demanded in the Frankfurt email that killed Concepts? Neither Abrahams nor Gregor names it explicitly, though Abrahams describes it as reflecting Bjarne's "original kind of desires" and being "incompatible with the state of the proposal."

2. What were the elements of Bjarne's original Lillehammer proposal that the Indiana team believed "there was no way to implement"? The specific technical issues are not named.

3. What exactly was the "is_edible" (SFINAE) technique that may have been invented in a hot tub at a conference? The attribution and circumstances are uncertain even to the participants.

4. What is the list of Boost libraries that Abrahams and Gregor consider the most successful examples of the incubation-to-standard pipeline? They reference TR1 but don't enumerate specifics beyond function and tuple.

5. How has the committee's behavior changed in the years since the Concepts debacle? Both participants imply it has gotten worse ("not as much trying it with real users," "more off the cuff design") but neither provides specific contemporary examples.

6. What would a modern equivalent of Boost's incubation role look like for C++ language features (as opposed to libraries)? The transcript identifies the gap but does not propose solutions.

7. Gregor mentions that what C++ "ended up with" for concepts "didn't make the experience better for generic programmers." What specifically does C++20 Concepts lack compared to the original Gregor-Bjarne proposal?

---

## Raw Transcript Reference

Source: `inputs/abrahams-gregor.md`
Video: https://vimeo.com/1152624358/b5b24d2896
Filmed: 2025-12-10, San Jose CA (verite documentary footage)
