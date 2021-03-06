---
title: Giving Windows a Chance
description: Why I’m about to attempt to use Windows seriously
date: '2016-12-24T06:48:24.845Z'
categories: []
keywords: []
slug: /@searls/giving-windows-a-chance-39f4d7f1b93c
---

I bought a Surface Pro 4 tonight. Over the next week I’m going to share my notes on getting used to it. And over the next month I’m going to attempt to do all of my open source work from it. but tonight, I want to first comment on the state of the Mac and PC so that I can get my own initial perspective and biases on the table.

Subsequent posts in this series include: [this](https://medium.com/@searls/registering-a-microsoft-surface-pro-4-17c05d6d2e7a#.rpnvcipn6) and [this](https://medium.com/@searls/warm-takes-on-microsofts-surface-pro-4-580f77634d2c#.ceo1tibrz).

#### I’m a Mac

Like many other “open source” developers, I used DOS and Windows throughout the 90s, then toyed with (but failed to successfully adopt) desktop Linux, before ultimately switching to Mac OS X. I bought my first Mac, an iBook G4, in the summer of 2004 — and I’ve never looked back. Well, until tonight, I guess.

Something about the “look and feel” of OS X has always been able to deceive my brain into believing I was interacting with _real_ windows and knobs and sliders as opposed to consciously clicking on crude geometric shapes. Whenever I found myself using Windows (which I had to do daily at work for the next five or six years) it was a stark reminder of how even one point of friction could dispel any illusion that the computer’s graphical interface represented real objects. This sort of friction could be found everywhere in Windows: its choppy frame rate, lack of transition animations, inconsistent shading, jarringly-instantaneous scrolling, unnatural mouse cursor acceleration, and seconds-long click delays.

Whenever I encountered that friction, I was sucked immediately out of productive flow and subsequently sidetracked into a rabbit hole of obsessive customization and configuration to attempt to ameliorate the issue.

#### The Windows comeback

“But that was the old Windows! It got better!” is a refrain I’ve been hearing more and more as Satya Nadela’s masterful turnaround of the mess Ballmer made starts to yield fruit. Friends of mine now work for Microsoft on open source, building support for languages that were verboten among the Microsoft faithful just a few years ago. Microsoft’s focus on services over platform dominance has given them the flexibility — perhaps even the imperative — to embrace outside software communities. This has earned them tremendous goodwill among many software developers.

But is it enough goodwill to convince developers to start working in Windows? That depends, in part, on two things: the degree of a developer’s mastery of Unix and the extent to which Microsoft succeeds in integrating a Linux subsystem into the broader Windows experience.

If the Mac’s convincing and coherent graphical interface drew developer flies to honey, then its certified Unix underpinnings served as the Venus flytrap. 10 years ago I could consider moving back to Windows, but only because I didn’t yet understand or appreciate how powerful the Unix toolchain is for facilitating software development. “Windows is an operating system for using applications, Unix is an operating system for _writing_ them,” some would say. Mac OS X had emerged as a superb contender on both fronts, simultaneously cutting off any inroads that desktop Linux was making while so delighting users as to capture virtually all of the industry’s profit in hardware sales.

It may seem counterintuitive that Microsoft’s throwing in of the towel on its decades-old strategy of platform dominance would suddenly increase interest in adoption of said platform, but the aforementioned goodwill is palpable. A lot of developers, apparently frustrated with Apple’s tight control of its ecosystem, have been eyeing the progress of Bash for Windows as a logical jumping-on point to give Windows a chance.

#### …and then Apple unveiled the Late-2016 MacBook Pro

The Apple keynote that unveiled the new MacBook Pro was a clarifying event for me. It reminded me that many of today’s developers got on board with Apple for the same reason I used Windows throughout the 90s: its dominance made it the default choice. Whatever a 2016 developer’s reason for using a Mac might be, it’s no longer assured that they do so because they first bought into Apple’s design philosophy.

The backlash following the unveiling was bewildering to the Apple faithful bloggerati. _These new MacBooks are better in every way than their predecessors_, they thought, _why would people threaten to jump ship?_ Perhaps it was because these ship-jumpers didn’t previously realize where the ship was heading. Most developers using Macs today have only ever owned one of them, and the 2016 model provided them a second data point from which to draw a line, thereby revealing the difference between Apple’s and their own priorities as they extrapolated forward.

Suddenly, a new generation of Mac users were outraged that Apple was factoring weight and size into the trade offs driving the design of their portable computers. A thousand tweetstorms were born on the assumption that the word “Pro” implied maximum theoretical computing power at all costs. Oh, and speaking of costs, it was too expensive for these “pros” to afford, as well. If this was the laptop of the future, its 16GB maximum RAM indicated it had failed… yet it was simultaneously insufficiently reverent of the past, sporting only USB-C ports.

This garbled, confused counter-messaging came courtesy of a diverse group of users who got on board with the Mac mostly because it had been the default, mainstream choice. As a result, that they represented a messy, discordant cacophony of viewpoints should come as no surprise. In fact, it should remind us of the dilemma Microsoft faced in the early 2000s as their Windows XP hegemony peaked. There was nowhere left to go but down, and the price Microsoft had paid in the form of extreme configurability and corporate control had sapped the platform of any freedom of strategic (much less tasteful) movement. Apple may not have achieved the same market monopoly Microsoft did, but they’ve effectively backed themselves into the same corner by thoroughly dominating the market of “people willing to pay a premium for a computer they will enjoy.”

#### Intentional (read: old) Mac users

The circumstances by which I switched to the Mac couldn’t have been more different. Apple was a scrappy underdog by nearly every measure. I decided to dive headfirst into their ecosystem after realizing how much less friction I would encounter if I simply relied exclusively on Apple's devices, services, and even their much-derided “stock” apps. (That’s right, I use Reminders, Mail, and Calendar, and it saves me a ton of time to do so.)

Where others bristle at Apple’s assertion of control, I find the constraints it places on me to be liberating. I used to buy devices only for the thrill of exploring all of the ways I could configure them. But I slowly became aware of the paradox of choice I'd surrounded myself with, realizing I was paying an ongoing customization tax, and that it was enough to severely diminish my productivity. Working within a thoughtfully constrained system — even if it required I acquiesce to someone else’s opinions — has helped me to focus my mental energy on the problem I’m actually trying to solve.

This was a humbling, multi-year transformation I went through, and I now see it was foolish to assume most other Mac users had gone through it as well.

To illustrate the effects this mindset-shift can have, consider hardware design. Many developers mock Apple’s love of thinness when it comes at the expense of maxing out a device’s technical specifications, but I’ve always found Apple’s hardware design to be calmingly consistent. I imagine Apple hardware design starts with a Platonic form residing primarily in the mind of Jony Ive. Suppose that the form of the ideal MacBook:

*   Is a 1mm thin piece of continuous aluminum that happens to crease at the halfway point
*   Has a battery that lasts for days on end and charges wirelessly
*   Has a trackpad and keyboard that — despite being impossibly thin — give one’s finger tips the _sensation_ of luxurious, clicky travel
*   Has a processor fast enough and memory ample enough for the spinning beachball animation to be safely deleted from the operating system (iOS never needed one)
*   Has a display that reproduces images as clearly as looking through a window
*   Weighs just enough to avoid floating off your desk and escaping earth’s gravity

I suspect Apple starts  there: with a perfect, unattainable design in mind. Everything that comes next is a painful trade off or unavoidable affordance deemed necessary to ship any product at all. Every Mac has been a reflection of the technical constraints of the day, but never so crudely as to be wholly defined by them. (Apple’s famous marketing then does its best to vault its products back into that Platonic heaven, starting with the the product photos backed by a pristine white background.)

But the average person, living on earth, reasonably evaluates the final physical products for what they are: compromised. They expect every component to feature best-in-class tech specs. They expect a price that matches the lowest-cost vendor. They expect everything familiar to them to be preserved in perpetuity. They expect to be wowed by surprising, innovative features.

Both Apple and its presently-disgruntled users think that they’re imagining the perfect computer, but they clearly go about it very differently. Where Apple starts at the ideal form and compromises down, its users look at the compromised form and appeal each of those compromises narrowly, often losing sight of the impact one trade off would have elsewhere.

#### Does Microsoft finally have taste?

So that’s a little bit about my experience living in Apple hardware for 12 years. My impression of Microsoft’s nascent consumer-facing industrial design is that it’s earnest. They’re hungry to find differentiating features to brag about, but also less concerned about the bulk and seams those features will require. But that’s about the extent of my thoughts so far. Before tonight I didn’t really know a Surface from a Surface Book. I wasn’t totally sure that Windows RT wasn’t still a thing (I was worried I might accidentally walk out the door with an ARM processor).

Like I mentioned, a lot of my developer friends have recently started singing Windows’ praises, but — in light of the discussion above about the Mac’s primacy among developers — I can’t be too sure that they were ever the sort of True Believer in the Mac that I apparently am.

Truth is, lately I’ve noticed something I’m not proud of: whenever I hear about a developer willfully switching to Windows, I struggle to relate to them and make a number of harsh, judgmental assumptions. But those assumptions are unfair, in part because they’re not based on at-all recent experience.

So, out of a profound sense of shame for the lack of empathy I’ve shown for developers who live in Windows-land, I bought my first-ever Microsoft-branded PC: a Surface Pro 4. I’m going to try to use it as much as possible for my open source development for the next month, using as many of Microsoft’s stock apps as I can.

I expect that I’ll walk away from this experience still thinking Windows is a usability nightmare, but I’m open to being convinced that Microsoft’s decade in the wilderness has given them the agility to turn Windows around. I’m going to do my best to document my observations as I go… observations I’m hopeful will not be overly negative.

So stay tuned for a lot of angry tweets as I struggle to get used to Windows! 👌