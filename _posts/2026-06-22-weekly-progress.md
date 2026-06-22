---
layout: post
title: "weekly progress log"
date: 2026-06-22 14:00:00 +0000
---

I think I want to try and make a habit of posting a progress log every Monday to keep me motivated and organized. The days can blend together out here, so it's nice to have a rhythm to return to. 

I also want to lay out my intentions for the week, or at least some of the backlog I'm selecting from.

With all that: here's my progress update for the last week! 

# site features
- Created an auth system with invite codes.
- Created the wild slime adoption flow: choose your first slime from three offered slimes.
- Created the slime training regimen. Slimes have three main stats: Brains, Brawn, and Bounce. Their caps are determined genetically, but their real values are determined by GRIT and PERSISTENCE (I also programmed a basic training system).
- Created genetic transparency gene. Some slimes you can see right through now!
- The whole rewrite of the colour system that I posted about [here](/2026/06/18/one-major-aspect-of/). It feels like it's in a good place, FINALLY.
- Worked on the shape system some too. Slimes can have 8 different shape alleles, and some of them blend (although some are genetically incompatible (okay, fine, my drawing algorithm needs more work before I can combine some of them, particularly the bumpy ones, for boring technical reasons)). Still, thirty total shapes isn't that bad!
- Added some eye types as well. Nine of them are inheritable, there are more that are just used as expressions.
- Added a cute "cameo" feature where sometimes one of your slimes will be interested in what you're up to as you're browsing the site. They're curious little guys!
- Added the ability to abandon your slimes to the wild... you monster...

# fixes
- Fixed a bug where the same slime could sometimes be adopted twice or two slimes could be adopted from the same selection by hitting the back button. Adopting slimes (whether wild slimes or from a litter you made by squishing) is now idempotent, atomic, and safe from race conditions.
- Fixed a bug where sometimes the cap on the amount of slimes you could have was not enforced.
- Capped gen-0 slime stats and genetics to make sure that some slime types can only be discovered by squishing.
- Security hardening.

# upcoming this week
This week I am torn! I want to work on what I consider one of my main "hero" features, slime racing, because it seems to be a big part of slime culture. I've read the paper I wanted to read about it - [about boids](https://en.wikipedia.org/wiki/Boids) - and I am excited to get started implementing the things I've learned. However, I think it's a better idea for me to work more on some of the slimes' minor stats and personalities, which will play into the way they race and interact.

I also have a lot of more boring work to do on allowing users to change their profile settings and preferences for things throughout the site, but since I'm raring to go on the fun stuff I think I'll get started there. I also plan on writing a post about the work I did on the shape: how I draw slimes and what makes them unique, and my far, far future plans for the shapes system to better reflect actual slime variety. 

That's everything from Goopiter for this week. Signing off.