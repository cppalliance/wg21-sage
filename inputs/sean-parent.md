# BOOST_SEAN_PARENT_STRINGOUT_v01

---
filmed Date: 2025-12-10
location: San Jose CA
camera: A / B
audio: Lav
type: INTERVIEW
video link: ​​https://vimeo.com/1152633745/2a73805542?fl=tl&fe=ec
summary: Parent was strongest on explaining C++ broad usage, including at Adobe, and how Boost libraries made difference there and why he has hired so many Boost people. He gave more background on one hire, Sankel, including about his 9 kids etc and had a moment we can use when asked why Sankel is a "hard no" with us "Oh, no, ha, I could not tell you why while the camera is rolling."
---

## Transcript Start

[00:00:00] 

[00:00:00] **CREW:** This is Sean Parent, take one. Soft sticks and second sticks.

[00:00:13] **CREW:** SEAN PARENT 

[00:00:13] **CREW:** I'm Sean Parent. I am a senior principal scientist at Adobe, uh, currently working in our tech foundations, uh, research lab. Uh oh. That's about it. Yeah. Yeah, I think it's pretty amazing. I mean, every operating [00:00:30] system. That's in common use, whether it's Mac, OS, or iOS, or, or Windows. Android is all sitting probably 90% C++ code underneath it, um, uh, with some C code at the very, very bottom level.

[00:00:45] **CREW:** Um, uh, pretty much every major application that you see is written in C++. So at Adobe, that's, uh, Photoshop, Acrobat. Lightroom, um. Uh, certainly in [00:01:00] Microsoft, it's word in Excel and the the office suite. Uh, so you know, it's the infrastructure that's underneath you. Even. Uh, the F 35 Joint Strike Fighter avionic system is written in C++.

[00:01:16] **CREW:** So Boost is a collection of open source libraries. Uh, originally started to, uh, uh, vet libraries for standardization. And it came [00:01:30] about at a time when the C++ standard was kind of stuck. We had C++ 98, and then many years later we had C++ oh three, which was just a very small kind of addressing defects in the language.

[00:01:45] **CREW:** And we didn't get a new major release of the language until C++ 11. And so that's, you know, from 98 to C++ 11 is a huge gap. 

[00:01:54] **RAY NOWOSIELSKI:** Yeah. 

[00:01:55] **SEAN PARENT:** And, and I think C++ in some sense, you [00:02:00] know, would've greatly diminished during that time period. Just from, from stagnation. Mm-hmm. Um, uh, and then the Boost Libraries started and they were a collection of, of open source libraries.

[00:02:15] **SEAN PARENT:** Uh, in some sense they built off some of the ideas that Alex Stoff laid down with the standard template library. And, uh, uh, they were written by a group of people who kind of find ways [00:02:30] to exploit, uh, aspects of the language and turn that into interesting and useful libraries. And so it became this growing collection of, of high quality libraries, uh uh, which both.

[00:02:45] **SEAN PARENT:** Kept the language alive, uh, and then turned into the foundation for features for C++ 11, uh, and beyond, uh, uh, as well as new library features that went into C++ 11 and beyond. C++ [00:03:00] 11 was a huge step up in the language. It, it took, uh. A lot of things that were very cumbersome to express and had to be done on a library side.

[00:03:12] **SEAN PARENT:** And even though Boost had facilities to make it more useful, uh, uh, it was still very cumbersome and, and very time consuming. And a lot of those features just got rolled into the language. So things like, uh, uh, uh, very templates. So you could have templates with multiple [00:03:30] arguments. Uh, came into the language in C++ 11 Lambda Expressions came in with C++ 11, and just a, a whole host of features that made the ergonomics of the language much, much simpler to use.

[00:03:43] **SEAN PARENT:** Um, uh, I've started at a little company called Orange Micro, which was outside of Anaheim, uh, uh, doing embedded software. I worked on a. On a smart cable called Grappler lq, [00:04:00] uh, uh, from there, uh, I attended a conference and met some folks at Apple, and that turned into a job offer at Apple. So I worked at Apple from 88 to 93, uh, in the system software group.

[00:04:15] **SEAN PARENT:** Um, uh, I worked on Quick Draw gx, which was a graphic system at the time, and then later worked on the transition, uh, that Apple went through, uh, from 68 K processors to power PC processors. So I was part of the team [00:04:30] that did that. Um, that turned into to a job offer at Adobe to help move Photoshop to Power pc.

[00:04:39] **SEAN PARENT:** Um, so I joined Adobe in 93, uh, worked at Adobe mostly on Photoshop. Uh. Uh, in the early days and then eventually started my own research team, uh, with Alex Stepanov uh, Paul Mc Jones, Matt Marcus, uh, Foster Breton. That was the software technology lab [00:05:00] and ran that for eight years. Uh, that came apart in what year would've been 2009, 2010.

[00:05:09] **SEAN PARENT:** Um, so I left the company briefly, uh, worked at Google on Chrome os. Uh, after a little more than a year on that, I came back to Adobe, uh, this time working on, on products. So I worked on a product called Revel, which kind of turned into Lightroom Mobile, [00:05:30] Lightroom Web, and I did Photoshop Mobile, Photoshop Web, um, and then we started Software Technology Lab and which now has become the tech foundation's research lab and, uh.

[00:05:44] **SEAN PARENT:** Uh, yeah. Uh, so Tech Foundation's research, our focus is improving the code that, uh, uh, uh, uh, developers write. Um, uh, uh, so we're not concerned with process like agile or scrums or things like that We're [00:06:00] concerned with what code do developers write when they sit down at the keyboard, and how do we get developers to write higher quality code?

[00:06:07] **SEAN PARENT:** We do that, uh, through a combination of developing tooling in libraries, um, uh, uh, doing research into new languages and, and being forward looking in where the industry is going. Uh, uh, so there's some component there that's collaborating, uh, with universities. And then there's an education component where we teach [00:06:30] classes and give seminars and lectures.

[00:06:32] **SEAN PARENT:** So. Boost libraries have been mostly at, at my career at Adobe. Um, when I worked at, at, at Google for the brief period of time there, they were actually not allowed to be used at Google. Um, I believe that that has changed at this point. Um, but at the time that was, that was the rule. Uh, uh. At Adobe, the Boost Libraries were [00:07:00] the first, uh, open source libraries that were allowed to be used within the company.

[00:07:05] **SEAN PARENT:** Um, I kind of spearheaded that effort and at the time, in the early days of Boost, boost didn't have a single license. So contributors to Boost were putting their code under their own license, uh, which means that there were over a hundred licenses inside of. The Boost Libraries. So I had to get that all vetted by our legal department here before we could get sign off.

[00:07:29] **SEAN PARENT:** And later I [00:07:30] worked with Dave Abraham's to to, to uh, uh, uh, push the, the Boost Foundation into, into establishing a, uh, a common library in moving the libraries under a, under a common library. Um. Uh, but they filled a significant need at Adobe as, as a, a kind of common substrate that was used within, within the products.

[00:07:55] **SEAN PARENT:** Uh, so I was, at the time I was [00:08:00] managing, uh, uh, uh, Adobe Soft Software Technology Lab, uh, when Boost first appeared and. Uh, uh, uh, Matt Marcus on my team represented Adobe on the C++ Standards Committee. So he had an awareness of, of Boost and it was upcoming. Um, I mentioned before that uh, we had Alex Stoff who joined the software technology lab.

[00:08:25] **SEAN PARENT:** He was the creator of STL and he was friends with B j a r [00:08:30] n e S t r o u s t r u p and so, so. We had a connection there with, with Bjarne, so we were kind of aware of what the standards committee was doing and the direction that that was going. Uh, we hosted a, a workshop on generic programming here at Adobe and had had many people from the standards committee and the generic programming community attended that.

[00:08:56] **SEAN PARENT:** So that kind. Connected me in into [00:09:00] that space. Uh, was also working on, on one of Adobe's first open source libraries, uh, Adobe Source Libraries, which bear some resemblance to boost. That is really hard. Um, uh, yeah, especially without insulting somebody. Um, uh, so, so standout boost authors, uh, uh, I'm gonna name a few, uh, uh, uh.

[00:09:26] **SEAN PARENT:** Uh, uh, certainly some of Doug Gregor's work is [00:09:30] brilliant. Um, uh, uh, uh, uh, you know, some of Dave Abraham's work, um, uh, Eric Neer's work is, is up there, uh, uh, Jeremy Sikh, um, uh, along with Andrew Lumsdaine who was Jeremy and Doug's advisor at, at. At Indiana University, uh, a boost graph library is just a phenomenal piece of work.

[00:09:59] **SEAN PARENT:** [00:10:00] Um, uh, so that's kind of a standout library. Why is that in the mix? It's the, uh, uh, the one example that we have have of using what Alex did with STL and generic programming as an example of doing something in a different, slightly different domain. And, and Alex always had this vision that, that his work on [00:10:30] STL should be an example of how you should write code.

[00:10:33] **SEAN PARENT:** And the boost graph library is kind of a stellar example of taking that in into the, the graph algorithm domain. Uh, 

[00:10:43] **RAY NOWOSIELSKI:** no Peter Dimov?

[00:10:44] **SEAN PARENT:** No. Only 'cause we were not working on kind of the same sections of things at the same time. Uh, uh, just let Alex tell stories. I don't, I don't know what he's gonna talk about.

[00:10:55] **SEAN PARENT:** I mean, certainly Alex had. Had no involvement with Boost other than, [00:11:00] than having an influence on, on Boost contributors. Um, yeah. Yeah, I think that's certainly true when you look at, when you look at the Boost Graph library, um, I, I think it's also Alex who, who, you know, he doesn't like, like credit for it because he's, he views it as a hack.

[00:11:20] **SEAN PARENT:** But he's the person who, who, who started this notion of meta programming in order to implement STL. But he will tell you, generic programming has [00:11:30] nothing to do with meta programming. It was a hack so he could implement generic programming, and it kind of became the thing in boost. And so it definitely has changed a lot over the years.

[00:11:41] **SEAN PARENT:** I mean, in the early days when kind of open source first appeared on the scene. Uh, it was viewed as being very, uh, uh, uh, uh, uh, uh, anti commercial use and, and so, so, you know, anti corporation and it was. You [00:12:00] know, kind of the, the, uh, uh, uh, communist view of, of open source software. Right? Right. And, and you had a lot of viral licenses out there.

[00:12:08] **SEAN PARENT:** And so, so if you, you know, and the idea with a viral license is if you include that open source project with a viral license into your product, then you also must open source your product. And, and so that, uh. Uh, uh, was very counter to commercial purposes, and [00:12:30] even though not all licenses fell into that category, a lot of legal departments at companies, uh, didn't want to touch it.

[00:12:37] **SEAN PARENT:** Um. Uh, uh, uh, uh, uh, so, so open source in the early days was, was an issue and a problem. Um, I think Boost is one of the projects that started to change that, that perception. Uh, it met a need, it had a very fairly liberal license. Uh, uh, it was, you know, open for commercial [00:13:00] use. You didn't have to put credit within your product to specify where you had, had, had picked this up.

[00:13:06] **SEAN PARENT:** Um. Uh, uh, and its focus was on language standardization. We were all working on, on C++. So there was value in now, uh, uh, contributing to the standard by contributing to the boost libraries and by, by pushing, pushing that forward. Um, uh, uh, so it started to change the, the perception of what open source [00:13:30] could be and what open source meant.

[00:13:31] **SEAN PARENT:** Uh, well. At the, at the time, and still to this day, right? Anybody who's working in tech has signed an agreement with their company that says that, you know, whatever they produce at whatever hours they produce it, uh, is owned by the company. So if you're gonna contribute and you're one of the major tech companies to an open source project, uh, you've gotta get permission from the organization.

[00:13:55] **SEAN PARENT:** Um, uh, these days, that's. Pretty simple to do. You know, you basically need [00:14:00] a, a manager to sign off and then, uh, a, a senior, senior engineer to sign off to say that what you're giving away is not trade secrets or patents or, or, or things of that nature. Um, uh, uh. Uh, uh, uh, but yeah, in the, in the early days, there wasn't a process at at, at companies to, to do that.

[00:14:22] **SEAN PARENT:** And so it meant you had to sit down with legal and try to make an argument. And, and every legal department, uh, uh, their job is to [00:14:30] mitigate risks. So their answer was gonna be no. 

[00:14:32] **RAY NOWOSIELSKI:** Had a little something to do with, uh, whole project called Swift?

[00:14:35] **SEAN PARENT:** A little something to do with that, I think, uh. Uh, uh, you know, Doug first, Doug worked on something called concept C++, um, which was slated to be part of the, the standard.

[00:14:49] **SEAN PARENT:** And, and he had, had, had done an implementation and the design of the language feature and vetted it, and it got rejected by the standards committee. [00:15:00] And it was, uh, a very political decision. There was a, uh, a competing proposal. He was out of. Out of, um, uh, Andrew Lumsdaine's team and there was a competing proposal from Stroustrup's team, and they couldn't reach consensus on the two.

[00:15:17] **SEAN PARENT:** Uh, uh, uh, the end result was both of them got pulled from the standards and neither went in. Um, uh, at that time, I think, uh, uh, you know, dug it. Put a lot of his personal [00:15:30] effort into this and, uh, uh, uh, uh, uh, was looking for something outside of C++ to go do, certainly it was a, within the community, it was a big political issue, pulling concepts out of the, out of the standard, um, 

[00:15:44] **RAY NOWOSIELSKI:** Hot potato?

[00:15:45] **SEAN PARENT:** Yeah. Yeah, it was a hot potato. It was very contentious. So there were people who were, who were very upset by it. Um, uh, uh, uh, uh. Uh, there was on both sides. [00:16:00] Um, uh, uh, uh, but I think certainly on, on on Doug Gregor's side, he had kind of the most invested in it, and he thought his design was sound. And so I thought, I think he, you know, part of what he wanted to go do was, was proved that his work was of high value.

[00:16:18] **SEAN PARENT:** And I think he did that in Swift. And so it, it became, uh, uh, swift protocols and is, uh, you know. A, a very, very useful and viable feature within the swift language. 

[00:16:29] **RAY NOWOSIELSKI:** [00:16:30] How did you, how many, um, amongst the, the major, uh, boost, you know, managers, authors, maintainers, the really impactful guys, uh, how many names would you tick off that you've personally hired at the one point or another?

[00:16:46] **SEAN PARENT:** Oh boy. Uh, uh, you know, the, I think it's. It's probably just Dave Abraham's maybe. Uh, you know, David Sankel I think has contributed some, some things to boost. But as far as a [00:17:00] major contributor, um, uh, uh, uh, Dave Abraham's would be, would be it. I never hired Doug. Oh. So, so, yeah. Yeah, yeah. Doug is at, at Apple.

[00:17:10] **SEAN PARENT:** Uh, I, you know, Dave and I have discussed this. We can't even remember the first time we met. Uh uh, it might have been at the, uh. A, a, a workshop that I mentioned before. We had a generic programming workshop here at Adobe, so that might've been the first time that we met. We also spoke [00:17:30] at a, at a very early C++ conference.

[00:17:32] **SEAN PARENT:** That was in Las Vegas. We were both speakers at the conference that we might've met there. Um, I attended one C++ standards committee in Bellevue, so we probably. Met or Remet there. Uh, Dave Abrahams, uh, uh, is somebody who ran a consulting business Boost Pro. Uh, he was a major contributor to the Boost Libraries.

[00:17:54] **SEAN PARENT:** He also did the standard library for Swift, uh, at Apple and [00:18:00] worked on Swift UI at Apple. Um. Uh, uh, uh, uh, uh, super smart, um, uh, uh, uh, quite prolific. Uh, uh, I give a talk on the history of generic programming. Dave gets a slide on that talk for his contribution of, of the, the guarantees for exception handling.

[00:18:23] **SEAN PARENT:** Um, uh, which was a very important contribution, uh, to generic programming. Uh, uh, [00:18:30] I think he was also involved with the, uh, pre-processor library, and there's a python interop library in there that he, he was involved with. We tried to hire each other kind of back and forth for a number of years, so he tried to hire me back into Apple.

[00:18:44] **SEAN PARENT:** Um, I tried to hire him here. The timing was just never right. Um, uh, uh, when I had the opportunity to reform the software technology lab at Adobe, he was one of the first people that I reached out to, [00:19:00] to pull into that, and the timing was just right, so I managed to snag him. Uh, uh, uh, pretty much everything we're doing is a collaboration, so, so it's, it's, uh, a constant.

[00:19:13] **SEAN PARENT:** I, I would say Dave Abrahams is incredibly detail. Oriented, uh, uh, he has a really good eye, uh, for, for making sure that language is precise [00:19:30] and that things are well specified and that there aren't any gaps in the specification. Um, that's kind of his superpower. Mm-hmm. So he's a good person to, to run a presentation by or run a paper by, 'cause he will find the holes, holes in it quite quickly.

[00:19:46] **SEAN PARENT:** Um. No, when, when I think of Dave, I, I just think, you know, he's just, he's a, he's a very nice guy and a very smart guy. Um, I don't know if I have any, any particular Dave antidotes. 

[00:19:58] **SEAN PARENT:** Dave is notorious [00:20:00] for, uh, uh, uh. Uh, not doing his own planning. So like the first business trip we went on, you know, we got to the hotel and we're checking in and he's like, he turns this to me.

[00:20:13] **SEAN PARENT:** And he's like, he's like, did you check me into the ho or did you make the reservation for me at the hotel? I'm like, I'm, I'm not your mom, Dave. No, I didn't make your reservation. Didn't book your flight. Didn't, uh uh, uh. Boy. [00:20:30] Yeah, I, you know, honestly don't know much about Matt's direct contributions to Boost.

[00:20:36] **SEAN PARENT:** That kind of happened before he joined my team. 

[00:20:38] **RAY NOWOSIELSKI:** Who is Matt Marcus?

[00:20:39] **SEAN PARENT:** Uh, so, so. Matt Marcus is a developer. Uh, uh, he had worked on a number of teams at Adobe. Um, uh, I pulled him into the first software technology lab 'cause he, uh, uh, was pretty vocal about C++ and clearly had strong, [00:21:00] strong programming chops.

[00:21:02] **SEAN PARENT:** Um. Uh, uh, uh, within the software technology lab, uh, he did a lot of work on the Adobe Source libraries that I mentioned before, or another, uh, you know, another set of set of open source libraries contributed a lot to that. Um, uh, uh, uh, within that he wrote, uh, uh, uh, one of the very early libraries that was a framework for doing type erasure.

[00:21:27] **SEAN PARENT:** Uh, so. Dave Sankel, another [00:21:30] very experienced engineer. Uh, I hired him out of Bloomberg. Uh, he had had managed a, a, a team at, at Bloomberg, um, also very well known in the C++ community. Um, had been a, uh. Uh, uh, had a strong involvement in, in Boost. Uh, now we started the Beman Libraries, which is kind of a successor, uh, uh, uh, to boost this time a little more focused on, on vetting libraries for standardization as opposed to [00:22:00] to, uh, a, a, a building out libraries as a, as a separate way of gaining experience.

[00:22:08] **SEAN PARENT:** So, so. Somewhat overlapping the Boost Charter, but within Boost. Yeah. The idea was to vet libraries and then if they seem to pan out, then turn them into standards proposals to incorporate into the standard. And the new Beman library is, my understanding is the idea is to start from a standards proposal and [00:22:30] then, uh, uh, you know, build out the library and gain some experience to improve the standardization effort.

[00:22:35] **RAY NOWOSIELSKI:** How did you first, uh, really get to know Dave Sankel? 

[00:22:38] **SEAN PARENT:** Uh, through Dave Abraham's, uh, uh, so they had just been friends, uh, uh, uh, I think from both being involved in, in C++ and with Boost and, and, um, uh, uh, so yeah, so, so when Dave Sankel, uh, uh, uh, kind of. [00:23:00] Reached out to Dave Abraham's that he was looking for a job Dave brought him to, to my attention, and we, we, uh, made it happen.

[00:23:09] **SEAN PARENT:** Uh, brought him on as a member of our software technology lab and, uh, uh. Originally he was reporting into me and I was managing the team. Uh, but one thing that, uh, attracted me to Dave Sankel, he is, he just has amazing skills for, for management and for navigating [00:23:30] corporate bureaucracies. And so, uh, groomed him to take over my role.

[00:23:36] **SEAN PARENT:** So now he's managing, um. Uh, the tech foundation's research and I just get to be a contributor.

[00:23:43] **RAY NOWOSIELSKI:** Do you have a sense of how he developed those skills. Common in tech?

[00:23:48] **SEAN PARENT:** Are they, they're not common in tech? Uh, uh, I think part of it has to be the, just the size of his family. I think he has, uh, nine going on, 10 kids here.

[00:23:57] **SEAN PARENT:** Um, so a very large family. [00:24:00] Uh, uh, uh, but he also, um, managed a fairly large organization inside of Bloomberg and, and so, yeah, so. It overlapped it a little bit. Uh, you know, as a research team, I give my, my employees the freedom to kind of pursue some of these, these outside, um, uh, uh, uh, uh, uh, uh, uh, interests.

[00:24:22] **SEAN PARENT:** So, so Dave Sankel tends to be involved both in standardization process and in, [00:24:30] um, uh, uh, several conferences and with Boost and now with Beman. So these are all. Somewhat as side projects, but they all do have a, a tie back to Adobe and that it's in Adobe's best interest to contribute to standardization and to boost libraries and things of that nature.

[00:24:47] **SEAN PARENT:** He's, uh, I believe he's Catholic or, yeah, Dave Sankel is catholic. Uh, his wife is from, from Spain, I believe. Uh, uh, uh. An amazing set of [00:25:00] kids. I mean, they put up a, he's another, another musician in the bunch. Uh, uh, he also plays guitar, so he likes to jam with Dave Abraham's, uh, Nick DeMarco, who's the other person on our team, also plays guitar.

[00:25:13] **SEAN PARENT:** I'm the 1, 1 1 individual who does not, uh, play, play music instruments. So 

[00:25:19] **RAY NOWOSIELSKI:** how would you. How would you rate them as musicians? 

[00:25:22] **SEAN PARENT:** Uh, I think they're all, all quite good. So yeah, I grew up around musicians, so, uh, uh, yeah. Yeah, I think they're all quite [00:25:30] good, all different styles. Um, but, uh, uh. Yeah, in 2022, I was, I was, uh, given the keynote C++ North.

[00:25:40] **SEAN PARENT:** Um, uh, uh, and I decided to call it the tragedy of C++. And I meant tragedy in the sense of kind of a Shakespearean tragedy, right? So, so I outlined, uh, uh, you know, three acts viewing C++ as kind of the protagonist in this story arc. [00:26:00] And, and so the, the, the keynote itself covers act one and act two, and Act three is a question mark.

[00:26:07] **SEAN PARENT:** Where, where do we go? And, and so in Act one, I cover the history of C++ and where C++ came from, and kind of the rise of our, our protagonist to, to, to dominate the world basically, as far as programming languages go. And, and then in, in act two, I focus on, uh, [00:26:30] uh, uh, uh, uh, some of, some of what I view as the, you know, uh, Achilles heels of, of C++ it's rising complexity.

[00:26:40] **SEAN PARENT:** Um, I show the implementation of, of. Stood pair in the language, which should just be a pair of two values and you would think would be trivial. Imple implementation. Uh uh, but stood pair within the standard library is something close to 2000 lines of code. It's ridiculous. [00:27:00] Um. And the standard library, in my opinion, should be an example of how developers should write their code.

[00:27:07] **SEAN PARENT:** And so if your example for how to write a pair of two values is 2000 lines of code, uh, the complexity is more than, than most reasonable developers can, can digest. Um, uh, also we tend to use C++ for performance, but if you're looking at just single threaded, uh uh, uh, uh. A [00:27:30] a C++ running on A CPU, uh uh, you're only able to use about 0.25% of the machine because most of the performance of the machine is locked up in the GPU and in the sim d units.

[00:27:44] **SEAN PARENT:** And C++ doesn't have a standard way to access those. It's the language. That is used to access those things, but within the standard, there's no, there's no standard GPU support. There's no standard sym d support. Um, uh, we do have standard multi-threading [00:28:00] support. Um. Uh, uh, uh, uh, uh, uh, but that's very limited and in some sense very harmful in that it encourages developers to spin up threads.

[00:28:11] **SEAN PARENT:** And you really don't want more threads executing on your hardware than you have cores on the machine to execute. Otherwise, you're overcommitting and you're pain attacks, um, uh, every time you have to, to swap context between those threads. Um, and there's no standard access for. For how do you [00:28:30] get to kind of this a system thread pool and, and, and access the, uh, the threads on that nature?

[00:28:36] **SEAN PARENT:** So, so there's these, these big, huge gaps that haven't been addressed by the language and, and this. In my opinion, the standards kind of overturned to, to optimizing in the small and not optimizing in the large. So there's a lot of complexity that goes into the language to try to squeeze individual cycles out of, [00:29:00] of, of function calls.

[00:29:02] **SEAN PARENT:** Uh, uh, uh, when you're leaving more than 99% of the performance on the table. So, so you're, you're counting cycles when you should be counting, counting in, in, in big buckets. And finally, there's this dilemma within the community that, uh, you know, C++ is a memory unsafe language, and that's causing growing concerns within the industry, especially, [00:29:30] uh, uh, kind of every major, uh, uh, uh, security agency in the world has issued, uh.

[00:29:39] **SEAN PARENT:** Uh, uh, guidance to stop using, uh, both C and C++ as as languages, um, uh, uh, and the standards committee. Has not adequately addressed that issue or taken a hard, hard pivot on it. There was one fairly strong proposal to bring memory safety to C++, [00:30:00] and that was shot down. The tragedy ending is it continues on, on what I view as kind of its current path of, of growing complexity and, and ignoring, uh.

[00:30:14] **SEAN PARENT:** Uh, uh, uh, kind of the landscape of modern hardware, um, uh, and modern security concerns. Um, uh, uh, you know, in which case, uh, uh, uh, uh, it becomes something that the industry just slowly [00:30:30] migrates away from. It becomes cobol, right? You know, 30, 50 years from now, there will still be, you'll still be able to make a, you know, great career writing C++ code 'cause it's not going away.

[00:30:42] **SEAN PARENT:** Um. Uh, uh, uh, uh, uh, uh, but it may not be what you think of when you think about starting a new project or, you know, it will be relegated to legacy systems and maintaining old legacy code. Um, uh, uh, uh, I [00:31:00] think in many sense, C++ is still set up, uh, uh, better than most languages to, to make a, a pivot.

[00:31:09] **SEAN PARENT:** Um, the two. Two competing languages in the space right now are, are swift and, and rust. Um, uh, uh, uh, rust certainly has growing momentum behind it and has a lot of advantages, but I don't think rust has proven itself out at scale. It's still [00:31:30] has some significant gaps. Um, uh, uh, you know, for, for. Commercial products, uh, uh, uh, and that's going to take time to fill.

[00:31:41] **SEAN PARENT:** So, so I think, you know, C++ could pivot, um, uh, uh, could address some of these concerns. Um, I don't know if it will or not. I, I think that Boost could help in, in, in a pivot for the language [00:32:00] in the same way. Um. Uh, uh, uh, that boost had such a major impact on, on C++ 11 and where the language was going in that timeframe.

[00:32:12] **SEAN PARENT:** In, in that, uh, you know, uh. Strong set of libraries that are written in a way, uh, uh, that both meets customer needs and sets a direction for where things can go, can influence significantly the [00:32:30] design of the language. And so I think if there was, uh, a more effort in rust to say this is what a standard sim d library should look like, I know there is a minimal sim d library.

[00:32:45] **SEAN PARENT:** Slated for Lake C++ 26, something like that. Um, uh, uh, uh, so Russ could do more there. If Russ could look at what would, uh, uh, uh, a common C++ standard language support [00:33:00] look like for GPUs. Uh, that could have huge value if they started to structure the libraries to say, look, if we had.

[00:33:10] **SEAN PARENT:** Safety features in the language then libraries structured in this fashion would be conformant that we don't, you know, we don't need aliasing and we don't need unsafe casting and we don't need these constructs in order to, to build a library. If they could demonstrate that and then come up with language proposals, uh, uh, [00:33:30] that we said, you know, if we had these language, we could make these guarantees and our code would still work.

[00:33:34] **SEAN PARENT:** Um, I think that that could have an. Huge influence. So I think there's an opportunity there to, to start to do that. Like I said, I don't know if, uh, uh, you know, I, I see no indication that that's the direction that the standard, uh, uh, is choosing to go in a lot of what I see that was driven in the early day days of, of boost.

[00:33:59] **SEAN PARENT:** [00:34:00] Came out of, of universities. A lot of it came out of Andrew Stein's team at at Indiana University. Um, uh uh, so I think, you know. Boost establishing strong connections with one or more universities, uh, could play a, a, a pivotal role. And some of the people who came out of Andrew Lang's team are now professors in their own rights.

[00:34:26] **SEAN PARENT:** There's like Jeremy Siek who might have some interest in this area. [00:34:30] Um, there's also that I can think of Hartmut Kaiser who has HPX for the high performance libraries. Uh, uh, uh, you know, his team might have, have some interest in this area. Uh, uh, uh, but I think, you know, getting that, uh, uh, you know, kind of young research focused, uh, uh, uh, uh, DNA re-injected into the project, um, uh, you [00:35:00] know, people who are looking at these, at these.

[00:35:03] **SEAN PARENT:** Big problems with, uh, uh, uh, uh, fresh eyes, a fresh view, um, uh, would be, would be one way to move forward.

[00:35:12] **RAY NOWOSIELSKI:** You lay out a three act structure. Uh, yeah. So you've got a story brain. Uh, you know, these stories tend to have protagonists and sometimes they have antagonists. Uh, yeah. Is there anyone to blame for the quote unquote tragedy of C++?

[00:35:26] **SEAN PARENT:** I would. Point fingers at the [00:35:30] community as a whole. Right. And I think the biggest failure that the, or, or I should say, I would point fingers at the, at the, for, for, for the antagonist, for C++ at the standards committee as a whole. And I think the biggest problem with the standards committee is, is an unwillingness to.

[00:35:56] **SEAN PARENT:** To specify what the [00:36:00] goals are and basically what the rules are for the, for the standards committee. So, um, every decision that the standards committee tends to make tends to almost be made in isolation. And, and they don't then document the rationale for that decision. And so when a similar decision is made, they ate it and maybe come up with a different answer.

[00:36:24] **SEAN PARENT:** And I think that's the reason for a lot of the inconsistency in the language, for a lot of the warts in the [00:36:30] language and for a lot of the complexity. So, you know, even what I would consider, you know, basic things like saying, you know, all, all new types within the language should be regular, uh, doesn't happen and doesn't.

[00:36:42] **SEAN PARENT:** Get held up, uh, regular in this sense is a, is a, a, a, a term of art for generic programming and concepts, uh, uh, uh, which means that a, a type has as a particular set of semantics and, and, um, uh, uh, you know, follows a set of [00:37:00] rules. So copies of that type are equal to each other. Bjarne Does, but Bjarne is not a dictator, right? It's, it's in fact the, you know, the way it's an ISO standards committee. So if you go and look at the rules, the way it's structured, even though. I, I think it, it may still be, it used to be a, a combination of an ANSI ISO committee where ANSI is kind of the US body, but the US body as a whole gets one [00:37:30] vote, right?

[00:37:31] **SEAN PARENT:** It's an international standard. And so each country gets one vote, uh, that has rep representation on, on the committee. So even if you have a hundred people from the us, Bjarne being one of them. That only gets to distill down to one vote. Uh, uh. So Bjarne might have a, you know, a, a a a more sway than most in, um, uh, in, in getting a vote through.

[00:37:59] **SEAN PARENT:** [00:38:00] Uh, uh, but he doesn't even have one vote, right?

[00:38:07] **SEAN PARENT:** I don't wanna speak for fear for Bjarne and how, how Bjarne feels about. Uh, a a about boost in, in particular? Um, uh, I think I, I definitely think he seems conflicted. There's certainly a sense that, that, you know, there are many different aspects of, of, of boost and, [00:38:30] and one criticism that you could have of boost is it kind of over pivoted on, on the idea of meta programming of, of using templates to write.

[00:38:42] **SEAN PARENT:** Programs that then the compiler uses to write your program. So it's a way to, to program a program. And, and this notion of meta programming, uh, uh, a lot of people view that as the, uh, uh, key piece of [00:39:00] boost. Um, uh, certainly there are things like, you know, MPL, which is the Meta Programming Library, which is a library in boost.

[00:39:06] **SEAN PARENT:** Um, and that just brings a lot of. Complexity and noise, and it's useful if you're a library author, but it shouldn't really be the, the, the thing that's held up as this is the, the thing that people should be using from boost. You know, at the same time, those facilities get build used [00:39:30] to build very concrete types like, like, you know, boost function or boost any, which are now part of the standard.

[00:39:36] **SEAN PARENT:** Um, uh, uh, uh, uh, which are just very elegant. Encapsulated things, even if their implementation might be very complex on, on the backside. Uh, there are things like the Boost Graph Library, which extends the notions from, from STL into, into graph data structures, uh, uh, which is another very elegant piece. Uh, uh, [00:40:00] so, so I, I can see being conflicted.

[00:40:04] **SEAN PARENT:** Right? Right there, there are pros and cons there, and I think, uh. You know, if you talk to a lot of companies right now, they will say, well, one issue that they have is, is now that large portions of boost have been standardized. They would like to be able to migrate to the standard versions. And in some cases that can be very hard.

[00:40:24] **SEAN PARENT:** And so, so boost becomes. Almost synonymous in, [00:40:30] in, within some organizations as, as legacy stuff that must be removed. Uh uh, but that's not completely true, right? There are, there are large portions of Boost that are not standardized and are incredibly useful. I, I certainly wouldn't refer to it quite that way, and that, you know, Beman very much set up boost as, as initially as a way to, to gain experience on libraries for standardization.

[00:40:57] **SEAN PARENT:** Um, uh, uh, [00:41:00] uh, uh, uh, and a lot of that happened, right? Right. Um, uh, uh, so I think in that sense, it was a, it was and is a very successful project. Um, uh, you know, my take on it is, is the boost demonstrated a lot of what. It was possible in C++. And it came with a lot of [00:41:30] complexity, and I would love to see more of that complexity pushed in into the, the, the language level.

[00:41:40] **SEAN PARENT:** So, um, uh, uh, you know, some of it has been things like very addicts came out of boost, things like Lambdas came out of Boost. Um, uh, uh. Uh, uh, but there's still a lot that's, that's, that's [00:42:00] not there, right? Just a common thing that you might, might see in boost is a type function and which is just a function that that takes a type and returns a type, as opposed to taking a value and returning a value, and yet the syntax within C++ to write a type function.

[00:42:20] **SEAN PARENT:** Looks nothing like how you would write a function for values. And that's only because, uh, uh, uh, [00:42:30] uh, type functions were developed kind of accidentally exploiting the template mechanism. And it's like, well, it's time to build that into the language as a first class thing. Uh, uh, uh uh, but that hasn't happened yet.

[00:42:44] **SEAN PARENT:** Uh, I was only involved with it in the sense that I was. Was pushing on, on, on Dave Abraham's at the time to say, look, you need one license. This is ridiculous. Um, uh, uh, it's, it has a serious impact on your [00:43:00] adoption within industry. And so he agreed it was just a question of what license and, and how to go about it.

[00:43:07] **SEAN PARENT:** And so, so when he did come up with a draft for license, you know, he could have, in my opinion, he could have picked. One of the commercially friendly open source licenses that was out there. You know, there's the, the Berkeley standard license, or there's the MIT license. Um, uh, uh, uh, uh, uh, he wasn't quite happy with [00:43:30] the terminology and those licenses, so he wanted to work with lawyers and develop his own.

[00:43:34] **SEAN PARENT:** Um, so you would have to ask him the whole story, but I think he contracted with a, with a lawyer to, uh, to draft the light. Draft the license and refine it. And then I ran it past, uh, Adobe Legal and, and fed their, their input back to Dave to make sure that it was, was, uh, uh, uh, acceptable for, for Adobe to use.

[00:43:59] **SEAN PARENT:** Yeah, so, [00:44:00] so the. Kind of standard defacto is if you author something, then you own the copyright on it, whether or not you put a copyright statement on it or not, and you own, own the rights for how that's distributed and how that's used. And so, you know, initially you just had authors stamping their, their thing, you know, copyright, you know, Franklin and uh.

[00:44:27] **SEAN PARENT:** That's a huge problem because now Franklin has just [00:44:30] declared that he has the total rights to this, and he hasn't said what those rights are or whether or not you can use it or, or, or how it's used. Legal gets upset too if you just have, uh, something that says, um. Uh, uh, uh, you know, this is, is free to use and we provide no guarantees on it because if you provide no guarantees on it, that means that you're not guaranteeing that somebody else doesn't have rights that are included in this.

[00:44:58] **SEAN PARENT:** So there's no [00:45:00] indemnification, there's no statement that says that, that I developed this and therefore you can have it. You're, you're basically saying. I'm not making any guarantees about the origin of this, whether I wrote it or not. Uh uh, so, so phrasing in, in that, uh. A, a, a sense becomes problematic. Um, you know, language that puts requirements on a product using it becomes problematic.

[00:45:27] **SEAN PARENT:** Whether it's, it's requirements about, [00:45:30] uh, uh, uh, giving credit and how that credit should appear and whether that credit should be, or whether or not you, you know, contributions also have to be open sourced. And where does that have to be hosted and how is that managed? Um, uh, so there are just all these little details when you're looking at.

[00:45:46] **SEAN PARENT:** How do you pull something in for commercial use and, and and, and, and, and what are the limits and how are you going to track them? And, and the more burden that's put on the commercial organization, [00:46:00] the less likely they are to, to accept that license. So. So, you know, you don't want something that says, oh, every time you launch Photoshop, you need to see scrolling credits of of every single library that went in before you can use the product, for example.

[00:46:17] **SEAN PARENT:** That would be problematic. 
