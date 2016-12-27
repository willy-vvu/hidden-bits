---
title:  "A Better Editor, Part 2"
date:   2016-12-26
author: willy-vvu
---

Merry Christmas! 🎄❄️

*This post will be about scattered design decisions that I made while pursuing the [aforementioned editor](/hidden-bits/2016/12/18/a-better-editor.html).*

### Scratch and Keyboards

<img alt="A screenshot of Scratch" src="/hidden-bits/assets/16-12-26-scratch.png" width="348"/>

Growing up, the [Scratch programming language](https://scratch.mit.edu/projects/editor/) (pictured above) was [my jam](https://scratch.mit.edu/projects/83958956/#editor). I would spend hours dragging blocks around to compose programs that would make onscreen sprites interact, in various small games.

Many of the features about Scratch I loved, and still do - how all the available blocks were laid out on the side, inviting play like a turned-over toybox, how every block could be run immediately with its effect visible (no compilation needed), how blocks would snap together by their visual shape (can't even make a syntax error if you tried!). I had a wonderful time *playing* in Scratch, and looking back, I've adopted many of these design values as my own.

Unfortunately, as project size and complexity grew, my mouse hand got more and more strained. Performance and screen size limitations aside, I would literally tire from dragging blocks back and forth using the mouse - long before the attention capacity of my brain faded. As my expressive capacity outgrew the constraints of Scratch, I moved on. Code, like language, is mostly symbolic. It turns out, the keyboard is a decent interface for symbolic input. A few millimeters : one keypress : one character.

That's why I've focused on the keyboard for this new editor. Keyboard keys help you whiz around the code and restructure like, well, a whiz. To ease the transition from traditional text editing, keys such as Backspace and Enter do pretty much what you'd expect. However, as manually inserting whitespace becomes irrelevant, the functions of Tab and Space can be reassigned to more useful, higher-level tree operations.

### Meta Prototyping

I'll admit it: look under the hood of the current prototype editor and you'll find it's full of cotton, springs, and spaghetti, but hey -- isn't that what rapid prototyping is all about? It barely works, but at least I hope it's good enough to make...

<img alt="The Birth of a New Editor" src="/hidden-bits/assets/16-12-26-meta.png" width="1278"/>

...a rapid prototype of the next version of the editor! The image's left side shows a snippet of source, which is run on the right.

Unfortunately, because the editor is written in JavaScript and edits Scheme, it isn't a "meta-editor" - it can't edit itself. But I hope that this property holds for future editors. If I keep going, creating prototypes that create prototypes -- that'd be meta prototyping! It almost seems like a chicken and egg problem, like a [programming language written in itself](https://en.wikipedia.org/wiki/Bootstrapping_\(compilers\)).

### Code as a Physical Object

It'll be a challenge to keep up the steam for rapid-prototyping editors. If I'm to create, say, an editor every week, I can't afford to create a large codebase on each editor. Thus, I'll actively need to think about how to squeeze every bit of functionality out of the code that I write.

I've heard stories from the days of old, when computer systems used to have kilobytes of memory, not gigabytes. Decisions about which software features to include where limited by the computer's memory, as extraneous code would simply not fit.

Compare this to modern software, many of which suffer from a phenomenon known as "software bloat". Adding new features is practically painless with a decent project: just a few more lines of code here, another file there. Update after update, onscreen menus acquire item after item in a steady trickle. The marketing team and userbase are all over it: "New Version: over ### new features!" Other features go unnoticed, buried behind the oversized/extra menus that grew to accommodate them, or tucked away deep into a mile-high settings pane. It is often later in the software that, the long-term repercussions become clear: massive program sizes, snail-slow performance and load times, strange bugs and crashes. What was once a lean codebase has now turned into behemoth bogged down by it's own filth.

Compare this to, say, a physical product. When was the last time you heard "New and improved hammer, now has a [built-in screwdriver](http://imgur.com/0K1JgLf)!" The constraints of the physical marry every function to a corresponding form. Thus, extra functionality---no longer an abstract concept---may detract from the overall aesthetics and usability of an object.
