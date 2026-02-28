# Dave Abrahams: Captured Knowledge

**Interview Date**: December 19, 2025
**Interviewer**: Ray Nowosielski
**Duration**: ~3 hours
**Topics Covered**: Boost origins and mission, STL and generic programming, exception safety in C++98, Beman Dawes and leadership, consensus-based processes, peer review, BoostCon/CppNow, Boost Software License, C++ committee dysfunction, concepts debacle, language evolution principles, Apple/Swift transition, Boost governance, libraries as infrastructure, object-oriented programming failures

## Executive Summary

Dave Abrahams is a co-founder of Boost, creator of BoostCon (now CppNow), pioneer of exception safety theory for C++98, and later a principal designer on Apple's Swift language. His perspective is shaped by having experienced the full arc of Boost from inception to governance transition, having successfully championed exception safety through WG21 as a non-member, and having ultimately left C++ for Swift when he concluded the committee could not evolve the language coherently.

Three dominant themes emerge. First, **libraries are the primary vehicle for empowering programmers**: they eliminate incidental complexity, provide design paradigms that remove decision-making burden, and let domain experts focus on their actual domain. Dave discovered this viscerally while building music notation software and encountering the STL. Second, **consensus-based processes can accomplish great things when led well**: Beman Dawes' inclusive, patient, non-partisan leadership in LWG and Boost created an environment where the best ideas emerged regardless of who proposed them, and Dave's own exception safety work succeeded entirely through consensus-building without ever having a formal vote. Third, **the inability to agree on principles dooms a standards body**: Dave's failed attempt to get WG21 to adopt evolution principles, followed by Google's identical failure, convinced him that the committee was structurally unable to make the decisions C++ needed, leading directly to his departure for Swift.

Dave also provides unique first-person accounts of Boost's founding rationale (creating existing practice for standardization), the design philosophy behind BoostCon (modeled on the Aspen Center for Physics), and the recent governance controversy around the boost.org domain acquisition.

---

## Principles

Distilled, actionable knowledge that can be applied agentically.

### P1: Libraries Empower Programmers by Eliminating Incidental Complexity

> *"Every time they have to go on an excursion to build an algorithm that is standard or a data structure or some other component that is outside their domain of expertise, they're doing something that there's economic pressure on them not to give it the attention it deserves. And for which they don't have the same chops. Somebody else should be doing that."*

**The Principle**: The core value of libraries is enabling domain experts to focus on their actual expertise by providing rigorously designed, documented, and tested components for standard problems that would otherwise consume their time and produce inferior results.

**Why It Matters**: Professional programmers are paid to develop expertise in their product domain. Every hour spent writing binary search, designing container interfaces, or inventing parameter-passing conventions is an hour stolen from that domain - and the results will be worse than what a specialist would produce. Libraries solve this by putting the right experts on the right problems.

**When to Apply**: Evaluating whether a library proposal addresses a genuine need. Ask: "Is this something domain experts are currently forced to build themselves, poorly?"

**Red Flags**:
- Programmers in the target domain already have adequate solutions
- The library addresses a problem that domain experts would naturally get right
- No evidence that the target audience is currently suffering from the lack

**Supporting Experiences**: E1, E9

<!-- METADATA
kind: principle
id: P1
source-type: explicit
category: belongs/library
applies-to: library
confidence: high
supported-by: [E1, E9]
related-principles: [P4, P11]
-->

---

### P2: Standardize Existing Practice

> *"There's a principle that is supposed to be followed or was supposed to be followed called standardize existing practice. The idea is, let's only make standard the things that are actually out there in use that have a track record and who's, you know, that we can evaluate in terms of how they actually worked in the real world."*

**The Principle**: Standardize only what is already in use, has a track record, and can be evaluated based on real-world results. Beman Dawes created Boost specifically to solve the supply-side of this principle for future C++ standards.

**Why It Matters**: Standardizing unproven designs risks permanent adoption of features that don't work in practice. The committee had already created a "black eye" by standardizing template features for the STL before any compiler supported them, resulting in years of lag before vendors caught up. Existing practice provides evidence that something can be implemented, is economical for vendors, and actually solves users' problems.

**When to Apply**: Evaluating any proposal for standardization. The question is not "is this a good design?" but "has this design been proven in the field?"

**Red Flags**:
- No implementation predating the proposal by significant time
- The design was invented during standardization rather than proven beforehand
- Compiler vendors have not demonstrated they can implement the feature
- The feature requires mechanisms that don't yet exist in practice

**Supporting Experiences**: E2, E6

<!-- METADATA
kind: principle
id: P2
source-type: explicit
category: evaluation/field-experience
applies-to: both
confidence: high
supported-by: [E2, E6]
related-principles: [P1, P10]
-->

---

### P3: Consensus-Based Processes Can Accomplish Great Things

> *"What the committee demonstrated for me at that time was contrary to what a lot of people say about design by committee and thinking of it as a bureaucracy, that you can actually accomplish great things by consensus."*

> *"That was another piece of evidence that you really can get great things done by consensus. Just by working with people to help them understand and talking, maybe you're even arguing, but you're arguing in a way that doesn't alienate them."*

**The Principle**: Genuine consensus-based decision-making, where stakeholders are heard and arguments serve understanding rather than dominance, can produce results superior to top-down or majority-rule approaches. The key is leadership that creates an environment of respect and inclusion.

**Why It Matters**: Technical communities often dismiss "design by committee" as inherently producing mediocrity. Dave's experience with Boost and WG21 demonstrates the opposite is possible when the process is run well. His exception safety work was adopted into C++98 entirely through persuasion - he never had a vote. Boost's peer review process achieved the same quality through the same mechanism.

**When to Apply**: Designing governance structures, review processes, or decision-making frameworks for technical communities. Also when evaluating whether a consensus-based process is functioning properly.

**Red Flags**:
- Decisions driven by voting blocs rather than argument quality
- Leaders who are partisan rather than moderating
- Participants who argue to win rather than to discover
- Individuals excluded from contributing despite having relevant expertise

**Supporting Experiences**: E3, E4, E5

<!-- METADATA
kind: principle
id: P3
source-type: explicit
category: process/navigation
applies-to: both
confidence: high
supported-by: [E3, E4, E5]
related-principles: [P5, P6]
-->

---

### P4: Good Libraries Reduce Decision-Making Burden

> *"It takes an element of decision making away from a programmer... The benefit of having had the STL take away things I had to consider from me, even what kind of design decisions I was gonna make in my own code, if I had an example, that completely changed the productivity landscape for me."*

**The Principle**: Beyond providing code, a well-designed library provides a paradigm - a set of conventions and idioms - that eliminates design decisions programmers should not have to make. Once iterators exist as a paradigm, no one needs to decide how to pass elements to an algorithm.

**Why It Matters**: Design decisions are costly. Every decision a programmer must make is a potential error, a consumed unit of attention, and a source of inconsistency across a codebase. When a library establishes a paradigm (iterators, ranges, concepts), it removes entire categories of decision from downstream programmers, multiplying productivity beyond what the code itself provides.

**When to Apply**: Evaluating library designs. Ask not just "does this provide useful functionality?" but "does this establish a paradigm that eliminates decisions for users?"

**Red Flags**:
- A library that provides code but no clear paradigm for extension
- Multiple inconsistent ways to accomplish the same task
- Users still need to make arbitrary design decisions when using the library

**Supporting Experiences**: E1

<!-- METADATA
kind: principle
id: P4
source-type: explicit
category: philosophy/library
applies-to: library
confidence: high
supported-by: [E1]
related-principles: [P1, P9]
-->

---

### P5: Leadership Must Be Inclusive and Non-Partisan

> *"What really super impressed me was this kind of ecumenical way that Beman ran the meeting where everybody's input was valued. He was patient and non-partisan and the meeting itself, the process that they had was extremely consensus based."*

**The Principle**: Effective technical leadership creates an environment where all contributions are valued, the leader moderates rather than advocates, and the process seeks genuine consensus rather than manufactured agreement. Beman Dawes' style in LWG became the model for Boost's peer review process.

**Why It Matters**: When leaders advocate for particular outcomes, participants optimize for persuading the leader rather than discovering the best solution. When all input is genuinely valued, the best ideas emerge regardless of their source. Dave, as a non-member at his first meeting, was able to contribute valuable insights because Beman created this environment. This same principle made Boost's review process "work really well for a long time."

**When to Apply**: Selecting review managers, working group chairs, or process moderators. The key qualification is temperament and fairness, not technical expertise.

**Red Flags**:
- A review manager who advocates for or against acceptance
- A chair who cuts off certain participants while favoring others
- Decisions that reflect the leader's preference rather than group consensus
- Non-members or newcomers who are excluded from contributing

**Supporting Experiences**: E3, E5

<!-- METADATA
kind: principle
id: P5
source-type: explicit
category: process/actual
applies-to: both
confidence: high
supported-by: [E3, E5]
related-principles: [P3, P6]
-->

---

### P6: Review Managers Moderate Consensus, Not Adjudicate Technically

> *"Their main role had nothing to do with their technical ability. It was to do that thing that Beman did in library working group meetings, which was to moderate the discussion, to help make sure that all arguments are heard. And then at the end it would be up to them to decide whether it was accepted or not. But they would be deciding, they would be ruling on what the consensus had been."*

**The Principle**: A review manager's primary qualification is the ability to moderate discussion fairly and assess consensus accurately. They rule on what the consensus was, not on what the technical answer should be. Technical ability is secondary to temperament.

**Why It Matters**: Conflating the moderator role with the technical authority role corrupts the process. If the review manager is also the leading technical voice, participants will either defer to their judgment or resist it, either way distorting the consensus signal. Separating moderation from advocacy is what made Boost's review process function.

**When to Apply**: Selecting review managers for Boost or any peer review process. Also when designing review processes from scratch.

**Red Flags**:
- A review manager who is the proposal author's main technical collaborator
- A manager who writes extensive technical critiques during the review they moderate
- Decisions announced that contradict the clear weight of review feedback
- Managers selected primarily for domain expertise rather than moderation ability

**Supporting Experiences**: E5

<!-- METADATA
kind: principle
id: P6
source-type: explicit
category: process/actual
applies-to: library
confidence: high
supported-by: [E5]
related-principles: [P3, P5]
-->

---

### P7: Generic Programming Succeeds Where Object Orientation Failed

> *"During, for thirty years during the object oriented programming revolution, people did not focus on algorithms. They thought of programming as wiring together loosely coupled components that would send each other messages. And somehow out of this big web of connected components, you would get something that functions right."*

> *"Object orientation - one of the main promises was you'd get better code reuse, but object oriented programming didn't really deliver on its promises of code reuse."*

**The Principle**: Object-oriented programming's promise of code reuse through inheritance hierarchies and message-passing was fundamentally flawed. Generic programming, which focuses on algorithms operating over abstract types defined by their properties (concepts), delivers what OOP promised by enabling true separation of algorithms from data structures.

**Why It Matters**: The OOP paradigm dominated software engineering for decades and still influences library design. Understanding why it failed at code reuse - its intrusive nature, inability to freely combine parts, and creation of "incidental algorithms" hidden in message-passing webs - is essential to avoiding the same mistakes. The STL demonstrated the alternative: algorithms as first-class citizens, parameterized by concepts.

**When to Apply**: Evaluating library designs that rely heavily on inheritance hierarchies or virtual dispatch for extensibility. Also when assessing whether a proposal's architecture is fundamentally sound.

**Red Flags**:
- Deep inheritance hierarchies as the primary extension mechanism
- Algorithms hidden in message-passing chains across objects
- Components that cannot be freely composed without modification
- "Everything is an Object" base class designs

**Supporting Experiences**: E1, E8

<!-- METADATA
kind: principle
id: P7
source-type: explicit
category: philosophy/library
applies-to: both
confidence: high
supported-by: [E1, E8]
related-principles: [P4, P9]
-->

---

### P8: Minimize Wording Changes When Modifying the Standard

> *"One of the big concerns that the committee had about accepting changes for exception safety is how many actual words would need to change in the standard. Because you had these working groups that did issue processing so that there was a large web of connected things in the standard that all were mutually consistent."*

**The Principle**: When proposing changes to the standard, minimize the scope of wording modifications. The standard is a web of interconnected, mutually consistent statements; large-scale changes are difficult to evaluate for unintended consequences, just as large code diffs are hard to review.

**Why It Matters**: Dave's exception safety work only succeeded because Greg Colvin helped him find ways to minimize the wording footprint. The committee is rightly conservative about large wording changes because they can introduce subtle inconsistencies that take years to discover. Small, surgical changes are easier to evaluate, more likely to be accepted, and less likely to introduce defects.

**When to Apply**: Drafting wording for any standards proposal. Also when deciding how to structure a proposal that requires broad changes - consider whether it can be decomposed into smaller, independently evaluable pieces.

**Red Flags**:
- A proposal that touches wording across many sections of the standard
- Wording changes that require understanding the entire standard to evaluate
- No effort to factor changes into independently evaluable increments
- Changes that could break existing consistency guarantees

**Supporting Experiences**: E4

<!-- METADATA
kind: principle
id: P8
source-type: explicit
category: wording/quality
applies-to: both
confidence: high
supported-by: [E4]
related-principles: [P2]
-->

---

### P9: Algorithms Are the Core of Programming

> *"Algorithm is a big, fancy word, but all it means is program. An algorithm is a method for accomplishing something... the foundational thing Alex is always gonna come back to is it's about the algorithms."*

> *"If you think about what computers do, they compute. That's in the name. The computation of these giant webs is hidden. It's obscured."*

**The Principle**: Algorithms - explicit, readable, locally reasonable computations - are the core of what computers do. Any design that hides computation in implicit message-passing, callback chains, or distributed object interactions obscures the essential work and makes programs harder to understand, optimize, and verify.

**Why It Matters**: Sean Parent's observation about "incidental algorithms" - the hidden computation that emerges from object-oriented message-passing webs - captures why OOP-heavy designs are so hard to reason about. Making algorithms explicit and central is not merely an aesthetic preference; it is a prerequisite for local reasoning, efficiency, and correctness.

**When to Apply**: Evaluating any library design. Ask: "Can I read the algorithm that accomplishes the user's goal in one place, or is it spread across multiple objects and callbacks?"

**Red Flags**:
- Control flow spread across multiple objects via virtual dispatch
- Algorithms that can only be understood by tracing message-passing chains
- Performance costs hidden in abstraction layers
- Code where "what happens when I call this function" requires global analysis

**Supporting Experiences**: E1, E8

<!-- METADATA
kind: principle
id: P9
source-type: explicit
category: philosophy/library
applies-to: both
confidence: high
supported-by: [E1, E8]
related-principles: [P4, P7]
-->

---

### P10: Permissive Licensing Maximizes Adoption for Standardization

> *"The license is permissive the way it is because of the fundamental charter to create existing practice for standardization. So the idea is make it as easy as possible for people to use. Don't put any strings on what they do with it, and then it'll get lots of use."*

**The Principle**: When the goal is to create field experience for standardization, the license must be as permissive as possible. Any friction in adoption - attribution requirements, copyleft obligations, legal review overhead - directly undermines the goal of maximizing real-world use.

**Why It Matters**: The Boost Software License was deliberately designed to have minimal requirements specifically because Boost's charter was to create existing practice. The result was visible: program after program displayed the BSL, demonstrating massive adoption. This adoption was the evidence that made C++11 library standardization credible.

**When to Apply**: Choosing licensing for libraries intended as standardization candidates. Also when evaluating whether a library has genuine field experience.

**Red Flags**:
- Copyleft licenses on libraries intended for standardization
- License terms that require corporate legal review before adoption
- Libraries with high adoption barriers claiming "existing practice" status

**Supporting Experiences**: E6

<!-- METADATA
kind: principle
id: P10
source-type: explicit
category: process/navigation
applies-to: library
confidence: high
supported-by: [E6]
related-principles: [P2]
-->

---

### P11: Without Agreed Evolution Principles, a Committee Devolves Into Politics

> *"I had tried a few years before to try just to get the committee to agree in principle on some principles for evolution... Are we willing to say that old code not necessarily compile with the next version of C++?... And I could get no traction with this."*

**The Principle**: A standards body that cannot agree on fundamental principles for language or library evolution - what backward compatibility means, what can break, what the priorities are - will make decisions based on individual opinions and political coalitions rather than coherent policy. This produces an incoherent language.

**Why It Matters**: Dave's attempt to establish evolution principles failed, and Google's subsequent attempt also failed. Without such principles, every proposal is evaluated ad hoc, every decision is relitigated, and the resulting language is the sum of individual political victories rather than a designed whole. This was a primary factor in Dave's conclusion that C++ could not evolve coherently.

**When to Apply**: Evaluating the health of a standards process. Also when proposing changes that touch on evolution policy (breaking changes, deprecation, compatibility).

**Red Flags**:
- No documented principles for how the language/library may evolve
- Identical policy questions relitigated at every meeting
- Decisions that are clearly inconsistent with previous decisions
- Inability to deprecate or remove anything

**Supporting Experiences**: E7, E10

<!-- METADATA
kind: principle
id: P11
source-type: explicit
category: process/politics
applies-to: both
confidence: high
supported-by: [E7, E10]
related-principles: [P3]
-->

---

### P12: Conference Design Should Prioritize Human Connection Over Content Density

> *"Part of the way we designed the conference was a half hour between sessions, to really encourage people to talk to each other... again, a long lunch break... it was intense and it was good to not pack the day with just one thing after another, to have all of that breathing room."*

**The Principle**: Technical conferences produce their greatest value not in sessions but in the conversations between them. Conference design should maximize opportunities for spontaneous intellectual interaction through generous scheduling, inspiring settings, and shared experiences outside the lecture hall.

**Why It Matters**: BoostCon was modeled on the Aspen Center for Physics, where Dave observed world-class physicists achieving breakthroughs through informal interaction. Scott Meyers' advice - "think about your fantasy of what you would like a day at the conference to be like and make that happen" - led to a design that prioritized the "hallway track." The result was the most beloved C++ conference of its era and the direct ancestor of CppNow and CppCon.

**When to Apply**: Designing technical conferences, workshops, or working meetings.

**Red Flags**:
- Back-to-back sessions with no breaks
- Convention center settings with no natural gathering spaces
- No shared meals or social activities
- Schedules that leave no time for spontaneous interaction

**Supporting Experiences**: E9

<!-- METADATA
kind: principle
id: P12
source-type: tacit
category: process/actual
applies-to: both
confidence: high
supported-by: [E9]
related-principles: [P3, P5]
-->

---

### P13: Governance Must Be Transparent and Work Through Official Channels

> *"Nobody outside the official governing body should have been trying to buy the domain, especially not in the shadows. Stuff should be above board."*

**The Principle**: Organizational assets and governance decisions must be handled through official channels with full transparency. Attempts to acquire organizational resources (domains, trademarks, authority) outside the official governing body - regardless of the acquirer's intentions or resources - undermine legitimacy and trust.

**Why It Matters**: The attempt to acquire boost.org outside the Boost Software Foundation's authority, regardless of the underlying motivations, signaled to community members that the official governance structure was being circumvented. Even if the BSF was failing at management, the remedy is to fix or replace the governance structure transparently, not to go around it.

**When to Apply**: Evaluating governance transitions, organizational mergers, or any situation where organizational assets are being transferred.

**Red Flags**:
- Asset acquisitions conducted outside official governing bodies
- Lawyers involved in transactions the governing body doesn't know about
- Resources being offered to circumvent rather than work with existing governance
- Governance changes driven by resource asymmetry rather than community consensus

**Supporting Experiences**: E11

<!-- METADATA
kind: principle
id: P13
source-type: explicit
category: process/politics
applies-to: both
confidence: high
supported-by: [E11]
related-principles: [P3, P5]
-->

---

### P14: Companies Systematically Underinvest in Library Infrastructure

> *"Somehow the business world doesn't appreciate the importance of spending money on infrastructure... the next feature is the thing that everybody's chasing and there's no investment in maintaining the quality of the code."*

> *"Libraries are infrastructure. They're not anybody's product. Almost nobody makes money selling libraries. And that means inside of companies there's no direct financial incentive to spend time building libraries."*

**The Principle**: The business world systematically underinvests in library infrastructure because libraries are not products and have no direct revenue attribution. The "next feature" always wins over infrastructure that would multiply future productivity. This creates a persistent gap that open-source communities like Boost fill.

**Why It Matters**: Boost was successful in part because it was volunteer work done outside of corporate feature pressure. Understanding this structural incentive problem explains why standardization of library infrastructure is valuable: it externalizes the cost of something companies need but won't build. It also explains why library authors often work as volunteers or academics rather than as employees.

**When to Apply**: Evaluating the sustainability model for library development. Also when making the case for standardizing infrastructure libraries.

**Red Flags**:
- Library proposals with no sustainable maintenance model
- Corporate-backed proposals where the sponsoring company has feature-level objectives
- Libraries that exist only because one company needed them and may abandon them

**Supporting Experiences**: E12

<!-- METADATA
kind: principle
id: P14
source-type: explicit
category: belongs/ecosystem
applies-to: library
confidence: high
supported-by: [E12]
related-principles: [P1, P2]
-->

---

### P15: Complexity Is the Enemy of Empowerment

> *"C++ was too complicated to be the vehicle for empowering programmers... Some people say that C++ is expert friendly. But I don't think it's actually friendly to experts. It's hard for everybody."*

> *"To program effectively in C++, you have to be an expert. So that's just not a recipe for empowering programmers."*

**The Principle**: A language or library that requires expert-level knowledge to use effectively cannot serve its purpose of empowering programmers. Complexity that accumulates through legacy compatibility obligations, feature accretion, and inability to remove things eventually overwhelms the benefits of any individual feature.

**Why It Matters**: C++ started with the genius move of extending C, inheriting its user base. But that same compatibility became an anchor: every old feature persists alongside every new one, the standard is thousands of pages, and no one can absorb it all. Dave identifies this as a structural problem, not a solvable one within the committee process, because the committee cannot agree on principles for removing or breaking anything.

**When to Apply**: Evaluating the long-term trajectory of a standard or ecosystem. Also when considering whether to add features that increase surface area without offsetting reductions.

**Red Flags**:
- Features added without any corresponding simplification
- Standards that only grow, never shrink
- "Expert-friendly" framing used to justify unnecessary complexity
- No deprecation or removal path for superseded features

**Supporting Experiences**: E7, E10

<!-- METADATA
kind: principle
id: P15
source-type: explicit
category: philosophy/evolution
applies-to: both
confidence: high
supported-by: [E7, E10]
related-principles: [P11]
-->

---

### P16: The Valuable Things Are Discovered, Not Invented

> *"One of the things that Alex said, or at least I learned eventually through Alex, was that the valuable things are discovered, not invented. At some level there's a truth that's out there, like a mathematical truth or a design truth, and your job is to discover it."*

**The Principle**: The best library designs, language features, and process structures are not invented by fiat but discovered through collaborative exploration. The attitude of discovery - that there is an objectively best (or at least better) answer waiting to be found - produces better results than the attitude of advocacy, where participants push pre-formed positions.

**Why It Matters**: Dave identifies this as the ethos that made Boost's golden age work. Participants were not engaged in meritocracy (winning) or politics (coalition-building) but in collaborative discovery. The 300-message naming convention thread was not a debate between opinions; it was a vehicle for collectively discovering what naming works best. This attitude requires intellectual humility and genuine curiosity, qualities that are easy to lose as a project scales.

**When to Apply**: Evaluating the culture of a technical community. Also when participating in design discussions - approach them as discovery, not advocacy.

**Red Flags**:
- Participants who arrive with fixed positions and argue to win
- Discussions framed as competitions between alternatives rather than explorations of the design space
- Libraries submitted to Boost primarily for career advancement
- Meritocratic framing ("the best person wins") rather than collaborative framing ("we discover together")

**Supporting Experiences**: E5

<!-- METADATA
kind: principle
id: P16
source-type: explicit
category: philosophy/coherence
applies-to: both
confidence: high
supported-by: [E5]
related-principles: [P3, P5]
-->

---

## Experiences

Relatable stories that illustrate and support the principles.

### E1: The STL Transformed Dave's Music Notation Software

**Context**: Dave Abrahams was working at Mark of the Unicorn in the late 1990s, building music notation software largely from scratch. There were virtually no reusable libraries; he was building algorithms, data structures, user interfaces, graphics, printing, and transcription systems all himself, with no mentor after his designated guide left the company a few months in.

**What Happened**: His colleague Mark Waxler showed him a magazine article about Alex Stepanov's STL. Dave had by then "learned a lot of hard lessons about programming" and immediately recognized the STL as "fascinatingly different from anything I had used." The rigorously documented components with precise contracts let him throw out his own unreliable binary search implementation (which he had gotten wrong multiple times) and replace it with a correct one. Beyond the code, the STL gave him a paradigm: when he needed to write his own algorithms, he now accepted iterators as parameters, eliminating an entire category of design decisions.

**The Outcome**: Success. Dave describes this as having "completely changed the productivity landscape for me." He could focus on his domain expertise (music notation) rather than reinventing standard computing infrastructure.

**The Lesson**: Libraries provide two layers of value: the code itself, and the paradigm it establishes. The STL didn't just give Dave algorithms - it gave him a way of thinking about algorithms that eliminated design decisions across his entire codebase.

> *"I cannot tell you how many times I wrote binary search incorrectly before. It's a very simple algorithm, maybe 10 lines... when I got the one that was in the STL, that whole problem was over."*

**Supports Principles**: P1, P4, P7, P9

<!-- METADATA
kind: experience
id: E1
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [STL, iterators, algorithms, generic-programming]
supports: [P1, P4, P7, P9]
-->

---

### E2: Boost Was Created to Produce Existing Practice for Standardization

**Context**: After C++98 was published, Beman Dawes was thinking about where libraries for the next standard would come from. The committee had a principle of "standardize existing practice" but had already strained it by inventing template features for the STL before any compiler supported them - a "black eye" that took years to resolve.

**What Happened**: Beman conceived Boost as a collection of open-source C++ libraries specifically designed to create the existing practice that future standardization would require. Open source was chosen to maximize adoption; the permissive license removed all friction. The idea was: five years of stability post-C++98, then five years of evolution, and Boost would have proven libraries ready for the next standard. The peer review process was modeled on the committee's own proposal scrutiny, with review managers moderating consensus.

**The Outcome**: Success. By C++11, "quite a few of the Boost libraries" were incorporated into the standard, "changed somewhat, but mostly the libraries came in with existing practice because they had been in boost and widely used and proven to be useful."

**The Lesson**: Creating a deliberate pipeline for field-tested libraries, with a permissive license to maximize adoption and a rigorous peer review to ensure quality, is an effective strategy for standards development.

> *"We need an organization to start developing libraries and getting them out into people's hands and actually used. And so that was the idea of Boost."*

**Supports Principles**: P2, P10

<!-- METADATA
kind: experience
id: E2
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [Boost, C++11, standardization-pipeline]
supports: [P2, P10]
-->

---

### E3: Beman Dawes' Inclusive Leadership at Dave's First Committee Meeting

**Context**: Dave attended his first WG21 meeting in Nashua, New Hampshire, while still working at Mark of the Unicorn. He was not a committee member and had no vote. The meeting was in a single conference room with a horseshoe of tables, committee members seated at them with thick binders of the working draft.

**What Happened**: Dave sat in a chair around the edge of the room, not at the table. When the group split for issue processing, Beman Dawes - the LWG chair - noticed Dave and invited him to come sit with everyone else. "I said, I'm not a member. And he said, it doesn't matter." Committee members were generous in helping Dave understand the process, and Dave was "able to make a few contributions that were valuable, like give some insights that help people resolve certain problems."

**The Outcome**: Success. Dave experienced a level of intellectual respect and collaboration he had never encountered in his regular job. This experience directly shaped his vision for Boost and BoostCon.

**The Lesson**: Inclusive leadership that values contributions regardless of formal status creates an environment where the best ideas emerge. Beman's simple act of invitation set the tone for an entire era of Boost culture.

> *"He was patient and non-partisan... this super impressed me and also the respect that I saw in the room among the committee members... was a level that I did not experience in my regular job."*

**Supports Principles**: P3, P5

<!-- METADATA
kind: experience
id: E3
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [WG21, LWG, committee-process]
supports: [P3, P5]
-->

---

### E4: Exception Safety Got Into C++98 Through Consensus Across National Bodies

**Context**: Dave had developed a theory of exception safety for the STL based on programming by contract (Tony Hoare, Bertrand Meyer). The community initially said the problem was "well known to be impossible," partly due to a misreading of Tom Cargill's influential article. The US national body was "extremely conservative" and was going to vote no because it was "too late a change."

**What Happened**: Dave worked on two fronts simultaneously: popularizing exception safety theory on Usenet, and building consensus within the committee via the reflector. Greg Colvin became his key ally, helping minimize the wording changes required. Despite the US body's conservatism, two other national bodies (UK and Germany) essentially said "we're voting no unless you put this in." Dave accomplished all of this without ever being a formal committee member.

**The Outcome**: Success. Exception safety was adopted into C++98. Dave describes it as "a huge accomplishment" and evidence that "you really can get great things done by consensus, just by working with people to help them understand."

**The Lesson**: Building understanding across multiple stakeholder groups, minimizing the footprint of changes, and finding allies who complement your skills can overcome institutional conservatism. Consensus doesn't require a vote - it requires persuasion.

> *"Being able to negotiate with all those people without flipping a table was an important skill I was working on there."*

**Supports Principles**: P3, P8

<!-- METADATA
kind: experience
id: E4
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [exception-safety, C++98, STL]
supports: [P3, P8]
-->

---

### E5: Boost's Peer Review Process Modeled on Beman's LWG Style

**Context**: Boost needed a mechanism to evaluate proposed libraries for inclusion. The question was how to structure the review process.

**What Happened**: The process that emerged was modeled directly on Beman Dawes' leadership of LWG. For every proposed library, a review manager would be selected - someone who would moderate discussion, ensure all arguments were heard, and then rule on what the consensus had been. The manager's role was explicitly about moderation, not technical adjudication. "Their main role had nothing to do with their technical ability." Participants would make informal votes and the manager would assess consensus.

**The Outcome**: Success. Dave says the process "worked really well for a long time." It produced a high-quality library ecosystem that supplied C++11 with many of its standard library additions.

**The Lesson**: Transplanting a proven leadership model (Beman's LWG style) into a new context (Boost reviews) preserved its essential qualities: inclusiveness, respect for all arguments, and consensus-based outcomes.

> *"People would make their informal votes and the review manager would look at the votes and decide whether there was consensus for including it."*

**Supports Principles**: P3, P5, P6, P16

<!-- METADATA
kind: experience
id: E5
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [Boost, peer-review, governance]
supports: [P3, P5, P6, P16]
-->

---

### E6: The Boost Software License Proved Adoption Strategy

**Context**: Boost needed a license that would maximize adoption. Existing open-source licenses were all "too uncom-" (Dave trails off, but the implication is too encumbered or too complex for Boost's purposes). The charter was to create existing practice for standardization.

**What Happened**: Boost created its own extremely permissive license - the Boost Software License - requiring essentially nothing of users. The strategy was simple: "make it as easy as possible for people to use, don't put any strings on what they do with it, and then it'll get lots of use."

**The Outcome**: Success. Dave describes the moment he realized Boost was "really a major force in the world": "program after program would display the Boost software license at installation or on startup, reflecting that they were using Boost." The license strategy directly enabled the field experience that made C++11 standardization credible.

**The Lesson**: When the goal is field experience and standardization, licensing strategy is not an afterthought - it is fundamental infrastructure. Every friction point in adoption is a library that doesn't get tested in the field.

> *"At some point that was like, oh wow, this is really a major force in the world."*

**Supports Principles**: P2, P10

<!-- METADATA
kind: experience
id: E6
source-type: explicit
category: history/successes
applies-to: library
outcome: success
features: [Boost-Software-License, adoption, licensing]
supports: [P2, P10]
-->

---

### E7: Dave's Failed Attempt to Establish Evolution Principles in WG21

**Context**: Around 2010-2011, Dave recognized that the C++ committee was making decisions without any agreed framework. He tried to get the committee to agree on basic evolution principles: Can old code break with a new compiler? Can separately compiled objects fail to link?

**What Happened**: Dave "could get no traction with this." The committee was unwilling to commit to any principles that would constrain future decisions. A few years later, Google came to the committee and tried essentially the same thing - to get agreement on specific evolution principles - and "also failed."

**The Outcome**: Failure. The committee never adopted evolution principles. Dave views this as evidence that the committee is "structurally unable to make the decisions that were necessary for C++ to continue to be the vehicle for empowering programmers."

**The Lesson**: Without agreed principles for decision-making, a consensus body devolves into opinion-based politics. Every proposal is evaluated ad hoc, and the resulting system is the sum of individual political victories rather than a coherent design.

> *"I had tried to get the committee to agree in principle on some principles for evolution... and I could get no traction with this. And it turned out that a few years later, Google came to the committee and tried to do this again, essentially, and they also failed."*

**Supports Principles**: P11, P15

<!-- METADATA
kind: experience
id: E7
source-type: explicit
category: history/failures
applies-to: both
outcome: failure
features: [WG21, evolution-policy, committee-process]
supports: [P11, P15]
-->

---

### E8: Object-Oriented Frameworks Failed to Deliver Code Reuse

**Context**: Before the STL, the dominant approach to code reuse was object-oriented application frameworks. These were "big monolithic libraries" based on inheritance hierarchies and virtual dispatch, where everything was modeled as an "Object" base type.

**What Happened**: OOP promised code reuse through polymorphism - write one sort algorithm that operates on "objects." In practice, this was intrusive, didn't let you freely combine parts, and hid computation in "incidental algorithms" spread across message-passing webs. Dave couldn't find a binary search, a B-tree, or other standard data structures in these frameworks. They covered narrow domains (UI, mostly) and left everything else to the programmer.

**The Outcome**: Failure. OOP "didn't really deliver on its promises of code reuse." The STL's generic programming approach - algorithms parameterized by concepts, operating on iterators - succeeded where OOP failed.

**The Lesson**: Extensibility through inheritance and virtual dispatch is fundamentally more restrictive than extensibility through generic programming. When the extension mechanism is intrusive (requiring types to inherit from specific bases), free composition becomes impossible.

> *"Object oriented programming didn't really deliver on its promises of code reuse partly because of this problem... it's intrusive. It doesn't let you freely combine parts very well."*

**Supports Principles**: P7, P9

<!-- METADATA
kind: experience
id: E8
source-type: explicit
category: history/failures
applies-to: both
outcome: failure
features: [OOP, application-frameworks, code-reuse]
supports: [P7, P9]
-->

---

### E9: BoostCon Designed After the Aspen Center for Physics

**Context**: Dave wanted to create a conference where Boost contributors could meet in person. He had developed meaningful intellectual relationships online but had never met many contributors face-to-face (including Peter Dimov, whom he never did meet). He sought advice from Scott Meyers.

**What Happened**: Scott Meyers told Dave to think about his "fantasy of what you would like a day at the conference to be like and make that happen," and mentioned a colleague whose conference included daily hikes. Dave drew on childhood memories of his father's time at the Aspen Center for Physics - the multicultural collaboration, Thursday picnics, collegial atmosphere, and informal talks. He designed BoostCon with half-hour breaks between sessions, long lunch breaks, and an inspiring mountain setting. At the end of each conference, a planning meeting filled volunteer roles for the following year.

**The Outcome**: Success. "I had more fun at that conference than I had ever had at any other conference." BoostCon became an annual institution, evolved into CppNow, and inspired Jon Kalb to create CppCon.

**The Lesson**: Conferences optimized for human connection and breathing room produce more lasting value than conferences optimized for content density. The hallway track is where the real work happens.

> *"Think about your fantasy of what you would like a day at the conference to be like and make that happen."*

**Supports Principles**: P12

<!-- METADATA
kind: experience
id: E9
source-type: explicit
category: history/successes
applies-to: both
outcome: success
features: [BoostCon, CppNow, conference-design]
supports: [P12]
-->

---

### E10: The Concepts Debacle Drove Dave Away from C++

**Context**: Doug Gregor, deeply influenced by Alex Stepanov's generic programming vision, built a principled implementation of concepts for C++. Dave was a strong ally of the Indiana crew (Doug, Andrew Lumsdaine, Jaakko Jarvi) in their quest to make concepts work properly for generic programmers.

**What Happened**: The concepts proposal "got torpedoed at the last minute and in such a way that it was clear that Bjarne was never gonna support what I considered to be the right design." C++ eventually got a version of concepts that "doesn't make life better for people who are doing generic programming" - it helps users of generic components but not writers of them. Combined with the failure to establish evolution principles, this convinced Dave that "C++ was never gonna get there."

**The Outcome**: Failure (from Dave's perspective). The version of concepts that shipped missed the point of generic programming as Alex Stepanov defined it. This was a primary factor in Dave's decision to leave C++ for Apple/Swift in 2013.

**The Lesson**: A standards body that cannot preserve the technical vision of its most important paradigm will lose the people most committed to that vision. Committee politics can override technical merit, and sometimes the only rational response is to leave.

> *"It became clear that was over. And at that time I was at a committee meeting with Doug, and I had started to fish around for jobs."*

**Supports Principles**: P11, P15

<!-- METADATA
kind: experience
id: E10
source-type: explicit
category: history/failures
applies-to: language
outcome: failure
features: [concepts, generic-programming, WG21]
supports: [P11, P15]
-->

---

### E11: The Boost Domain Acquisition Controversy

**Context**: After Beman Dawes passed away, the boost.org domain name - which Beman had personally registered because Boost had never been a legal entity - needed to be transferred. Sonda (Beman's wife) held it. The Boost Software Foundation was the official governing body.

**What Happened**: Dave was contacted (he believes by the BSF) to talk to Sonda about transferring the domain. When he called her, she told him she was about to finalize an arrangement with "these other folks" - people associated with the C++ Alliance - who had been trying to buy the domain. Sonda said she didn't want money, just wanted it in the right place, but the Alliance "really insisted on wanting to try to pay me and there were lawyers." Dave told Sonda to give it to the BSF instead.

**The Outcome**: Mixed. The domain eventually went to the proper channels, but the governance of Boost was subsequently transferred to an entity associated with the Alliance by community vote. Dave remains concerned: "I certainly worry about Boost in the hands of an organization that would try to go around the official governing body to acquire the domain."

**The Lesson**: Governance legitimacy depends on transparency and process. Even when an organization has more resources and arguably better management capacity, circumventing official channels to acquire assets poisons trust. The BSF's failures as a volunteer organization were real, but the remedy should have been transparent governance reform.

> *"Nobody outside the official governing body should have been trying to buy the domain, especially not in the shadows. Stuff should be above board."*

**Supports Principles**: P13

<!-- METADATA
kind: experience
id: E11
source-type: explicit
category: history/failures
applies-to: both
outcome: mixed
features: [Boost-governance, domain-acquisition, C++-Alliance]
supports: [P13]
-->

---

### E12: Libraries as Infrastructure That Companies Won't Build

**Context**: Dave worked at Adobe, where imaging libraries are essential infrastructure shared across many products (Photoshop, etc.). He observed the same pattern across the industry.

**What Happened**: Despite depending on internal imaging libraries, Adobe and other companies consistently prioritize "the next feature of Photoshop" over infrastructure investment. "There's no direct financial incentive to spend time building libraries" because libraries are not products. The investment that would "let us develop more things faster in the future" requires "engineering time today that doesn't produce an immediate result." This investment systematically doesn't happen.

**The Outcome**: Mixed. Boost succeeded partly because contributors were volunteers working outside corporate feature pressure. But the structural problem persists: infrastructure that would multiply productivity is perpetually underfunded.

**The Lesson**: Open-source libraries fill a structural gap in the market: companies need infrastructure but won't build it. Standardization further externalizes this cost by ensuring every vendor implements the infrastructure. Understanding this dynamic is essential to appreciating why Boost and standardization matter.

> *"The next feature is the thing that everybody's chasing and there's no investment in maintaining the quality of the code... which require us to invest engineering time today that doesn't produce an immediate result."*

**Supports Principles**: P14

<!-- METADATA
kind: experience
id: E12
source-type: explicit
category: philosophy/tradeoffs
applies-to: library
outcome: mixed
features: [infrastructure, open-source, corporate-incentives]
supports: [P14]
-->

---

## Evaluation Checklists

Actionable checklists derived from principles, for evaluating proposals.

### When Reviewing Library Proposals

- [ ] Does the library enable something previously impossible, impractical, or genuinely difficult? (P1)
- [ ] Is there documented field experience from users outside the proposer's organization? (P2)
- [ ] Can the proposer articulate what programmers must do today without this library? (P1)
- [ ] Does the library establish a paradigm that eliminates design decisions for users? (P4)
- [ ] Are algorithms explicit and locally reasonable, not hidden in object graphs? (P9)
- [ ] Is the design based on generic programming rather than inheritance hierarchies? (P7)
- [ ] Has the library been available under a permissive license long enough for genuine adoption? (P10)
- [ ] Is there a sustainable maintenance model beyond the original proposer? (P14)
- [ ] Are wording changes minimal and independently evaluable? (P8)

**Questions to Ask**:
1. "What was previously impossible or impractical that this library makes possible?" (P1)
2. "Who outside your organization has used this, and what was their feedback?" (P2)
3. "Does this library provide a paradigm, or just code?" (P4)
4. "Can I read the algorithm in one place, or must I trace through object interactions?" (P9)
5. "How long has this been available for public use, and under what license?" (P2, P10)

<!-- METADATA
kind: checklist
category: evaluation/library
applies-to: library
proposal-type: feature
derived-from: [P1, P2, P4, P7, P8, P9, P10, P14]
-->

---

### When Evaluating Governance or Process Changes

- [ ] Are all decisions being made through official governing bodies? (P13)
- [ ] Is the process consensus-based with inclusive leadership? (P3, P5)
- [ ] Do review/decision roles separate moderation from technical advocacy? (P6)
- [ ] Are there agreed principles for how the standard/project evolves? (P11)
- [ ] Is the community culture oriented toward discovery rather than advocacy? (P16)
- [ ] Are asset transfers and governance changes conducted transparently? (P13)

**Questions to Ask**:
1. "Is this decision being made through the official channels, or around them?" (P13)
2. "Is the review manager moderating or advocating?" (P6)
3. "What evolution principles guide this decision?" (P11)
4. "Are we trying to discover the right answer, or arguing for pre-formed positions?" (P16)

<!-- METADATA
kind: checklist
category: process/actual
applies-to: both
proposal-type: feature
derived-from: [P3, P5, P6, P11, P13, P16]
-->

---

### When Evaluating Language Evolution Proposals

- [ ] Is there an agreed framework of evolution principles this proposal fits within? (P11)
- [ ] Does the proposal add complexity without corresponding simplification? (P15)
- [ ] Does the proposal serve generic programmers or only users of generic components? (P7)
- [ ] Can the committee agree on whether this feature should be breakable/removable in the future? (P11)
- [ ] Has the feature been implemented and used in practice before standardization? (P2)

**Questions to Ask**:
1. "What evolution principle justifies this change?" (P11)
2. "Does this make the language simpler for non-experts, or only more powerful for experts?" (P15)
3. "Has any compiler shipped this, and have real programs used it?" (P2)
4. "What gets deprecated or removed to make room for this?" (P15)

<!-- METADATA
kind: checklist
category: evaluation/language
applies-to: language
proposal-type: feature
derived-from: [P2, P7, P11, P15]
-->

---

## Open Questions

1. Dave mentions that Boost's review process "worked really well for a long time" - what changed, and when did it stop working as well? What are the specific failure modes that emerged?

2. Dave says the committee process "got messier and more fraught and more political as time went on." Who are the "several individuals" he believes increased politicization? What specific incidents marked the transition?

3. Dave's consulting business (Boost Consulting / Boost Pro) handled financial and organizational aspects of BoostCon. What happened to the organizational knowledge when Dave left for Apple? Was there a handoff?

4. Dave alludes to "a string of sexual misconduct problems" around the C++ community and conferences. How did these affect committee culture and the governance transition?

5. What is Dave's assessment of Swift's success in delivering on the generic programming vision that C++ failed to achieve? Has his mission of "empowering programmers" been fulfilled there?

6. Dave mentions the Beman Project as "Boost 2.0 without the dependency problems." Does he view it as the rightful successor to Boost's original mission, or as a fragmentation?

7. Dave says he "set up a board to help govern Boost going forward" before leaving, and "that was a failure." What specifically went wrong with that board?

8. What are the "other stories" Dave has heard about interactions between the BSF and people associated with the Alliance that "were not good"?

9. Dave's observation that "Boost carries a lot of legacy" parallels his critique of C++ itself. Is there a general principle here about when accumulated legacy becomes an existential threat to a project?

10. Dave credits Sean Parent with the concept of "incidental algorithms" and says he owes "a lot of the things I normally think of as my core ideas to Sean." Which specific ideas?

---

## Raw Transcript Reference

Source: `inputs/dave-abrahams.md`
Filmed: December 19, 2025, San Jose, CA
Video: https://vimeo.com/1152633977/77d3f828e6?fl=tl&fe=ec
