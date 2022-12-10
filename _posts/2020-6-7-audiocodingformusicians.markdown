---
layout: post
title: HOW TO GET INTO AUDIO CODING AS A MUSICIAN
date: 2020-6-7 16:01:00
description: Audio coding can be a rewarding field for musicians, and this post gives an overview of the field and how to get started.
---

## What is audio programming?
<br>

A few weeks ago, I gave a short talk for the Sound Recording Technology program at my ~alma mater~ DePaul University which gave an 
overview of the world of audio programming. I had wanted to do this for some time because audio programming
is a fairly niche field, to the point that a lot of capable audio engineers and musicians miss out on careers and opportunities that
they might totally love if they only knew about the possibilities. This post comes from that mini-talk and is meant to be just another
voice to consider for any musically inclined folks who are looking to apply their passion for music in a way that might be less obvious.

Audio programming is a great way to combine one's passions for music and technology. Even though the field is niche, it is still vast and widely
varied. Audio programming skills are needed to design audio effects plugins, music notation software, spatialized audio simulations in video games, noise reduction in conference call software, audio engines for digital pianos, audio implementation for the interior of a high-end car -- any piece of audio 
gear or software that you love was probably designed and written by some other audio nerd. 

While there are many ways to categorize the various disciplines within audio software, I tend to split up the specialties based on the skills
required to get many specific jobs. These three areas -- applications, systems, and DSP -- tend to overlap *significantly*, though they are distinct
in the skills required and day-to-day work that would be involved if you got a job with one of them in the title. (Though of course, an Audio Systems Engineer
probably knows some DSP, and an Audio DSP Engineer probably knows their low-level audio APIs to an extent, for instance.) Also, many audio companies
such as audio plugin or digital guitar effects pedals developers tend to be small (<10 employees) shops where there may only be one or two developers that are
competent in all three of these areas.

# Applications Focus
<br>

Audio applications engineers generally are the folks who most directly make audio products. They use frameworks/software development kits (SDKs) 
such as JUCE to make DAWs, audio plugins, or standalone audio apps or Wwise to program generative music, spatialized sound effects, or dynamic
vehicle engine sounds in video games. The audience for their work consists of musicians, gamers, and anyone with ears.

This speciality also usually involves a fair amount of GUI (graphical user interface) work, especially in music apps that have cool looking sliders, 
waveform editing tools, or audio visualizations. 

# Systems Focus
<br>

Audio systems engineers generally write software that is not "user facing" in a direct way. For example, these folks might be the developers of JUCE or Wwise;
they write performant and easy-to-use software libraries that runs on many different platforms, and the audience for their work is generally audio
applications developers that will use the systems developers' code to create audio products.

Typically, systems engineers will know a lot about various types of audio hardware and the nuanced considerations they have to make in order to design a system
that audio software can run on. One thing that is cool about this discipline is that audio systems engineers have to dive deeper than anyone else into
the minutae of audio technology: they may have to implement systems to a spec like MIDI 2.0 drivers, an AAC codec, or audio-over-USB drivers, and at that point,
there are no more excuses to hand-wave over the more grizly details of these technologies like you can get away with in most audio engineering disciplines.

# DSP Focus
<br>

Audio digital signal processing (DSP) as a discipline in the current context is all about creating or optimizing audio algorithms that run in audio products. 
DSP is a field of mathematics (spanning much wider than just digital audio signals) rather than a subset of programming. Thus this specialization, compared to the other
two, involves more higher level prototyping in languagess like MATLAB and Python to design innovative and great sounding algos for audio effects like
physical modeling, convolution, dynamics processing, etc. These engineers then port their protoyped DSP algorithms to C or C++ and optimize them to run in real time. 

DSP is generally considered to be an arcane art, and unlike programming, I don't feel qualified to tell you that this isn't the case! Audio DSP is a fascinating
subject and fun for anyone to learn the basics of in order to make their own audio gizmos -- in fact, pretty much any audio software developer is (or probably should be)
"conversant" in audio DSP. But entry level positions in audio DSP are quite rare and may be less flexible when it comes to educational background than other
audio software positions. So if this field interests you, you may be better off going to grad school for it if you want to find a job, unless you are a very 
bright bookworm that can make an impressive portfolio or are looking to employ yourself to make some cool audio plugins.


# Other Music Software Careers
<br>

The above specializations involve a fair amount of programming, usually in C or C++. There are two other technical audio software specializations I'd like to mention
that can be equally as rewarding for musically inclined folks and involve less programming overall than a strictly "audio programming" position.

# Audio Quality Assurance (QA)
<br>

This speciality is meant for audio engineers that are very detail oriented and generally have very solid ears. These engineers do things like:

- Manual test grids where they use DAW or plugin power-user skills to push an audio application to its limits and write up bugs
- "Golden ears" skills to A/B test differences between hardware and emulation software (ie, real LA-2A vs a plugin version) to bless an algorithm as "sonically accurate"
- Automated scripts, usually in Python, that run a battery of tests automatically on an audio codebase to increase confidence in the codebase.

Audio engineers tend to have a lot of the skills required for this role and should use job listings to fill in the gaps and become qualified.

# Virtual Instrument Sound Design
<br>

The name of this position can be a little misleading -- usually, audio engineers looking to get into "sound design" are the folks who record, mix, and master
sound effects and dialogue for games and movies. This role is not that, and the job pool is less overcrowded than a regular "sound design" role. Virtual instrument sound 
designers are responsible for curating and scripting sample based instrument libraries for samplers such as Kontakt; examples of these "sound desgin" companies
are Spitfire, Cinesamples, and Embertone. They use audio engineering skills to record and sort sample libraries (keyboards, string libraries, guitars, etc) 
and then write scripts to control the behavior of these samples when played from a sampler like Kontakt. This can be a very interesting field for musicians
and while it requires scripting knowledge specific to a given sampeler (like Kontakt scripting), the learning curve is a lot lower than real-time audio programming
in a language like C or C++.


### Why get into audio programming?
<br>

Many audio-technology-inclined students don't realize that this is a path they could  pursue because software development has a reputation 
for being a complicated and grueling field with a sharp startup cost. The reason I'm making this post is to let you know that should not 
stop you from checking it out. Becoming an expert is hard, sure (I'm definitely not even close to that yet), but learning how to program 
and make cool audio stuff has never been easier or more accessible.

There are boring but practical considerations for choosing to pursue audio software development as a musically inclined individual. Unlike
many music careers like performance, sound engineering, or lesson teaching, audio software developers get many of the ubiquitous perks that all
software engineers enjoy: full-time, salaried work, with benefits. And if you are willing to move, you will always be able to find a job.
Some people are totally allergic to the whole "9-5 office job" thing, and maybe that's why they got into music in the first place: to be an adventerous
night owl that spends all their time creating art and connecting with an audience. Audio tech jobs are not going to be like that; there is a lot 
less glory, and for some, less satisfaction than playing or producing music. But if you are driven by the quiet satisfaction of making things 
beep and boop, this may be the field for you.

### How to Get Started
<br>

There are a million ways to get into programming, so I'm just going to give my take as someone who pursued a music education and ended up
audio programming full time. First, before anything audio specific, you need to just learn programming in general! It will likely be awhile
before you can apply your skills to anything audio related in a big way (for me it was around 2 years). You may be able to get away with much sooner,
but I'm mentioning that in order to set your expectations. Learning programming is totally doable, but isn't something you should be able to expect
to pull off in a week or even a month.

#### Learn Programming First
<br>
I started off with the Python programming language, using the book "Learn Python the Hard Way". This book was great for people with no prior
programming knowledge because it gets you acquainted with skills that are useful in all programming languages (language constructs as well as
getting comfortable with the command line and writing/running programs). I had the benefit of starting my path while still in my undergrad, so
I was able to take programming classes at no extra cost to my primary education: first taking an intro Python course, then a C++ course, and
then (most importantly) a three-semester project class on writing a video game engine in C++. This was good for me in a "school" context, but I 
mention it because self-driven people can also get similarly useful resources and projects for free online. The fact that I took these classes
didn't help my credentials at all, and it was instead all about content -- so in my opinion, getting a "computer science degree" is not necessary
to get an audio programming job. The main takeaway for me is that school forced me to do the "1000 hour" thing with programming, and writing a 
game engine in particular forced me to solve a lot of problems on my own. This was invaluable, since problem solving and debugging really are 
the main skills needed for developing software that are difficult to teach. 

You'll know you are ready to move on to audio specific stuff when you know enough programming to be "dangerous". Some good litmus tests
are that you got through a book and you can make basic programs with little-to-no looking up language syntax. Think of it like learning an instrument:
at some point, when learning guitar for instance, you don't need to look up chord fingerings to play from a lead sheet. Being "competent" at a
programming language feels similar to this. You will probably always need to look up some stuff, but you won't need to look up comparison operators,
for-loops, function definition syntax, etc. At that point, you will have enough space in your brain to start putting in some in-depth audio software
knowledge.

#### Get Some Direction
<br>
It was also extremely helpful for me to have a "checklist" to guide my studies and keep myself honest. When I started college, I looked at a job
listing for Universal Audio (where I ended up working after graduating) and just noted down all the requirements, using it as a "personal syllabus"
to determine the skills I needed to acquire to be able to work at an audio company. It's easy to get lost at all the forks in the road when learning
programming and forget where you want to go or what you need to learn, so reading through job descriptions and deciding which one sounds like a fun
end goal is a great way to stay on track. I have attached some examples at the bottom of the article -- not all job descriptions are created equal,
but the specific/in-depth ones about which technologies and skills to learn can be very helpful.

#### Do Some Projects
<br>
Once you learn enough programming to be dangerous (as described above), projects are an invaluable way to forward your programming journey,
and that's where you want to get audio-specific. Projects will teach you problem solving and give you an intuitive understanding of *why* 
certain audio-specific rules of thumb exist. There's no better way to learn than the hard way! 

When it comes to learning audio programming, note that resources tend to be few and far between. When you can't find classes or
resources that are audio or music specific, video games are a very relevant substitute (and have a huge community of support in comparison). Many of the
considerations (real-time, low level programming for interactive applications) for video games are directly applicable to audio. In the past few years,
there has been an increase in the area of audio programming resources and evangelization, but it still lags far behind the video game community.

# Some project ideas:
<br>
- Writing audio plugins for all the basic algos, like delay, reverb, EQ, compression, using a framework like JUCE
- Doing a "game jam" (working with a team to make a video game in a short period of time) and implement all the audio functionality for the game
- Build a digital guitar pedal using a Bela kit, or a regular Beaglebone/Raspberry Pi
- Write a game engine and your own audio engine for it using a platform audio API like ALSA or CoreAudio
- Write a WebAudio DSP effect for a webpage or HTML5 based game

# Some Books
<br>

For good measure, here are some books that likely will prove helpful in your journey:
<br>

[Learn Python The Hard Way](https://shop.learncodethehardway.org/)
- Mentioned above as the book I used to start learning programming. Great intro to computer science concepts and getting started as a programmer.


[TheAudioProgrammer](https://theaudioprogrammer.com/blog/)
- Starter resources and community to get a taste for this stuff


[DAFX](https://onlinelibrary.wiley.com/doi/book/10.1002/9781119991298)
- Free PDF available. Cookbook-style for writing audio DSP algorithms


[Pirkle books](https://www.willpirkle.com/about/books/)
- Good for tying together C++ programming and basic DSP skills


[ThinkDSP](https://greenteapress.com/wp/think-dsp/)
- Free DSP book using Python


[Game Engine Architecture](https://www.gameenginebook.com/)
- Great in-depth overview of practical low-level C++ systems skills


[Bela](http://youtube.com/watch?v=aVLRUyPBBJk)
- Lectures on embedded Linux audio systems, using Bela/BeagleBone Black



### In Closing
<br>
Hopefully this article gave you some ideas or insight about what audio software development is like and how to get into it. I think the field can be isolated, and generally
I see music people who are just starting out say they had no idea it was an option, and that's why I wanted to advocate for it. It's not for everyone (either due to computer
chops or interest!) but it is worth consideration if you are technically and musically minded -- you might find a new aspect to your passion!

Feel free to reach out if you have any questions (or suggestions for this article) and Happy Coding!



## Example Job Listings
<br>

As mentioned, here are a few example job descriptions I grabbed from some music companies. They can give an idea of the skills needed for
each discipline of audio software engineering. They aren't perfect or all-inclusive, but it should give you an idea!

# Audio Systems Software Engineer (Native)
<br>

The ideal candidate will have extensive experience with audio programming in C++, DSP, instrument plugins (VST/AU/AAX), cross-platform development, disk streaming, MIDI, UI implementation, and an understanding of current music market conditions and demands.

Desired Qualifications/Experience:

C++ and object-oriented programming

Real-time audio development

DSP and audio effects

JUCE / VST / AU / AAX Frameworks

UI design and implementation

Cross-platform (Win/macOS) development

Knowledge with existing music audio engines (ex. Kontakt, Mach5, Play, fMod etc)

Self-motivated with the ability to work under minimal supervision

Excellent written and communication skills

Ability to be time-effective and handle multiple parts of a project at the same time

Musical background

Required Qualifications:

Bachelor’s degree or equivalent in Computer Science.

Demonstrable experience working in C++.

Experience with any of the following: macOS, iOS or Windows APIs.

Experience working with other programmers under a source code control system such as git or perforce.

Desired Skills:

In-depth knowledge of MIDI, audio and signal processing.

Experience with CoreAudio, Audio Unit, ASIO and VST APIs.

Experience with C++, boost and gtest.

Good understanding of software Design Patterns.

Ability to define, improve and transform software architectures.

Familiarity with automated build systems such as Jenkins or buildbot.

JavaScript, Python and bash scripting.


# Audio Systems Software Engineer (Embedded)
<br>

Responsibilities will include understanding product feature development, systems design, performance tuning, board bring up, and driver development.

 Job Duties 

· Develop and maintain Linux based OS with a low latency kernel, fast boot, and high reliability 

· Develop Yocto recipes to generate firmware images 

· Develop low level bootloader, and microcontroller code 

· Work on hardware security design and implementation 

· Coordinate with manufacturing engineers to assist in build, flash, and test 

· Proactively document all work and write automated tests 

Required Skills & Experience: 

· Rock-solid C or C++ programming, Python shell scripting 

· Linux device driver programming 

· Network programming using TCP/IP, UDP sockets 

· Low level programming of peripherals and interfaces, including experience with a developing for microcontrollers 

· Ability to read hardware schematics at a basic level 

· Experience with digital audio technologies including I2S, S/PDIF, ALSA 

· Music or audio background or interest, with experience with music creation software 

· Linux image building using YOCTO

# Audio DSP Algorithm Engineer
<br>

Required Skills and Experience:
 A passion and interest in music and audio.

 Ability to perform circuit analysis for passive and active systems.

 Awareness of nonlinear models for silicon and magnetic devices.

 Experience with audio signal processing, incl. dynamics, filtering, modulated delays, feedback systems, etc.

 Experience with filter design, sampling theory, and DSP.

 Exposure to state-space and lattice structures, and basic control theory.

 Awareness of iterative solution methods for nonlinear systems.

 Experience with finite word-length artifacts in signal processing.

 Facility working in MATLAB, SciPy, or similar computing environment.

 Experience with C, C++.

 Exposure to coding for DSP processors. SHARC experience preferred.


Principal Duties and Responsibilities:
 Working independently to carry out algorithm design projects based on product specifications.

 Design and implementation of novel signal processing methods and structures for modeling audio circuitry.

 Implementation and integration of algorithms into an existing software framework.

 DSP porting and resource optimization.

 Management of development and test schedules.

 Collaboration with product management, SQA, customer support, and marketing.

# Audio QA Engineer
<br>
(Example from a Universal Audio posting)

Universal Audio is looking for a quality assurance engineer to test UA virtual instruments software from inception through shipping, running numerous tests, recording and tracking bugs and validating fixes. Use your expert knowledge of audio recording to help flesh out the test grid, validate audio workflow and insure that our products ship with the highest quality possible. This position will test hardware/software integration including compatibility with various PC and Mac Operating systems, computer hardware, popular DAWs and plug-in formats.  

Responsibilities 
· Test UA hardware and software and hardware/software integration.  

· Help formulate test plans.  

· Check products against specs and compatibility matrix.  

· Run grid tests to expose errors, write up clear understandable errors and track the progress of fixes.  

· Test product and software workflows and insure product usability.  

· Work closely with engineering, product management, program management and other QA team members.  

· Attend product and QA meetings. 

· Ensure all products adhere to strict UA compatibility standards.  

· Report project status and issues weekly. 

Requirements 

· Excellent understanding of audio workflows.  

· Good working knowledge of DAWs including Protools, Logic and Live.  

· Experience working with bug databases like JIRA.  

· The ability to read and understand product specs.


# Virtual Instrument Sound Designer
<br>

Overall responsibility: Program next-generation sample products for Kontakt engine

Core Requirements:

Familiar with Kontakt 5 scripting

Ideally previous experience with legato programming in Kontakt engine or similar

Ability to take pre-existing scripts and advance them

Ability to edit/manipulate samples

Ability to take feedback and be a part of a team

Previous experience with noise-reduction tools (ex. Izotope RX)

All candidates must have extensive experience with Kontakt and ability to create scripts based on specs. Preferably the candidate also has experience in UI design.

