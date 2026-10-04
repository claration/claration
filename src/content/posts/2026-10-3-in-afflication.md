---
title: 'In affliction'
pubDate: '2026-10-03'
tags: ["Personal"]
---

This blog is gonna be a bit different than what I would usually write, rather it's something a lot more personal than the others.

It's gonna be a bit of a reflection on who I am and what I worked on, along with some of my experience in working with open source, and other things related to me! Though don't mind the title of this post, I thought it would be a cool name to name something like this x)

## My Open Source Experiences

As you may know I do a lot of open source work! Some small projects, some big, and anything in between. Many of which are related and geared towards a specifically community or space, in particular the iOS-modding or jailbreak scene. This is a scene where I originally came from, and even started by development career.

[**Feather**](https://github.com/claration/feather) – On-device sideloading application. \
This is my first big project directly on my profile, I even asked for stars when I first open-sourced it. That's how excited I was to get something like this out!

This project was mostly made out of spite, it's the first open-source sideloading app of it's kind, which uses raw developer certificates distributed from signing services (or Apple themselves). I worked on it with someone else, who doesn't work on it anymore, but figured out how some of the functionality from Esign (the closed source app I wanted to make an OSS alternative of) worked, we worked on it together and eventually did a first prototype on it installing applications on-device! The project was mostly made for myself at the time, and now it's used by hundreds of thousands of people around the globe!

After a few months of development with Feather, a new signing app similar to it came up called [QuickSign](https://quicksign-team.github.io/) and it was actually open-source before Feather, albiet not that "public" since the link wasn't really shared. Though I managed to find it by just searching some keywords on GitHub. I ended up joining their server to see it's development, and I've shown them that I've been working on my own version and shown clear signs that I've been looking through their open-source code.

I've even recommended them to use GPL-3 for their [plistserver](https://github.com/nekohaxx/plistserver), in which they did! However, a few days later they ended up deciding that they didn't want me looking at their code, and [changing the license of plistserver](https://github.com/QuickSign-Team/plistserver/commit/69c1bcf527926a55f833c707674723591b145838) so they can have the "upper-hand" presumably and not wanting me to use it? Though GitHub was a funny feature of just.. Rolling back to a previous commit where this change never happened in the first place, this change was super petty and was obviously done to hinder my development on Feather, which was honestly not really a cool move. While they were doing that, they also closed source their QuickSign app as well. Though, that wasn't under any license so they were in their legal right to do what they want with their project in that regard, but still, it's extremely petty and honestly in my opinion I think it's just something you shouldn't do in the open-source space. Why even be passionate of open-source if you're gonna close source out of spite?

QuickSign has also gotten a lot more popularity that Feather has ever gotten on X/Twitter, which is expected since there were a lot of big names at the time working on it. Though there were a few tweets shitting on Feather (and never once, have I done the same with QuickSign) which was honestly really disrespectful and gave a bad taste in my mouth.

- ["Feather app is kinda mid ngl" - sourceloc](https://x.com/sourceloc/status/1822969577002725685)
- ["feather breaking before 2025 is just bad engineering lmao" - quicksign team](https://x.com/QuickSigniOS/status/1869347016012435736?s=20)


Similar to QuickSign, I've gotten a lot of hate from the people involving [KravaSign](https://www.kravasign.com/), where I've gotten a lot of snarky comments on Feather for "stealing features" and the part where someone close to be reversed engineered their app just so Feather could support importing from [Esigns repositories](https://github.com/claration/feather/blob/main/AltSourceKit/Sources/AltSourceKit/Utilities/Key/EsignSourceKey.swift#L1-L433) (this is a extremely dumb feature that had to be implemented just so people can migrate to this app).

Even from the hate I have gotten from these people, I did push out Feather and it did get a lot of popularity, which I'm extremely thankful for, and it has gotten me a lot of motivation to work on other things, so thank you to everyone who supported me and this project throughout the few years its been out. I appreciate every one of you who took the effort to contribute and even use it, especially [Nyasami](https://github.com/Nyasami) (though I met them from them violating Feather's license funnily enough).

What's next for Feather is really unknown, and recently some functionality broke due to the revocation of the SSL certificates it's relied on.

[**Impactor**](https://github.com/claration/impactor) – Cross-platform sideloading application. \
This app is neat in a sense where it was the first truly cross-platform sideloading app, supporting Linux, macOS, and Windows. Written in Rust (oblitigory though not really mention), and since its in this language its very portable across these platforms, and has very good version support in general. However, there's a lot of downsides to maintaining something like this, but this is more geared towards specifically me than really anyone else.

One of the downsides is that it's written in a language that I'm fairly new in, it's only written in this language because conveniently there's a lot of libraries (which extremely surprised me at the beginning) that was needed for this project to even work. The library to communicate with iOS devices ([idevice](https://github.com/jkcoxson/idevice)) especially, though along with many others that were conveniently on crates.io, like the macOS codesigner replica and a library which communicates with Apples GSA services.

This language takes a new approach to its memory model compared to others, I've struggled a lot to understand a lot of concepts established within the language since its so vastly different than things like C or Swift. Though, the build system and package management is really lovely and I've been very happy working with it, it's genuinely so easy to use that it puts a lot of others in shame.. At least in my own opinion! I often don't work on Impactor due to its reliance on 1,000+ dependencies depending on the platform, which heavily made me consider rewriting it in another language, but the benefit to this is very miniscule for me and a lot of other people. And there's gonna be a lot less things to work with, like open-source signing libraries that actually do what I ask for & such.

I also don't like how the language looks or even functions in a GUI context, it's really ugly and every time I look at it it makes me just wanna go back to my other projects. Sometimes I regret using rust, I could've been using Qt or something else.

Similar to Feather, there was another cross-platform signing application being worked on where I was basically competing with called [iLoader](https://github.com/nab138/iloader). There was different goals in mind on what I wanted Impactor to be compared to what they wanted iloader to be, even though they essentially provided the same functionality and goals, which is just to sideload an app on your phone.

- Impactor is supposed to be an open-source [Sideloadly](https://sideloadly.io) alterative, which would provide features like customization and tweak injection to the app, along with providing basic utilities like sending pairing-files to the phone and macOS (Apple Silicon) sideloading.
- iLoader is or was supposed to be a cross-platform [AltServer](https://github.com/rileytestut/AltServer-Windows) alternative, which really does one thing and one thing only, properly install AltStore/SideStore on the device.

Even though Impactor could do the same thing as iLoader but with more features such as automatic resigning over-the-air and tweak injection, evidentally it didn't match the popularity iLoader was because Impactor was never recommended in SideStore's install guide, and didn't provide convenience of automatically downloading SideStore, which was never the point of Impactor. Which is too bad I guess.

---

A lot of these projects are again in the iOS-modding/jailbreaking space, and eventually I want to completely move away. There's a lot of people I appreciate and adore from this scene, regardless of all the bad experiences, but I want to mostly move away for a couple of different reasons. All these projects are basically in their own bubble, barely anyone contributes, and the ones that do contribute are already well established in their work, which is very little people. There's a lot of knowledge in this space but it's so condensed in so little people that it just makes it not fun to be in, I want to one day make an open-source project that everyone would be able to contribute to, no-matter the skill or entry level, for everyone, and not something that's niche towards a specific community. I've wanted to make something like this for quite awhile now, but when everything else is so established already it's hard making something new that people would like. None of the things I make are unique, never have been, they've always been inspired and ideas essentially taken from other people, but just in my own unique way.

I've had a lot of stress when it came to developing both Feather and Impactor due to competition. Both had an amazing start and I appreciate everyone who even uses Impactor and contributed because of it. Both Feather and Impactor had rough development, and will probably continue to be that way for quite awhile, I'm not a good developer or programmer, even though I like to think otherwise with the current skills that I have.

There's many times throughout the development process where I often think that I shouldn't be working on this, and struggle with the idea of making it just for my own sake, when I know many people will be using them.

## Being My Own Idol

To me this is a fairly new subject that I will be talking about, but have you ever looked up to someone so much to where you really wanted to be like them?

There's a lot of things I want to be, I've always wanted to do renders and even music, but with my current situation right now it's not really that applicable to completely go off rails and learn a completely new thing, I want to become my own person that I want people to look up to, and appreciate for the things that I make for people and myself. I also wanna go traveling, go to other places in the world to meet so many people, I really wish I was able to do these things without needing to worry about anything, but I can stay hopeful for the future.

## My Social Presence

I've always wanted to post on social media but I don't exactly have the mindset to be constantly posting on there. And I wouldn't really know what I would want to post, maybe niche tech subjects or facts, or criticizing things like a big tech companies decisions, I don't exactly know.

## In affliction

There's a lot here that I didn't talk about, that I may talk about in the future, but for now this is all I'm going to say about myself and the things I've been dealing with. Eventually I want to talk about a lot of the people I'm friends with and say how much I appreciate them, but maybe for another blog post :) you know who you are if you're reading this.

ALSO! A lot of this blog isn't co-herent!!!!
