---
layout: post
title: "a bag of numbers"
date: 2026-06-24 16:00:00 +0000
published: true
---

Earlier I wrote about [how slimes get their colour](/2026/06/18/one-major-aspect-of/). The other, most major half of "what does this slime look like" is its SHAPE, so this week I want to walk through how I draw a slime and how shape gets passed down when two of them squish together.

And, sorry in advance: between colour and shape, shape is definitely more mathematically complex. I'll try to keep this pretty light on numbers, but there's only so much I can do here.

# goals for shapes

Any time you're designing a system, the first step is to lay out your goals: what do you want your system to achieve? These goals are what your design compass should always point back towards, and when you start getting lost in the weeds on the actual design, while you're struggling with problems and setbacks or maybe just getting too enamoured with the process, you need to remember to sometimes stop and look down at your compass.

Here are my goals:

1) Slimes should have a real variety of distinct silhouettes that have personality. A slime is usually a friendly and simple little blob, sure, but "blob" can convey a lot! Check out these examples:

<div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem; margin: 1rem 0">
  <figure style="margin: 0">
    <img src="/assets/images/dragon_quest_lime_slime.webp" alt="A lime-green slime from Dragon Quest, a classic round blob with beady eyes and a wide smile" style="width: 100%; height: 160px; object-fit: contain" />
    <figcaption>Dragon Quest</figcaption>
  </figure>
  <figure style="margin: 0">
    <img src="/assets/images/terraria_slimes.webp" alt="A variety of colourful slimes from Terraria, each a round blob with simple eyes, ranging from green to blue to purple" style="width: 100%; height: 160px; object-fit: contain" />
    <figcaption>Terraria</figcaption>
  </figure>
  <figure style="margin: 0">
    <img src="/assets/images/zelda_chuchu.png" alt="A ChuChu from The Legend of Zelda: The Wind Waker, a translucent blob creature with big round eyes" style="width: 100%; height: 160px; object-fit: contain" />
    <figcaption>Zelda: Wind Waker</figcaption>
  </figure>
  <figure style="margin: 0">
    <img src="/assets/images/ragnarok_online_poring.webp" alt="A Poring from Ragnarok Online, a round pink gelatinous creature with a happy face" style="width: 100%; height: 160px; object-fit: contain" />
    <figcaption>Ragnarok Online</figcaption>
  </figure>
</div>

2) Shape should be inheritable. What slimes do to make new slimes isn't *breeding*, per se, so classical genetics don't always really apply, but the offspring's shape always seems to logically descend from its parents. Just like with colour, I wanted a feeling of mixing and combining.

3) It all has to be able to be drawn by code, live, in the browser. Every user-owned slime on the site is generated from its genes on the fly. This allows for unique opportunities for morphing and allows for a lot of freedom and modifiability when it comes to the slime's appearance.

# first, draw a circle

At first my idea was simple: a slime is a radial function. They sound scarier than they are: pick a centre, and for every angle going around it, ask "how far away from the centre is this point?" Walk a full circle of angles, drop a point at regular intervals (I popped down 32 of them), and then you have a ring of points. Then all you have to do is draw closed curve through them - AKA a spline - and ta-daaa, slime.

You can modify the distance from the centre at any given point by layering other functions on top of your circle function. You want those functions to be periodic so that they end at the same place they begin, closing the circle. This is called harmonics! And here's what THAT looked like:

<video controls style="max-width: 100%; margin: 1rem 0">
  <source src="/assets/images/early_early_slime.mov" type="video/quicktime" />
</video>

Neat! But not particularly captivating.

# then, draw the rest of the freaking slime

I played around with my circle function a lot at this point. I ditched the harmonics (another elegant mathematical solution lost to the sands of time). I flattened the bottom, stretched it a bit, and ta-daa: here are the two variations I ended up with as a better starting spot.

<div style="display: flex; gap: 1rem; margin: 1rem 0">
  <img src="/assets/images/early_slime_blob_with_feet.png" alt="An early version of the goo grotto slime shape: a rounded blob with small nubby feet at the bottom" style="width: 50%; object-fit: contain" />
  <img src="/assets/images/eye-gumdrop.png" alt="An early goo grotto slime with eyes added, resembling a gumdrop" style="width: 50%; object-fit: contain" />
</div>

I felt these had a little bit of zhuzh, and when I added eyes I got a little attached. I made the feets an inheritable trait so I could also start experimenting with genetics, and then I was off.

# how i learned to stop worrying and love the blob

With this as a framework to start from I started coming up with more slime shape variations. I won't linger on this too much, because all it was was basically tweaking the generation function a bunch. I failed often. It was slow going at first. I would change a number, go to the page, refresh it, and have to go back and adjust. I tried a lot to programatically combine shapes, but it always ended up in slimes losing that visual identity a few generations in and reverting back to a typical circle. Bleh.

I eventually did something right, though: I took a step back, stopped banging my head against the wall, and decided to invest a day in reducing friction and frustration for myself. I ended up making a "slime designer" tool that allowed me to squash, stretch, and generally mess with the individual parts of slimes in real-time in the browser. I lost a day in direct dev work, but with my new toolset I went from designing 3 slimes over the course of two days to finishing my core slimes.

It was a really fun feedback loop: I'd design more slimes, which would give me ideas for more slimes, which would give me ideas for the visual identity of the site overall... I'm the first to admit I'm not much of a designer, but I started to see it grow into itself incrementally. I wanted the slimes to feel cute and coherent with the site, like the site was a place they could live and wander.

Once I was satisfied with the number of base slimes I had, I moved on to figuring out how to squish them together.

# spliney combiney

I tried a bunch of stuff programatically. At first I experimented with interpolating between points on the slime directly, but I knew already that'd create the problem of slimes inevitably losing their uniqueness as everything descended towards the accursed mean. I tried to similarly give each slime a "profile" - flatness, the size of the dome of the head, number and amplitude of bumps - and interpolated between parents' profiles, which worked better, but still lacked a certain something. 

<video controls style="max-width: 100%; margin: 1rem 0">
  <source src="/assets/images/lerpvideo.mp4" type="video/mp4" />
</video>

I ended up leaning into my debug tool again, and building out more functionality for myself. I made it so I could copy the points from the mid-point slimes in my interpolator (shown in an early stage above), import them into my slime designer, and adjust the values as necessary to make satisfying and fun mid-point slimes.

<div style="display: flex; align-items: center; gap: 0.75rem; margin: 1rem 0">
  <img src="/assets/images/redslimeresized.gif" alt="An animated red slime" style="width: 30%; object-fit: contain" />
  <span style="font-size: 1.5rem">+</span>
  <img src="/assets/images/blueslimeresized.gif" alt="An animated blue slime" style="width: 30%; object-fit: contain" />
  <span style="font-size: 1.5rem">=</span>
  <img src="/assets/images/purpleslimeresized.gif" alt="An animated purple slime, the result of combining the red and blue" style="width: 30%; object-fit: contain" />
</div>

It was manual, sure, but the workflow I made for myself made it feel fun and breezy. I knocked out 20+ combos in one go and had a blast doing it.

# far future plans

What's here now is a good foundation, but it's still pretty coarse and required a lot of hand tuning. Real slime morphology is way more varied than that, and the function I'm using can definitely be expanded to allow for a more procedural generation, but I have so many plans for the site that I think I need to let this system settle for a bit. I do want to get it right, and I have plans for versioning the algorithm later so I can expand it into a V2 with more slime qualities and better inheritance, but... for now I'm happy that slimes look at least a little bit like slimes. 

# morals
- invest in reducing your own friction and give yourself time to experiment! it pays off!
- sometimes you have to let something be good enough.
- (unless you're the designer of the Aeronautilus Economy Model Autonomous SpaceBoat, in which case you should have done a better job.)