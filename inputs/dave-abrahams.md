# BOOST_DAVE_ABRAHAMS_STRINGOUT_v01

---
filmed Date: 2025-12-19
location: San Jose CA
camera: A / B
audio: Lav / Boom
type: INTERVIEW
video link: ​​https://vimeo.com/1152633977/77d3f828e6?fl=tl&fe=ec
summary: Abraham provided everything to “carry” first half of film, “golden age” leaving after Concepts WG21 debacle, drawn to Apple to develop Swift language; talked about youth, college playing in band with Phish lead (bestie), Doug Gregor, Dawes, IU contingent; He explained visiting Sonda story, threw much criticism at Foundation for years of poor management, and explained the community voted for alliance bc it was choice of overworked volunteers versus well financed org that could get things done. only thing he came after Alliance hard about was “Nobody outside the official governing body should have been trying to buy the domain, especially not in the shadows. Stuff should be above board. It worries me to see Boost in the hands of an organization that would go around the official governing bodies to acquire the domain.” (Falco to refute in his interview)
---

## Transcript Start

[00:00:00] 

[00:00:00] **DAVE ABRAHAMS:** I am Dave Abrahams. Uh, I have been a computer scientist since, uh, for a little over 40 years. Um, and, uh, I'm here to talk about Boost. I, I guess one important thing is that, that there, [00:00:30] the, the person who actually is most responsible for starting Boost is Beman Dawes, and he hasn't, uh, he passed away a few years ago and, and isn't generally known.

[00:00:46] **DAVE ABRAHAMS:** He was not, he was not a big self-promoter and, uh, and his, his ethos was really central to, to making what Boost is, um, [00:01:00] or making boost what it is. And I, I found it really fascinating that any documentary filmmaker would actually be interested in this, in this area. And, um, I, I guess also, I, I think there are a lot of people out there with something to say about this, and I wanna make sure the right story is told.

[00:01:26] **DAVE ABRAHAMS:** Well, the, so I, I heard about the film because the [00:01:30] filmmakers contacted me. Um, and, uh, the, the, there was some reticence, uh, because, um, I've been out of, out of the Boost process and Boost Community for the most part, for, for quite a few years now, since 2013. Um, uh. But, uh, but there was recently an upheaval in the, in the [00:02:00] governance of Boost And, and, uh, for what seemed to be good reasons, there have been, uh, there were a lot of emotions around that.

[00:02:10] **DAVE ABRAHAMS:** And, and the, the organization or the parent organization, I don't understand all the details, but the parent organization of the organization that now runs Boost, um, uh, uh, is, uh, apparently [00:02:30] funding, uh, this documentary. And, um, and so I was, they have a, a very particular slant on, on how things were going with Boost.

[00:02:43] **DAVE ABRAHAMS:** And I was concerned that they might have, uh, undue influence on the content of the, of the documentary. The a, um, talk to you about it at one point. Uh, well, yeah, I mean, we were involved in an [00:03:00] email thread, uh, herb Sutter sent when you contacted him, uh, herb Sutter sent out a message to a whole bunch of people that he imagined might be involved, uh, or been asked to interview and wanted to, wanted to find out what our take was.

[00:03:19] **RAY NOWOSIELSKI:** What do you think most people, at least in the coding world know about Boost? 

[00:03:24] **DAVE ABRAHAMS:** So things, things change pretty quickly in that world, and, [00:03:30] and I've been mostly out of the C++ world for, uh, for 13 years, um, more or less. And so I don't actually know what people think. I haven't been talking to them about Boost.

[00:03:46] **DAVE ABRAHAMS:** Um, I, I can tell you, I imagine that, that the history. Um, is not all that well known. And the, [00:04:00] and I think, I think the, the first association a lot of C++ programmers have with Boost is these days, uh, a negative one because of the way using it. The, the easiest way to use Boost the, and the, and the way that, that, uh, it is often delivered is as a big [00:04:30] unit and, and it's a very big unit.

[00:04:33] **DAVE ABRAHAMS:** Um, even though there are, there are, you know, many sub libraries and you can use them, uh, as long as you pull in all of the other dependencies of that library that are in boost without pulling in all of Boost, um, uh, programmers really don't like having that heavy a source code base, uh, as something that they're, they [00:05:00] depend on.

[00:05:01] **DAVE ABRAHAMS:** And keeping track of which of which parts you're actually using is not, not the easiest thing to do. So I think there's that, there's also, you know, boost, uh, was started in, uh, 89, I think 89. That was when, when the first C++ standard was. Um, 98 Was 98. Okay. Yeah. All right. I'm getting old. [00:05:30] Um, uh, so, so Boost was started in, in 98, uh, when the C++ standard was only at its first version, and many compilers at that time didn't even support, uh, that.

[00:05:48] **DAVE ABRAHAMS:** Well at all. In fact, we're very far behind that. And so there is a lot of code and conditional, conditionally included code in [00:06:00] Boost, uh, that is designed to work around that problem, work around the problem of compilers that don't actually work properly and, and, uh, and that have different features, and to try and make the landscape for boost code, uh, more uniform so that there was a way to write a piece of code and have it work everywhere.

[00:06:27] **DAVE ABRAHAMS:** And, and all of that [00:06:30] machinery is, is a legacy burden for people nowadays who are using, um, who are using more modern C++ compilers. I think the idea that Boost is a monolith is, is part of it. Yeah. I think that that's the only thing that really comes to mind. The i the idea that you have to take all of it if you, if you want any of it.

[00:06:56] **DAVE ABRAHAMS:** Um, and maybe you know that [00:07:00] when you, when you tell programmers that it's often, well, like I, you know, I don't care because even if I take the parts that I, that I am using, there are too many dependencies inside of Boost and you know, that's too much code and I don't want to, to consume that much and be dependent on it.

[00:07:25] **RAY NOWOSIELSKI:** Curious, how much of a cinephile are you, are you a movie fan? 

[00:07:29] **DAVE ABRAHAMS:** [00:07:30] Uh, I like good movies, but I, but I don't watch a huge number of them. Why? 

[00:07:37] **RAY NOWOSIELSKI:** I was kind of curious, what if you, I mean, you're obviously artistic. Um, you were making this movie on Boost, what? What would be the elevator pitch? What would be, you know, what's the story you you would tell as a movie on Boost?

[00:07:55] **DAVE ABRAHAMS:** Yeah, that's, um,[00:08:00] 

[00:08:00] **DAVE ABRAHAMS:** well, uh, don't ask me to make it elevator pitch concise, but, but I, I think, I think Boost is, is pretty unique among open source projects in, uh, in demanding or, or at least trying to promote a level of, of rigor and, uh, [00:08:30] and sort of, and also, uh, uh, progress by consensus. Um, and so I think that's, I think that's a really interesting story.

[00:08:42] **DAVE ABRAHAMS:** Probably one of the longest lived large projects, uh, out there that keeps growing. Um, and, and so that's probably, that's probably interesting too. I grew up in Princeton, New Jersey. Um, [00:09:00] my father, uh, was a physics professor at Rutgers. Um, and my mother, uh, was a choreographer. Uh, during, uh, my, my early childhood she had a job, uh, teaching dance and doing choreography at Princeton University.

[00:09:25] **DAVE ABRAHAMS:** And then, uh, later when, when I was around, when I was in [00:09:30] high school, she started her own dance company and started putting on her her own productions. Arguably my dad, um, uh. I I didn't really try to do any dance until I was, until I was, uh, much older. But, but, you know, they were both, they, you know, my dad was a [00:10:00] big appreciator of the arts and my, and so was my mom as well as being an artist.

[00:10:07] **DAVE ABRAHAMS:** And, uh, and so art and music were always, uh, an important part of my, my life, or at least, at least by the time I was in high school, music became a very, very serious part of my life. So my dad, uh, you know, I, I would always, I would see him working. He was a theoretical physicist, [00:10:30] so that means he's working at home.

[00:10:32] **DAVE ABRAHAMS:** He's, he's writing these, these equations, you know, and, and, uh, you know, it's, it's calculus and all of these, you know, Greek symbols in it. And it captured my imagination a little bit. I, I, you know, wanted to understand what all of this, what all of this was about. Um, so, uh, so, you know, [00:11:00] that fed my scientific side for sure.

[00:11:02] **RAY NOWOSIELSKI:** If we ask your parents, uh, to describe, uh, what you were like as a kid, what do you think they would say?

[00:11:09] **DAVE ABRAHAMS:** I was troubled, um, uh, and, uh, and very creative. And, uh, people often said I was smart and, and wasn't fulfilling my potential, but I think my, my [00:11:30] parents, uh, would, would say that I was, I was unwilling to do stupid things, uh, that were.

[00:11:38] **DAVE ABRAHAMS:** That were, uh, required of me by my school or whatever, let's say, uh, rebellious. No. I mean, there were a lot of things at which I, I didn't apply myself. Um, I would only apply myself to the things I was interested in. Um, uh, you know, like an [00:12:00] example from, from my, from the first grade that my mom always talked about was, uh, there was, there was an assignment in some workbook where, uh, it was something like a bird and you're supposed to color the wings blue and color the beak red or whatever.

[00:12:18] **DAVE ABRAHAMS:** And, and I, you know, put a little blue mark in the wing and a little red mark in the, in the beak. And my teacher complained that I wasn't really doing the, you know, I wasn't really doing the [00:12:30] assignment. And like, I hated working with crayons anyway. 'cause like, I, I was already somebody who did drawing and stuff, and I, and crayons.

[00:12:41] **DAVE ABRAHAMS:** I never felt like I had much control over them. I was not, this was not an artistic exercise. The, the idea was to under, I was probably to make sure you understood the, the words you were reading, right. The instructions. Um, so, [00:13:00] so yeah, it was, there was that. Um, and I was able to, to get by in school without doing a lot of the work, uh, for a lot of the time.

[00:13:15] **DAVE ABRAHAMS:** And, and therefore, you know, I got by getting B'S and, and only, only a's in classes where, where my spontaneous performance was, [00:13:30] was what mattered. Right. And so I, I think people saw that in. And, uh, and decided I wasn't fulfilling my potential. I think I always, I always had this story that, that in my mind somehow that life was really gonna begin in college.

[00:13:51] **DAVE ABRAHAMS:** That's where the, that's where the interesting stuff happened. And, um, late in my high school [00:14:00] career, I, I realized that, that if I wanted to get into a good college, I was gonna need to apply myself. And, and so I started doing that maybe late junior year or more, possibly, possibly senior year. Um, uh, but I still didn't, I still didn't really know how to study and I, uh, and I only learned that after some,

[00:14:29] **DAVE ABRAHAMS:** [00:14:30] some, uh, trial and error at college. 

[00:14:33] **RAY NOWOSIELSKI:** What did you think you wanted to do with your life or your, you know, professional goals, 

[00:14:37] **DAVE ABRAHAMS:** but, well, I, I knew I was really interested in computers, but I was also, I, I was also really into music, but I never saw that as, as a potential until I, until I started to see the, the success of my friend Trey.

[00:14:59] **DAVE ABRAHAMS:** Uh, [00:15:00] Trey Anastasio was somebody I grew up with. Uh, he's the leader of the band, Phish. And, uh, and yeah, during,

[00:15:14] **DAVE ABRAHAMS:** during my college years, I started to, to see him doing some incredible things and, and, uh, the idea that maybe, maybe music would be a, a good choice for me also or something, uh, started to [00:15:30] become a little bit. It's more prominent, uh, more realistic? Well, okay. I mean, there was something I, I observed with my dad and the way he was with his colleagues and, uh, that, that really, that really influenced the, well, I would say, I would say more than anything, it influenced where, where Boost Con, uh, was started and the spirit with which it was started.[00:16:00] 

[00:16:00] **DAVE ABRAHAMS:** I mean, there was this kind of sense that he was engaged in, in a collaborative intellectual endeavor. And that's the way I thought of Boost, you know, when that came along. 

[00:16:14] **RAY NOWOSIELSKI:** What about, um, was Trey , Trey been, um, a close friend for most of your life? What, what was your, how did you meet Trey and what was your friendship like?

[00:16:24] **DAVE ABRAHAMS:** Um, so we were, we were in school together in high school, um, [00:16:30] and we didn't start to really know each other until, uh, until we both started playing guitar. And, uh, then, you know, we were doing all this freeform improvisation and, and, uh, and we got, we got pretty close through that. Uh, then the, the, [00:17:00] the other two core members or founders of my high school band, uh, which Trey was not in, ended up, uh, ended up dropping out of college.

[00:17:13] **DAVE ABRAHAMS:** Uh, and Trey was also taking a year from college, and they, they got together and started making music and I, I, you know, got involved in that occasionally. And then, you know, once, once Phish became a thing. [00:17:30] Uh, we went to a lot of shows and, um, you know, uh, we were at Trey's wedding and, uh, yeah. Um, so we were, we, we visited Trey a few times.

[00:17:46] **DAVE ABRAHAMS:** Actually. We were pretty close. 

[00:17:48] **RAY NOWOSIELSKI:** What was the sound style of your high school band?

[00:17:52] **DAVE ABRAHAMS:** I would've thought of it at the time as, as kind of, uh, progressive rock. Um, it [00:18:00] was had kind of elements of, of folk in it. It was also, it, it was also homegrown in a way that I, I totally wouldn't have appreciated it at the time, but, uh, you might say it was kind of punk in that way.

[00:18:17] **DAVE ABRAHAMS:** It was like, um, we, we weren't, uh, we weren't trying to be slick. Um, uh, there were, there were raw elements. [00:18:30] Okay. Wait a second. You want to, uh, before, before we do that, don't you want to know how I got into programming? Um, I got into programming because, uh, uh, so this high school that I went to had, actually, it was when I was in middle school.

[00:18:48] **DAVE ABRAHAMS:** It was a combined high school and middle school. Um, when I was in middle school, some kids showed me the, the teletypes to [00:19:00] the computer system at the school. And, uh, you know, people nowadays probably don't even know what a teletype is. Um, it was kind of a computer terminal that, you know, printed the, the output on, on paper.

[00:19:17] **DAVE ABRAHAMS:** Um, it was just letters, right? It was like a typewriter essentially that was computer controlled. And so it could listen to your, your keystrokes and. And print stuff on the [00:19:30] paper. Uh, it also had, it also had a, a tape rea, a tape reader, um, paper tape, uh, used to, to save programs. Anyway, the, this kid showed me the, the teletype to this computer system, which was a, a PDP eight, which was, you know, a refrigerator sized, um, very low power, uh, computer by today's standards, [00:20:00] minuscule with, with magnetic tape drives for long-term, uh, uh, storage and, you know, blinking lights on the front panel and switches where you could enter binary, um, uh, you could enter machine instructions in binary and, you know, really, uh, primitive thing.

[00:20:22] **DAVE ABRAHAMS:** Anyway, the, this computer was connected to a bunch of, of teletypes [00:20:30] around the school, and you could play, you could play various games on these teletypes, and they were actually games from a, a book 101 Basic Computer Games. I was, I was fascinated. Um, this, you know, I thought, I thought this was cool.

[00:20:50] **DAVE ABRAHAMS:** I wanted to understand how this worked. And, uh, and so eventually I started learning how to program in basic, and I was able [00:21:00] to write programs on these teletypes. And, um, and I eventually got that book, uh, learned that, that, or maybe my, my dad in, uh, told me about that there was a much larger computer, PDP 10 at.

[00:21:20] **DAVE ABRAHAMS:** At, uh, Rutgers that maybe I'd be interested in, in working with. And, um, it was [00:21:30] basically a room sized computer. And not only did it have basic, but it supported, uh, few other programming languages, uh, like Alga and Fortran. And so I started, I started, uh, getting interested in Alga. I think at some point. Uh, my, my brother, since he was really into video games, ended up getting an Atari computer, which I started, I started to program.

[00:21:59] **DAVE ABRAHAMS:** And then [00:22:00] the key, uh, a key thing that sort of, um, broke open my, you know, my perspective on, on computing was, um, somehow I learned that, that I could get accounts on the computer system at Princeton where my mother worked. And um, actually I don't think I was supposed to be using it. I think it was, I think it was supposed to be her account.

[00:22:29] **DAVE ABRAHAMS:** Um, [00:22:30] uh, but this computer system, uh, had, it was an IBM 3 70. It had a PL, uh, which, uh, was, is a language with all the funny symbols that my dad was using as part of its normal character set. So, um, so I found that really fascinating and it, and a PL is really a completely different perspective than, than basic.

[00:22:57] **DAVE ABRAHAMS:** Um, and so that really [00:23:00] opened my eyes and I started doing, uh, some, some, I guess by today's standard super primitive 3D graphics. I was really interested in that. I was interested in the idea of using, of using computers for architecture, um, which wasn't a really a thing at that time. Um. And, and the, the a PL system had these vector graphic displays, which, you know, would, would essentially [00:23:30] draw smooth lines that wasn't broken up into pixels the way the way most displays are today.

[00:23:36] **DAVE ABRAHAMS:** Um, and, uh, and yeah, so that, that lent itself to, um, to things like architecture. I was pretty obsessive about working on this stuff. I would, I would actually, uh, break into the Princeton University engineering building to go use the system. [00:24:00] Um, and, uh, it, you know, I didn't, I didn't damage the building, but it was pretty easy to slip a stick or a card in the, in the door and get it to unlock.

[00:24:11] **DAVE ABRAHAMS:** And, um, so, so yeah, that was, uh, by the time I, I reached college, computer science was definitely one of the things that I wanted to, wanted to study. And so I entered Penn with, with computer science major [00:24:30] and a music minor. I think I found out about the, about the Princeton system from a friend of mine who I went to school with, whose dad was in charge of it.

[00:24:42] **DAVE ABRAHAMS:** Um, and, uh, and yeah, uh, uh, his name was Yra Azzoni. Um, and, uh, uh, yeah, but, but [00:25:00] none of my friends, aside from him, and we were only, we weren't really close. Uh, uh, none of them, aside from him were as were as into it as I was. I, I'd always been. Fascinated with how things work. When I was doing, when I was doing music, I started to build my own effects pedals, um, you know, from, from other people's [00:25:30] designs.

[00:25:30] **DAVE ABRAHAMS:** So I wasn't, uh, you know, I wasn't, uh, that great, but, but I was really into it. My dad had been, my dad had built a, a TV from a, from a kit. Um, there was a company called Heath Kit that sold, um, various kinds of electronics kits and, uh, and so I kind of had that, uh, that, you know, exploring technology thing [00:26:00] going on, uh, for a long time.

[00:26:02] **RAY NOWOSIELSKI:** It's just a lot of people in the boost orbit that we've interviewed, they, um, what we've been hearing is, uh, their other great passion is either, um, culinary puzzles or the big one that's come, comes up again and again is, is music either playing or writing? And what do you, what do you think that is? 

[00:26:22] **DAVE ABRAHAMS:** There, there's sort of, there's two ways to understand music, right?

[00:26:24] **DAVE ABRAHAMS:** One is it's in your spirit and, and you [00:26:30] feel it. And, and there are people that need nothing else, right? But as soon as you start to analyze music, you, you realize that it's very mathematical. Um, and that's the other way to understand music and, uh, and, you know, to have the most power as a musician, I think, I, I think you, you need to have both things going on, right?

[00:26:56] **DAVE ABRAHAMS:** And, uh, so I think, I think that [00:27:00] mathematical structure, um, the, you know, the rules and um, and ways the parts of music play off of each other is, is a lot. Like math and, and programming as Alex Steppen of would say is, is mathematics plus memory. So, um, so it's, you know, programming's very mathematical. Uh, my brother [00:27:30] is Jonathan Abrahams.

[00:27:31] **DAVE ABRAHAMS:** He's, uh, he's a, uh, screenwriter in, in, uh, you know, the Hollywood area. Um, uh, and, uh, he's, uh, he's very creative. Uh, he has, uh, he has two daughters, um, that are, that are also spectacular. Uh, um, we were very different from each other. My, um,[00:28:00] 

[00:28:02] **DAVE ABRAHAMS:** you know, I, my brother might disagree about this or, or not, but I would say in some ways that my brother, uh, was, was trying hard not to be like the rest of the family. And an example of that is, uh, he's, uh, he's an incredible golfer. In fact, uh, he developed an interest in golf and that was just so far outside the orbit of things that any, that my [00:28:30] family would do or be, be interested in.

[00:28:33] **DAVE ABRAHAMS:** Um, uh, so that, that's, that's one example. Um, he was, he was always, you know, he's a younger brother. He was always better at sports than me. I, I felt that he was more, uh, uh, he was, he was definitely more socially adept.

[00:28:52] **RAY NOWOSIELSKI:** In your brother's language, we might call it the "meet cute." I still haven't heard the "meet cute" about How you met [00:29:00] C++.

[00:29:01] **DAVE ABRAHAMS:** Meet cute. Ah, yes. How did I meet C++? I'll give you a little bit more after, uh uh, after. College, I didn't really know what to do with myself. Um, in fact, I was a little panicky about what, what the future might be.

[00:29:18] **DAVE ABRAHAMS:** But I, I got into the PhD program at Carnegie Mellon University. And, um, and so I went there and, and [00:29:30] among other things, I started studying, uh, studying electronic music. Um, and, um, uh, but I was also, I was also, you know, reaching out to people to find people to play with. And, and, you know, there was a, there was a annual sort of annually formed band called Boic, which, uh, is [00:30:00] a whole story unto itself.

[00:30:02] **DAVE ABRAHAMS:** Um, well, BOIC was a, was a fictional CMU student who, who supposedly founded this band. And every year the, the Boic would play at this, these picnics. And, and so I was involved in that and I, uh, you know, I was involved in, in jazz, I met a saxophonist who, who I, uh, who, you know, we liked playing together and we performed there.

[00:30:29] **DAVE ABRAHAMS:** And, [00:30:30] um, yeah. So I was always really trying to pursue this music. And I, and you know, after about a year at CMU, I realized I was, you know, more passionate about the music than I was about the, the computing thing. And so I thought, okay, you know, I should really get an education. I'll enroll at Berkeley College of Music in, in Boston.

[00:30:58] **DAVE ABRAHAMS:** And I did that, [00:31:00] and I spent about a semester there. Um, I think I was done with school at that point. Um. Okay. My attention was also stretched with other, other things I was involved with. In any case, uh, after a semester, I realized I needed to get a job. And so I found a job with, uh, mark of the Unicorn, which is a very strangely named company.

[00:31:25] **DAVE ABRAHAMS:** Um, but, uh, they had just a [00:31:30] few years earlier transitioned from, from their main product being a word processor to being a company that made music software. And, and, uh, so my job at Market, the Unicorn became to develop this, uh, a new version of the notation software that they, that they sold, which was called Composer.

[00:31:53] **DAVE ABRAHAMS:** And, you know, when they hired me, they asked me what I thought of Composer. And I, and I had [00:32:00] looked at it and I said, I thought it was kind of clunky. And they were like, okay, make something better. And, um, you know, I was, I don't, I don't know what it's like in college these days, what, what people learn. I'm gonna find out.

[00:32:19] **DAVE ABRAHAMS:** 'cause my son just started as a computer science major. But, um, but when I got out of college, I didn't know anything about being a [00:32:30] professional programmer. I didn't know software practices. I did not know, uh, like I, I, I'm not even sure version control was a thing at that point, but, um, but you know, I, I didn't know what made good code, um, anything.

[00:32:50] **DAVE ABRAHAMS:** And the person, there was actually a person who had been very successful at Mark of the unicorn who was supposed to mentor me in this project. Um, [00:33:00] and he, he left, uh. A few months after I started. And so I was on my own for, you know, trying to build this, this piece of software. I was super excited about it, but, uh, and I didn't, I didn't know what I didn't know.

[00:33:20] **DAVE ABRAHAMS:** I didn't know I needed to know more things and, and that there was, that there were things that experience would've taught me [00:33:30] that would've made my work better. Um, onus was on me to complete this, this piece of software. You know, I collected a salary and it took, it took three years, I think before, before it could get released.

[00:33:46] **DAVE ABRAHAMS:** And in the meantime, uh, competing companies, notation software came out, which eventually, you know, it was, it was a monster and it was massively complex and not [00:34:00] necessarily well designed, but it could do, uh, almost anything. And, uh, and it, it ate up the market while I was working on this. And so, so the, there was a lot of pressure for me from the management to, to get this thing done and get it out there.

[00:34:19] **DAVE ABRAHAMS:** I, I felt like I was under the gun and, and I didn't have, you know, I could have used, uh, an ally and somebody, somebody to guide me [00:34:30] through this process. Um, uh, and I knew that. But, um, yeah, so that, you know, I ended up sort of combining my, my interests in, uh, in this job, or at least that's the way I viewed it.

[00:34:50] **DAVE ABRAHAMS:** Turns out, you know, making music software is a lot more about software than about music. Um, uh, but, [00:35:00] um. But yeah, so, and, and this, this really Connects, connects to Boost the Way programming was at that time. You almost, well, so notation software is complicated. Um, uh, there's graphics, there's printing, which is a whole separate thing.

[00:35:25] **DAVE ABRAHAMS:** Um, uh, there's transcription, you [00:35:30] know, you want to be able to write out what people play into the software. Um, uh, uh, there's a user interface. Many, many aspects, right? And so there was a lot to learn. I found it really, really engaging to do all this stuff. But you had to build all of these parts yourself.

[00:35:52] **DAVE ABRAHAMS:** There weren't libraries, basically. There were very few libraries available to, to take care of, [00:36:00] uh, you know, specific problem domains. And, and, uh, so,

[00:36:12] **DAVE ABRAHAMS:** okay, so the, so the user interface was the first wa was the sort of first problem that I started to tackle that would often be done by a library. And all, all I had to work with was see at that point. And, um, [00:36:30] and at some point I discovered, uh, you know, the way you learn things in those days is you would get Bite Magazine and, and you would read the article, right?

[00:36:44] **DAVE ABRAHAMS:** Um, and there was an article about an object oriented programming system. And you could somehow, somehow get this using your, your modem over the, over the. [00:37:00] Whatever was beginning to be the internet at that time. And, uh, and I got the source code and I played around with it and I thought, oh, this is really cool.

[00:37:10] **DAVE ABRAHAMS:** This would be really useful for the user, user interface in my program, but I can't program in this other, this other language I have to program and see. So how do I do that? Well, I, I built a, uh, system of macros [00:37:30] that would let me do something like what C++ programmers call classes with virtual functions.

[00:37:37] **DAVE ABRAHAMS:** Um, some kind of, some kind of, uh, simulation of object oriented programming. And I used that to build the interface. And then eventually we got, uh, the, uh, company that made the C compiler came out with something called Think C, which had had classes built into it. [00:38:00] And I switched to using that, and that was all an approximation to C++, which was, uh, which we still couldn't get our hands on for a Macintosh.

[00:38:11] **DAVE ABRAHAMS:** Um, uh, but yeah, I, I eventually got that and we, we ended up switching to using C++. Um, but all, all of the, the, there still were not many useful libraries. There were [00:38:30] big monolithic libraries called application frameworks that were, that were based on this object-oriented paradigm and turned out to not be all that great for code reuse.

[00:38:44] **DAVE ABRAHAMS:** Um, why not? Uh, mostly because of the object-oriented paradigm, which is something you might, you might learn more about from, from Alex. Um. Uh, I can say that it, [00:39:00] it, it's, it's intrusive. It's, it doesn't let you, uh, freely combine parts very well. Um, it all, it has other weaknesses too, uh, which, you know, I, I hope we'll get to talk about at, at some point.

[00:39:24] **DAVE ABRAHAMS:** But, um, but, you know, a lot of people use these [00:39:30] application frameworks, but they were, but they were still very limited in terms of, of domains that they would cover. Like, like, um, you know, you wanted a binary search algorithm, might not be in your application framework. Um, uh, uh, you know, you wanted a beat tree data structure, um, probably won't be in your application framework.

[00:39:57] **DAVE ABRAHAMS:** Where do you get these things? These are, these are [00:40:00] standard known ideas in programming. Well, nobody's giving them away. And, and nobody in, in my domain was selling, uh, know a library that I could use. Um, 

[00:40:15] **RAY NOWOSIELSKI:** what, around what year was this that you're having this realization? 

[00:40:18] **DAVE ABRAHAMS:** 87, 88. There was an issue with libraries, but I didn't know it because the libraries weren't out there.

[00:40:27] **DAVE ABRAHAMS:** So this is the way it was. [00:40:30] And, and I'll tell you when things, when things changed was in, in 97 or 98, probably 97, my colleague Mark Waxler came into my office and showed me this, this magazine. Uh, uh, he showed me the magazine that had an interview with Alex Stoff [00:41:00] about his library, the STL. So I have to say by that time, I had learned a lot of hard lessons about programming.

[00:41:09] **DAVE ABRAHAMS:** Not enough, but, but a lot of them, and about, uh, about, uh, you know, how to do things right? I got a whole, I, I read this article and this thing seemed, seemed, actually, actually, it was fascinating, fascinatingly [00:41:30] different from anything I had used. And, uh, and I started to learn about it a bit more. Like this whole idea of, of iterators and separating them from algorithms was, was really interesting.

[00:41:45] **DAVE ABRAHAMS:** I didn't know what that meant. Um, uh, so, you know, I got my hands on it and started to, started to work with it. And the thing about this was, it was, it was this whole [00:42:00] family of really well designed components written by somebody who's an expert in those domains. And, and probably most important, each one was rigorously documented.

[00:42:18] **DAVE ABRAHAMS:** So you could, you could actually tell what the correct ways to use it were, what the incorrect ways and, and precisely what the, the results should be, really [00:42:30] shifted. My programming experience. It didn't cover a lot of the domains that I needed, but, but, uh, it covered algorithms and containers and, um, not completely had really very good coverage of algorithms.

[00:42:46] **DAVE ABRAHAMS:** But, uh. But it was enough to make a huge difference in my programs. And let me throw out a lot of code that, that I had been using. And I'll tell you, I cannot [00:43:00] tell you how many times I wrote binary search incorrectly before. It's a very simple algorithm, maybe 10 lines, um, that, that, uh, you know, when I got the one that was in, in the STL, like that whole problem was over, right?

[00:43:20] **DAVE ABRAHAMS:** I could throw out my own reliable code and throw out the test for my unreliable code and just use the [00:43:30] component that worked. And, you know, I, I don't know when, when I finally realized this, but, but at that point, I had become a world class expert in one thing in music notation software, right? This, it's this crazy little niche where there's, there's no money to be made.

[00:43:50] **DAVE ABRAHAMS:** Um, uh, but, and so, so it's not hard to become a world class expert because there's only, you know, a [00:44:00] few other people that do this. But, but I had really developed a lot of expertise in that area. And, and at some point I realized, you know, that's what, you know, pro programmers that build products are paid to develop the expertise in, in their product domain in, and, and every, every time they have to go on an excursion to build a, [00:44:30] an algorithm that is standard or a data structure or some other component that is outside their domain of expertise.

[00:44:41] **DAVE ABRAHAMS:** They're, they're doing something, they're doing something that there's economic pressure on them not to be, not to give it the attention it deserves. And, and for which they, they don't have the, they don't have the same [00:45:00] chops. Somebody else should be doing that. Right? And so this is where I, where I discovered what the power, the importance of libraries was.

[00:45:10] **DAVE ABRAHAMS:** It was, it was the ability to get the, the people who were really best at a thing working on, on that thing and focused on it. I, I had certainly read Brianna's books. Um, uh, the design and evolution of C++ was a huge, uh, uh, a huge eyeopener [00:45:30] for me. The, there was, there was something called the annotated Reference Manual, um, which, which I still, I still think, um, stands as a really interesting example of something that was trying to be, uh, formal documentation, but also gives you the expository stuff that you need to sort of appreciate why the things are the way they are and, and, [00:46:00] uh, understand like how things are intended to be used.

[00:46:03] **DAVE ABRAHAMS:** So like a formal reference manual like tends to, tends to just, it's just the facts man, basically. And um, so, uh, so it would be cool to see more documentation in the style of the annotated reference manual or the arm is what people called it. Um, so there was that. And I believe also his book, the C++ [00:46:30] Programming language, I think also existed then.

[00:46:32] **DAVE ABRAHAMS:** And I'm pretty sure I had read that. And um, so, you know, I can. I can say more now about what that material should tell you about BNA than, than I can definitely vouch for it having revealed to me at the time. Um, uh, can try and speak to that. The, the, I think [00:47:00] the, the sort of killer feature of C++ is that it was an extension of C and, and the idea that that all of your C code could run as it was, and that, and because c was a, a dominant language at that time, um, it's, it's an immediate, you know, it's an immediate available user base for [00:47:30] you.

[00:47:30] **DAVE ABRAHAMS:** And you know, it's a language that becomes approachable, um, uh, immediately for a large community, which is sort of the same theory behind, uh, languages like Mojo, uh, which Chris Latner, uh, and company, uh, are developing, which is like, uh, you know, an extension of Python. You can look at it as, um, um, so, [00:48:00] so above all, I would say it was, that was an incredibly practical thing to do and I think, I think practicality is a lot of what, uh, you know, drove Bjarne's design decisions in C++.

[00:48:16] **DAVE ABRAHAMS:** Yes. Uh, so Luanne, um, uh, so I met Luanne through some personal growth seminars we were both doing, and um, [00:48:30] and uh, there she is. Uh oh, okay. So. Um, I ended up inviting her to a party that, that was happening at my, at the house I was living in, thrown by these, these two other guys that, that lived there, um, who I was not particularly close with.

[00:48:56] **DAVE ABRAHAMS:** It wasn't their particular kind of story, [00:49:00] uh, sorry, it wasn't my particular kind of party. Um, so it was nice to have somebody there and we, you know, just ended up talking and talking and discovered we had a lot in common. Um, you know, I had an Ella Fitzgerald album, which, which just, you know, uh, made it for her.

[00:49:21] **DAVE ABRAHAMS:** She was, she's, uh, so Luann, uh, really, really interesting [00:49:30] person. She, she was born and grew up in Alaska, um, in Anchorage and was in some ways, I say born 40 years too late because of the, the popular culture that she's really interested in is, is like the thirties and forties. Uh, and, uh, and, uh, you know, super smart.

[00:49:57] **DAVE ABRAHAMS:** Uh, she went to, to [00:50:00] Bryn Maw r College, which, um, you know, in the same neighborhood as Penn where I went. Uh, but I, but, uh, we never met, although, although we knew people in common. Um, uh, uh, and, uh, Bryn Mawr is, uh, really, I didn't actually learn this until I, until I met her, but Bryn Mawr is a super rigorous school that demands a lot in [00:50:30] intellectually from people and, and her.

[00:50:33] **DAVE ABRAHAMS:** Her strengths as a human are, are very different from mine. And so we compliment each other. Well, I think, um, 

[00:50:42] **RAY NOWOSIELSKI:** um, how do you think your boost itself actually, but also, you know, maybe your life and career would be different without that partnership with Luanne? 

[00:50:51] **DAVE ABRAHAMS:** Oh yeah. I mean, for sure there were, I went through many difficult [00:51:00] crucibles, um, with my work that, that, um, you know, Luanne was essential in helping me through.

[00:51:09] **DAVE ABRAHAMS:** And, um, and, uh, you know, she's, she's somebody whose take I always value and, and, uh, and actually, you know, by the time we were doing Boost Con, uh, well, I guess I [00:51:30] should, I should say at some point I started my own consulting company called, uh, boost Consulting, and we eventually changed it to Boost Pro. But, um, but, uh, she, so she, her, her family, uh, her family business when she was growing up was Alaska Bering Corp.

[00:51:57] **DAVE ABRAHAMS:** And they sold sold machine, [00:52:00] machine transmission parts. And, and you know, if you think about the oil pipelines up there, um, there was, there was a lot of need for that kind of mechanical stuff. So that was, that was part of her background. But she, um, she had to learn how to do accounting there. And, um, and then, you know, on her way to, to working as the, [00:52:30] uh, as an assistant director at the Harvard Art Museums.

[00:52:33] **DAVE ABRAHAMS:** Uh, she had to take a lot of other jobs and accounting was a big part of that. And by the time we started Boost Consulting, in addition to her job at Harvard, she took on all of the financial, uh, uh, aspects of, of running a business for, for my company. And, um, and that was absolutely essential. And [00:53:00] then, you know, when it comes to planning, you know, we always joke, oh, there you go again.

[00:53:05] **DAVE ABRAHAMS:** Luanne planning, you know, because I'm like the, the Wing it spontaneous guy more or less. And, and she's, you know, amazing at planning. And so for planning things like, like Boost Con and how it's gonna work, and the first one, um, you know, she was always, she was always right there and, and Boost Con was a [00:53:30] Boost Pro production for, for quite a few years.

[00:53:34] **DAVE ABRAHAMS:** So, so, um, you know, she was a big part of that. What do you think she saw in you? What was she looking for that you took? You know, uh, physically I was her type. Um, but, but like I said, you know, the Ella album, the fact that I was into jazz, um, uh, I think that, I think that was, I think that was a big deal. But, you know, you could probably [00:54:00] get a, you could probably get a few minutes of Luann on camera if you want to find out, uh, if you want to find out more for sure.

[00:54:08] **DAVE ABRAHAMS:** So the STL was amazing and it was, it was solving lots of problems for me. And, and, uh, you know, I incorporated it, incorporated it into my application right away. And, and it really, it changed a lot. Um, there was still plenty of domains that it didn't cover, but, [00:54:30] but that was like. Algorithms and data structures.

[00:54:34] **DAVE ABRAHAMS:** There's, yeah. You know, Alex sort of started at the bottom at the, the core key concepts of programming. And so that really supports everything else. Um, oh, another thing I didn't say about it, aside from the documentation is that it had, it, it gave you a paradigm for, for doing things like, like if you wanted [00:55:00] to, if you had your own algorithm that you had to write, uh, how were you going to accept the elements to work on?

[00:55:08] **DAVE ABRAHAMS:** Well, once we had the SDL as an example, we were, of course, we were gonna accept iterators as the parameters to this algorithm. And, and this another property of libraries that I learned to appreciate from that is that it takes an [00:55:30] element of decision making away from a programmer. That which, which is not trying to figure out how to, you know, how to communicate with an algorithm is not, again, another piece of, of, you know, uh, knowledge that, that somebody who's a music notation software expert is [00:56:00] gonna know, is gonna, and needs, needs to spend time on in order to, to, um, in order to make their product.

[00:56:11] **DAVE ABRAHAMS:** You know, they, they do, they, they inadvertently end up spending time on that. And, and you know, what I found was, was my project was, was a huge. Huge intellectual undertaking, and there were so many things to consider. And [00:56:30] the, the benefit of having had the STL take away things I had to consider from me, um, just even, even what kind of design decisions I was gonna make in my own code, if I had an example that completely changed the, the productivity landscape for me.

[00:56:49] **DAVE ABRAHAMS:** So, so at the time I, I discovered the STL it was, it was just being incorporated into the C++ standard and, um, [00:57:00] right. So, you know, you said there was rock and roll before Elvis, there were collections, there were container libraries and, and a few algorithm li a few algorithms out there. First of all, that like, the foundational thing Alex is always gonna come back to is, is it's about the algorithms.

[00:57:23] **DAVE ABRAHAMS:** And, and, uh, nobody had ever [00:57:30] focused on the algorithms as, as the core, the core feature. So if you think about, and I, I've said this in, in talks that I give, is how I, how I talk about appreciating what an algorithm is. Algorithm is a big, fancy word, but all it means is program, right? I mean, an algorithm is a method for accomplishing something.

[00:57:55] **DAVE ABRAHAMS:** And, and, uh, [00:58:00] during, for, for 30 years during the object oriented programming revolution,

[00:58:10] **DAVE ABRAHAMS:** people did not focus on algorithms. They, they thought of programming as wiring together, loosely coupled components that would send each other messages. And somehow out of this big web of connected components, you would get something [00:58:30] that functions right. So, and uh, I'm, you know, I'm glad you're talking to Sean.

[00:58:38] **DAVE ABRAHAMS:** Uh, what Sean will say about that, about that web is there's what he calls an incidental algorithm in, in that giant web. In other words, every time you do something in this program, this web of things sends messages back and forth and, and you [00:59:00] get some result, right? But you can't, you can't understand that that process, because it's all encoded in the connections between things and the, the code for, for this thing, sending a message over here is spread out from the response to that message that that happens over here.

[00:59:22] **DAVE ABRAHAMS:** Right? So, so there, it had become [00:59:30] the, the fashion that this was the way to get things done. Of course, it ends up being incredibly in inefficient and also hard to reason about. It's very hard to understand what a system like that does, right? Because, because there's some code over here sends a message over here, and there's code over here that's like responding to different messages in different ways, talks to, okay, it's, uh, it [01:00:00] isn't, uh, conducive to local reasoning.

[01:00:03] **DAVE ABRAHAMS:** Um, and if you think about, coming back to my definition of algorithm, if you think about what computers do, they compute, right? That's, it's in the name, right? The computation of this giant webs is hidden. It's obscured, and it's encumbered by the, by the cost of sending [01:00:30] messages back and forth and allocating the separate objects in the web and all of that.

[01:00:36] **DAVE ABRAHAMS:** And, and Alex, you know, said, you know, the, the keys to computing the core stuff is all there in the work of Donald Knuth, more or less that, and, and the, uh, algebraic structures, uh, of mathematics. So Alex can tell [01:01:00] you himself, the, the story of, of where he had the insight about, about programs and in a, in a fevered, in a fevered state, in a hospital, I think is where it happened.

[01:01:18] **DAVE ABRAHAMS:** Um, where he, he understood the, the connection between algebraic structures in math and programming. So this is the first thing, Alex, [01:01:30] Alex focuses on the algorithms. It's to bring, bring the code to together in one place. Understand, understand what it means, and make it efficient. So that's step one. Uh, step two, um, you have two kinds of computer languages.

[01:01:51] **DAVE ABRAHAMS:** Uh, there are lots of kinds, but, but one of the major divisions is [01:02:00] static typing versus dynamic typing. Uh, Python, uh, is essentially, uh, a, uh, dynamically typed language, which means that when you create a component, so you might have a piece of text. There's a type that the traditional name for a piece of text, text is, is data is a string.

[01:02:27] **DAVE ABRAHAMS:** You might have a number. There are [01:02:30] various number representations, there's integer numbers and floating point numbers. And, and most computers there are different sizes of, of integer numbers. So integers are, are, you know, whole numbers and they're negatives. So 0 1, 2 minus one, minus three, things like that.

[01:02:52] **DAVE ABRAHAMS:** And one of the ways we, we both make programs efficient and [01:03:00] help ensure that they're, that they're correct and, and meaningful is to label in our programs what types certain things need to be. So the primary way we expressed a computation or an algorithm is with something called a function. A function takes arguments, that's data coming into the function and returns the result.

[01:03:27] **DAVE ABRAHAMS:** And, and [01:03:30] in a statically typed language, you say, you say, uh, what the type of each argument to the function has to be and what type of result you get out. And so as you build up the program by connecting the different parts, the, there's a compiler that whose part of whose job it is is to make sure that, you know, strings are only flowing into places that accept strings, for [01:04:00] example.

[01:04:00] **DAVE ABRAHAMS:** That helps us get programs right. It's hugely, hugely beneficial to programming. Um, so CC++ are, are statically type languages and in statically type languages. Um, if you want to do an algorithm. There are, there are lots of algorithms that make sense over many different data types, almost all of them.

[01:04:24] **DAVE ABRAHAMS:** So like sorting, for example, is a simple classic algorithm. You've got a list of things, [01:04:30] um, you might wanna sort them alphabetically, but those things might also be also be integers. So those, you wanna sort numerically, let's say an extent, uh, uh, ascending order. Okay? So you want to write this algorithm once.

[01:04:47] **DAVE ABRAHAMS:** And so code duplication is a big problem in programming. It makes more code. There's more to maintain. Nobody wants to do it. A big [01:05:00] principle in programming is don't repeat yourself. So we try to factor common parts out, lift them out of, of repeated code. You wanna write one sort algorithm, and, but how do you write one sort algorithm that works on both integers and strengths?

[01:05:20] **DAVE ABRAHAMS:** Well, the object oriented answer to this is what you do instead is you, you have a, a special type called object [01:05:30] and you say integers are also objects. Strings are also objects. And I'm gonna write one sort algorithm that operates on objects. So this has all kinds of inefficiencies associated with it, but more importantly, it, it makes parts harder to put together.

[01:05:55] **DAVE ABRAHAMS:** Um, I don't, I don't think I could, [01:06:00] could explain that without, you know, going to a whiteboard and drawing pictures and whatnot. But, but this is part of the problem with those classical object oriented frameworks is that they didn't deliver. So object orientation. One of the main promises was, was you'd get better code reuse, but object oriented programming didn't really deliver on its promises of code reuse [01:06:30] partly because of this problem.

[01:06:32] **DAVE ABRAHAMS:** So that, that saying that a string is an object and an integer an object was a, was an object oriented programming idea. And, uh, so Alex, the, the other thing that Alex brought was this idea of generic programming, which uses, uh, in practice we use different programming, uh, different language mechanisms than object oriented programming.[01:07:00] 

[01:07:00] **DAVE ABRAHAMS:** And C++ was, was the first language Alex found that had the mechanisms that really allowed him to express his ideas of generic programming, um, which he had been working on for years in languages such as Lisp and ada. Um, and in fact, in fact, C++ didn't have all of the things that, that he felt he [01:07:30] needed.

[01:07:30] **DAVE ABRAHAMS:** And so, as the STL was being standardized, basically the, the C++ committee, uh, uh, did something very unusual and, and essentially invented these features for, for making the STL work and put them in the standard before any compiler actually had implemented them. Well, okay, so, so on the way is how I got [01:08:00] connected with WG 21.

[01:08:02] **DAVE ABRAHAMS:** So, STL was amazing, as I was saying, making a big difference for my application. But there was one key problem. Which was that I used in my application this feature C++ feature called exceptions. Um, and, uh, the STL basically didn't, didn't support exception handling. What it it said [01:08:30] is, if you, if you essentially, if you try to use an exception in when you're working with the STL, all bets are off.

[01:08:39] **DAVE ABRAHAMS:** The program is allowed to do arbitrary things. This is one of the, one of the things about C and, and also C++ is it has this notion of undefined behavior, which is essentially, um, when you use the language incorrectly, [01:09:00] your program, the compiler can turn your program into anything. It's allowed to shave the family dog, launch the rockets, whatever.

[01:09:08] **DAVE ABRAHAMS:** Now usually the results aren't that bad, but this is fundamentally the, um, the reason for, for, so that there's so much interest in, in what are called safe languages now, is that, is that safe languages don't have this idea of [01:09:30] undefined behavior where it can program can go off the rails and, you know, undefined behavior is the source of security vulnerabilities.

[01:09:40] **DAVE ABRAHAMS:** How, how hackers get into systems, um, you know, could result in, like, if you think about it could result in your, your power plant shutting down, losing power to a hospital, you know, the kind, the consequences can be really terrible, um, crashing an airplane. Okay? So if you [01:10:00] try to use exceptions with the STL, the, the status quo is undefined behavior.

[01:10:05] **DAVE ABRAHAMS:** And my program used exceptions. So what was I gonna do? Well, it was. Of the time, you know, Alex's email address was published in the article, and so I wrote him a letter because I, I, you know, was handling exceptions in my own code. And I thought, I think I understand how I could make this, the [01:10:30] SDL also do it, um, do the same, you know, by the same principles.

[01:10:35] **DAVE ABRAHAMS:** And he was very nice. He wrote back to me, uh, he said, I, I, I think he said, um, I'm really glad you're, you're interested in addressing this. I, I have to warn you though, um, the chance of getting it into the C++ standard, uh, is probably very low now because, because they're already late in [01:11:00] delivering the, the final standard, and they're, they're very reluctant to accept, uh, uh, changes and, and especially changes of a large scope.

[01:11:13] **DAVE ABRAHAMS:** So, but he said, I, I suggest you get in touch with, with somebody. I don't know. He might've, I don't, he might've put me in touch with Greg Colvin as the first person, although, although I, I'm not sure that they, they knew each other. [01:11:30] Um, uh, but he, and it, it was more likely an Andrew Koenig, um, Andy Koenig, uh, uh, and Andy somehow got me on what C+ post calls there reflector, which is essentially big mailing list.

[01:11:49] **DAVE ABRAHAMS:** And, um, and I started having conversations with people about, about, [01:12:00] uh, making this change to the standard. I also, as, as part of this, you know, went and took an, got an implementation of the STL. Um, uh, I think I, I used STL port, which, which was essentially the S-G-I-S-T-L, which had, which was an evolution of the H HP STL, which is what Alex had originally written.

[01:12:28] **DAVE ABRAHAMS:** I believe Alex was [01:12:30] at SGI for a time. So they put out an STL, but, and then STL port was, was an effort to make all of that code work on lots of different platforms and compilers, um, by Boris fev, uh, FACHE. And, um, I, uh, so, so that was, that was publicly available code. And I modified that code, um, because that was the code I believe [01:13:00] I was using in my application.

[01:13:01] **DAVE ABRAHAMS:** 'cause I had to run on a Mac and SGI made their own machines. So anyway, so, um, so I modified that code to support exceptions and I started talking to people on the reflector about, about exception handling. And, uh, one of the first things that people said is, this is well known to be an impossible problem, as I remember it.

[01:13:29] **DAVE ABRAHAMS:** Um, [01:13:30] and, uh, that's partly because, uh, I think that was partly due to a misreading of a very influential article by Tom Cargill, um, uh, which basically explored using exception handling with a particular, uh, component and laid out all of the problems that he saw. And, [01:14:00] um, and I was like, well, no, I've got a, got a solution.

[01:14:04] **DAVE ABRAHAMS:** And there became, and at some point Andy said to me, uh. This is all very well and good to have these discussions, but if you want to have any influence on the standard, you have to come to a meeting. And I was living in Massachusetts at that time. It so happened that the, the next meeting was in Nashua, in New Hampshire, and I got my boss to [01:14:30] let me go up to the, to the meeting.

[01:14:33] **DAVE ABRAHAMS:** And um, and this is where I met Beman. It was entirely in, uh, one, I believe it was entirely in one big conference room in a, in a hotel. Um, the, there were tables set up in a horseshoe around the, roughly around the edge of the room. Um, and, and the committee members [01:15:00] were all seated at the table and they all, uh, they all had in front front of them a, you know, hefty binder full of, uh, full of a document that turned out to be the working draft of the C++ standard.

[01:15:19] **DAVE ABRAHAMS:** Um, and, um, and there were chairs also around the edge of the room, uh, which I guess were [01:15:30] just not being in use. And so I, I went and I sat in one of those chairs not being a committee member. And, um, they started, you know, they were doing some business that I didn't understand. And, uh, at some point they, uh, work shifted to issue processing.

[01:15:50] **DAVE ABRAHAMS:** So issue processing is, uh, you know, somebody discovers something wrong or inconsistent in the document and [01:16:00] excuse me, the committee thinks about how to resolve the problem, right. And come, comes up with new wording for the document, uh, and. You know, and there would be some, some informal vote I think that they used to, to decide, uh, questions when there was a disagreement.

[01:16:21] **DAVE ABRAHAMS:** And, um, and it may be, it may be that we broke [01:16:30] into two rooms at the, for issue processing. I think that's what it was. 'cause there were sort of two main components to the, to the standard. One was the core language and the other one was the library and Beman's responsibility. He was the library working group chair.

[01:16:48] **DAVE ABRAHAMS:** And so, so the exception safety of the STL being a library problem, uh, I, I stayed with the library group for, for [01:17:00] their issue processing and, um, you know, Beman, uh, even though I wasn't a committee member and he didn't know me, he, you know, asked me to come up and sit with everybody else. And, um, and, you know, help me sort of, uh, people were, were generous with helping me sort of get up to speed on what they were doing and how it was done.

[01:17:26] **DAVE ABRAHAMS:** And I was actually, I, I think able to [01:17:30] make a few contributions that were, that were valuable, like give some insights that help people resolve certain problems. So that was, that was really cool. But what, what really super impressed me was this kind of ecumenical way that Beman ran the meeting where, where everybody's input was valued.

[01:17:55] **DAVE ABRAHAMS:** He was, he was patient and, [01:18:00] um, non-partisan and, and to, to solutions. He, and, and the, the meeting itself. Like the process that they had was, was extremely consensus based. I eventually learned the, like even getting the standard to be, to be accepted was a consensus operation in, in that, in that you [01:18:30] really didn't want any national body voting.

[01:18:33] **DAVE ABRAHAMS:** No. You, the, the committee's charter was to really, uh, was to really bend over backwards to make sure that all of the stakeholders were, were, uh, satisfied. Um, and, and overall this, so this super impressed me and also the, the respect that I saw in the [01:19:00] room among the committee members and, and, uh, I, I would eventually, I think, come to learn that this was the, in large part generated by the environment that Beman supplied this respect was something I, it was a level that I did not experience in my regular job.

[01:19:20] **DAVE ABRAHAMS:** And, and it made me aware that something, something else was possible in, in [01:19:30] working with colleagues in the way, the way we could be together. And I, I think I, you know, that, that also made me appreciate what my dad did eventually. Um, didn't even remind you at all of your father or, you know, I wouldn't have said it is an interesting point.

[01:19:51] **DAVE ABRAHAMS:** He, you know, I think they definitely have, have [01:20:00] had things in common, uh, uh. You know, I, I think this, I think this way of being with the people that they were working with was very, was very similar. Um, it's, yeah, I hadn't thought of that before. Um, I think the first interaction was Beman inviting me to come to the table and I, I said, you know, uh, you know, I'm, [01:20:30] I'm not a member.

[01:20:31] **DAVE ABRAHAMS:** And he said, it doesn't matter. I think something like that, um, just be, so I never actually asked Beman what his age was. Um, uh, I, if I had to guess now, let's see. I would say, I would say early fifties maybe. Uh, I don't know what I, uh, and I [01:21:00] pretty sure he was still living in Virginia then. I don't think that he, during the time I knew him, he lived anywhere but Virginia and then eventually Florida.

[01:21:09] **DAVE ABRAHAMS:** Um, uh, he, as far as I remember, his, his job was, was making, making some kind of mapping related software. Like, uh, [01:21:30] yeah, something that, that had to do with representing maps in computers. You know, it was long before MapQuest and Google Maps and all of that. I think it's worth, uh, telling because I, I think this is also important.

[01:21:45] **DAVE ABRAHAMS:** Um, uh, so, so the process of, of getting exceptions accepted into the standard, [01:22:00] um.

[01:22:04] **DAVE ABRAHAMS:** It happened on, it happened on two fronts. Uh, one was inside the committee and the other one was in the community because the, you know, there was cross bodied influence. And one of the challenges in the community was to, was to help people understand that it wasn't mysterious. That, [01:22:30] that it was possible.

[01:22:31] **DAVE ABRAHAMS:** So I, I basically, I developed a, you know, it's not, not complicated theory of exception handling that was based on, on principles of, uh, that originated with Tony Whore and were eventually, like, I learned about them through the idea of the ideas of Bertrand Meyer, uh, called programming by contract. Okay. So [01:23:00] programming by contract, basically.

[01:23:02] **DAVE ABRAHAMS:** It, it's part of what I, what I saw in the STL that I loved was, was the contracts for components were well specified. That's what I mentioned before. It's like, what are you allowed to do? What can you expect? You know, what are you allowed to give this function? What can you expect in return? Right? And using that basic logical framework I came up with, with a theory of [01:23:30] exception safety.

[01:23:31] **DAVE ABRAHAMS:** And so I had to, and, you know, popularizing that on Usenet was, was one fork of it. And the other fork was, was in the committee trying to create the, a consensus around these ideas. And, and, uh, you know, this became, this was a, ended up being a really valuable skill, really important [01:24:00] skill in my career that, that I.

[01:24:03] **DAVE ABRAHAMS:** Learned how to work with people to shape, to shape their understanding of a problem. And, and you know, what I saw was people become gaining power over their problems Ha by having this understanding. And so that, you know, eventually would become my, my professional mission would be to [01:24:30] empower other programmers.

[01:24:31] **DAVE ABRAHAMS:** And, and I see boost as a big part of that, uh, li like what I said about libraries, right? That's libraries give you the power to focus on your domain of expertise, for example, among, among other things. Okay. So, um, so instrumental in the getting things standardized, like you want to, you want to know, uh, [01:25:00] this is an important part of how Greg Colvin fits in this story.

[01:25:05] **DAVE ABRAHAMS:** Greg became my ally on the, on the committee reflectors. And, and like I said before, one of the big, uh, concerns that the committee had about accepting changes for exception safety is how many actual words would need to change in the standard. Because like, [01:25:30] you know, you had these working groups that did issue processing so that there was a large web of connected things in the, in the standard that all were mutually consistent.

[01:25:41] **DAVE ABRAHAMS:** And you want to not break any of that consistency by making changes. And if you make large scale changes, evaluating what they've done to the standard is hard. It's just like doing a large scale code review. That's why we, when we change code, we like [01:26:00] to. Make small incremental steps. Um, uh, and so Greg was instrumental in working with me to help me find a way to, to make the wording changes as small as possible.

[01:26:16] **DAVE ABRAHAMS:** And, and that really helped. Um, being able to, to negotiate with all those people without flipping a table was an important [01:26:30] skill I was working on there. Um, uh, but, uh, but yeah, that 95, that was before my time. Um, 

[01:26:38] **RAY NOWOSIELSKI:** I mean, did you learn anything about bureaucracy or human nature and, and trying to, did you find yourself, um, attuned to navigating it or did you find it to be a thing that was a little foreign to you?

[01:26:50] **DAVE ABRAHAMS:** Well, it was, it was foreign and new, but I, you know, I actually, I actually appreciated it. I think, [01:27:00] I think what the committee demonstrated for me at that time was, was contrary to what a lot of people say about design by committee and, and, you know, thinking of it as a bureaucracy is that you can actually accomplish great things by consensus.

[01:27:21] **DAVE ABRAHAMS:** And, um, and un unfortunately, uh, at that time though, some of the, [01:27:30] the representatives for the US National Body were, were extremely conservative. And although they, they liked my work, they, they were gonna vote no because it was too late a change. And, um, and what ended up. Ultimately happening was that two other national bodies essentially said, we're voting no unless you put this in.

[01:27:59] **DAVE ABRAHAMS:** And, [01:28:00] um, and yeah, this, this no vote I was talking about would be, would've been a vote inside of the, i I forget the organizational structure. There's a, there's a US body that, that does voting and then takes the results of that to the, to the big, uh, vote. And, and so the, these national bodies were, were at the top level.

[01:28:26] **DAVE ABRAHAMS:** So that was, uh, England and Germany both, both said, unless you get [01:28:30] exception safety in the standard, we're, we're not accepting it. And, um, and that was sort of the, the end of the story. Um, that's how it happened. Uh, it was a huge accomplishment for me. Um, I was, uh, I, I was psyched. Um, and I was still, you know, I was still not an official committee member and, and you know, I didn't have a vote officially [01:29:00] in anything.

[01:29:01] **DAVE ABRAHAMS:** And so that was another, another piece of evidence that you really can get great things done by consensus. Right? Just by, just by working with people to help them understand and, and talking, you know, maybe, maybe you're even arguing, but you're arguing in, uh, a way that doesn't alienate them. Um, that where now at the origin moment, right, the, the standard gets, [01:29:30] gets accepted and, and published and, uh, yeah.

[01:29:35] **DAVE ABRAHAMS:** The next meeting, I thought, I thought Geneva, but I, it's, there's, there's a correct record. So if you say France, I, I believe that, um, uh, yeah. And I, I, I'm not at that meeting. Um. Uh, because like I said, I'm not a committee member. Uh, in fact, I was pretty sure I was still, yeah, I [01:30:00] was still working for Market The Unicorn.

[01:30:02] **DAVE ABRAHAMS:** Uh, they weren't gonna, it was a very small company. Didn't want to pay for me to be, to go to France and be part of this committee that didn't have any direct relevance to the, their business. I didn't even bother asking. Right. Um, so, so I hear about this later, I think, I think from Beman. I think Beman tells me, you know, a group of us are, you know, so, [01:30:30] so the name story is cute, but, but not really important.

[01:30:35] **DAVE ABRAHAMS:** Um, was it, you know, something to do with booze? Yeah. So Java was the, was the big language at the time. It was getting a lot of, a lot of attention because mostly because of this misguided, uh, attachment to object orientation. I think the, the question was, okay, we need a competing drink, you know, if we want to be [01:31:00] popular, and somebody said, yeah, it's gotta be booze.

[01:31:04] **DAVE ABRAHAMS:** And, and then the idea was maybe we will call it Boost. Okay. So, uh, secondhand, um, that's the story secondhand. If you can find Robert Klarer, maybe you can get, get the firsthand account. The, the important thing is why Boost. So, so Beman is, is thinking about what [01:31:30] about the next standard? And after you standardize, um, I don't know if this is normal practice, but the way C++ decided to do it is we want people to take this standard seriously.

[01:31:44] **DAVE ABRAHAMS:** So we're gonna have five years of stability where we don't do anything but. But fixed problems. More, more issue processing. And then, then we'll have another five years where we, where we make changes and, and then [01:32:00] a new standard. And Beman is thinking, where are the libraries for the new standard gonna come from?

[01:32:08] **DAVE ABRAHAMS:** Well, there's a principle that is supposed to be followed or was supposed to be followed called standardized existing practice. The idea is, let's, let's only make standard the things that are actually out there in use that, that have a track record and who's, you know, [01:32:30] that we can evaluate in terms of how they actually worked in the real world.

[01:32:35] **DAVE ABRAHAMS:** And, um,

[01:32:41] **DAVE ABRAHAMS:** and the, the committee had already strayed from that a little bit in order to get the STL in. As I told you, they, they developed some, some, uh, template features, uh, just to, to make the STL work. And that was, that was a concern. [01:33:00] And, uh, I'm not sure if there was, it was, it was certainly many years before, or it felt like that, it felt like many years before, before Major compilers supported all of those features.

[01:33:14] **DAVE ABRAHAMS:** And yeah, it was many years. And, um, and that's actually, you know, that's kind of a black eye for the committee, right? Like, you don't, if you standardize something that's not in practice, who knows if it can even be [01:33:30] produced or whether it's economical for a, a vendor to produce it, right? So you, you want to be standardizing things that are out there and, uh.

[01:33:42] **DAVE ABRAHAMS:** And so Beman thought, well, we need, we need an organization to start developing libraries and getting them out into, into people's hands and, and actually used. And so that was the, that was the idea of Boost. Um, [01:34:00] so you asked where, where peer review came from. Um, I know you said some people credit me with it.

[01:34:10] **DAVE ABRAHAMS:** I, I don't know that that's true, but you know, I always saw it as, as an extension of the, of the committee process, you know, proposals would get, you know, the way, the way you make changes [01:34:30] to the standard is via proposals. Proposals would get scrutinized and, and, you know, there would be a whole feedback process with, with peers before they, before they were ever accepted into the standard.

[01:34:45] **DAVE ABRAHAMS:** Sometimes even before they were brought as, as actual proposals. Um, and, uh, yeah, and, and so, so, [01:35:00] so that was the model? That was the model and, and it was consensus based again, and yeah, I don't know, I don't know who said to do this, but, but the idea was, um, the, the review process became, we, we, for every new proposed library, we would get a review manager and that person would be, you know, they would either [01:35:30] volunteer or be selected from a, a group of people who had, you know, done some, some work in the library, uh, before, I think, but the, but their main role had nothing to do with their.

[01:35:42] **DAVE ABRAHAMS:** Technical ability. It was to do that, that thing that Beman did in library working group meetings, which was to, to moderate the discussion, to, to, you know, help make sure that the, that the all [01:36:00] arguments are heard. And then at the end it would, it would be up to them to decide whether the it was accepted or not.

[01:36:08] **DAVE ABRAHAMS:** But they would be deciding, they would be ruling on what the consensus had been. So people would, would make their informal votes and, you know, the review manager would look at the votes and decide whether there was consensus for including it. And, um, yeah. And, and that [01:36:30] process worked really well for a long time.

[01:36:33] **DAVE ABRAHAMS:** Um, a a bunch of us, you know, eventually I started going to the WG 21 meetings and, and a bunch of us would meet each other. There, there are, there are people who I worked with on, on Boost early on who I still would've liked to have met, like Peter Dimov, who we never got him to travel to the, to the [01:37:00] us. Um, and, um, yeah, I mean, not, not meeting my fellow boosters was a big part of the reason I thought we needed boost Con in the end.

[01:37:14] **DAVE ABRAHAMS:** Um, so 

[01:37:17] **RAY NOWOSIELSKI:** have you ever seen Peter Dimov's face? 

[01:37:20] **DAVE ABRAHAMS:** I think I may have seen a picture of him at some point, but no. 

[01:37:27] **RAY NOWOSIELSKI:** Well, because I, I was actually kind of [01:37:30] curious about the community that initially assembled. And what their kind of nature was, who was drawn to this idea those first few years?

[01:37:38] **DAVE ABRAHAMS:** Yeah. It was a, it was a community.

[01:37:40] **DAVE ABRAHAMS:** I mean, um, you know, we, we had a mailing list and so that's how, that's how we communicated. Um, you could only tell what you could tell from f from from emails, right. Um, I, [01:38:00] I don't think, I don't think we used a lot of exclamation points. Um, so, so there's the, it's, it's hard to tell how, you know, you didn't get a good emotional read on people.

[01:38:17] **RAY NOWOSIELSKI:** Yeah. I'll see like a 300 email chain involving dozens of people over a, a naming convention debate. 

[01:38:24] **DAVE ABRAHAMS:** Yep. Yeah, that's true. Yeah. I mean, when you get technical people together [01:38:30] and it's, it's very common to have to have debates over things. And, and I, I think, uh, one thing I can say is that the level of the level of thinking and debate was, was really great.

[01:38:48] **DAVE ABRAHAMS:** Um, and another thing I can say is that, that, I don't know, I don't know if this applies to, to lots of other engineers, but one thing I discovered about myself [01:39:00] early on, which was when I was commu contributing to, to like, uh, a lot of discussions happened on, happened on Usenet, unlike comp blank C++ moderated.

[01:39:13] **DAVE ABRAHAMS:** Um, when I was contributing to these discussions, what would normally spur my insight would be somebody would post something and I would be like, that's not right. Why isn't that right? And then I would like, [01:39:30] like. Ha be forced to explain to myself, like really lay it out and then write it for other people to, to understand which I, which I viewed as, you know, again, part of my empowering other programmers by through, through their understanding.

[01:39:50] **DAVE ABRAHAMS:** Um, but, but I, I think you are gonna find a lot of technical debates happen because at least, [01:40:00] at least for me, it was, it was, I would read something and I was like, no, that's not right. Why? Why don't I think so, oh, here, here's something I think they're not considering. I can help them understand the problem better by, by adding it.

[01:40:16] **DAVE ABRAHAMS:** And so you get engaged at that level. So what is Boost? Boost, uh, is a collection of libraries. Um, the part of the original intention was f for it to be a collection of, [01:40:30] sorry, open source C++ libraries, uh, suitable for standardization and, and why Open source existing practice, right? You want to give it away.

[01:40:44] **DAVE ABRAHAMS:** You want to make it as easy as possible for people to consume so that it gets a lot of practice. And one of the dynamics you see with open source software is there's, you get pressure from your users because they submit bug [01:41:00] reports and the software gets better, right? Or, or feature requests. And you know, and if you have five years of evolution on a library before you bring it as a standard library proposal, um, now you've got a lot of credibility.

[01:41:18] **RAY NOWOSIELSKI:** Creative c o m m o n s of code is one term we heard when people are driving. We would ask, uh, different parties in Boost World, uh, what was the secret sauce? What made this [01:41:30] work? And work so, so exceptionally. Creative Commons of code was one that got thrown out a formal review. The license sometimes gets mentioned.

[01:41:39] **RAY NOWOSIELSKI:** Some people say it was specific to the people that came together at that time, and the same outcome wouldn't have happened at a different era of different people. Um, do you want, what, what do you think was the, the secret sauce? 

[01:41:52] **DAVE ABRAHAMS:** I think the caliber of, of the people involved was, was hugely influential.

[01:41:59] **DAVE ABRAHAMS:** [01:42:00] And, and one of the, you know, for better or worse, one of, uh, one of the, the attributes of C++ is that it's, it's very complicated and it's even much, much more complicated than it was when, when Booth was starting. But, but even, even then, it's very complicated and it required a, to be good at it required a lot of expertise and requires a lot of [01:42:30] expertise.

[01:42:31] **DAVE ABRAHAMS:** Um, so, so in some ways you had a self-selecting group of, of really smart people. Um, 

[01:42:41] **RAY NOWOSIELSKI:** well, Andrew Lumsdaine told us, um, he actually got yelled at, at, at an event, um, for bringing up C++ and boot, because this, there, apparently there are people who feel that it's almost, um, club like it's designed for the exclusionary, well, only [01:43:00] people who understand need a, you know, need apply.

[01:43:03] **RAY NOWOSIELSKI:** You know? Did you see that, uh, 

[01:43:05] **DAVE ABRAHAMS:** uh, in C++ 

[01:43:07] **RAY NOWOSIELSKI:** and Boost? 

[01:43:08] **DAVE ABRAHAMS:** Yeah. Uh, right. No. Uh, no. We were, uh, we, we were, we were as inclusionary as we, as we, we tried very hard to be inclusionary in, in Boost. I don't think people showed up that, that. Didn't [01:43:30] already have an interest in C++, and, and you would've had to get your, your foot in the door there.

[01:43:37] **DAVE ABRAHAMS:** But, you know, I mean, cultures also change and evolve and, and I'm sure that Andrew didn't get yelled, yelled at back in the old days. I'm sure that's more of a modern, uh, phenomenon, I would guess. Anyway. 

[01:43:54] **RAY NOWOSIELSKI:** Culture, you brought up the word culture. That's what I'm, I'm getting at a little bit is no one would probably [01:44:00] be in a better position to describe the culture of the people who, uh, who made Boost Golden Age a success than you.

[01:44:07] **RAY NOWOSIELSKI:** And I'm kind of wondering, is there, is there a type, are these rebels? Are they punk rock? Are they meritocracy, devotees? Is there an ethos? 

[01:44:16] **DAVE ABRAHAMS:** There, there, there were people that would show up that were just in, like, just showing up to get their library into boost. That's what they were, were, you know, that's what they [01:44:30] were about.

[01:44:31] **DAVE ABRAHAMS:** And, and those could be any kind of people, um, but the people who were sticking around, you know, who were, were community oriented, they, they saw themselves as, as engaged in something worthwhile and, and, you know, worth, worth doing collectively. And I, I think that is a, you know, that is a [01:45:00] type, um, maybe not a very narrow type.

[01:45:04] **DAVE ABRAHAMS:** Uh, and I think in general, I think we were, we were in a lot of ways, you know, at a, at a different level and not as, not as fundamental level, but, but. As, as Alex, you know, one of the things that Alex [01:45:30] said, you know, or at least I learned eventually through Alex, was that, that, uh, you, you, the valuable things are discovered, not invented there.

[01:45:48] **DAVE ABRAHAMS:** Uh, at some level there, there's a truth that's, that's out there like a mathematical truth or, or a design truth or something, and, and [01:46:00] your job is to discover it. You know, that's what I felt everybody wa involved in Boost was, was interested in, was in, you know, discovering the world of, you know, what's the, what's the way to approach this problem?

[01:46:22] **DAVE ABRAHAMS:** Um, you know, what's the best way for C++ to approach the problem? How do we, um, [01:46:30] yeah, how do we structure boost? Things like that. All all those things we were engaged in as a kind of, as a kind of, uh, process of discovery rather than, rather than, uh, you, you mentioned meritocracy and the first thing I think about that is, well, in a meritocracy that's about the most worthy person winning, and it was not about anybody winning.

[01:46:57] **DAVE ABRAHAMS:** That's that much I can tell you. [01:47:00] What was it about? Uh, well, like I was saying, I think it was about, it was about discovering the truth of like, what libraries did the, does the world need? What should they look like? You remember, you mentioned a whole, you know, 300 message thread on naming conventions. Well, what is the best way to name things, things like that.

[01:47:24] **DAVE ABRAHAMS:** Those are. You know, those aren't things that we just came [01:47:30] into with an opinion and then, and then argued back and forth. It was the ar the argument was a vehicle for, for coming to a consensus. And, and that consensus was gonna be reached by a process of, of discovery. Let's, let's see all the angles. Let's, you know, 

[01:47:52] **RAY NOWOSIELSKI:** C a n you d e mystify the relationship that developed and, and the roles between, [01:48:00] uh, Beman and yourself.

[01:48:01] **RAY NOWOSIELSKI:** We've had many describe you two as sort of a dynamic duo type with beman being, uh, kind of a good shepherd, and you being a bit of the enforcer who didn't suffer fools, uh, any accuracy there. How would you describe 

[01:48:18] **DAVE ABRAHAMS:** I, I would say that, that that certainly, uh, that, that, that reflects our personalities somewhat.

[01:48:29] **DAVE ABRAHAMS:** [01:48:30] Like, you know, my, eh, I don't know how to, how to say this, sort of being, uh, being precise, concise and, and maybe sometimes, maybe sometimes too blunt is, is, you know, kind of my, my natural mode. Like I said, a lot of times my, my insights are prompted by realizing that something is [01:49:00] wrong and, and why, and so that, you know, that has a natural dynamic of making me look like somebody who's, who's, you know, 

[01:49:14] **DAVE ABRAHAMS:** um, 

[01:49:15] **DAVE ABRAHAMS:** I 

[01:49:16] **DAVE ABRAHAMS:** wouldn't say enforcing, but, but, uh, uh, I don't know.

[01:49:23] **DAVE ABRAHAMS:** I, I guess, I guess an argument could. Could shut people down or, or, you know, could end up [01:49:30] looking like winning or something. Um, uh, I mean, Beman had a, a kind of level of calmness that, that, um, we, I don't know, was, was important. Um, I think we, I think we very much [01:50:00] saw eye to eye on, on things, and I think the, the most important thing was the sense of partnership.

[01:50:06] **DAVE ABRAHAMS:** The sense that, you know, you could count on somebody that, that you were working with and you were gonna be headed in the same, same direction. Yeah. I mean, you know, it might, for some of this, it might be [01:50:30] valuable for you to dig up all reflector conversations and actually quote them to me because I don't, there's a lot I don't re remember.

[01:50:39] **DAVE ABRAHAMS:** And, and you can get a, you can get a sense of who I was and who Beman was by, by looking at that and, you know, maybe I was an enforcer. Um, I don't know. 

[01:50:52] **RAY NOWOSIELSKI:** When did you guys know this was very successful that you'd done something special? [01:51:00] Was there a, a moment that comes to your mind where you go? That was when we knew we had a championship team, so to speak.

[01:51:08] **DAVE ABRAHAMS:** I don't think we, I don't think we ever, we ever said that to each other. Right. Um, but I can tell you it must have been after the license because my. From my perspective, what I started seeing was, even though the [01:51:30] license was, was permissive and didn't require you to do anything, program after program would display the Boost software license at installation or, or on startup reflecting that they were using Boost.

[01:51:46] **DAVE ABRAHAMS:** And, and, uh, yeah, at some point that was like, oh wow, this is really a major force in the world, you know? Um, and yeah, that was it. [01:52:00] That was really something. Um, but, but I always, you know, I always felt Boost was, well, maybe not beginning at the very beginning, it was just a little germ of an idea. But it, at least, you know, by the time a year before Boost Con, the first Boost Con, I was like, you know, this is something, this is really something and it deserves to be [01:52:30] nurturing and, and, uh, and we want to get, we want to get people together so that they can, they can have those inventive conversations that don't normally happen by email, you know, well, and have to say, uh, this is, this is part of, like, BusCon wouldn't be the way it is if it weren't for my dad.

[01:52:58] **DAVE ABRAHAMS:** So, [01:53:00] so my dad, as I said, was a, a theoretical physicist. He was, um, connected actually on and off since I was a very small child at the Aspen Center for Physics. Um, uh, and, uh, by the time I was in middle school or something. Uh, the, the center runs its main sessions in the summer. We would go to Aspen every summer, [01:53:30] and this was before Aspen is what it is today, you know, was not, it was not, uh, rodeo Drive and movie stars.

[01:53:40] **DAVE ABRAHAMS:** Um, uh, uh, it was still at, at least in most, most ways of a funky little town in mountains. Um, and, uh, and you know, this, this, it's this amazing setting [01:54:00] and, uh, even, you know, I would, I would, so the physics center would have every Thursday night, I think it would, it would have a picnic. And so the families would, would all go to the picnic and, you know, so I, I was ended up around the grounds.

[01:54:21] **DAVE ABRAHAMS:** I would see how they, how the physicists were interacting. They would have, they would have these talks. Uh, [01:54:30] at some point my, my dad invited me to go to a, a couple of these talks. Um, you know, I got to observe them, you know, sort of doing the, doing the collegial intellectual discovery thing in person. And, um, and so when I started to think about, oh, actually, you know, Scott Myers was in, ended [01:55:00] up being instrumental in this decision too.

[01:55:03] **DAVE ABRAHAMS:** When I started to think about running a Boost conference. Um, I was actually, I was actually in Santa Clara at, at some conference. That doesn't happen anymore. Uh, and I talked to Scott Meyers about. His, his advice for this would be like, what his feedback would be. And he said, he said, you know, [01:55:30] have he mentioned somebody else who, who he said, what he said was, um, think about when you think about your, essentially your fantasy of what you would like a day at the conference to be like and make that happen.

[01:55:47] **DAVE ABRAHAMS:** He is like, do you know so and so? I don't remember who he runs a, he, he runs this conference and every day at, at, you know, it's, it's beautiful place in the woods and every [01:56:00] day at two o'clock, uh, the conference goes for a hike. You know, I was like, wow. That's, you know, a lot of, I, I love that. A lot of good thinking happens on a hike.

[01:56:15] **DAVE ABRAHAMS:** You know, we could be in a, a beautiful setting. You know, the next logical conclusion from that was Aspen, since I had been exposed to all of that and there were all of these activities and so like, um, [01:56:30] part of, part of the way we designed the conference was, was, you know, uh, I think a half hour between sessions, so that to really encourage people to talk to each other and, and have all that stuff that, that happens in the hallway track now.

[01:56:49] **DAVE ABRAHAMS:** They call it, you know, outside of sessions, uh, to sort of encourage that as a main thing. And, um, again, a long lunch break. The, [01:57:00] and you know, the stuff that we ended up talking about in sessions, it was intense and, and it was good to, to not pack the day, you know, with, with just one thing after another to the, to have all of that breathing room.

[01:57:16] **DAVE ABRAHAMS:** Um, yeah. And, and. People would, and the physicists that that came to the center were from all over the world. And so that was another, [01:57:30] that was another thing I got to see. I got to see the sort of multicultural thing happening and how these people all worked together in pursuit of like what the actual underlying truth of the universe is.

[01:57:43] **DAVE ABRAHAMS:** Um, you know, that's, that's real science. I always thought, thought of my, what my dad did as real science and computer science as a kind of a weak, uh, a weak second or third. But, um, but it inspired a bunch of us met each other for the first time. [01:58:00] Uh, uh, I met Jeff Garland for the first time there. Uh, uh, uh, I, I think I met Sean for the first time there, and I, and I don't, I don't actually know how, oh no.

[01:58:21] **DAVE ABRAHAMS:** You know what? I must have, I must have met Sean through [01:58:30] Alex, 

[01:58:31] **DAVE ABRAHAMS:** who 

[01:58:31] **DAVE ABRAHAMS:** I'm, 

[01:58:32] **DAVE ABRAHAMS:** yeah. 

[01:58:33] **DAVE ABRAHAMS:** I'm really, I'm really a little bit bad on the sequence of events here. But, but at some point,

[01:58:42] **DAVE ABRAHAMS:** at some point, people in the C++ committee started working on features to explicitly support generic programming. The, the paradigm that Alex essentially invented on. And, and [01:59:00] Alex invited a bunch of people who were involved to come to, uh, a summit in, in Silicon Valley to, to talk about it. And it was, it was like Bjarne and, and Jaako Jarvi and Doug Gregor.

[01:59:18] **DAVE ABRAHAMS:** And, and I was invited and. I believe Alex was already working with Sean at that time, and that's, that must be how I met Sean. I don't, I don't know what I had been exposed to that [01:59:30] made me want him as the first keynote speaker, but, but, but I'm pretty sure that I met him for the first time at that Boost Con, or, or no, I was saying I might have met him at this summit, but like really talked to him for the first time at that Boost Con.

[01:59:46] **DAVE ABRAHAMS:** That's where I, I really got to know him and we were like instantly, like on the same, on the same wavelengths and, and I later, I I [02:00:00] oh, a lot of the, the things I, I normally think of as my core ideas to Sean. Hmm. Actually, 

[02:00:09] **RAY NOWOSIELSKI:** what, what did, um, so what did it accomplish that that wasn't already happening for Booster?

[02:00:14] **RAY NOWOSIELSKI:** The, that, what, what do you see as gone having achieved, like after you walked away from that first one in, what did you feel done? 

[02:00:26] **DAVE ABRAHAMS:** I, I, I think I had started the first, [02:00:30] the first annual C++ conference. Um, and, you know, uh, part of the, part of the project that at the end of BoostCon was a planning meeting for next year.

[02:00:45] **DAVE ABRAHAMS:** And that's where you actually get, get the people who are, who are gonna put their own butt on the line to volunteer for, to, to make the next one happen. And, you know, there were, [02:01:00] the planning meeting was, was, you know, quite full. Not, you know, it wasn't the whole conference or anything, but, but there were plenty of people and, and the, the important roles got filled.

[02:01:13] **DAVE ABRAHAMS:** Um, and uh, and so I knew this was now a going concern. I had more fun at that conference than I had ever had at any other conference for sure. Um, I mean, you know, actually one of the things I thought [02:01:30] about when I thought when Scott prompted me was, was, what are other conferences? Like, oh, they're in these convention centers and hotels.

[02:01:38] **DAVE ABRAHAMS:** I hate that environment. I had actually been to a, uh, a conference in Vegas, and Vegas is like the antithesis of, of the environment in Aspen, which is like all outdoor being let in, like you're completely enclosed. There are no s in the building. It's always midnight in Vegas as far as you can tell. [02:02:00] Right.

[02:02:00] **DAVE ABRAHAMS:** And Tanner. And so, you know, yeah. I I I felt that we, that we had done something really special. People loved it. Very few things in my, in my career are capped by somebody, uh, by like some declaration of victory, you know? Um, 

[02:02:25] **RAY NOWOSIELSKI:** around the same time did you guys get a fiscal sponsorship for Boost from the Software [02:02:30] Freedom Conservancy?

[02:02:31] **RAY NOWOSIELSKI:** What's that story? 

[02:02:34] **DAVE ABRAHAMS:** It was not a fiscal sponsorship and so, but yeah, it's not, it's not coincidence that it was around the same time and I forgot this part of the story, so thanks. So the deal was if we wanted to use the Aspen Center for Physics, we had to be a nonprofit 5 0 1 C3. And, and so I actually, my dad was actually in a [02:03:00] relationship with the person that ran the, the physics center at that time.

[02:03:03] **DAVE ABRAHAMS:** So I have had, uh, uh, a lot of opportunity to talk to her about how, how this could get done and, and you know, when she. And when she said it, you know, she told me it was, it had to be a five oh C3. That was because that was because, uh, that of how [02:03:30] this, the physics center is structured not because of, you know, something that she was demanding.

[02:03:35] **DAVE ABRAHAMS:** Um, and I talked to Luann about it, uh, and, and she said, let me tell you 5 0 1 C3, it's a pain. Um, you know, you have to have a board. There's this requirement. You have to, I looked at that and, and, and was I, I probably talked to Beman about it. [02:04:00] In fact, in fact I think it was Biman that told me that 5 0 1 C3 is a pain.

[02:04:06] **DAVE ABRAHAMS:** 'cause he was involved with several. I think that's actually what happened. Yeah. So, so talk to Biman about this. He said, this is a pain, you know, we should try and find, find an alternative. And, uh, yeah. I don't know how, how the Software Freedom [02:04:30] Conservancy came to my attention, but they were an umbrella organization, I think still ares for, uh, various open source projects and, and they are a nonprofit.

[02:04:43] **DAVE ABRAHAMS:** And so if you become a member, you know, care of Software Freedom Conservancy, you now have nonprofit profit status. And like remember, boost wasn't anything officially, legally Boost was not an [02:05:00] entity. Right. So, um, yeah, I mean, because presumably if we had made Boost, uh, a non-profit, then that would've opened Boost to being sued, you know, part of.

[02:05:18] **DAVE ABRAHAMS:** Cover the software, boost software licenses. You know, you use this on your own, it's your own risk, you know, you know, we, we don't ask anything of you and, [02:05:30] and we don't take any responsibility because we aren't a thing

[02:05:37] **DAVE ABRAHAMS:** being an an entity at all. Not being a thing is just how we, how we evolved, right? Like there was never a question about whether we were gonna be a thing before the 5 0 1 C3, um, uh, thing came up. The license is, is permissive the way it is because of the fundamental charter to, [02:06:00] to create existing practice for standardization.

[02:06:04] **DAVE ABRAHAMS:** So the, the idea is make it as easy as possible for people to use. Don't put any strings on what they do with it, and, and then it'll get lots of use. And it did, 

[02:06:17] **RAY NOWOSIELSKI:** but 

[02:06:18] **DAVE ABRAHAMS:** it's interesting that the, that the boost software license is not more popular among open source licenses. Um, 

[02:06:26] **DAVE ABRAHAMS:** what, 

[02:06:27] **DAVE ABRAHAMS:** so one of the weird things is [02:06:30] companies use open source software, right?

[02:06:32] **DAVE ABRAHAMS:** But, but in order to do that, their lawyers need to get involved, right? So they need to scrutinize things and lawyers will like to have an entity that they're dealing with, right? And, and other, you know, there's also a momentum thing. Other open source software they're using is probably not using the Boost [02:07:00] software license.

[02:07:02] **DAVE ABRAHAMS:** So they then, so they use, you know, they, they prefer something else, I guess. I don't know. I 

[02:07:12] **DAVE ABRAHAMS:** mean, 

[02:07:12] **DAVE ABRAHAMS:** I don't know what to make of it. And I, there's a reason that we didn't adopt an existing license. Um, they were all, and if I remember right, it was because they were all too uncom. I think the, I think you could probably, you know, find [02:07:30] more detail about this in the male and West wanted to have BusCon because, because the relationships that I had developed with people online were meaningful, they were intellectually meaningful.

[02:07:44] **DAVE ABRAHAMS:** Right. And, and like the, what we were doing in Boost, we wouldn't, we wouldn't have personal conversations like you would have over a beer. 

[02:07:53] **RAY NOWOSIELSKI:** Hmm. 

[02:07:54] **DAVE ABRAHAMS:** Right. Um, I didn't know about anybody's family or anything. Like, that's the [02:08:00] kind of thing I would only Warren at, you know, at BusCon. Um, uh, and, uh, you know, I, I might have started BoostCon because I wanted to meet Peter Dimov, which never happened.

[02:08:16] **DAVE ABRAHAMS:** Um, I don't know what it is for these Eastern European guys that don't wanna, don't want to meet anybody, but, uh, that's, that's hilarious. Um, I mean the, the, [02:08:30] there, the people that were involved were hugely interesting. A lot of, uh, you know, I learned so much from, from, from these guys. Um, and I don't even remember what the, what the specific lessons were, but I, but you know, I, I credited them with, with, with insights that I carried forward into my career that I thought were really valuable.

[02:08:59] **DAVE ABRAHAMS:** [02:09:00] Yeah. So Doug, um, Doug showed up at, around Boost, um, and I think his first contribution was, I think, was. Either boost function or signals and slots, I guess signals and slots depended on function. So function was a, was a very, um, was a very fundamental library and signals and slots. It was a, a [02:09:30] very o oh type thing that was, uh, object oriented type thing that, uh, that uh, of the sort, I would, I would avoid like a plague today, interestingly.

[02:09:44] **DAVE ABRAHAMS:** But anyway, Doug showed up on, on the boost list. I only knew him as a remote contributor. Then one day I was at a committee meeting [02:10:00] at lunch and somehow I didn't know it, but there was this, I didn't know who he was. There was this young guy there, this, he was like a kid really? He was super young. Um, and, and I think I, I think I was kind of rude, like, like he was assuming he was joining a group of us for lunch.

[02:10:27] **DAVE ABRAHAMS:** And I, and I like, kind of [02:10:30] made it so that he wasn't, because I didn't know who he was or something like that. I, anyway, I, I, later, I later apologized to him. But the, the point was, he, he was this really unassuming looking, very, very young guy that when I first met him and, um, and, you know, eventually he, like, he became the, he [02:11:00] went into, uh, pub science PhD program, which is something that, that I, I failed to complete and became like a really serious powerhouse computer scientist, like the science part.

[02:11:14] **DAVE ABRAHAMS:** Not just an engineer. Um, and, uh, and there were, we, we saw eye to eye on a lot of things and we were, we were both like [02:11:30] everybody I think and, and Andrew's lab, uh, deeply influenced by Alex DevOps work and trying to, you know,

[02:11:46] **DAVE ABRAHAMS:** trying to do our best to, to, um, make good on, on what we had learned from Alex really do credit to, to, to what he had taught us. And, um, [02:12:00] and I think, you know, our first, you know, our, the deep, the deepest bonding came when, when we started working on the, on the, uh, I think this is right, yeah. On the, on, on concepts.

[02:12:25] **DAVE ABRAHAMS:** Um, uh, [02:12:30] my, my memory of the order of things is terrible, but, but, uh, I know that we, we worked on, we worked on some problems having to do with moose semantics. Um, and, you know, we would just, we ended up getting together at meetings because there was something needed to be solved and we were thinking about it and we would like hunker down together and, and, you know, write a paper and write some programs [02:13:00] to, to demonstrate the issues.

[02:13:02] **DAVE ABRAHAMS:** And, and it was, it was just kind of really cool. We, we thought the same things were important and, um. And I think we learned from each other. Uh, yeah. So, uh, so yeah, that I, I became, I became kind of a strong ally of the Indiana crew in their, in their quest to make concepts good. Uh, [02:13:30] and, uh, 

[02:13:33] **RAY NOWOSIELSKI:** yeah's what we hear.

[02:13:33] **DAVE ABRAHAMS:** So my pullback from C++ started,

[02:13:40] **DAVE ABRAHAMS:** I think, um, and I think maybe 20 11, 20 12, I, I started to realize that, that the committee process was and was [02:14:00] not, I think dysfunctional is too strong a word maybe. But the committee was not capable of making the kinds of changes that I thought were needed for C++ to, to continue to, to be, uh, the vehicle for empowering parameters.

[02:14:26] **DAVE ABRAHAMS:** Um, and I think there were, [02:14:30] so one of the things that happened was, was, uh, that I had tried, uh, a few years before to try, just to get the committee to agree in principle on some, some principles for evolution. Here's what we believe we can do. Are we, are we willing to say that, that the new code, [02:15:00] I mean old code, not necessarily compile with the next regiment C++.

[02:15:07] **DAVE ABRAHAMS:** So yeah, it would, might require some modification. Are we willing to say that? Are we willing to say that that existing compiled things can't be linked with new compiled things? These, these are like really kind of fundamental language evolution questions, but there are other questions like, you know, do we value this or that?

[02:15:29] **DAVE ABRAHAMS:** What's [02:15:30] the, you know, so, so that we have some framework for, for making decisions that isn't just people's opinions that, you know, and I could get no traction with this. And it turned out that a few years later, Google came to the committee and, and tried to get a another, I mean, tried to do this again, essentially.[02:16:00] 

[02:16:00] **DAVE ABRAHAMS:** Um, um, and they, they, they had some particular things they wanted to be agreed to. I was just like, let's agree to something, you know, but, but Google also fickled and, um, and, you know, I had come to realize that that C++ was, was too complicated to be the vehicle for [02:16:30] empowering. It was, it was more complicated than it needed to be.

[02:16:34] **DAVE ABRAHAMS:** And, and my, you know, I, I've since become clearer and clearer about that. It's, it, you know, some people say that C++ is expert friendly, which might go to something about what you, you refer to as, as being exclusive. But, but I don't, honestly, I don't think it's actually friendly to experts. It's hard for everybody.[02:17:00] 

[02:17:00] **DAVE ABRAHAMS:** It's, it's, uh, it's incredibly complicated. There are too many ways to step wrong. The consequences for stepping wrong are too high. Um, so between the, the inability to, to evolve the language in directions that, that I wanted, or even a coherent direction and that problem [02:17:30] of, uh, um, complexity and, and general danger, uh, when using C++.

[02:17:39] **DAVE ABRAHAMS:** And I think there, there's also another factor. Um, so there had been an effort, as I mentioned before, to get support for generic programming into C++ that, that exploded in the most unfortunate way. And, and if you're talking to [02:18:00] Doug Gregor and bni Str Stripp, you can get firsthand accounts from from them.

[02:18:06] **DAVE ABRAHAMS:** From them. I, I was, I was peripherally involved in that. And, and, you know, heard, heard lots of reports of how, how this went, uh, uh, from Doug mostly. Um, uh, but, but Doug had done a massive amount of work [02:18:30] on to get, to get, uh, a principled implementation of concepts for C++, uh, into the language. And it got, it got torpedoed at the last minute and in such a way that it was clear that that bona was never gonna support, uh, what I considered to be the right design.

[02:18:57] **DAVE ABRAHAMS:** The, the difference between the, [02:19:00] the,

[02:19:03] **DAVE ABRAHAMS:** we eventually got something like what that Bjarne supported, which, which. We, I, I'm not in C++ anymore. C++ eventually. Got that. And, and essentially the, the problem with it is it, it doesn't make life better for people who are doing generic programming. It does, it does

[02:19:29] **DAVE ABRAHAMS:** [02:19:30] make, it made may make, uh, life better for people who use generic components, but people that, that it. So I haven't really said all, all that much about generic programming, but, but, um, and, and you should get the full story from Alex, but, but, uh, as far as I'm concerned and, and, uh, [02:20:00] a lot of the people I work with, that it's a, it's a truly visionary way of approaching programming and it really matters.

[02:20:10] **DAVE ABRAHAMS:** It really matters to the future of software. And even, even with, um, generics features in, in languages, most people are not using those features to do generic programming the way Alex talks about it. Um, so from my point of view, [02:20:30] it's hugely important to get that right and to make it easy for generic programmers.

[02:20:34] **DAVE ABRAHAMS:** And C++ was never gonna get there. It was, it became clear that was over. And, uh, and at that time, so in 2012, I was, uh, at a committee C++ committee meeting with Doug, and I had started to, to fish around for, for, oh, my, my [02:21:00] consulting business had also reached a point where, where, you know, we weren't getting new business and.

[02:21:08] **DAVE ABRAHAMS:** I was tired of doing it. Basically, you know, to run a business you either need, you need either people who have expertise and, and lots of things that I don't, or you need to be good at it yourself, like marketing and I'm, I don't think about marketing, right? [02:21:30] So, so, uh, so I started to look around for, for jobs and I asked Doug if Apple might have the use for me.

[02:21:44] **DAVE ABRAHAMS:** Doug was, had Apple working on, as far as I knew, his whole job had been to produce the, the clang C++ compiler, the, you know, clang before Doug started working on it was a c [02:22:00] compiler and adding, you know, this was becoming the, the open source competitor to GCC, um, uh, and that, that's a huge achievement.

[02:22:14] **DAVE ABRAHAMS:** Uh, uh, and so I was super impressed with that. I loved working with Doug. We had done a lot of work together in the committee, um, written a bunch of papers together, uh, and, uh, so Doug said we might have a, [02:22:30] a place for him and, and so I set up some interviews and, uh, yeah, he was in, in the development tools area and they started fishing around for, they were kind of cagey about what, what the job would be, but they were fishing around for like how of my allegiance to C++ was, and, and, uh, other things that made it [02:23:00] clear they were probably working on a new program in language and, and the chance to do.

[02:23:08] **DAVE ABRAHAMS:** So programming languages, new programming languages come along every day and die in obscurity. I mean, that is, that is really true. It's very hard to, to, you know, bring up a programming language. There are a lot of, uh, a lot of, there's a lot of peripheral work that's needed on tools like editor support and, [02:23:30] and things for using it.

[02:23:32] **DAVE ABRAHAMS:** Um, debuggers, uh, there, there's, you know, just collecting a user base. Nobody wants to, wants to invest in writing code in a, in a language that nobody else is using. Anyway, the chance to work on a language that was fully backed by Apple and was gonna be the language for, you know, for doing stuff on Apple platforms next, you know, that was, and [02:24:00] it, that was like, uh, a recipe for success, right?

[02:24:04] **DAVE ABRAHAMS:** And to do it with the people that were on the project, you know, um, Doug and Chris Latner. Uh, note, most notably, those were the ones that I, that I knew that was a huge, huge opportunity. And so I took it and, uh, and one of the things they told me, not right away, but, but as I [02:24:30] was getting ready to go to BoostCon in 2013, they said, you know, you can go to this one, but, but you really need to pull back your open source.

[02:24:42] **DAVE ABRAHAMS:** Val and Apple had, had just entered a really draconian, uh, period. I don't know if they're still doing this, but they, some engineer somewhere had said something that some executive didn't like in a, in a conference, and they, [02:25:00] they basically said, you know, engineers can't talk. You know, we're we. Let, we'll put 'em on stage at ww DC and we'll very carefully manage, you know, what they, what they can say, but they can't go out in the world and talk because, you know, probably some, some information about a product may have leaked or something like that.

[02:25:23] **DAVE ABRAHAMS:** So I had to pull back from, from Boost and, and Boost Con after that in order to work on [02:25:30] Swift. And I was willing to do it, um, in part because I didn't see, you know, I was clear on, on my mission to empower programmers and I didn't see C++ being the vehicle for doing that. And Boost, BoostCon had become CppNow.

[02:25:48] **DAVE ABRAHAMS:** Now, partly because, uh, we, we started to realize that there were topics outside of, outside of Boost that people wanted to talk about. [02:26:00] And it was this great, uh, uh, intellectual forum for that stuff. They were, in retrospect, they were talking about topics outside of C++ sometimes too. And I think we, it should have become more broad than that, but I don't know what you call it, programming now.

[02:26:20] **DAVE ABRAHAMS:** Um, it was, it, the Shift was suggested by John Kalb to me, and, and it was trying to acknowledge [02:26:30] the fact that, that we were not limited to Boost. Um, and also that, uh, at that time there was no, there was no other C++ conference. 

[02:26:44] **DAVE ABRAHAMS:** Hello. 

[02:26:44] **DAVE ABRAHAMS:** And I think John really wanted to, to have a C++ conference.

[02:26:49] **DAVE ABRAHAMS:** And John eventually did go on to, to after, after Boost Con or C++ now he, he went to build [02:27:00] Cpp Con, uh, which is, which is a huge, very. Kind of traditional conference in a big conference center in Aurora, Colorado, then, you know, not the kind of thing that BoostCon is at all C++ now it's her and John, I think are the people that lead it.

[02:27:15] **RAY NOWOSIELSKI:** Um, companies like Apple, I mean they benefit from open source libraries. Uh, did what you run into like kind of a change amongst many of these major tech companies regarding how they [02:27:30] dealt with open course libraries and things like 

[02:27:33] **DAVE ABRAHAMS:** Well, one of the big, so one of the big things was that the, the Free Reseller foundation, I think is, is the, is the thing that manages the canoe licenses.

[02:27:50] **DAVE ABRAHAMS:** So, so at some point around this time, and this is part of what, uh, maybe a little bit before this, it's part of what spurred Apple to [02:28:00] make claim. The, the pre software foundation had, um, they, they have a, a what I would call very extreme analyst religious devotion to a certain model of free software, which is that you cannot charge for it, you like.

[02:28:26] **DAVE ABRAHAMS:** And, and it's, and, [02:28:30] and they, they realized that their, that their license that they had been using did not prevent people from incorporating software in commercial. They incorporating free software in commercial products. And so the free software foundation went from the new public license version two to to version three, which, which changed that [02:29:00] scheme.

[02:29:01] **DAVE ABRAHAMS:** And at that point. Whole bunch of companies 

[02:29:04] **DAVE ABRAHAMS:** needed 

[02:29:04] **DAVE ABRAHAMS:** to scramble to make sure that they were not dependent on any GPL three software. Um, and that included, one of the shifts was, was, uh, that included, uh, shipping code that was generated by, uh, A GPL license compiler. [02:29:30] So the next version of GCC, you know, was licensed under GPLV three, and that meant if Apple was using GCC to build their software, uh, that had to stop.

[02:29:45] **DAVE ABRAHAMS:** And that's why they need a claim, which has a, a less religious, um, license than the gbl. Um, and that's why, why Doug was working [02:30:00] on C + + compiler. Um, and yeah, so that was an industrywide industrywide shift. And, and, uh, at that time, you know, lawyers for companies start to become more cautious about, about what open source software people were including and, and what the licensing implications are.

[02:30:28] **DAVE ABRAHAMS:** And it, interestingly, [02:30:30] we're, we're now having, uh, uh, kind of similar, um, somewhat similar revolution because, because of the, the interest in, in safety and, and security and every time you include a piece of software from outside your company into your soft, into your product, you potentially open security holes because of flaws in that software.

[02:30:59] **DAVE ABRAHAMS:** [02:31:00] So everybody's trying to manage the risk of, uh, including, you know, third party libraries. And most, most of that is now in this world is open source. So C++ 11. Well, as I said, the plan after standardizing, standardizing C++ was five years of stability, and then, then we start working on immune version.

[02:31:29] **DAVE ABRAHAMS:** [02:31:30] So in, in theory, uh, you know, 98 to 2008 should've been the release of the next version of C++, but in fact it took longer. So, so it came out in, in 2011, and that's why it's called C++ 11. Um, the versions of c+ cluster named after the year sit there that they're released in. [02:32:00] And, uh, I guess I, I, it's interesting to hear you describe C++ 11 as the success of Boost, but, um, but in a sense, like, you're right, C++ 11 included quite a few of the Boost libraries, um, changed somewhat, but, [02:32:30] but mostly, you know, the, the libraries came in with existing practice because they had been in boost and widely used and, uh, we, and proven to be useful.

[02:32:45] **DAVE ABRAHAMS:** So, 

[02:32:46] **DAVE ABRAHAMS:** yeah. You know, the libraries are only a part of, of the language standard. 

[02:32:51] **DAVE ABRAHAMS:** Hmm, 

[02:32:51] **DAVE ABRAHAMS:** right. But, um, but they were, they were a significant part of the language standard and a big contribution, uh. [02:33:00] Um, it boost, uh, was a lot broader than what was standardized in C++ 11 and is even broader now, um, than what was standardized, than what has been standardized from Boost.

[02:33:15] **DAVE ABRAHAMS:** And actually, I don't know, uh, I don't know how much standardizing of Boost Libraries has gone on since, um, since that time. In part, the, [02:33:30] the concern over legacy baggage, uh, and um, and the, you know, size of dependencies that you get has, I think, caused some library authors not to want to be part of the Boost.

[02:33:48] **DAVE ABRAHAMS:** Uh, whereas getting into Boost was, uh, or has been a, a good way for, for people to get to evolve a user base to get, [02:34:00] you know, because, because Boost ships on all of the Linux distributions, it's widely used anyway, so you know it, if you make a library and it gets into boost as soon as whoever upgrades the next version of Boost your library's available to them and, and, um, at least if they're using Boost as a monolith, which sure almost everybody does.

[02:34:24] **DAVE ABRAHAMS:** There, there were a lot of changes in C++ 11 that weren't libraries. That's, that's basically, [02:34:30] uh, the main thing that I want to tell you. Uh, so keeping in mind that I disconnected only two years after 2011, um, so getting anything into the standard is hard. It's really hard. And, and the, and it got, it's, it, it certainly, I I would say the committee process got, got messier and, and more fraught.

[02:34:58] **DAVE ABRAHAMS:** And more political, [02:35:00] um, as time went on. And so that might have been part of the, part of the reason. And so, you know, it's hard. It takes a, a lot of, a lot of time commitment, you know, once even getting something into Boost, you know, you have to go through the formal review process there. And, and at least one contributor, I know, you know, has described that, described that as painful.

[02:35:23] **DAVE ABRAHAMS:** David. Um, you know, I guess his library went through a few separate reviews because it was, [02:35:30] it was sent back, it was rejected at first. Um, and then, you know, you go through the, the sort of the same process with higher stakes with the committee. Um, you know, that's a lot. Uh, so, so there may have been, and also also standards are coming out more frequently now, so there's, [02:36:00] there's nothing like, you know, this library's been out there for, for six years, you know, in service and now, and, and so it's proven itself so we can accept it, right.

[02:36:14] **DAVE ABRAHAMS:** So I, I imagine it's, it's harder to get in and, uh, and I think, uh, like the, the libraries that were accepted were more fundamental. So, um, [02:36:30] so there's all of that. Um, I think, I think there are several individuals who, who, uh, have, have increased that increased the politicization of the process. Um, uh, but I mean, there, there are all kinds of, there are all kinds of factors there.

[02:36:53] **DAVE ABRAHAMS:** There has been a, a, uh. [02:37:00] A, there a string of, uh, sort of sexual misconduct problems that have happened around the C++ community, uh, in various conferences and, and, and from C++ committee members. That's one. You know, that's just one aspect to, to, uh, to the problem. Um, you know, [02:37:30] uh, and hey, I, I wish, you know, I, I couldn't, I, I can't give you more specific examples.

[02:37:42] **DAVE ABRAHAMS:** I've been away from it for too long, you know? No, it, there, there wasn't really, um, uh, what I had done was, I, I, I don't, I don't think Beman was, was taking responsibility for almost anything at [02:38:00] that point, I think. And he, and he, that may have been something he negotiated, you know, talked to me about or, or whatever.

[02:38:07] **DAVE ABRAHAMS:** I'm, I'm like, I don't say that with any blame. I'm just sort of trying to remember where it, where things were, because I, I know before I, I pulled back, I tried to set up a board to, to help govern Boost going forward. And ultimately, I, I think, [02:38:30] I think that was a failure. And as part of the reason that, that the governance of Boost changed recently, um, uh, uh, I have to say the, unfortunately the last memory I have of is from our, our one, the one negative interaction that, that, that, you know.

[02:38:58] **DAVE ABRAHAMS:** And,[02:39:00] 

[02:39:02] **DAVE ABRAHAMS:** and I, my memory's not great ally, that that didn't, that didn't define our relationship. So I didn't, I didn't think of that as like breaking our relationship or anything. Um, but, but it's the last, the last thing that I can remember. And unfortunately it sticks with me. And it's not, it's not how I'd like to remember, remember him because he, [02:39:30] he made, uh, such a, uh, difference in my life.

[02:39:34] **DAVE ABRAHAMS:** And he was such a sweetheart overall, you know? And, uh, yeah, we loved him. Um, so, 

[02:39:44] **RAY NOWOSIELSKI:** um, I'd be remiss in storytelling about Ash. What was that? 

[02:39:48] **DAVE ABRAHAMS:** Oh, it was, I, I was presenting some, some idea for a built system at Boost. And, and he kind of, it, he was, [02:40:00] he was very challenging from the audience. Uh, and then, then we talked afterwards and, and he just, he just wouldn't back down.

[02:40:09] **DAVE ABRAHAMS:** And it was, it was not, it was not very beman like it was, it was very, you know, very unlike what I would normally expect from him. And, and, you know, Beman, uh, I think, I think, um, even had an aspect of the Nons suffering fools thing also. [02:40:30] Um, and, uh, but, but he was very good at, at managing it. And I think maybe, you know, just with me, 'cause I, 'cause we were so familiar, you know, uh, he failed that moment.

[02:40:46] **DAVE ABRAHAMS:** I don't know. Did you, did you hear in advance or did you have inkling 

[02:40:51] **DAVE ABRAHAMS:** that, um, asked? No.

[02:40:58] **DAVE ABRAHAMS:** I might have heard from his wife [02:41:00] Sanda. I don't, I think that's, I think that's probably, that, that's probably what would've happened. I mean, we were, we were quite close to the point where when, you know, when Beman had cancer, he got cancer in New York and, and he needed some support, um, he called me to come and I came down from Boston to, to be with him and son and help them get [02:41:30] through a little phase.

[02:41:31] **DAVE ABRAHAMS:** And, you know, that was something they always, they always remembered. And, um, well, yeah. Um, so, so it was very sudden it surprised Soda and I think, uh, I don't think he was sick or anything. I believe I called her. Um, well, I mean the people who were running the Boost Foundation or somebody, the person who [02:42:00] was running it, uh, actually, I'm not sure.

[02:42:02] **DAVE ABRAHAMS:** I think, uh, the, the foundation was trying to, we wanted to own the domain name boost.org, which BI had had owned and, um, you know, boost, like this totally informal thing. It's not that he owned it because he wanted to keep it or anything. It was just like somebody had to set up [02:42:30] a domain. He did, you know, like remember Boost wasn't a thing, um, wasn't a, a legal entity.

[02:42:38] **DAVE ABRAHAMS:** So, so, and, and I, I guess I was asked to talk to soa, I believe. I think this is how we got, he got to me talking to soa. So. So I called saa and, and she said, [02:43:00] oh, I'm, I'm glad you called. I've just been about to finalize this, I think finalize this, uh, arrangement with, you know, these other folks from the, that have, have been trying to, uh, have been trying to buy this, this domain from me.

[02:43:24] **DAVE ABRAHAMS:** And I told them, I don't want any money, you know, I just want it to be in the right place. And, [02:43:30] and they wanted to, I, my memory is so poor, but what I think I remember, she said they, they wanted really insisted on wanting to try to pay me and there were lawyers and whatever. And it was, it was getting complicated.

[02:43:46] **DAVE ABRAHAMS:** And, and this was a big surprise. So, so who is trying to buy the Boost domain out from under the, [02:44:00] the Boost Software Foundation? Well, and it's people associated with the C++ Alliance. And you know, the stories I heard, so I, like I I said, aside from having a poor memory, I don't wanna speak about, about things I have no firsthand knowledge of, but the stories I heard of about the interactions between, between the Boost Software Foundation and, and [02:44:30] people associated with the Alliance were not good.

[02:44:33] **DAVE ABRAHAMS:** Um, and, uh, you know, of course I was talking to the Boost Software Foundation people, um,

[02:44:43] **DAVE ABRAHAMS:** but it all, you know, and it seemed very traumatic to them. And, and, uh, you know. Boost Software Foundation was the official governing body for, for Boost. So regardless, nobody else should [02:45:00] be trying to buy the domain, especially not with, without negotiating it with the Boost Software Foundation. Right. That, to me, that just is, is wrong.

[02:45:10] **DAVE ABRAHAMS:** Like it stuff should be above board. Um, you know, so I, I told saa, you know, please don't do this. I think, yeah, I think you should give it to the, to the, the Software foundation. And, and [02:45:30] uh, that was the, that was the first time I was really alerted to the, to the kind of conflicts that were, that were happening there.

[02:45:39] **DAVE ABRAHAMS:** And, you know, my my understanding is that like things like, like things like that should have been taken care of a long time ago. And so from my point of view, that was, you know, the fact that it hadn't been [02:46:00] is a failure on the part of the Boost Software Foundation. And my, my understanding is there are other ways in which it failed to manage Boost as well as possible.

[02:46:16] **DAVE ABRAHAMS:** Um, now Boost Software Foundation is all volunteers, no one's paid. Uh, the C++ Alliance, as I understand, is funded by one very wealthy individual [02:46:30] and, and pays a lot of people and therefore can with those resources, do management for Boost stuff that, that the Boost Software Foundation will have a harder time doing.

[02:46:45] **DAVE ABRAHAMS:** You know, people, people with real lives who aren't being paid sometimes, you know, don't. Don't get the things done that they say they're gonna get done. And so, so I, so the community, as I [02:47:00] gather, voted to transfer governance to the, to the alliance or to some entity associated with the, the Alliance. Um, and, uh, you know, this, you know, whether this changes the nature of Boost, I don't know.

[02:47:17] **DAVE ABRAHAMS:** It's something I certainly worry about. I certainly worry about boost in the hands of an organization that would try to go around the official governing body to, to [02:47:30] acquire the domain. Um, the other stories I've heard concern me, but they're secondhand stories of which I only know half the, half the picture.

[02:47:41] **DAVE ABRAHAMS:** RAY NOWOSIELSKI

[02:47:41] **DAVE ABRAHAMS:** B r y c e L e l bach said Boost had its day and now its over. 

[02:47:49] **DAVE ABRAHAMS:** D A V E A B R A H A M S

[02:47:53] **DAVE ABRAHAMS:** There, there are vast domains of-- there are no libraries to surface, [02:48:00] right? I, you know, at least know open source libraries for sure. New libraries are invented all the time. This is just like a normal part of, uh, a normal part of, um, the evolution of the software ecosystem in the world. Um, the pro, the idea that the idea that all problems have been solved, like we know how to address them in the best way with programs is, [02:48:30] I, I, I'm sure, I'm sure, I'm sure Bryce didn't mean that.

[02:48:36] **DAVE ABRAHAMS:** Uh, I, I believe like, to an extent is probably

[02:48:42] **DAVE ABRAHAMS:** like, you know, I would say by the same token, C++ has run its force. Um, I mean in, from my point of view, it, it has become,

[02:48:58] **DAVE ABRAHAMS:** it has become. [02:49:00] Complex and difficult to, to the point of impracticality, to, you know, to, and, and you know, it was, it was already too much like that in, in 98, and it's only gotten bigger. The, the standard is now thousands of pages long. Um, nobody can, nobody can absorb that or even come [02:49:30] close, right? Um, so, and, and to program and effectively C++ in C++, you have to be an expert.

[02:49:39] **DAVE ABRAHAMS:** So that's just not, that's not a recipe for empowering programs from my point of view. Uh, C++. So why is C++ so com complex and, and difficult? A lot of it is that it's encumbered [02:50:00] by its legacy. One of the brilliant things about C++, right from the beginning was that it started in C and it retained compatibility.

[02:50:09] **DAVE ABRAHAMS:** That was a, that was an absolute genius move on Bjarne's part in the beginning. Now, C++ is carrying all of the, all of the old parts as well as the new parts into the future. And the, you know, the committee can't agree on any [02:50:30] principles that would've let it jettison old things or, or, you know, make, make old code not compile with the new compiler in any way.

[02:50:43] **DAVE ABRAHAMS:** Um, so right, I I talked about how I didn't think the, the committee was functionally able to make the decisions that were necessary for C++ in the future. Um, and you know, by the same token. Boost carries a lot of [02:51:00] legacy, and, and I'm sure somebody has already told you about the Beman project, right?

[02:51:07] **DAVE ABRAHAMS:** Um, the Beman project, the way I, the, the short capsule form is, uh, uh, boost 2.0 without the, you know, trying to avoid the, the dependency problems. So, so it's a bunch of, it's a bunch of [02:51:30] individual libraries intended to be targeted for standardization and based on the very latest C++ standard, so that they don't carry a huge, you know, mess of code that's designed to deal with, with, you know, the, the problems that are, that are easily avoided now.

[02:51:56] **DAVE ABRAHAMS:** Well, I, I think in part, [02:52:00] oh, I think, I think it, it had already started because of that, because of what you, you said was the Achilles heel. I, I don't, uh, I think it, it's the thing that, uh, you know, Achilles heel implies a fatal flaw, right? Boost isn't dead. Um, but it, but it really does put a lot of drag on adoption for a lot of people.[02:52:30] 

[02:52:30] **DAVE ABRAHAMS:** Um, so, okay. Um, and yeah, number of people involved with, with Boost and, and I, I believe that they thought boosted. In fact, I, I believe they thought that Boost never had a focus on, on getting a library standardized, which is. Not true. I, I had to correct their memory on the history or whatever. [02:53:00] Um, uh, but, but clearly by the time the Beman Project was created, um, uh, boost must have lost its focus on libraries for standardization, or they wouldn't have believed that.

[02:53:16] **DAVE ABRAHAMS:** So they wouldn't believe that it, it was never targeted at that. So I think I, I think that, uh, bunch of people wanted to be unencumbered by that stuff, and they wanted to focus [02:53:30] on libraries for standardization and, and use modern C++ techniques to do it. And then the whole, uh, the whole governance change happened and many of the people that had been putting their volunteer blood, sweat and tears into Running Boost were also, you know, associated with Beman.

[02:53:55] **DAVE ABRAHAMS:** And, and this gave them an out, a [02:54:00] way to keep working on C++ libraries. And the, the basic goals of Boost as Beman created, uh, without having to be associated with, um, what's going on in the actual healing boost sphere, I, I tend to, I tend to look at, at what I've done in my profession as relatively unimportant.

[02:54:26] **DAVE ABRAHAMS:** I, I think if I had to do it over again, I would be a [02:54:30] doctor. Um, I, you know, in, in seeing, uh, in, in seeing how, you know, how people operated, taking care of, uh, uh, people I know, like my, my dad and, and I was, I've just been super impressed and like that. That's, that's a, a profession that, that matters, right? [02:55:00] Um, yeah.

[02:55:01] **DAVE ABRAHAMS:** Uh, I've empowered some people to make software and that's great. Um, Johnny Cash, you know, I, I, I do tend to value, uh, value art, I guess, in a way that I, that I don't value, uh, technical work, um, anymore. But,

[02:55:28] **DAVE ABRAHAMS:** but what are the lessons [02:55:30] to, to be learned from Boost that can be useful for a general audience? Um, it's interesting, you know, I talked to my, talked to my son about, he, he worries about the future a lot. There's a lot of dire forecasts about, about what, what life is gonna be like for, for computer programmers.

[02:55:52] **DAVE ABRAHAMS:** He's a freshman in college at credit and, and just at the beginning of his real [02:56:00] adult life, and, and I, you know, I've been quite successful in my field. I, I tell him, like, I didn't, I didn't get successful by trying to be successful. I went to, you know, I, I went after the things that I, that fascinated me.

[02:56:20] **DAVE ABRAHAMS:** And, you know, I think Boost was another one of those, was one of those labors of love that, you know, it, it eventually I [02:56:30] did spin it off into, into the consulting business and, and you know, it's a laurel that has helped me get, that has helped me get jobs since. Sure. But, but it came out of, uh, you know, wanting to do something I was interested in.

[02:56:50] **DAVE ABRAHAMS:** And I think that's. I think that's an important, uh, that's an important part. I did notice somebody trying to get a [02:57:00] library into Booth because they, because they thought it would make their career better. And, and that really stuck out like a sore thumb. Um, you know, uh, uh, but I think like some of the, some of the basic, the principles that, that we ran boost on, I still ring true for me, that the idea that you [02:57:30] can, you can't actually accomplish things by consensus.

[02:57:34] **DAVE ABRAHAMS:** That, that, you know, open discussion and respect, uh, uh, it's not a general audience thing maybe, but, but, you know, libraries, uh, libraries are a powerful enabler for people to build, to build useful things. And I, I guess this, you know, this might be of some interest, you know, [02:58:00] libraries are infrastructure, right?

[02:58:02] **DAVE ABRAHAMS:** They're, they're not anybody's product. Almost nobody makes money selling libraries, right? And that means, that means inside of companies there's, there's, there's no direct financial incentive to spend time building libraries. Even though some companies like absolutely [02:58:30] depend on libraries, even libraries that they develop internally.

[02:58:33] **DAVE ABRAHAMS:** Like, you know, for example, Adobe, where I work, you know, we have, we have libraries for imaging because we use imaging in lots of our, our applications, right? Lots of what we build has to do with, with creating visual media. Um. So, so who gets paid to make this, this piece? It's not, it isn't the next, the next feature of Photoshop.

[02:58:59] **DAVE ABRAHAMS:** [02:59:00] Right? And, and the, somehow,

[02:59:10] **DAVE ABRAHAMS:** somehow the business world doesn't, doesn't appreciate the importance of spending money on infrastructure. We see it over and over again that the, that, you know, not just in my company, across the industry, the next feature is, is the thing [02:59:30] that everybody's chasing and, and there's no investment in maintaining the quality of the code.

[02:59:39] **DAVE ABRAHAMS:** You know, creating the parts that will, that will let us develop more things faster in the future. You know, which require us to invest engineering time today that doesn't, that doesn't produce an immediate result, but next year then we'll be able to make three features, [03:00:00] right? Instead of one That kind of, that kind of investment doesn't happen.

[03:00:04] **DAVE ABRAHAMS:** And, and uh, you know, boost in part was successful because people did it as volunteers outside of their work. And then Boost got used in lots of commercial settings. So part of the reason that part of my consulting business was, well, I mean, the consulting business was, was great when I was, when I was actually doing consulting.

[03:00:28] **DAVE ABRAHAMS:** I loved that [03:00:30] because I loved working with people in person. Um, and, you know, ideas spark and you can really, you can really see people's minds working in their faces and, and, um, yeah, I love doing that. And so, so when I was doing consulting on site, that was, that was very rewarding and especially. A lot of my business was teaching.

[03:00:53] **DAVE ABRAHAMS:** Um, that was, that was very rewarding. But after, after 10 years of doing it, [03:01:00] one thing I, I realized that, um, that was only a fraction of the time I was spending working in. And a lot of the time I was, I was by myself and only interacting with people online. Um, and that's part of the reason that I wanted to quit doing a consulting business and, and get a job, you know, and why I went to Apple.

[03:01:24] **DAVE ABRAHAMS:** And that was, you know, it was actually, it was great to go into the office every day and have a, a [03:01:30] team of people, you know, that I, that I was working on the same project with and, you know, could consult with. Um, yeah. So for me, the in-person thing is, is super valuable. I, I don't like doing the online meetings that are part, part of everyday life now.

[03:01:51] **DAVE ABRAHAMS:** Um, standing in my business.
