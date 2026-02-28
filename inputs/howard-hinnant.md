Transcript of huddle in howard.hinnant on Jan 7 from 12:05 PM to 1:04 PM Pacific Time (US and Canada).

This transcript is auto-generated, so some information may be inaccurate. It won’t be surfaced in search results.
@Vinnie [3:28]: OK, so I'm talking to Howard Hinnants, longtime WG 21 committee member and the purpose of this conversation, it's a very friendly interview and I just want to learn about how you think, your experiences with code C++, of course, Elliott's stories about failures, those are also great.

@Vinnie [3:48]: So I guess And of course the committee experience is wonderful. So Howard would can you just introduce yourself and tell me like when you first got started with WG 21 on a technical level like what were you involved in?

@howard.hinnant [4:03]: All right. well, let's see. I, I went to work for MetroWorks in 1998, and they sent me to my first committee meeting. Which I believe it was either 98 or 99 And that's how I got started in in the committee. Metro I was MetroWorks' standard live guy.

@howard.hinnant [4:25]: Implementing their standard live, fixing it, maintaining it. Team of one And Pretty much brand new to see, well, not brand new to the language, but brand new to the standardization Community

@howard.hinnant [4:42]: And gosh, it's it's been a ride since then and As as Vinny knows, I went to work for Ripple, Vin he hired me. And that was in 2014 and I was with Tripple for a little over 10 years.

@howard.hinnant [5:02]: So, Vinny actually knows me pretty well.

@Vinnie [5:06]: Well, that's, that's a very kind. OK, so now that, now that we got that introduction out of the way, I want to get, I want to get down and nerdy. Tell me about your first experience in WG 21, but again, technical, was it a library component? Did you propose a paper where you reviewing like tell me what happened.

@howard.hinnant [5:26]: I was, because I was the standard live implementer for Metroworks. I was immediately drawn to the LWG and at that time there was no evolutionary incubator study groups. There was only Evolution core and library.

@howard.hinnant [5:44]: And so I camped out in library since that was my job. And One of the I, I did not come with proposals. I came just to learn and represent MetroWorks' interest.

@howard.hinnant [6:00]: And one of the first things I was hit with was I, I'd just implemented Vector Bull for MetroWorks And one of the first defect reports that we studied at my first meeting Was that Vector Bull was not a proper container. Which by now is old news

@howard.hinnant [6:18]: But This C++98 had just come out. And I was shocked that here it was The standard wasn't, but a few months old. I had fully implemented this thing And The The, the issue was basically to just

@howard.hinnant [6:36]: Tear it down and do it over and just have a plain vector boo as they should have done in the first place. But I was just blown away that such a massive bug Appeared in the Standard.

@Vinnie [6:49]: Yeah. Spector bull is a cautionary tale. So how did it happen? Like what, how did it happen? What was there a process failure? How did they not realize?

@howard.hinnant [6:50]: And Yeah I don't know because that was my first meeting and so Vector Bull was standardized before I ever came to a meeting.

@howard.hinnant [7:07]: So I don't know the details of of how it was standardized, but my reaction Was, wow, I thought you guys knew what you were doing. And, and I unfortunately said that out loud instead of just thinking it. and Beaman Dawes taught me my first lesson, as standardization is don't be an asshole.

@Vinnie [7:32]: Well, I hope I learned that lesson one day.

@howard.hinnant [7:36]: He, he was very kind about it, you know, he just gave me a look and says, you know, we're, we're here to, to fix the problems and

@Vinnie [7:44]: That's really, that's actually very interesting and I, I, I had forgotten Beaman was very involved, so what did he give you advice? Was he like a mentor? Like did he transmit knowledge to you? What did he do?

@howard.hinnant [7:54]: It was He was definitely a mentor of mine. he, he guided me along in the in the library working group. He taught me the ropes of, you know, how to work with the standard committee.

@howard.hinnant [8:10]: He, advised me, I, I became library working group chair in 2005, and he was very instrumental in helping me get started as chair and, and do it the right way and advise me of the the right way of doing things.

@howard.hinnant [8:27]: And, and so, yes, he was very much a mentor and a friend.

@Vinnie [8:32]: That's really cool. Do you Who, who Occupies that mentor role now? Does anyone, is anyone mentoring people the way that he did for you?

@howard.hinnant [8:44]: For me, I'm pretty much retired now, and so I'm not I don't really have anybody that I consider a mentor at this time.

@Vinnie [8:55]: I mean, I mean NWG 21, is there anyone mentoring new people?

@howard.hinnant [9:00]: Oh, I'm, I'm sure there is. But it's, it's not like a An official roller and it, you know, a publicly recognized role or anything like that. Just people develop rela relationships and I'm sure there are people on the committee who

@howard.hinnant [9:17]: Serve as mentors to other people. I would have no doubt

@Vinnie [9:21]: But there's nothing formal

@howard.hinnant [9:22]: No formal

@Vinnie [9:24]: Do you still attend the meetings

@howard.hinnant [9:26]: I do not. It was pre-COVID last time I attended a meeting, which I'm thinking was 2020 or it might have been 2019. I'd have to look up.

@Vinnie [9:37]: We, when, when, so when you were attending that you would, there would be new people would show up. Did you help onboard them? Like, what kind of orientation did did they get? Like what were they taught when they first attended a meeting?

@howard.hinnant [9:52]: There really was no Recognized onboarding, just, you know, we would welcome people Especially in the in the full session at the beginning of the week. There was always, you know People who are here for the first time, raise your hand, introduce yourself, that sort of thing.

@howard.hinnant [10:10]: But besides that, there was no general recognition of new people on the committee. Just, you know, If people had questions they would ask, you know, find somebody to ask and Pretty much learn as they go along

@Vinnie [10:28]: Fair OK OK, so You were, so you were you were running the library site. I mean, I love libraries, you know me, and you taught me so much and you've written several libraries. So you can when you evaluate a library proposal, that is a proposal that's like library only. What do you look for? Is there anything you should look for? Is there anything that people should be looking for? Are there any general principles?

@howard.hinnant [10:52]: I'm gonna assume you mean when I evaluate a library for standardization as opposed to Some other use.

@Vinnie [10:59]: Yes, exactly. Standardization.

@howard.hinnant [11:04]: But I'll look for first in a library is Is there some other way to do it that is already standardized. And if so, how easy is it? And how error-prone and how obvious and Stuff like that. I am not a fan of

@howard.hinnant [11:20]: Making something that is easy to do already. But not in the standard of putting it in the standard. I like when I standardize, I prefer to make what was previously impossible or impractical, possible.

@howard.hinnant [11:37]: Or if not that, to make something that is very difficult or hard to make it Easy

@Vinnie [11:44]: Very interesting

@howard.hinnant [11:45]: But But making the easy easier, I find very uninteresting and not worthwhile to standardize. Not that we haven't done that a bunch in the past. We have.

@Vinnie [11:56]: That's a really good and powerful insight, Howard. I got to say I, I got a little tingle when you, when you said that. So is this written down? Where is this written down? Like, do you, is this, do you explain this? Do you have like a blog post where you explain like your design principles like also, how do you know this? Like why? Why do you have this principle? What, what's the motivation?

@howard.hinnant [12:16]: And the motivation is the The, the, the standard, the, the library part of the standard is, is pretty large. And we just, we don't need more stuff that Unless it adds real value.

@howard.hinnant [12:33]: Like making something that is really difficult or impossible Easy. But You know, sometimes we We do standardize things, I don't know Trying to think of a

@howard.hinnant [12:50]: An example

@Vinnie [12:51]: How about linear algebra

@howard.hinnant [12:53]: Linar algebra is hard. And I am not familiar with the newly standardized linear algebra package, but before I got into the C++ community, linear algebra was my day job. I I use linear algebra to study the dynamics of helicopters and other rotorcraft.

@howard.hinnant [13:12]: Fine

@Vinnie [13:13]: Well, what, what are the, what benefits the standardization provide for linear algebra that can't be obtained, say, using a package manager and installing something third party library or getting it from Boost.

@howard.hinnant [13:25]: That's a good question, and Since I'm about 3 decades out from using linear algebra for for anything. But I would guess that the main standardization is that It makes it easier to port from platform to platform. If you can grab it from the library, that means you don't have to install a third party library, which is naturally going to be

@howard.hinnant [13:53]: Probably a non-portable process from platform to platform. So it probably be easier to use And it would hopefully be, and I don't know if this is true of our standard LIBE or not because I haven't looked into it, but I would hope it to be more C++ like and less sea-like or Fortran-like.

@howard.hinnant [14:18]: Just in the style, the safety, the memory management. That sort of thing

@Vinnie [14:24]: And that's really interesting. So I think, correct me if I'm wrong, but what you're saying is is that one of the benefits of standardization is that It, it compels implementers to make it available on their platforms, and this assures end users that it's going to be available on all the platforms.

@howard.hinnant [14:43]: Right.

@Vinnie [14:44]: Yet the implementers, the, the, the someone who writes a linear algebra library who's an expert in linear algebra and then publishes it on GitHub, for example, or proposes it for boost. They're like a subject matter expert, right? So, but then when it gets standardized and now we've tasked Compiler implementers with putting it into their standard, those people who author the Standard library may not be linear algebra experts, so we're asking people who are not domain experts to now implement something? Is

@howard.hinnant [14:58]: Right

@Vinnie [15:14]: There an impotence mismatch there?

@howard.hinnant [15:17]: There is, and it, I would say it's Partially offset Because the, the standard lives themselves, elves these days are open source and so you can get experts to help you implement it if you're a, if you're an implementer and need help

@howard.hinnant [15:37]: That getting that help Doesn't require your company to hire somebody. It just requires you to motivate a standard expert you may, you may know to, to help out. Maybe directly contribute or maybe advise you.

@Vinnie [15:53]: Interesting. OK. So can you What about library proposals that you rejected or that you thought were like maybe not a good fit. Do you have any specific examples and like do you have any stories of Proposals maybe that you thought were a good fit, but that got rejected and you felt like that was a mistake or something got accepted when you thought that it was a mistake and it should have been rejected like specific stories.

@howard.hinnant [16:19]: I guess I've got lots of stories about ones that I thought should be At least small, small things that are shot that I thought should be standardized that didn't, my success rate on the committee at proposing things was probably around 50%. So half the stuff I submitted was rejected.

@Vinnie [16:37]: Hey, 50% ain't bad.

@howard.hinnant [16:42]: Well, you know, it's not bad, not great, but I was, I was happy with the stuff that, that did get accepted. I would have loved to have seen

@Vinnie [16:49]: Fair

@howard.hinnant [16:52]: And this still may happen, I would love to have seen A smarter allocator model. Especially for containers like Vector, where you could When you request memory from an allocator, if you could turn around and say, OK, I know I requested X amount, but usually that amount gets rounded up somewhat to meet

@howard.hinnant [17:14]: You know, the allocators needs, whether it's, oh gosh, what do you call it? I'm blinking, alignment. Alignment requirements

@Vinnie [17:22]: Yeah

@howard.hinnant [17:24]: I would love to be able to turn around and say, OK, how much memory did you give me? Because if, for example, you've got a, a string or a vector of char. You're, you're very likely to have gotten more memory than you asked for. Maybe it's only a few more bites, but if you can use those few more bites, why not? Why just waste them?

@Vinnie [17:44]: What if there was a way that that's, that's, I agree with you, by the way, and can tell me what you think about this. What if we went beyond that? What if we said not only can you ask for something and then get more, but then later you can say, by the way, I only use this much and then put the remainder back.

@howard.hinnant [18:00]: That'd be good. It would also be good to, to ask the allocator, can you expand this in place?

@Vinnie [18:07]: Right, right.

@howard.hinnant [18:07]: A like a resize that doesn't move things around if it can't.

@Vinnie [18:11]: Or, or even how about if we have like I know that there's the new polymorphic resource type APIs, so they previously we had the allocator template parameter which I mean it was important at the time because they had to support the memory models and the pointers were different, and then because of all the template and stantiations we came up with the polymorphic allocator, which in principle sounds like a useful addition. However, something that I noticed was, if you have like an arena-based allocator, you can't just ask

@Vinnie [18:41]: How much can I get right now? You have to request a certain amount, so it's, it's, it's a new API, but it's ignorant of actual real world needs. How did that happen? Is that a design failure?

@howard.hinnant [18:54]: Oh I don't know if I'd call it an out and out failure because generally alligators have been fairly successful, if not a pain in the ass, but still successful. But I would say that it would definitely improve the allocator API if we could do things, ask the questions like we've been discussing for the past few minutes.

@howard.hinnant [19:13]: And I did try to standardize something like that and failed.

@Vinnie [19:17]: So, can you, I want to hear about that story. What is the specifics? And you can talk function signatures, anything.

@howard.hinnant [19:23]: Oh gosh, you know, it's been over 10 years since I've done this, so I'm not going to be able to pull it out, all out of memory, but there's papers back there, I with guests in the 2010 time frame. Plus just a few years.

@Vinnie [19:35]: So broad stroke, one of the broad stroke.

@howard.hinnant [19:38]: I'm sorry

@Vinnie [19:39]: What are the broad strokes

@howard.hinnant [19:41]: Brostrokes was To be able to ask the allocator how much memory did I, do I? Did you give me Can you expand this in place? I don't think I had in there shrink it, but that would be a good option as well.

@howard.hinnant [20:05]: And I I realized that for it to really be successful, there would have to be the the the C committee would have to standardize it too.

@Vinnie [20:15]: Oh, that's interesting. Why

@howard.hinnant [20:19]: Because all the allocators basically come from C, you delete, you know, come from free. Alec and Mali and Free. And so I was trying to add on to the API of Mali and Free.

@Vinnie [20:28]: Interesting. Interesting

@howard.hinnant [20:34]: And then on top of that, build a smarter Allocation, Well, standard allocator.

@Vinnie [20:43]: That's really cool

@howard.hinnant [20:44]: And I was I was unsuccessful at getting the C committee interested. Which isn't too surprising cause I didn't I, I did not regularly attend the sea meeting and so I was kind of a stranger. They didn't know who I was and

@Vinnie [20:52]: And is that, does that hurt?

@howard.hinnant [21:01]: So that was kind of doomed to fail.

@Vinnie [21:05]: Fair OK, well, so let me ask you this. How do we, how do we evaluate vocabulary necessity versus utility convenience.

@howard.hinnant [21:19]: Is it, is it possible? Is it practical for somebody to do it today? And if the answer is no Then And sta and if With standardizing it becomes possible, if not easy, Then That's a no-brainer

@howard.hinnant [21:35]: I've got an another example you'll like for the for this. You were in you were my co-author on the hash proposal.

@Vinnie [21:35]: But Yes,

@howard.hinnant [21:44]: That didn't, that failed The, this was a hash proposal to Let me see if I can describe it right. It was a way to hash Multiple objects with a single hash function as if they were contiguous memory.

@howard.hinnant [22:04]: So that the integrity of the hash algorithm was Was sustained as opposed to The boost combined method where you hash two things and then you form another hash of those two hashes.

@howard.hinnant [22:21]: Which I dislike because You, you don't know what you have at the end. Do you, you don't have a particular hash algorithm. You've got a a mix of unrelated hash algorithms.

@Vinnie [22:35]: So the

@howard.hinnant [22:35]: Which to me is garbage in, garbage out.

@Vinnie [22:38]: I think I was a co-author and I remember in your tests your conclusion was that if you take the hash of hashes, you lose the valuable properties like the mixing and the avalanching.

@howard.hinnant [22:51]: Yeah, you, you basically, you, I, I'm not an expert on hash algorithms, and so I have a high respect for for those who are because it's somewhat as much of an art as it as it is a science. Those who know how to do it, have a have a real talent.

@howard.hinnant [23:08]: And so I would like to be able to hash multiple objects Using a hash algorithm and not mess it up because Once you do, you, you really don't know what you're doing if you're not one of those hash experts.

@Vinnie [23:23]: That's very interesting. What, so when, when that paper was making its way through the committee. Do you remember what the arguments were? Were there any hashing experts present? What was the rationale for the rejection? Like, tell me as much as you can. Tell me the story of that paper moving through committee.

@howard.hinnant [23:41]: Google got excited about the at the same time on the same subject. And there was Pretty intense disagreement over Over details on, on how to accomplish it, what exactly the API should be like.

@howard.hinnant [23:58]: And we argued with each other until both Google and myself were tired of arguing, and we both just dropped it. We just lost interest in In continuing

@Vinnie [24:11]: I mean, the fact, the fact that there were two major proposals, and especially one from Google that suggests a need. How is it possible that despite the recognized need And I think, I think you would agree that hashing is one of those things that belongs in the standard because it needs to be a vocabulary type. All types need to hash the same way so that you can compose or else you have a fragmented ecosystem. How is it possible that we have an improvement to the standard that has clear need that is solved by two different papers, you know, perhaps in a different way, completely justifiable minimal on the standard, really. I mean this is not very elaborate framework. I mean, the

@Vinnie [24:51]: Amount of wording, at least for the concept, wasn't that great. How did it just get dropped and then ignored? Like, why isn't this more of a higher priority?

@howard.hinnant [24:59]: I would say the basic reason is because the committee's a group of volunteers and not an organization, not a Organized organism. I'm not sure how it's not, it's not a, excuse me It's not a business

@howard.hinnant [25:18]: And so With a with a group of volunteers, although there's working group chairs and there's conveners. There's different leaders There's no one who can say, I want you to do this, and if you don't, you're fired.

@howard.hinnant [25:36]: But, you know, you can't fire somebody.

@Vinnie [25:39]: So the committee lacks executive power is what you're saying.

@howard.hinnant [25:43]: Yes, that's a good way of putting it, succinct.

@Vinnie [25:47]: So interesting, that's very interesting. OK, So if it's a group of volunteers, then, and then what is the mechanism for ensuring that the work outputs of the committee are in alignment with the needs of the greater C+ community. Like what's, where's that mechanism?

@howard.hinnant [26:07]: Well that To to ensure alignment The committee has to agree by consensus. That a new proposal Goes in. And consensus is more than a majority. It's roughly 2/3,

@howard.hinnant [26:24]: Although if, if enough national bodies object, then even it has to be even higher than that.

@Vinnie [26:33]: There?

@howard.hinnant [26:34]: I think for Nash, you know, if more than one national body objects, A vote is probably doomed.

@Vinnie [26:43]: So just as a personal note, I've noticed that there's Sometimes, and this is not a problem with WG 21 specifically. This is kind of a general problem of consensus-driven processes, but you have what I call framework first, that is a proposal for some type of framework, whatever that is, and it's very elaborate, it's very academic, it's very mathematically correct. It has very strong theoretical foundations, people who look at it at every stage of the process, who maybe they maybe they're familiar with the domain and the mathematical terms.

@Vinnie [27:17]: Or maybe it appeals to their sensibilities because it makes sense conceptually. These things make their way through, and then at the end we find that we have the framework, but we don't have the things that users actually need. Like we're missing some types and we're missing some use cases or even worse, we discover that when we actually go to use the framework, there's usability problems just because the framework was designed from the top down, whereas compare that to use case first, that is, start with

@Vinnie [27:47]: The motivating use case. Start with what the user wants to write, the task that they want to achieve, and then you discover the design based on that, and this way then when you're done with that, your use cases, they become your tests like does it solve the problem that you intended to solve. So I just want to hear your thoughts on the committee process and how it approaches use case first versus framework first design.

@howard.hinnant [28:11]: My personal viewpoint is that nothing should be standardized unless it has some positive field experience under its belt. And so field experience will Will bang out, you know, use cases, you know, if you if you design something and Nobody can use it because the use cases are all screwed up.

@howard.hinnant [28:31]: Then It's not going to get positive field experience. It may get negative field experience. There have been a few times when we have Standardized something without A terrible lot of field experience, and sometimes it, we get lucky and it works out and sometimes we don't.

@Vinnie [28:50]: What are the costs? Like, every, what are the costs of adding something to the standard.

@howard.hinnant [28:55]: It's significant, takes up committee time, takes up vendor implementation time And it is very hard once something gets into the standard, it's fairly difficult to take it out. we have a mechanism for doing that. We do do it, but it is difficult enough that

@howard.hinnant [29:12]: We're not very good at it

@Vinnie [29:15]: So is this rela related to ABI stability. I remember What do you know about ABI stability and the committee's position on it.

@howard.hinnant [29:26]: To tell you the truth, I don't, I'm not an expert on ABI stability, even though I was a vendor. It is important, you do try to maintain it But it does get broken once in a while, and I lean towards being able to break it once in a while, otherwise

@howard.hinnant [29:45]: If you're really rigid about A ABI stability, then you just paint yourself into a corner eventually where you can't improve things. So ultimately you've got to be able to break ABI at least every once in a while.

@Vinnie [30:01]: That's, yeah, I, I agree. So I'm gonna, I'm gonna inject my opinion. I want to make it clear these are my opinions, not yours, and then, and then you can just kind of like riff off of it, right? And you can feel free to critique me. You tell me I'm full of it. I, I won't be offended. So

@howard.hinnant [30:08]: OK.

@Vinnie [30:17]: It seems to me that like, Claims that something might break ABI stability. It's almost like it's a, it's like a very effective veto in the committee. It's like a way to shut down a conversation, and all you need to do is just say, well, this is an ABI break, and then there's no critical thinking that takes place. We don't evaluate is the feature worth it? How much does the ABI brake cost? Like there's no quantitative analysis of the benefits versus the costs.

@howard.hinnant [30:46]: Yeah, I, I think you're basically right. A classic example of this Was moving from a rough-counted string to a short string optimization. That was a huge ABI break. And it hit Google, I mean, not Google, GCC, the hardest.

@howard.hinnant [31:04]: It took GCC years and years to transition its users from one design to the other. And so the cost was very, very high But in my opinion, the benefit was equally high. Or higher

@howard.hinnant [31:23]: And so in my opinion, that's a case where The there was an ABI break. It was a huge ABI break. And yet we still did it, and I'm glad we did. It was still worth it. The Where, where the community is today is better off than when it was before the ABI break.

@Vinnie [31:43]: That's so interesting. I wouldn't, I never experienced ref counted strings. Do do you have any other examples, like more recent?

@howard.hinnant [31:52]: Nothing more recent, but one of my worst stories from when I was Working for Apple was that I was of course aware of ABI breakage, and I wanted to minimize it. And one of the ways I minimized ABI break, and this does, I want to emphasize the word minimize this does not

@howard.hinnant [32:15]: This technique I'm about to say does not eliminate ABI breakage, but it minimizes it. So I wanted to keep as much as possible out of the, the dynamic library that was compiled when you compiled the standard library to ship it. And that is basically, you know, you keep stuff in the headers, keep it as templates

@howard.hinnant [32:34]: You don't Explicitly instantiate templates into the dynamic library. So that there is no ABI there to break. Now, you could still get ABI breakage because the, the customer will Compile your headers into their libraries, and when that changes, it can break their the customer's ABI.

@howard.hinnant [32:56]: But that's a more rare case than When you bake your ABI into your own dilli. And so I had a policy of keeping as much as possible out of the dialib, and my Apple managers did not see the value in that. And so LIPsi++ has

@Vinnie [33:05]: Hm.

@howard.hinnant [33:18]: Some extra fragility On its in its ABI that can't be broken because My managers Forced me to To explicitly instantiate things like vector into the dilub.

@Vinnie [33:34]: How did they, how did those managers make that decision? Like, do they have some body of knowledge? Do they have like some guidelines and some principles like, is there, do they have a retrospective where they look back and they're able to evaluate if that decision like made any sense. What did they, what do they have in terms of like knowledge if you could, nothing proprietary, just general terms.

@howard.hinnant [33:53]: Sure, their, their reasoning, they're, their motivation was so that things would compile and link faster. Which is a, a decent goal But I thought that that benefit was outweighed by the disadvantage of baking in the ABI.

@Vinnie [34:12]: Did, were were they presented with any evidence later that that decision was wrong?

@howard.hinnant [34:17]: No

@Vinnie [34:19]: OK, fair. Let's, I want to talk about variant, OK, what happened with variant, Howard?

@howard.hinnant [34:26]: I was not active in standardizing variant, but I, I know somewhat of the controversy you'll you're talking about, and I at least let me tell you, and you tell me if I'm talking about what you're thinking about. I believe it's the move assignment operator variant.

@howard.hinnant [34:43]: Had a problem if The user's code through an exception during that move assignment. What state would the variant be left in? Is that what we're talking about?

@Vinnie [34:54]: It's definitely related to that, and just, I'll give you a more of a hint is that in I believe the standard library has a variant that can be valueless. In other words, not have a value, whereas Peter Diemov, he created one in Boost called Varian 2 that always has a value. It's guaranteed to have a value, and it and it and and it gives that requirement. It offers that that capability when the type, one of the all the types that are being held are like at least one of them is default constructible, I think, don't quote me on that.

@Vinnie [35:23]: But there's a, there's a schism, and Peter, Peter's variant too got popular, which shows that there's a need. So let you, so go back to, you tell me what happened, like what's the story of the standard variant.

@howard.hinnant [35:37]: Just from a 50,000 ft view because I don't, I don't know the details, but there was a, a big decision about What should the variants be value be? If there's an exception thrown during a move assignment.

@howard.hinnant [35:54]: And and the compromise that was finally standardized over much gnashing of teeth, and I think I believe, I'm not sure I believe it missed several standard deadlines, got standardized years later than otherwise would have. Was that

@howard.hinnant [36:11]: It takes on a, a, a special value. It's almost like a floating point man. It's some, I don't remember the details of what the state is called, but it's essentially not a value.

@Vinnie [36:26]: Yeah, it's called it's valueless.

@howard.hinnant [36:28]: Yeah Something like that. And I'm not familiar with, with Peter's work on variants. So that sounds like a very interesting solution I would, I will make a note to educate myself more about that. I can always, never can go wrong with Peter's work. He, he always comes up with good ideas.

@Vinnie [36:42]: He's No, I know, it's crazy. He's always like he's always right.

@howard.hinnant [36:49]: Yep, he, he's He's a terrific library developer.

@Vinnie [36:53]: He, he recognized the need that, you know, he recognized that little, that little mismatch. I think, I think one of the reasons is he needed a variant to implement like the boost version of like expected, and it was allowing the variant to be valueless, just messed everything up.

@howard.hinnant [37:10]: Yeah

@Vinnie [37:12]: So, OK, so what about exception safety? Exceptions I want to get technical. What do you have any wisdom on exceptions, error codes, when to use what as a library implementer, what do you do? How do you handle them? What are the pitfalls

@howard.hinnant [37:30]: I really like to use exceptions, especially for parsing user input. Cause you can just It, it just makes the code so neat And usually when you're parsing input, you discover your your problem several function calls into

@howard.hinnant [37:50]: Where you would otherwise handle the error. And, and so I'm a, I'm a big fan of using exceptions. I know that there's You know, performance issues with them. They're hard to use and embedded environments because there's often a limited runtime library. I also know that they are extremely difficult to implement both, well, I don't know about the language level, but the standard runtime library support.

@howard.hinnant [38:22]: Is very hard to implement. Now I know from personal experience, So I, I did that for, for Klein apple slash apple. And it's You know, it's, it's not as fast as as returning an error code. Now I've also heard that people have come up with with much better, much faster implementations, and I'm really happy to hear that. I'm not familiar with how, you know, the, the techniques that they use to implement them to achieve those performance gains.

@howard.hinnant [39:00]: And You know, sometimes I use error codes to to return errors. That is simple, it's fast. But sometimes your users forget to check error codes, so it's by no means foolproof. the, the advantage is you can always use it in embedded environment, so that, that part's good.

@howard.hinnant [39:26]: So far, I, I think we're, we're in a state where We You know, sometimes exceptions are the right answer and sometimes error codes are in the right answer, and that's frustrating because we would like to have one single answer that works.

@howard.hinnant [39:43]: Optimally everywhere, and we probably don't, we're not there yet. Maybe someday we'll, we will be.

@Vinnie [39:51]: So this is, that's very interesting, just like relating my own experience, you're right, like the the exceptions are very convenient because you can just write your code without worrying about them. However, you know, I do a lot of, I write a lot of networking code, and I implement protocols like Jason or, you know, URLs and my experience is that

@Vinnie [40:11]: If you have Untrusted inputs, right? In other words, if you have inputs that are coming from the internet or possibly adversarial source is that you really do want that error code. You, so for me, my design principle is never allow untrusted inputs to generate infinite exceptions.

@howard.hinnant [40:21]: Yeah. Hmm

@Vinnie [40:32]: So, I usually

@howard.hinnant [40:33]: Yeah, OK, so, yeah, an adversary could take you down performance wise, I guess.

@Vinnie [40:38]: Exactly I still offer the exceptions, like for example in a constructor, so if users have the use case where they don't, they don't have untrusted inputs like let's say they're constructing from a like a constant string that has to be in a certain format. They know it's OK. Then they can use that. But I also try to give them a path for the error code.

@howard.hinnant [40:52]: Mhm Yeah

@Vinnie [41:00]: So tell me this

@howard.hinnant [41:00]: I

@Vinnie [41:01]: Sorry, go on

@howard.hinnant [41:03]: Well, I was just gonna say I, you mentioned as construction using string. I've, I've recently becoming very enamored with constructing objects Via strings or string views, Just, use it as an explicit conversion operator from string. It's, it's a really nice way to, to parse an object in is to construct it from a string view.

@Vinnie [41:26]: That's the pole design principle of boost.URL. It uses views extensively. Of course, Nikolai Jessis is not really happy about that because it's effectively it's a reference. A string view is a reference, and it can dangle

@howard.hinnant [41:40]: Yeah.

@Vinnie [41:41]: So what are your thoughts on that? Can you, can you share any technical insights about like it String view dangerous? What, what, what, how do we deal with this thing?

@howard.hinnant [41:54]: I would say any good tool is dangerous. I mean, I'm a big fan of pocket knives and Kitchen knives and all that sort of stuff, but they can, they can really help in the kitchen or they can chop your fingers off. You just know how to use them. And so yes, string views are dangerous. That's not meant to be a a damning statement though.

@howard.hinnant [42:14]: When you use it in a constructor. You have to be smart enough to Take the string view and completely consume it into your own memory before returning. You know, you don't Keep a reference to a string view because as you say, there's no telling what what you're pointing to after the constructor returns.

@howard.hinnant [42:37]: So if you use it right, it's, if you use it with the knowledge of how to use it correctly, it's not dangerous, but if you use it carelessly, or in ignorance, then it is.

@Vinnie [42:38]: Wow, that's, that's. Dude, that's, I love what you said about the pocket knife. That's amazing. It's so good. That's really good advice. That's such practical advice. I mean, it's relatable, it's very visual, and it kind of like underscores the point and like, to me, that's a really good design principle and I mean, we don't, we, isn't this the spirit? Isn't this what C++ is? It's the pocket knife.

@howard.hinnant [43:09]: Yeah, yeah, it really is.

@Vinnie [43:12]: OK, next, let's move on. Let's talk about everyone's everyone's favorite subject performance. So, people are all obsessed with performance, sometimes they're prematurely obsessed. sometimes they're rightfully obsessed, but there's a tension between interface ergonomics and performance, right? In other words, the best, the most ergonomic interface is not necessarily the most performant. So can you share any technical insights, especially stories from your, your, your career that relate to that.

@howard.hinnant [43:19]: Hm

@howard.hinnant [43:52]: I don't think I have any good examples that that depend on Interface or the API versus performance. I, I can't talk about Something slightly related, and that is correctness versus performance.

@Vinnie [44:08]: Love it. Let's do it.

@howard.hinnant [44:09]: For for me, performance is the 2nd most important goal When when writing a program or when writing code, And the most important goal is correctness. And every once in a while, We seem to reverse those two.

@howard.hinnant [44:27]: And, and prefer performance over correctness. And I have a specific example in mind. The, the optimization that compilers do. When they stumble over undefined behavior. And do stuff like just remove code that the user has written because it

@howard.hinnant [44:49]: Has undefined behavior in it I consider that performance over correctness.

@Vinnie [44:56]: Hmm

@howard.hinnant [44:57]: If, if the compiler had not made the optimization, the code would Would work right, you know, get the right answer Although For example, signed integer overflow. That's, that's literally the example I'm I'm looking at. And I think this may have changed in the, in the latest standard. I haven't kept up with it, but just a few years ago at least

@howard.hinnant [45:20]: Signedger overflow was undefined. And it, I don't recall, I don't know if it still is or not today. But all implementations, you know, down at the hardware level. If it overflowed, it just wraps to complements.

@howard.hinnant [45:37]: And such code Would usually do what the programmer wanted it to do, would always do what the programmer wanted to do if it were just allowed to overlap to to Yeah, over Overwrite over wrap. What, what's the word I'm looking for there?

@howard.hinnant [45:55]: Wrap on over

@Vinnie [45:55]: Rap. Wrap around

@howard.hinnant [45:57]: Yeah, like, like unsigned integers. And so there's, there's infamous cases of, you know, Programmers putting in checks to check for overflow. But in check, but the check itself allows overflow to happen before it checks.

@howard.hinnant [46:14]: And, and so it's undefined behavior and the compiler comes along and says, oh, that can't happen. I'll just remove the check. And it makes correct code incorrect. In the name of making the code faster.

@Vinnie [46:28]: That's kind of a, that's kind of a dig on the compilers though, but what about for for the authors of libraries.

@howard.hinnant [46:28]: And so For, for authors of libraries that That You know Need to work with today's compilers that will do things like this. They need to

@howard.hinnant [46:48]: They need to be experts in avoiding undefined behavior.

@Vinnie [46:53]: The C++ make it easy to get undefined behavior? How is this a problem that the committee is addressing. Do, when, when library, when library or language proposals are made? Is there an analysis of like what's the undefined behavior possibility? Like are there retrospectives when undefined behavior emerges, like what's the collective WG 21 wisdom with respect to UB.

@howard.hinnant [47:16]: I think for for a long time it was You know, while I was active It was Perfectly fine to have you be in the programmer's got to be smart enough to avoid it. In more recent years, I'm

@howard.hinnant [47:33]: I haven't been involved as much. Maybe I was the cause, cause now that I'm not so involved they're fixing it, but,

@Vinnie [47:38]: That's

@howard.hinnant [47:41]: You know, it, it sounds to me like they're, they're backing off of that stance with things like erroneous behavior.

@Vinnie [47:48]: Hmm

@howard.hinnant [47:49]: Which I'm not an expert on, but I'm My general impression is that Undefined behavior is Is not a Is, is not a strongly sought after as it, as it once was.

@howard.hinnant [48:05]: So it's, I think it's a, it's a recognized problem and it's a A work in progress that is slowly improving But I was just not a fan of undefined behavior, especially when it comes to things like

@howard.hinnant [48:24]: Signed integer overflow where The hardware has a behavior and it's well defined, and the standard just says nope, we're not going to, we're not going to go that way.

@Vinnie [48:35]: Very interesting. I, I'll just give you, I'll give you a story of my own. So I, there is a tension between performance and the desire to avoid undefined behavior, just something as simple as if you have a function with a narrow contract and you want to make it to have a wide contract, then you maybe you need to do some kind of check. And that is, is a performance loss and you're making everyone who calls the function pay for it, whether they're passing, you know, the right parameters or not. So there's a natural tension there. So what I learned, well, I, I, what Peter Dimov told me is that there's a general principle

@Vinnie [49:14]: Again Adversarial in the functions that accept adversarial inputs should have wide contracts. So for example, like a Jason Parser, like a URL parser code like that, you don't, you wanna make sure that like the function can accept everything. So if you have a parser, it's a call, like let's say there's a programmer error like the caller calls a function at the wrong time. In for performance, you might just want to let that be undefined behavior, and you just have to tell them you have to use it correctly. However, if you're being exposed to

@howard.hinnant [49:23]: Yeah.

@Vinnie [49:45]: Adversarial inputs and you have a parser and you want it to be robust, maybe you should do the check and throw an exception. So that's an example where there's like a trade-off that has to be made there. So I think that there's, there's some principles for making that trade-off that maybe we, at least in the committee, maybe even the larger C++ community have not really captured and formalized.

@howard.hinnant [50:06]: I, I think that's a good point and it, it's a good distinction that that you and Peter make there. one thing I'd like to add to it, and I'm sure you already know this, but It, it, it's often good to have like a two-layer API, a low level layer that is unchecked.

@howard.hinnant [50:23]: And then a a safer layer, checked layer built on top of that, so that The end user no the the higher, the mid-level say writer programmer, knows whether he's got this adversarial input or not?

@howard.hinnant [50:40]: And can choose the appropriate layer For, for his software, that the the the checked layer or the faster unchecked layer.

@Vinnie [50:50]: Dude, that, that's amazing. I think, so this is, so this is so good. So this is a design principle. So what you're saying is, when, when, when designing An API that needs to have a wide contract. If you, you should also consider if there are use cases where the callers may want to eliminate the performance loss and offer a narrow contract instead, which is which is more fundamental. Yet both APIs exist.

@howard.hinnant [51:20]: Yeah.

@Vinnie [51:21]: I really like that a lot.

@howard.hinnant [51:21]: Yeah.

@Vinnie [51:24]: Tell me this, what Questions should every paper answer? Like, if we're, if we're evaluating papers, WD 21, their stock in trade is papers. That's like their currency. Papers in, papers out. What should every paper answer? What question?

@howard.hinnant [51:41]: What problem am I solving and if this paper's not accepted, How, how does the programmer solve this problem without this solution.

@Vinnie [51:52]: You mean, are you telling me that every paper doesn't already have that?

@howard.hinnant [51:56]: Well, I would hope every paper does, but You know, if it's If it's something If it's a convenience API that's being offered. Like, I don't know, Standard exchange, real simple function.

@Vinnie [52:15]: Yes.

@howard.hinnant [52:16]: It doesn't really do much It offers a slight convenience But You know Do we, do you, if if standard exchange weren't there, how hard would it be to To do what Standard exchange does. It, it'd be

@Vinnie [52:33]: You tell me

@howard.hinnant [52:34]: It'd be easy

@Vinnie [52:36]: So you're saying that facility shouldn't exist.

@howard.hinnant [52:39]: I didn't vote for it So

@Vinnie [52:42]: Well then, what evidence demonstrates genuine demand like, so we're in the context of evaluating papers. There's a lot of papers in my opinion, I think too many papers that 3-year cadence is crazy. There's a, there's pressure to ship things in like before they're be completely usable. So I think we, I think an evaluation framework should be formal. So if we had a formal evaluation framework, what would you require as evidence that demonstrates genuine demand.

@howard.hinnant [53:13]: I'd like to see You know, something along the lines of a a GitHub project or similar hosting. That That shows evidence of people using it. Successfully and happily.

@Vinnie [53:29]: So you mean like, so the paper should include hyperlinks to multiple open source projects that are already using the facility for a library only proposal.

@howard.hinnant [53:39]: Yeah, that'd be nice

@Vinnie [53:41]: That'd be amazing, but, but if they, but then if they do that, isn't that evidence that there's not really a coordination problem. They were already able to get the library.

@howard.hinnant [53:42]: Hm. True But Still, if it's, if it's providing a, a, a huge benefit to enough people.

@howard.hinnant [54:03]: Then It would, it would have an even larger audience if it were in the, if it came with the standard library instead of, you know, Joe Schmos or Howard Hinneitz or Or Vinny Falco's GitHub link.

@Vinnie [54:22]: There How do we how do we distinguish from a pro a proposer-driven proposal from a user-driven proposal, and what I mean is proposer driven means that the author, maybe they have like a personal interest in seeing something get accepted versus a user-driven proposal is one which is sourced from an actual need in the market that's been identified. How do we distinguish those two types of papers. And first, do you even accept the binary? Do you accept that taxonomy?

@howard.hinnant [54:54]: I'm not sure because a user, what's you're describing as a user-driven proposal. Still has to have a champion that's willing to put in buku of time writing the proposal and going to the Standards Committee and arguing about it and You know, it's got to have this champion

@howard.hinnant [55:13]: So I don't see a user proposal happening without The The other one that I, I've already forgotten how what you called it.

@Vinnie [55:22]: User-driven versus proposer-driven.

@howard.hinnant [55:25]: But yeah, I don't, I don't see a user-driven proposal even appearing without a without it also being a proposal-driven. Paper, because without the proposer, There's nobody to do the work, and it's a huge amount of work.

@Vinnie [55:42]: We're gonna, we're gonna wrap this up in a few minutes, but before I do that, I was, I want to give you the opportunity to say Anything about The committee. So the committee's accomplished quite a lot. It's definitely producing things like there's no question, papers are written, they move through, they go into the standard and the standard ships on time. So, there's no question that the committee is producing output, but my question is, is it valuable output? And I'm not asking you to answer that, of course. I mean, that would be pretty self-serving, but my question is, how do we measure, how do we measure if the output that's being produced is valuable. What are the me

@Vinnie [56:21]: Tri c s A business that's a for-profit business can't survive without metrics. They have to know, are they satisfying their customers? Are they bringing in money? What are the metrics that WG 21 uses or in your opinion, what should they use to evaluate the quality of their work output in a retrospective.

@howard.hinnant [56:39]: I've, I've seen some email threads going around lately among committee members that are looking at the number of C++ users versus the number of programmers and in other languages, and the change from year over year.

@howard.hinnant [56:57]: And I, and I don't remember the source they got, but they, they have gotten a source that they seem to trust. That I think is a pretty good metric that if you're If you're growing your user base And you're growing it as faster, faster than other languages are growing their user base

@howard.hinnant [57:18]: That's hard to that's hard to argue that that's not a good metric, as long as the data is believable.

@Vinnie [57:25]: And yet, and yet that simply might be indicative that society as a whole is having more of the types of problems that C is better at solving compared to the other languages. I mean, we have to be careful

@howard.hinnant [57:39]: Yeah, but if C++ is better at solving them, and C++ is literally made up of all of these proposals. Then You're doing a good job.

@Vinnie [57:49]: Well, no, that's, that's definitely true, but people might be adopt, people might be using C++ grudgingly, right? They might be using it despite whatever issues that they are, because that's their only alternative. Like, we could be measuring feature, like people, people

@Vinnie [58:06]: Maybe they're, they're using C++, but what's the feature adoption rate? Are people using the new facilities that we're adding? What's the time to usability when the committee ships a major feature, for example, senders and receivers or co-routines. How long, how many years until people actually adopt the feature. What about like workarounds C++ puts out a new version, but yet every corporation seems to have their own big library, Absale, Folly, BDE. Why do corporations have to maintain their own huge libraries that mimic a lot of what the standard library does

@Vinnie [58:36]: If the committee is producing outputs that everybody needs.

@howard.hinnant [58:39]: I would say that that some of that is gonna, is gotta be historical because As things are added to the To the, to the standard, if you wind back the clock, those things weren't in the standard years ago, and yet the those same companies still had those needs and so there are some there's a a fair amount of things that companies wrote themselves and then it later got standardized. Either that

@howard.hinnant [59:07]: Either they got their library standardized or similar functionality got standardized that could be could replace their library now, but then they'd have to rewrite a bunch of code to use the standard stuff.

@Vinnie [59:21]: That's, that's fair, that's fair. And yet those statistics that you quote show that while the number of C++ users is definitely growing, the adoption of new versions of the language does seem to be a little bit sluggish. I mean, there's a lot of people in the older versions of the language. Could one not argue that the reason that there's not a big rush to adopt the latest version of the standard is because it's not providing significant value over the previous.

@howard.hinnant [59:47]: That could be part of it. There's also just inertia. It takes time for companies to Decide that they are going to go to the expense to upgrade the benefit of upgrading has to outweigh the, the cost. And then there is a, a

@howard.hinnant [1:00:03]: I'm afraid to say that one of the things that companies will wait for is all the compilers they target have to implement all the features that they're going to upgrade to. And if, if one particular vendor is behind and providing features.

@howard.hinnant [1:00:20]: That may hold up their migration, you know, a company's migration to a new standard.

@Vinnie [1:00:26]: I gotta say I'm one of those people.

@howard.hinnant [1:00:28]: Yeah, and I, and I find that very, I find that quite frustrating and I wonder if the, the standardization cadence is not so rapid that it is making it harder for implementers to stay up to date.

@Vinnie [1:00:30]: That one You know, I wonder, I wonder the same thing.

@howard.hinnant [1:00:45]: I, I Yeah, I don't know the answer to that question, because I'm, I'm not That close to vendors anymore

@Vinnie [1:00:54]: But what about, what about retrospectives. So WG 21 process, it moves, papers are created, but do we, it seems that there's no system where we say, OK, let's, let's put a pause and let's analyze. What's our, what's our performance, what's our metrics? How do we measure what we're doing? Have we made any mistakes? Are we continuing to make mistakes? How do we add to our institutional knowledge so that like when people come on board, we can help them understand like what WG 21 principles are, not which room to go to after the orientation, but like why things are sometimes marked no except versus not.

@howard.hinnant [1:01:31]: Yeah I, I think there's a need for that. And, and to the best of my knowledge, excuse me. I don't think it exists at this time.

@Vinnie [1:01:43]: Yeah, it's hard

@howard.hinnant [1:01:43]: But, but I'd love to see stuff like that in, in writing.

@Vinnie [1:01:48]: I like that too. Well, listen, Howard, I really appreciate it. This has been super amazing, and I, I think I'm gonna show you the context of like where, what, what this is going to be put to use with, and I think you're going to be very excited. So,

@howard.hinnant [1:01:49]: Hm OK. Well, as

@Vinnie [1:02:04]: I'll, I'll

@howard.hinnant [1:02:05]: It was good talking with you, Penny

@Vinnie [1:02:07]: Oh, definitely a pleasure and I'm, I'm so glad you, you sounds like you're doing, really doing great. You're enjoying yourself. Wonderful. And I really enjoy the time that we spent together at Ripple. Thank you so much and God bless.

@howard.hinnant [1:02:16]: Oh, thank you, Vinnie

@Vinnie [1:02:18]: Bye bye

@howard.hinnant [1:02:18]: Talk to you later