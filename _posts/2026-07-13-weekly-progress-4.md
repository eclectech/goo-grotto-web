---
layout: post
title: "weekly progress log 4"
date: 2026-07-13 01:00:00 +0000
published: true
---

Hello again! Last week I promised myself this would be a "polishing" week where I got my front-end into shape and stayed away from anything too shiny or new. I did the polishing. I also found some shiny new things. Oops.

# the design system

This was the actual planned work, and I'm really happy with it. My CSS had grown into kind of a tangled pile, so I sat down and untangled it.

- Did a design-system pass: collapsed my palette down to a set of standard colours and shapes and gave myself a visual reference for all of them. 
- Tidied up buttons and errors, as well, everything just generally looking more consistent
- Made some navigation more fluid so at least it actaully works on a phone, even if it isn't the best yet
- Added a home empty-state hero (still a WIP) so a brand-new visitor doesn't land on a barren page.

# racing

I said racing wouldn't eat the week buuut... racing ate a good chunk of the week. It's genuinely better now though.

- Slimes are now aware of traffic. They can finally *see* the other slimes around them. They steer around other slimes and pick lanes instead of blindly bonking into whoever's ahead, instead they try to slingshot around them.
- A slime's personality now affects how it acts on the track. Aggressive ones commit harder to corners, cautious ones brake earlier, etc.
- Balancing generally. I built a little harness that measures what each stat is actually *worth* on each track in terms of time, then re-tuned the physics model around it because it showed me that the smarter slimes actually started performing WORSE than the dumber ones. So I changed the cornering grip, implemented late braking, updated wall behaviour, created "towing" behvaiour that allows smart slimes to close gaps.
- Race circuits now live in the database instead of being hardcoded. I can now draw new circuits pretty straightforwardly, but validation is still a little touchy (is that corner too sharp? etc.)

# betting and money

I couldn't resist laying the first stones of the economy.

- Every user now has a kroma wallet (kroma being the site currency). 
- Added a calculating phase to the race cycle: before betting opens, I run som Secret Calculations to determine who is most likely to win, and base the wager odds on that.
- Built a betting board that shows the markets. You can't wager yet since money isn't really real yet, but you'll be able to best on who you think is going to win and who you think is going to finish top 3. 


# boring stuff

- Verified email at signup, and hardened the password/signup paths, general auth hygiene.
- Made it so mail-delivery failures retry instead of silently failing.
- Added proper lint rake tasks and shrank the race sims in the test environment so my CI suite doesn't take forever any more.

# upcoming this week

Now that the design system has a spine and the betting board is sitting there begging for real money behind it, I think the honest move is to finally build out the economy for real. I'd also like to get onboarding into a state where a new visitor is guided somewhere sensible. We'll see.

That's all! Someday I'll write that race overview post, but honestly I'm still not QUITE ready to share it and I'm tuckered out anyway. Someday... 