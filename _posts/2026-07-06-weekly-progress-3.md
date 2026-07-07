---
layout: post
title: "weekly progress log 3"
date: 2026-07-06 01:00:00 +0000
published: true
---

Hiya! No tech post this week because I've been really heads-down.

I did a LOT of work on the site this week. When I was going through my commits I was downright shocked at how much it was... the list itself isn't as long as last week's, but a lot of the individual items are bigger. The racing infrastructure and drama beats were especially time-consuming.

# racing

- Races now runs on a time cycle, with a new race beginning every hour. Users have 20 minutes to enter their slimes in the race, 20 minutes to bet (although betting itself isn't implemented yet because, uh, money isn't implemented yet), and 20 minutes after the race to review results. Users who review results within the last 20 minute period will get an extra little bonus.
- As a result of the timer, races can now accept slimes from multiple people. NPC slimes should almost never appear in races now, because slimes who are idle will join races of their own volition. (Okay, they get recruited to fill slots whether they want to or not.)
- Added two tracks, "speedway" and "hairpin", to help me tune how slime stats affect their racing performance.
- Added a "drama beats" feature to racing. Races now look for exciting moments to highlight! I plan on leveraging this for accessibility and fun later. 
- Reworked the motion of racing. The slimes now move more like jellyfish than cars, and kind of pulse forwards.
- Fixed collision. When slimes collide with each other, they now appropriately transfer momentum based on speed and volume instead of one just bouncing off another.
- Made lots of little "feel" tweaks generally. Racers now have eyes (doesn't help with how much they bonk stuff), there's a little podium ceremony when they finish a race, and instead of abruptly stopping at the finish line they now coast.

# ui/ux work

- Reworked the views for the laboratory and the slime pasture. The slimes no longer just sit around in a big white void.
- I also created a generalized interface for the action of "picking" a slime or multiple slimes. This is used for selecting a slime to participate in a race or squishing right now, but I imagine it'll get used in lots of spots in the future.

# boring stuff

- Since I had to add a queue system for the racing timers anyway, I also ported my transactional email system over to a queue system, so password resets and such are better off.
- The above also surfaced a server error that would happen when someone changed their emails to nonsense, which I fixed.
- Configured my JavaScript linter and security scanner tools. I wrote enough JS that I couldn't justify not having these any more.

# upcoming this week

My focus this week is going to be on polishing the UX and UI further. Now that things are starting to take shape it's clear I need to look through my front-end code so that I can develop it faster instead of digging through my files are they are... I need to create a shared structured design that slots together everywhere in an organized way. Once that's done, I think it'll be good to go through my onboarding. 

As much as I'd like to lean into making the money and inventory system, I think it'd be good if I took this week as a "polishing" week!

That's all for now! Byeeee.