# Transcript: Huddle with Matheus Izvekov

**Date:** January 7  
**Time:** 9:51 AM to 11:02 AM Pacific Time (US and Canada)

*This transcript is auto-generated, so some information may be inaccurate. It won't be surfaced in search results.*

---

**Vinnie [1:42]:** OK, Mattias, all right, so I'm gonna ask you some questions. So do you remember when your first meeting at WG 21 was?

**Matheus Izvekov [1:52]:** It was the one in Saint Louis, middle of 2024, I mean, the first one in person, yeah.

**Vinnie [2:02]:** Oh wow, 2024. Had you attended any meetings virtually?

**Matheus Izvekov [2:04]:** Yeah. Not not like a full mini but like some, you know, like, extra medi, you know, not, not, not the ones that happened, they're schedule. They're like, they're like everyone, right? They have the plenary, but like some sessions, you know, like sometimes core or EWG does an extra session that's online only and I participated in a couple of those before that.

**Vinnie [2:37]:** Oh, very nice. And do you remember when was the first time you wrote a paper?

**Matheus Izvekov [2:43]:** Oh, that was a long time ago actually. That, that one was around 200014. It was, yeah, like it was the the mall, bug fakes, paper, they're like someone else, took it over from me eventually, because I, I, at the time I couldn't attend, you know, so I that was the first one and then

**Matheus Izvekov [3:12]:** I didn't do another one until like I was, well, each like doing clank stuff and then I joined Bloomberg and some of the Bloomberg, you know, things that are, I had done for them was write papers for them.

**Vinnie [3:30]:** When do you remember the subject of your first paper or the paper number? Like what was the technical topic?

**Matheus Izvekov [3:36]:** It was about, Trivial, a trivial copyability, right? was a very weird issue that we had before Cpospola 17. Well, like type could have like deleted, destructors, you know, or like copy constructors, stuff like that, and still like be considered trivially copyable. that there was something

**Matheus Izvekov [4:10]:** That like it was eventually merged and fixing, she was 17, but like building off with someone else build off out of my work in following papers, but I, but I'm looking for the paper number here. Hold on.

**Vinnie [4:26]:** That's actually very good. So, yeah, if you could find the paper number, I would like to have a look at that paper and then I want to ask you some specific questions regarding that paper.

**Matheus Izvekov [4:36]:** OK

**Vinnie [4:37]:** I think it was called Disallowing Inaccessible operators from trivially copyable.

**Matheus Izvekov [4:43]:** Yes, yes, that's the one, yes.

**Vinnie [4:45]:** So that's document number N4148 dated in September 24, 2014, addressing the PLC and the evolution Working Group. This proposal aims to solve a serious flaw in the definition of the trivially copyable concept. Presently classes with deleted or inaccessible copy and move constructors, copy and move assignment operators and disruptors are allowed to be trivially copyable, which might seem counterintuitive. Is that what you remember?

**Matheus Izvekov [5:19]:** Yeah, yeah, that, that, that's what I heard, yes.

**Vinnie [5:22]:** Do you, how did they, how did people discover the problem?

**Matheus Izvekov [5:27]:** No, the so, I discovered the problem, like basically in an argument on the STD proposals, you know, like I was, you know, like arguing something with someone, and they're like as part of my research into one of those points, I found that issue, well, like it was related to something that I was doing at the time

**Matheus Izvekov [5:57]:** There was like basically, you know, like some, some rappers, you know, like, I had I was riding a wrapper while I, I was expecting that I would somehow be able to preserve trivial cultability, you know, so like basically if the type being wrapped, like it's tributed copyable. I, I wanted to guarantee, you know, like my rapper would be as well and the, there's like tos of like little

**Matheus Izvekov [6:27]:** Issues. So I, I don't remember all the details right now, but there are tons of little issues that still exists today, but like don't, don't allow you to like write a rapper, you know, in C++, the like, you know, it's the guaranteed to like never, you know, cause some kind of performance regression, you know, because sometimes, like you can make, you know, like a function call with that wrapper, have a different

**Matheus Izvekov [6:57]:** ADI then we we the rapper, you know, other things are, there are allowed, they're like very hard to like fix in the standard, right? and I was working on that and then it came upon that issue that like same like simple enough to solve on its own, right? But it's a small part of the problem, yeah.

**Vinnie [7:06]:** OK, let me So Mattias, let me see if I can summarize. So what you're saying is that before this, the bug fixed in this paper, it was impossible for someone to create a rapper that propagated the trivial or copyability from the inner object to the wrapper.

**Matheus Izvekov [7:39]:** So like, not, not it doesn't, the, the paper doesn't fix that entirely, right? That paper came out of me like looking into that problem, but only solves like a small subset of that, you know, like, about, you know,

**Matheus Izvekov [8:03]:** If you like if you're Wants, you know, like the reverse, like preserving non Popular triviality, you know, then there's something that, that paper might fix, but it, it, it doesn't solve all that problem, that that's the point that I, that I'm trying to get, right.

**Matheus Izvekov [8:27]:** But, but, but, but at least that one like it was eventually

**Vinnie [8:27]:** Yeah

**Matheus Izvekov [8:32]:** Went into C++ 17 and it's fixed now, so.

**Vinnie [8:37]:** Yeah, that makes sense. So, so now let me ask you this. Is it possible for this type of Flaw in the definition. So in other words, so your paper addresses a flaw in the wording, right? In other words, the standard itself had a bug, so to speak. It's not a bug in the code, it's a bug in the wording of the standard C++ specification. So is it possible that this type of bug could happen again? In other words, when people are working on either standard library proposals or language proposals. Is this the sort of thing that could happen again and then it would need another fix.

**Matheus Izvekov [9:15]:** Well, let, so, we, we gotta make like a small like the limitation differentiation here, right? There's like what do you mean like when you say like a wording bug, there's so there's like two classes Or two kinds of major bugs, I would say like in the standard. There's like editorial bugs. They're exactly like problem, how, the standard was worded, you know, like people wanted it to say something and then the standard said something else, and that's like a very simple thing to fix because like a fix to that kind of problem, like it's just like me

**Matheus Izvekov [10:00]:** Sometimes not even the paper, right? There's sometimes fixing editorial issue doesn't even require a paper, but like it goes through CWG directly and then, you know, like they just fake the standard draft, there's no vote or anything and then like it just goes there, there are no technical vote at least I mean, and then like he goes to the standard and, and, and becomes a DR

**Matheus Izvekov [10:30]:** If applicable, right? It's like an old thing, but like, another thing is that like, Problems in the wording where like, it looks obviously wrong, but like you can't exactly make the case, like people didn't want to say that because you can't like really see, you know, like from whatever source that came from, like what really, people wanted to do there instead of like being just, you know, like something people didn't think through and those kinds of things usually like

**Matheus Izvekov [11:07]:** Require a paper that nowadays like we're being even more bureaucratic than we used to be. You know, they're usually like even needs to go through EWG to fix that kind of stuff, you know, and then like you present the paper, you know, like, technical vote, they then plenary, and they go to CWG so like tho those kinds of issues are more complicated and and and like that paper is that kind of issue, right? Like it wasn't

**Matheus Izvekov [11:37]:** Something that the like could be fakes, very, you know, like efficiently, you know, within the bureaucracy, right? So that, that's why I didn't, you know, like, carrying it over the finish line myself, and I relied on someone else that was, you know, like a to go be present at the meetings and everything at the time.

**Vinnie [12:03]:** Understood. Well, that's, that's, so that's very interesting. So, when you You're, you're describing a lot of the process. In other words, you're telling me that some things require a big vote. Some things are less procedural. Some things are like bug fixes and they're not as hard to get through because they just require like a very small change to correct and obviously visible defect. How did you learn about that process? Like did somebody teach that to you? Was that written down somewhere? Was that something that you were doing? Did somebody explain it to you? Who, what did

**Matheus Izvekov [12:25]:** Yeah No Yeah

**Vinnie [12:38]:** Anyone like, was anyone a mentor to you and to kind of guide you through the process. How did you tell me about your experiences. I want to hear about your subjective experience.

**Matheus Izvekov [12:48]:** So I, I can't Like I, I can definitely say that like no one came to me, you know, like they try to explain all those kinds of things at once, you know, like that, that kind of mentorship never happened to me like I, I always, you know, like try to like figure out stuff on my own, right? And like a, a lot of that stern stuff, you know, I probably like learn a little bit, going through, you know, like the, the

**Matheus Izvekov [13:20]:** Whole process is 2014, and then, you know, like it became more solidified as I started going to the meeting, you know, and that like all the stuff became visible, because like I, I right now I'm working on, I, I have papers. My papers are in flight, I kind of like very technical bug fixing things, and then and going through like a lot of

**Matheus Izvekov [13:50]:** You know, like process, right? There's a lot of process overhead, you know, like, part of it, you know, is that it, it is bureaucratic but part also the like one of the only You know, like persons, the like that know understand the, the problem that there is like still active, you know, like WG 21, like the, you know, like things around overload like template, partial template specialization partial or you know template deduction, this is like our, are things that like,

**Matheus Izvekov [14:31]:** Were specified and worked on mostly, you know, like even like way before C++11 rate and the people that worked on that kind of stuff like kind of retired or like become very inactive, you know, like, a long time ago and I'm kind of like

**Matheus Izvekov [14:54]:** Trying to feel that void a little bit. So part of that, you know, is a, is, is a really some of the problems are hard, you know, like, and, my experience lies more in like the compiler implementation, you know, like, I'm not as an expert in the wording as I am in like how everything is, you know, like implemented in the compiler. It's, it's sometimes it's hard for me like to translate, you know, like what I know

**Matheus Izvekov [15:24]:** From like knowing how the compiler does it from like how, you know, like people mentalize this, you know, when they read their standards. So the, the, the, there's a lot of, you know, like work, you know, in that kind of problem, you know, like where I, you know, I try to make a wording, you know, and then I realized, OK it's like that wording wasn't exactly what I, what I thought, you know, like, was supposed to mean, you know, and, and,

**Matheus Izvekov [15:54]:** There, there's like people That, you know, like, yans, you know, and some, some people in court, they they like that can help with that kind of stuff. But like the, there are, you know other points that they're like overloaded with other kinds of work. So they are only times really that, that, you know, like those aspects of my paper, get any help from those people when, you know, I, I get a fashion, you know, like my, my paper is gonna be seen, and then I, I got feed

**Matheus Izvekov [16:27]:** B ack in that session and then I got to work it and then, you know, like several months. Later, I got up, come back, you know, and yeah, and then sometimes I will have worked, in the other problems, you know, for a long time and and things would not be as fresh.

**Matheus Izvekov [16:48]:** You know, in my memory anymore. So yeah, that, that, that, that, kind of like overhead, you know, like that gap between sessions is all like not very helpful, you know, but it, but, but it, you know, like that, that's I, I don't have, you know, like a solution for that, you know, like we've gotta fix the standards somehow and got a go through the process, I guess.

**Vinnie [17:14]:** Very good. So would you, so I'm gonna, I'm, I need, if you could just give me like short, I want to ask a series of questions very quickly and I just want a short quick answers for now. So you know a lot about templates.

**Matheus Izvekov [17:22]:** Oh OK Yeah, I guess, yes.

**Vinnie [17:28]:** How did, how did you learn, how did you get interested in knowing about templates.

**Matheus Izvekov [17:34]:** Like from, you know, like, use their perspective, you know, like my work and my hobby projects in the past, like I have written a lot of coreli on templates, and then I like, like them, you know, and then, when I started working on plan that, that's like the area I was focused on mostly, right?

**Vinnie [17:57]:** So ear earlier, I think it helped me understand. I want to make sure that I understand something that you said earlier. I think what you were saying is, is that you have a deep understanding of templates and the template machinery and in your mind you have an intuition of how a compiler should implement things. However, very often you have difficulty communicating those ideas to others and especially in coming up with the wording for how the templates aren't supposed to work because standard ease is very difficult, and the

**Vinnie [18:27]:** Specification has to be perfect, and it's also a very complicated field. In other words, template instantiation and specification. It's highly complex with a lot of little corner cases and edge cases, and you have a lot of knowledge and experience with that, and it's sometimes it's difficult to capture in writing.

**Matheus Izvekov [18:46]:** Yeah, yeah, like in, yeah, yeah. I, I mean mostly working, right? Like the wording is like very falls very short, you know, like everything, but like the copala does is not like very as exactly, you know, describing of things, you know, and it has like kind of like a different anthology, you know, then like what the Copala does, so like the, there's a a little bit of difficulty in translation, you know,

**Matheus Izvekov [19:16]:** Like the standardized ontology, you know, like the clang ontology, right?

**Vinnie [19:21]:** Yes. So when you, so when you write a paper having to do with templates, and then you go and it goes to committee, so other people have to read the paper and then they have to understand it and then usually there's a vote or there maybe there's some feedback. So where would you say that you rank in terms of your knowledge and expertise, and I'm not, I'm not trying to critique anyone. I'm not trying to throw anybody under the bus. We don't need any names. However, the reality is that certain certain areas have individuals with expertise.

**Matheus Izvekov [19:24]:** Oh.

**Vinnie [19:51]:** And maybe the other people, their expertise lies in different areas, right? Not everyone knows everything about every domain in the C language. So when you participate in discussions when your paper is being presented, where do you think you land in like on the skill level, towards the high end, towards the low end.

**Matheus Izvekov [20:08]:** Yeah Yeah, like that, so like for, for the subject, you know, like that I described, you know, and like certainly for the subjects of my paper suddenly on the very high end, right, because clearly, you know, like, people, you know, like don't really know much about, you know, like, you know,

**Matheus Izvekov [20:33]:** Template argument deduction or like partial ordering anymore, right? So the definitely on those subjects on the high end, sure.

**Vinnie [20:42]:** So when those, when those meetings take place and you have to, and you have to convince other people that you're, that your paper is correct. You're interacting with other people that don't have like that same level of deep understanding of the templates that you have, does that affect your paper? Does that create a negative outcome? Like, do, does that just result in you maybe you have to take some extra time to explain things to them, like, what's that experience like for you?

**Matheus Izvekov [21:12]:** I, it has been, I, I wouldn't say it like that, Like, that's sometimes I, I get like the Opposite difficulty, you know, they're like you, you would like first think of it, you know, because like I will, I will like explain so I my my, my first experience with my, my first paper that Saint Louis session was like when, you know, like in front of everybody, you know, like, wrote a very long like well explained paper, and, you know, like, at the end, like I got the feeling

**Matheus Izvekov [21:54]:** That a lot, not a lot of people, you know, like really absorbed, you know, like you, you know, like 30 people voted and those were not like high quality folds, you know what I mean? And then, you know, like when, when I got to court, they're like people in court, like they understand like other things, better or differently than like the people in evolution, right, and they found, you know, like things,

**Matheus Izvekov [22:24]:** That, you know, like I can't like, or your, your paper title, you know, like doesn't, you know, like suggest they're like, the, the paper containing this kind of change, you know, like, because maybe I had to do some, some slightly related change and then like they, they're putting question and, you know, like did people, you know, like really wanted to vote this, you know, and they're like I wanted to, had to go back to confirm things, you know

**Matheus Izvekov [22:54]:** And then, you know, like during the course session, realized like some kind of people like had initially misunderstood some things that I said, you know, and then like in the course session, they realized and that basically made me, you know, have to come back, you know, like, second time because of that and the drafted those concerns and everything. and, but besides

**Matheus Izvekov [23:24]:** That, you know, like, my, my, my paper has been flied for a long time, like some, some of the problem is that, but the other problem was the whole, you know, like we're shipping C++ 26 now, so we only looking at papers that are like important for C++ 26, you know, like features they're like gotta get in in the deadline and people say, oh, your paper is like,

**Matheus Izvekov [23:54]:** You know, like defect report, so like what whatever gets approved, it's gonna like, you know, get appro applied, you know, to the past versions anyway, it's like it's not urgent. So like I had some difficulties scheduling of some my papers, you know, in the, you know, like last few sessions because of the, that kind of issue. But, but, but that's kind of seasonal, right? And we're, we're going

**Matheus Izvekov [24:24]:** Back for general work, this year, so yeah, so.

**Vinnie [24:26]:** OK So let me clarify for the transcripts. So there, there's there's, there's two groups, there's two umbrellas. There's language and then there's library and temp things having to do with templates address the usually the language part of WG 21, and language is divided up into two working groups. You have the core working group, and then you have evolution Working Group and papers for language first go to the evolution working group where they are evaluated for their suit

**Matheus Izvekov [24:30]:** Mhm.

**Vinnie [24:59]:** Ability not at a deeply technical level but just directionally is this right for C++? And then if EWG approves the paper moves to the core working group for wording, and that is where there's a team of experts that have a very deep understanding of the C language, and they do the hard work of actually writing the standardese. However, the core working group is really unable to change any of the design. The only thing that they can do is send it back to the evolution working group for Changes.

**Matheus Izvekov [24:59]:** Yeah

**Vinnie [25:29]:** Yes or no. Is that correct

**Matheus Izvekov [25:31]:** Well, that's like technically on paper, correct, right? But like, the, the, there, there can be sometimes, you know, where, you know, like, people that are in car, they, you know, like see something that will have like an evolutionary objection, you know, the, they're like they feel strongly about something and they, they find some reason, you know, like to get things back to EW

**Matheus Izvekov [26:01]:** G you know, like more people to look back again, but like formerly like what what you're saying is like correct process. I mean, I would add that like nowadays, we also have like a third group, like EWGI, the EW gene incubator like some papers when they're like very early or from non-experienced, you know, orders and things like that. Sometimes those papers go to EWGI

**Matheus Izvekov [26:31]:** To like getting in good enough shape to go to EWG and then go on so forth, right?

**Vinnie [26:37]:** OK, that makes sense. I, I definitely hear what you're saying. However, with the, the reality is, is that it seems like

**Matheus Izvekov [26:40]:** Right.

**Vinnie [26:45]:** The, the split between core and evolution has separated the experts from the non-experts, right? In other words, core is very specialized. Not everyone can work there because Standard E is very hard to write, whereas evolution, the barrier is lower. I mean, it's much easier to come up with ideas without having the technical skill and the technical understanding to know if those ideas are going to be compatible with the wording that's already in the standard

**Matheus Izvekov [26:55]:** Yeah Yeah Yeah, yeah, what the, the, and that's like some problem that has been on my mind, a lot of times that like I mean fashion because like I realized CWG have, have some people that are like fully dedicated to CWG, you know, they like almost never in all the rooms, but they have like evolutionary concerns, right? And like when, you know, and a, a lot of paper

**Matheus Izvekov [27:41]:** S you know, maybe they go through EWG too quickly, you know, they wouldn't have gone, they would have gone like in a better shape to pour if some of these people were able to attend EWG sessions.

**Matheus Izvekov [27:58]:** But because they are like simultaneous and a lot of people are doing that on, you know, chattable, you know, being charitable with their time, you know, they're not actually, a lot of people are actually getting paid to be there, right? So like you can't really demand, oh, you know, like you should be somewhere, you know.

**Vinnie [28:20]:** OK, next, I want to move on to Let's talk about Tell, do you, do you remember any proposals that you looked at that they looked good on paper. In other words, like it seemed like a good idea, but then it actually failed in practice. Maybe it was standardized and then there was a problem that surfaced afterwards or maybe it went through many, you know, it went through several meetings and nobody saw anything, but then there was a problem that was found. Do you remember anything like that?

**Matheus Izvekov [28:50]:** So, I, I mean I, I can tell the story about It's still about my, my first paper, or not the first paper, but the, the first one that I did that I I was a member, in the, IO, that, that I defended in Saint Louis. So like that, that paper.

**Vinnie [29:08]:** I, can I, can I have the paper? Sorry, I'm sorry, Mattias, can I have the paper number, please? I would like to look it up and have it in front of me.

**Matheus Izvekov [29:17]:** Yeah, yeah, I, I believe it's B3310.

**Vinnie [29:24]:** OK, solving issues introduced by relaxed template template parameter matching ha ha ha, wow. Oh my God, OK.

**Matheus Izvekov [29:32]:** Yes

**Vinnie [29:34]:** This sounds very complicated. Wait, hold on, she's done. Let the tre let the transcript show that we're discussing P3310 are 6, which is published on June 8, no, May 18th, 2025, authors Matthias Isvikov and James Tutan. The title is Solving Issues Introduced by relaxing template template parameter matching. OK, please tell me the story about this paper from beginning to end

**Matheus Izvekov [29:34]:** Yeah, so like Yeah, so

**Matheus Izvekov [29:55]:** Yes Oh yeah So yeah, the, the story about this paper is that this is a bug fix, to, earlier paper by James Stoughton, right? They, they like joined me on my on the last revision because he he contributed with the wording on that paper and his paper basically

**Matheus Izvekov [30:25]:** So explaining a template template parameter matching a little bit before C++ 17, like a template, template parameter had to like match the like template had all the signature of the argument template exactly, right? you know, like she, she had an aunt, you know, template parameter, then no, they had to be in in both things, you know

**Matheus Izvekov [30:55]:** That there's like a small exception to that rule, but it, it doesn't matter right now. but then James Saker, proposed, you know, like, relaxing those rules to like say, like if the template, you know, like argument would work for that template parameter, you know, like you could, so the stood it, you know, into the body of the template like it would work for any kind

**Matheus Izvekov [31:25]:** Of like parameter you could pass through it, then like we would accept that match, that would be like a a tight theoretically like correct extension to the language, and his paper, basically somehow I, I wasn't active at the time, but it basically didn't go through EWG, right? It went straight to court and got merged and, and, and worse than that, like,

**Matheus Izvekov [31:55]:** It, it was considered like like a defect report, right? So like it was retroactively applied to the standard, and then like when people started implementing that on the compilers. They realized, oh, like this specification is really lacking here because we we like allow this extension, then like a bunch of codes, the like

**Matheus Izvekov [32:26]:** Relies on partial or like we we start relying on partial ordering because now, you know, like more than one template will match, you know, because the match is not exact anymore, but then like the paper completely lacked any wording explaining how, you know, like partial ordering works with that.

**Matheus Izvekov [32:50]:** With that, you know, like new wording, new feature, and then like that was broken for a long time because James didn't have time or the expertise to, you know, like figure out the solution. And and like some compilers implemented workarounds, but like it was never fixed and the workarounds were never good. And that, that was something actually that was

**Matheus Izvekov [33:20]:** Holding supplying for a long time for from like advertising C++17 performance. It was basically because we implemented that feature but we implemented no workarounds for it. So like, like we put it behind the flag that was disabled by default, so that, that basically made of not considered, we, we couldn't consider that we had implemented that.

**Matheus Izvekov [33:50]:** And then, you know, that was the reason, you know, like basically, oh, let me close a clang, 17 finally, you know, like we're already implementing 23 and the thing is not fixed yet. And then I worked on a solution and then I the solution worked was great, we got deployment experience and then I, I, I wrote the paper proposing that solution for Bloomberg,

**Matheus Izvekov [34:20]:** And, and, you know, and, and that was kind of like the story about like how in the past, you know, like sometimes featured features with the ne through core, and now we learned hard last from people sometimes bring that up as an example why things have to go throughWG first, right? So the, so the, that's one story.

**Vinnie [34:48]:** Yeah My question is this

**Matheus Izvekov [34:52]:** Yeah

**Vinnie [34:52]:** So What did, what did the committee miss? What did you miss? Like what did people miss? How did the paper go through and like what could have been done differently? Like, is there anything to be learned there, like, was there a retrospective after the fact, like after there was a bug fix, did, did anyone get together and say, here's what went wrong. Like, what are your thoughts on that?

**Matheus Izvekov [35:15]:** Yeah, so like, regarding the overall issue, you know, people are, are more sensitive, you know, about not, you know, like, sneaking, things, out of not going through EWG, right? And like now, now sometimes it feels like we're, we're kind of like, a little bit on, on the opposite extreme on that and where, where like

**Matheus Izvekov [35:45]:** If things like smell, even faintly as a feature that they go through EWG, right? but I, I, I think like that, that last song was learned, like even before I I joined, the officially the committee, but like I, I learned some other things, you know, about the, the difficulty of going through that paper, through EWG right where every like you flew

**Matheus Izvekov [36:15]:** Over almost everyone's head, but like I, since I didn't know, you know, like my, my, my experience with people, you know, from the committee, or like a, a group of people that made me like severely overestimate, you know, like, how much people understood about templates, you know, you know, like even in the committee, right? Because I, I was

**Matheus Izvekov [36:44]:** Like a lot a lot of my, you know, like interactions were like with Richard Smith, you know, which was like one of the biggest, C++ language experts, you know, and he kind of like Colored my view a little bit, on that and like that made me realize

**Matheus Izvekov [37:07]:** You know, like that I gotta be more careful, you know, about assuming that just because I presented my paper and the like everyone, almost everyone voted for it like it was. My, my, like my, the vote for my people was awash, right? Like my first ever paper to the committee and like the, there was almost basically owned animals for sensus, right?

**Matheus Izvekov [37:36]:** And, but, but like that didn't mean that like people really, you know, understood what, what was going on there and they had some difficulty later because of that.

**Vinnie [37:47]:** OK, I wanna, I wanna switch, I wanna start getting very technical. I don't want to talk about committee process. I don't want to talk about other people. I want to talk about your favorite subject. I want to talk about templates. I want to talk about how the language specifies them, how the users use them, how the compilers compile them and how implementers need to be mindful, so let's start with this.

**Vinnie [38:13]:** If you What would you like everyone in the committee to know about templates, if in for people that are evaluating changes to the language or changes of the standard library. What do you wish that they knew at a technical level.

**Vinnie [38:30]:** And you can talk in terms of compiler implementation as well, and I want to know your experience, like, what have you learned about templates? What knowledge do you have about compiler template implementation that would be useful for people in the committee to know.

**Matheus Izvekov [38:45]:** Yeah, so like, Well, one thing, like I, I, I wouldn't say that that's like really essential to everyone because of like a lot, a lot of people can go buy, fine, you know, like when, without like doing a lot of templates, but a lot of things that I learned, going into, you know, from, language user to, you know, like work on the comp

**Matheus Izvekov [39:18]:** Il you know, it's like how, you know, the compiler doesn't really offer you much of like type checking, you knowing templates, right? Like the they can write. Sorry

**Vinnie [39:37]:** That's OK

**Matheus Izvekov [39:47]:** Yeah, like the, the people, Like, how easily, you know, like you can write a template, you know, like that's not Really correct, you know, like for all, you know, inputs, right, like all types so you can use it and how, you know like not really feasible, or like really would be like really real challenge to like really improve the language to the point where, you know, that, that's not an issue anymore, that like you could be sure that like you ride, you know, your template and then like

**Matheus Izvekov [40:29]:** This valid, like just from type checking perspective, and like concepts don't really give you that, you know, like they help a little bit, but they, they're not like a real solution, at least not the C++ training concept, right? The C++11 ones maybe, but that, that ship has sailed and we probably can't, you know, like go back on that anymore because we kind of like closed the

**Matheus Izvekov [40:59]:** Language design space, so, And like the the the templates, they, they're really expensive, you know, On the compiler, right? So like I

**Matheus Izvekov [41:16]:** When I was a user, I tended to like write way more templates that I do now, you know, because, you know, now I'm more mindful of that, you know, and having, you know, like, cold based of like compiles fast and like it's easy to understand when a problem happens. So, the, the, like, you know, like a lot of areas, you know, like even over

**Matheus Izvekov [41:46]:** Load resolution, you know, I, I don't, even though like I'm an expert on that. Like I, I don't think that that's like good, you know, like, language feature of we have that historically, but like people shouldn't like be riding cold that relies on that too much because it has kind of like some usability problems, you know,

**Vinnie [42:10]:** Hold on, let me stop you there. That sounds OK, my dear, that sounds very interesting. OK. So overload resolution, can you please give me like exactly describe the overload resolution in the context of this problem and then explain your guidance for users, whether why they should avoid it and what they should use instead.

**Matheus Izvekov [42:11]:** That's about Yeah

**Matheus Izvekov [42:34]:** So, like, overall resolution, it's mainly about how the the rules for, for overall resolution. They really Complicated and no one like really understands them fully, right? Like, not even in the committee, I like all the, all the, like implications of some of the exceptions, we, you know, allow, right? So, yeah, so that I, I, I mean like it's not like a really it's all often a problem that will cause

**Matheus Izvekov [43:15]:** You, run time problems that you be, you know, like safety issues, that kind of stuff. But like some some problems they can cause, you know, by relying, you know, like too much on, things that can be changed by this exceptions to the rule. It can be, it can be really surprising, right? The outcome of over

**Matheus Izvekov [43:45]:** All resolution, that, that's like my main Take from, from that and like from what, what I see, you know, in, new language, you know, like success successor languages to C++ is that like people are avoiding, you know, like overload resolution, they, you know, like, making, the cases where they are at least making where they allowed more restrict,

**Matheus Izvekov [44:17]:** So the, the, that's like one, you know, like, take from this, I, I think like people should use you know, like language features that they understand well and like no one really can understand overload resolution while in my opinion, right? So like don't use that because of that reason, I guess

**Vinnie [44:41]:** So it's interesting that you bring up overload resolution because We also have argument dependent lookup, and I believe Eric Niebler in Rangs, he developed an interesting technique that we call the kneebloid, which is, it's basically a constant variable which has a function call operator and by expressing function call syntax that way in terms of like a callable object, you have no argument dependent lookup, so give me your thoughts. Was he, did he

**Matheus Izvekov [45:03]:** OK.

**Vinnie [45:14]:** Implicitly recognize the overloading problem and what and whatever happened to that whole principle, that design, whatever happened to that design.

**Matheus Izvekov [45:24]:** So, not, not an expert on that subject, but I believe, like Eric Niebler is very mindful of coal time performance rate, and, bypassing ADL, that's like, well, good wind in, in that area because ADL is low because you kinda like have to build this huge sad, you know, like that.

**Matheus Izvekov [45:54]:** You know, they do a lot of tasks, You know, and, and that, that's some like it's a fish calledal time efficient technique, but like,

**Matheus Izvekov [46:13]:** So I haven't been following the the library side of the of the C++, very much, but I do believe he dropped or like she's not trying to standardize them anymore, they kinda, kind of fell out of favor.

**Matheus Izvekov [46:33]:** For that, but like I don't, I haven't really catched up on that subject, so I I don't remember why his not pursuing that anymore, I guess.

**Vinnie [46:44]:** That's fair. OK, next, as a compiler implementer At a technical level, I want you to get as technical as possible. What would you like? People in the committee to understand so that they're, they can make create designs and wording that's more friendly for compiler implementers.

**Matheus Izvekov [47:09]:** Yeah, so like, From, from the library side, I, I, I think a lot of Basic language things, the, you know, like, like for example, STD move, you know, and things like that, they're used everywhere, but they're implemented in terms of templates, they, they cause a lot of overhead, you know, like in, cold bays because templates are expensive, right? But, a lot of these things, you know, like

**Matheus Izvekov [47:53]:** Some things like simple enough and like it's gonna get used a bunch, probably be more efficient to make that you know, like a language features instead of library feature. I think the, the committee historically, you know, have, has had, you know, like, troubles, you know, I accepting, stuff, you know, I, and, and, and I think that like it's making

**Matheus Izvekov [48:23]:** It so that like sometimes she comes up with the kind of like a better, you know, like I would be kind of like a better, you know, effectiveness, you know, for, for this specification or some of the things, you know, I think like for example, atomic, probably would have been better as a language things out of the library thing, I think like S

**Matheus Izvekov [48:53]:** The move Forward, you know, a lot of like very You know, like Basic foundational things, in the language, I think, there's a lot of stuff to improve, the language, in around the subjects like the mat mathematical stuff, like, for example, the, ants with the arbitrary bitwi right and even things that there were working on right now that, not even in a paper, like for example,

**Matheus Izvekov [49:36]:** Having, rigor like a need or a sign ne where it can control the wrapping or non-wrapping behavior, And, like I, I, I fear that like some of these future where we're doing better job, you know, like when, when we

**Matheus Izvekov [49:57]:** Implement them, you see, because we like make them type specifiers, qualifiers, and these things aren't cheaper, like they, they're more trouble, like they're more work for the, the compiler implementer, you know, like the, the at least the person that the laments the the compiler part of the, the language, but, but we can do like much better job and when there's an error, we can explain their like so much better

**Matheus Izvekov [50:27]:** More efficiently. and I, I fear, you know, like some of the, these things that like we we're gonna eventually try to bring them to C++, and people are not gonna, you know, accept. That, that we do them as a language extension that they want to do them as a library. They, they did, they would feel weird that they're not all library thing and there's this idea that like everything that we could should be done in the library, and I, I, I think that can be

**Matheus Izvekov [51:01]:** Counterproductive because like implementing something from the Popa side, it can, you know, like, end up with, with a much more polished experience for the users, I think.

**Vinnie [51:15]:** OK, that sounds really good. I like that. OK, now, now I got to talk about something. I think you know what's coming. I want to talk about trivial relocation. So, just so to let the record show, do you remember the paper number?

**Vinnie [51:35]:** Was it

**Matheus Izvekov [51:35]:** Trivial relocation, you mean the, the one, the, the, the proposal for Pablo, the one that that went into that, that was pulled out when to and then went out of C++ 26, right?

**Vinnie [51:43]:** Yeah Yeah. Do you remember the paper number?

**Matheus Izvekov [51:52]:** No, I don't remember. I, I didn't work on that paper. even though like I was with Bloomberg with working with those people. I wasn't working on that, so I, I don't remember that.

**Vinnie [52:03]:** OK, I Do, do you know anything about it? Like, do you know anything about it?

**Matheus Izvekov [52:10]:** Just some of it, you know, like more about the controversy, you know, that Arthur was trying to push something that was, you know, like more in line with what everyone in the industry was already doing expecting and Pablo, did the kind like a more radical change. I, I, I think like,

**Matheus Izvekov [52:43]:** Our tourists, paper in general had like more legs, but it still had problems and I wouldn't have voted for it. so, like, like, for example, Arthur's paper didn't try to like really like like the language, figure out

**Matheus Izvekov [53:08]:** If a type should be trivially, reluctable, right? Like, so, basically, at some point, it, you know, like us, the, you know, type order like they do, do you, you know, guarantee your

**Matheus Izvekov [53:26]:** Type type is or not, and Pablo's paper, tried to avoid that. But like I, I wouldn't have voted for like a proposal that didn't have like a, you know, like that solution that the like a type teratically correct thing solution figure out, but at the other point, I saw that like Pablo's paper had a lot of

**Matheus Izvekov [53:56]:** You know, weird things and unanswered things that wasn't really You know, like, confident to vote for it, and then Louis, who is the Leap C++ maintainer. He, he came up and like made a little

**Matheus Izvekov [54:19]:** Showing tale about his experience implementing it in deep C++, and he had like a lot of negative You know, impressions for and I do trials his opinion a lot on that stuff. So his, you know, like, his presentation had an impact on my vote against Pablo's paper in the the committee as well.

**Vinnie [54:51]:** That sounds good. OK. Well, is there anything you want to tell me? We're gonna wrap this up. This has been really, really productive. I really like the insights. Is there, is there any last things that you want to say just in terms of like for example,

**Matheus Izvekov [54:58]:** OK

**Vinnie [55:07]:** Let me give you some examples. Like Like a feature that got standardized that you wish it didn't go in or a time where you had a very difficult decision on a proposal or a proposal that went through the process very easily and you thought it was like very successful.

**Vinnie [55:27]:** Any story

**Matheus Izvekov [55:27]:** I, I, I know, so like one thing I can say, is I, I, it's not just me, but I started being very mindful about the fact that we're creating A lot of work

**Matheus Izvekov [55:45]:** In like in in the standard Committee for the implementers, like, from the library side, just recently, we have, we have approved, Like the linear algebra, you know, feature into the C++ standard library, but like I know like from my work, my my personal relationships, that this barely anyone

**Matheus Izvekov [56:16]:** Right now working on the C++, right? And like, yeah. De Arja is a crazy amount of work for, for like not having anyone to do it. So I just on, on those grounds, you know, like I would severely, you know, I've trottled down, you know, like the amount of features that are coming in because like people don't, don't have time to implement them, you know, like you're probably only gonna get them down to like 5 years, it's like we we probably

**Matheus Izvekov [56:52]:** Would have been more productive to like just hold them and try to get them in later when we're we're not so, we don't have so much stuff to do, right?

**Vinnie [57:04]:** Yes, you know, OK, this is actually a very good subject, and I think actually that we do have a lot more to say. So let me ask you this Let's talk about libraryon proposals, that is proposals for the, for the standard library that don't require any changes to the language, right? No changes to the language. I want to talk about that. So you brought up linear algebra. So it sounds like you're saying that you don't believe that that was a necessary component for standardization

**Matheus Izvekov [57:36]:** No, I, I know, I, I definitely See that as something that would be worthwhile, you know, like that would like a normally you know, like take all the boxes of the things that, that we should have, you know, like in the standard library because it's like something fundamental. It's something like base, you know, like fundamental mathematics and the, the language, you know, like,

**Matheus Izvekov [58:09]:** Or how, like the problem space hasn't really changed in a long a long time, right? So like I, I would feel that like a free got something in the they're like a lot of people would have a lot of good use of it and like it wouldn't get like obsolete very quickly, right? just because of how

**Vinnie [58:28]:** OK, but what's What what's the, what's the evidence, OK, people can get libraries from a package manager. You can download boost. You can download from GitHub. So just because, you know, just because linear algebra is important doesn't mean that users are not able to get it. So do you agree that the, the bar for what should be in the standard. It should not be just because something is useful, it needs to be that this benefits of standardization justify the costs because.

**Matheus Izvekov [58:31]:** Yeah

**Vinnie [59:01]:** The users can get linear algebra. Like why did linear algebra need to become part of the standard instead of being a package that users can download. Where, what was the evidence? Do you remember any evidence being presented that this was going to solve a coordination problem that there was this was going to solve friction, and type boundaries or an API boundaries that this was going to solve an issue where like different libraries need to interoperate and they need to agree on linear algebra types like where's the evidence? Tell me.

**Matheus Izvekov [59:01]:** Mhm

**Matheus Izvekov [59:29]:** Yeah, so like yeah, I wouldn't be able to, to like really Tell you, I, I, I mean like from my like bystander perspective, or, or at least, I, I was, so I, I was an author of mathematical C++ library, a long time ago, like around 2014, and the problem that I, I observed, was a lack of like

**Matheus Izvekov [1:00:04]:** Way for like mathematical libraries to interoperate, right? I mean, there's a lot of aspects to it, but, in general, I think

**Matheus Izvekov [1:00:22]:** If we get a like a good design approved, you know, that, that, that would kind of like sad, you know, like Caton or like expectation for people about like how they expect like mathematical types in C++ to look like, and, you know, like behave and that that was certainly improve how libraries interoperate.

**Matheus Izvekov [1:00:52]:** So, like my, but like from my personal votes, that, that would be a reason. I, I think like C++ really lacks in that department, but, but I, I don't have like a very strong opinion and I didn't follow, you know, like this paper, very closely as as it was going through LWG. So like I, I wouldn't like be able to remember

**Matheus Izvekov [1:01:22]:** Like arguments that were presented at the time. This is, this is more my about my perception of about it.

**Vinnie [1:01:30]:** Let me just, let me just ask you point blank. In your opinion, what belongs in the standard library that is what makes a component a good candidate for standardization? What are the, what are the elements

**Matheus Izvekov [1:01:45]:** I, I, I think like that they should be things that like, like it should be more about the idea of building a vocabulary, right? It's like, like, for example, STD vector being in the standard library helped because like, like people are still wanna like implement like create their own factors because they're going to be specialized in

**Matheus Izvekov [1:02:15]:** Better in some aspects, right? Like if they don't have any reason to be different, you know, like from SD vector in some aspect because it doesn't matter, that they shouldn't be, right? and then I, I mean that that's clearly something that like you ever

**Matheus Izvekov [1:02:36]:** Program like did anything non-trivial and see, you see that sea suffers a lot from it, right? Because like if you want an STD map and see now you're gonna get a bunch of libraries. They're like Luke in have like very

**Matheus Izvekov [1:02:54]:** Different concepts about how things should be done, and it can't like easily, you're like you decide, oh, this SD map, you know, like, I doubt backing algorithm for it it's not like the best thing for my use case. Maybe I should try that other library, you know, you, you're gonna have a hard time seeing to swap those things. Wearing C++ like you can't like.

**Matheus Izvekov [1:03:22]:** You know, like switch them, you know, like the amount of work is much less because they're gonna be much more similar, right? And the, and the, yeah, and I, and I think like for, for that kind of stuff, you know, like for types that like people are are gonna be like passing between libraries, you know, that kind of stuff. It's really important to standardize and it does feel to me like the linear algebra types are that kind of stuff, right?

**Vinnie [1:03:31]:** Yeah

**Matheus Izvekov [1:03:55]:** I, I mean, it's certainly like need to do that kind of stuff. Like when you're doing a game, like if you're in a game, then you're, you're gonna have like a physics library, you know, and

**Vinnie [1:04:05]:** Can they do? Can't they just download it as a third party library? Like, what's the evidence of need?

**Matheus Izvekov [1:04:14]:** I mean that's like it's more it's like right now you can't like really make Much of a case, right? Because you, you're gonna get into that situation where like for example you have a game, then you have your physics engine, and then you have like your graphics library, and they kind of like need to pass around like in their algebra types between them and then like you have one solution. And then if you, for some reason need to use another, you know, like you decide all these other linear algebra library, you know, like does

**Matheus Izvekov [1:04:51]:** Something better. Let me know, try to rewrite my program to use that, you know, like my experience is that like the look completely different and it would be like a huge amount of pain. So I 41 yeah.

**Vinnie [1:04:57]:** Yeah, yeah Yeah Yeah. Was there any, was, was there any evidence of that problem, or is this just theoretical? because I didn't hear any complaints from the games industry like the papers that proposed linear algebra. All they said was that this is useful, and here are the domains that it's used at, and that's all perfectly true, but where is the evidence that games developers were having trouble integrating because as far as I can tell, games developers, the problems that they have, they look nothing like that. No one's complaining, oh, we don't have a uniform API

**Vinnie [1:05:34]:** For linear algebra. I've never seen that complaint. I've actually talked to game developers. Nobody says that. The actual problems that they have is they want things to compile fast. They want to be able to be able to refactor their code base. They want to be able to reuse code between projects. They're never say game games usually have custom built like stacks, technology stacks that are highly proprietary that they use that they're in-house like they have like unreal engine, the Unity engine, and these frameworks are usually comprehensive, like they provide their own matrix. They

**Matheus Izvekov [1:05:41]:** OK OK.

**Vinnie [1:06:04]:** Provide their own vector. They provide their own algorithms, and when the company that provides the framework improves the algorithms like all the game developers benefit. So the reality is that if like if you look at those, the linear algebra proposal, there was no evidence of need. It was only stated as a fact. This is useful because it's useful. There is no evidence

**Matheus Izvekov [1:06:25]:** I, I mean, I, I wouldn't be able to argue on that because I didn't follow the paper. So I, all I said was like from my personal perspective or like having just a little bit of experience, doing that, but like not professionally, really, I, I have never been in the games industry, but I have done something or another as a hobby, but, I, I, I mean like, it could be that like

**Matheus Izvekov [1:06:55]:** You're right, but like the that, that, that thing that should be argued in, you know, like in EWG or, or even before that because like a a library like dinner algebra spent a lot of time in the in the like mathematical, mathematics,

**Matheus Izvekov [1:07:25]:** Working group Right? So like, remember that this has been something that has been going on for a very long time. So if you really just go and like just look at the papers that, that, were looked at, you know, I had EWG probably a lot of that rationale, they could be like not there or like not mentioned because

**Matheus Izvekov [1:07:57]:** A lot of people that work on that already discussed that in the, the study group, right? So like they came out of the study group to EWG with that proposal would probably, you know, like not sure here, but like just explaining how these things can happen. Is that like people when they came to that point, there, there wasn't a disagreement anymore, right? So like few start following

**Matheus Izvekov [1:08:27]:** The, the, the, the work just when it goes 3WG you can miss a lot of that context, but that, that would be all right, you know, like, but, but like if you're there in the, the EWG session. You can ask those questions, right? It's like, where's your? And they're like people realize oh like not everyone agrees with this and then they got come back on a later paper, you know, they explained why

**Matheus Izvekov [1:08:57]:** Why did the, you know, like they, if they address all the objections you had, you know, and then

**Vinnie [1:09:03]:** So what Matthias, let me make sure I understand this. So what you're telling me is, is that in the evolution group, it's very possible that the evidence that I'm referring to was presented. In other words, that there were, there was evidence of need. There were like business use cases that were enumerated. However, that was oral and none of it was recorded and none of it was added to the paper so it's possible that in the transition from the evolution group to the core group that that information is lost. We have the outcome of the process

**Matheus Izvekov [1:09:07]:** Yeah

**Vinnie [1:09:33]:** But we don't have the rationale. We don't have the supporting evidence. We don't have the reasons. And then later on if nobody's using linear algebra like in other words, if we do a retrospective to ask the question, is WG 21 effective? I it's producing things, but is it producing things that people use. After a feature ships, we might want to start asking that question in order to know if the committee's resources are being used productively. So in this case, if there's a if there's not adoption of linear algebra

**Vinnie [1:10:03]:** Then we have nothing to go back to and say, well, what was made up the decision is because all that knowledge was lost. Is that the case?

**Matheus Izvekov [1:10:11]:** Yeah, so like, what, what you're saying is like in general correct and the problem, like how I was going a bit further than that. I'll explain a little bit, but like, what you said is true, right? Like a lot of times I, I need to figure out, you know, like why, like something in the paper, or some idea was considered, you know, and you cannot find that on the paper, right? Like sometimes you, like if you go to the WG 21 we

**Matheus Izvekov [1:10:41]:** Ki and you're like find the transcripts of all the sessions where the papers were were presented. Sometimes you, you find that information, but sometimes not even then and like he gotta ask the author and other things, but like what I was saying even further than what he's saying like the, the information being lost between the trans the transition from EWG to core

**Matheus Izvekov [1:11:11]:** What I was saying is there is also before that a transition between like the mathematics study groups in EWG, right? Because like a big feature like that gets worked on study groups like dedicated study groups that are dedicated for a certain cause, right, like we have UB study group. We have mathematics, study group and like proposition like line

**Matheus Izvekov [1:11:41]:** Ar algebra went through that study group, you know, and a lot of discussions, you know, about that, we're like probably lost in the transition, you know, from the study group to the evolution group as well, and like people didn't like ask a question in a, you know, you know, session, EWG session, then it's not gonna be like the answer is not gonna be

**Matheus Izvekov [1:12:11]:** Anywhere, right? If people didn't really press hard on a question that is like the authors didn't feel like a question was like something controversial, they probably like wouldn't even try to clarify it on the paper, right? so that, that's definitely a problem.

**Vinnie [1:12:26]:** Yes Mattias, this has been so productive. I mean, I got to thank you 1000 X. This, this information is so good. I can't wait to get the transcript and show you like you know what we're going to get from this, but I thank you once again. I appreciate your time.

**Matheus Izvekov [1:12:44]:** All right No problem

**Vinnie [1:12:47]:** All right. God bless. Have a great day.

**Harry Bott [1:12:49]:** Awesome to listen, awesome, awesome to listen in, guys. Thank you. Thank you, Matthew.

**Vinnie [1:12:53]:** All right Hey bye.

**Matheus Izvekov [1:12:54]:** Oh no problem. All right. Thank you. Bye-bye.

**Harry Bott [1:12:57]:** Bye.

**Matheus Izvekov [1:12:59]:** Bye-bye.