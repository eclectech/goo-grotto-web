---
layout: post
title: "weekly progress log 5"
date: 2026-07-20 01:00:00 +0000
published: true
---

Hello! I'm really exhausted today because this weekend I participated in a game jam. It was technically meant as a "break" from Goo Grotto, but... of course it was more intense work than this is because it's on a bigger time crunch. Still! Here is what got done.

# racing

- I rebuilt the racing clock. The ticks for the racing slimes used to be mapped directly from the anchor of the actual real-life time, but now the playhead drives itself forward each frame. This wasn't hard to do, and even describing it bores me, but it was necessary to enable some future plans and fix some issues with my racing debugger.
- I built a "director" camera system that enables zooms and slow-motion. I think of the race replays being run by different people: the director, the announcer. The director controls where the camera is and how things LOOK, whereas the announcer finds the dramatic moments and frames what's happening.
- Also, I added a little checkered finish band to the races instead of just a line. It's cute.
- Tried to give circuits a palette, but they ended up ugly. I might be burnt out on the visual work of circuits for a bit.
- I threaded the names of the circuits through the race cycle runner and now instead of "INSERT TRACK NAME HERE" it shows the actual track name, haha.

# slimes

- I made a "expression" system in the slime renderer. There had been some eyes that weren't genetic that I wanted to use solely for the slimes to be able to express their emotions - now they can do that! They can be surprised, dizzy, they can wink, they can "smize", they can be tired. I now use it to show that the winner of any individual race is thrilled!

# boring stuff 

- Hardened password reset and email confirm against race conditions. 

# what's next?

Well, it's a little hard to say right now given how sleepy I am. But I think I'm going to work on the actual wagering next. I have some more race balancing to do for sure as well, but I think it might be time to switch gears and work on my first-user walkthrough and the economy for a while.

I'll be back next week with more changes, and hopefully more energy! Phew!!