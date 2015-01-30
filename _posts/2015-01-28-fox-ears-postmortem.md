---
layout: post
title: "Fox Ears Postmortem (GGJ15)"
categories: Postmortem, Games, GGJ15
excerpt: "My account of our Global Game Jam 15 game, Fox Ears."
tags: [ggj15, ggj, game, jam, fox, ears, postmortem]
image:
  feature: FoxEarsBanner.png
date: 2015-01-28T16:18:13-05:00
---

Last weekend was Global Game Jam 15, and since Toronto has a wonderful dev scene, jams are always a great experience. On top of that, I find jams are always really creatively cathartic, and despite usually being intense and draining, usually lead to me feeling way more productive afterwards. So needless to say, I was pretty excited for this weekend.

### The Team

<a href="https://twitter.com/britney_coates">Britney Coates</a>, artist and designer. She gets the credit for the idea, and was responsible for all the 3D assets and animations, as well as the colour palette.

<a href="https://twitter.com/matthewpereira">Matthew Pereira</a>, musician and 2D artist. He crafted the beautiful theme and the sound effects used in the game. He also designed the main menu art.

And finally, I was the programmer and dabbled in some level design.

### The Idea

We wanted to make a game that was driven and influenced by music, but without being as restrictive as some other rhythm games are. We wanted to retain the user's freedom of movement (and not, for instance, lock them to only moving on the beat) while still rewarding them for recognizing and utilizing the beat.

So, we decided an infinite-runner-esque game would probably be a pretty solid choice, especially for a jam game, since we would be able to make it modular and scale to however many puzzles/tiles we were able to create. We brainstormed a few ideas for style and puzzles, and we were ready to jam!

### The Jam

If you've never been to an on-site game jam, I really can't recommend it enough. Being surrounded by so many awesome people all being crazy productive is super contagious, and the energy there is fantastic. The three days all kind of blurs together, and you pretty much think about the game non-stop. 

By the end of the first day, we had basic movement and our level generation system in place. By the end of the second day, we had beat detection, and a few tiles made, and most of the props in place. And by the end of the third day we had a playable (buggy) game! 

### The Game

Overall, I'm very happy with how our game turned out. It's definitely the best result I've had from a jam game so far. While there are a couple of bugs (mostly players falling out of the level), the game worked as intended for the majority of play throughs I saw. We also really nailed the aesthetic we were going for, and are super happy with how the game looks. 

As it currently stands, the game is a sort of action-platformer crossed with a rhythm game. You play as a fox, and run through procedurally generated levels trying to live through the entire song. The camera steadily moves forward, bringing with it a magical deadly fog, so your only mission is to keep away from the near edge of the screen. 

As you progress through the level, you encounter various puzzles and obstacles you must overcome. Most of these are designed with a musical element; blocks slide around to the beat of the music, switches must be pressed in time with each other and the music, etc., etc. Your character can also benefit from a good sense of rhythm; your usually short jump gains double the length when it's timed with the music, and if you perform two of these jumps in a row, you can execute a double jump.

At the end of the song, a special tile spawns with a large flower, which is your goal. Our (temporary, forged late one night during the jam) story currently goes that everyone in your fox village has fallen ill, and the only thing that can save them is a plant that grows in the magical forest of the owls. When you go to them for help, however, they saw you must pass their test in order to retrieve the flower. 

### The Future

Most times, after a jam, I don't want to even look at the project for at least a couple weeks. After committing to it so heavily for three days, I usually just need to step back from it for a bit before continuing to work on it. 

This time, however, I was stoked to keep working on it. People's positive reactions were definitely part of that; almost everyone who played commented on how good it looked (we even had a couple people ask if they would be able to buy prints!). 

There's all sorts of feedback we got from people who were kind enough to play our game, and it's given us lots of ideas about where to take the game from here. The biggest thing for me, at least, is increasing tile diversity. We only had time to make four tiles (such is the nature of game jams), which makes the game very repetitive at the moment. Having a plethora of tiles would make the game feel way better, and really spruce it up. I also want to add a series of obstacles that aren't statically attached to tiles, but randomly introduced, to help prevent players from simply memorizing ideal paths.

We had a few ideas along those lines when we were originally brainstorming the game, but didn't have time to implement them. What we really want is to design certain elements that have a drastic effect on the game world, and have them trigger at climactic moments in the song. 

Currently, I've started working on some more flexible tile design tools, as well as a general cleanup of the code from the jam. I'll probably start documenting some of that stuff on here, so keep an eye out for that! 