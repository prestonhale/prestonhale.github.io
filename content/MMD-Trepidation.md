---
title: Moment-Driven Design - Trepidation
date: 2026-3-8
---

# The Moment
When you crest a drop-off and see an unfamiliar area with unknown risks.

# The Result
![A short video showing a player on a grid descending into a kelp forest](./images/MMD_trepidation.mp4)

# The Emotion
I would probably call this **apprehension** or slight **unease**. I'm not going for dread here. I want something more slow burn. The player's desire to push out further into the world coming into conflict with their quiet concern about new areas.

# The Mechanics
Unrecognized alien creatures at the edge of vision create a sense of **novel and poorly understood threats**.

The area itself **obscures vision** making threats harder to detect until the player is already near them which adds to the unease.

Threats mean that there must actually be a **real danger with consequences** to the player in this area.

The desire to acquire new and better resources creates a **reason to descend** into the deeper, potentially more dangerous water.

# The Translation

## Novel And Poorly Understood Threats
Subnautica adds "Stalkers" in the kelp. They're minimally dangerous but look frightening and are the first aggressive thing the player encounters. 

For my implementation I wanted something similar but that also interacts directly with the environment to add the sense of novelty.

I used a creature that "hides" in the kelp. I really like the idea of increasing the tension of an area by introducing creatures of potentially ill-intention who directly benefit from the environment itself.

The Subnautica stalkers are visually threatening with long teeth and large predator-like snouts. Obviously this isn't possible to represent on a single colored grid square but I still wanted to communicate danger to the player to add to the feeling of apprehension. I went with the time-honored tradition of "making the bad thing red" as the simplest solution.

## Real Danger With Consequences
The sawtooths need to present a genuine but avoidable threat, so when the player is near, they emerge from the kelp. If they get even closer they lunge out. 

There's a lot of options for what happens when the player is "attacked" but this moment is really only about creating tension so we need the simplest possible consequence. In this case, the game resets. It's a really small game. That's fine.

Allowing the player to be defeated when touched and not allowing them to see behind them created a moment of frustration when something snuck up and killed the player without being seen. As a concession I added 3 squares of vision all around the player to give them a half second of knowledge of what snuck up on them. 

## Increasing Ability to Understand Threats
**Note: I don't actually think this mechanic was necessary for achieving the desired moment. If I could start over I would not have included this mechanic in this week's project. See the section on [Sub-Mechanics](#mechanics-can-generate-sub-mechanics) below**

Subnautica relies heavily on sound to communicate danger to the player. Every single creature has a series of (very cool!) sound effects to communicate state changes (idle, alerting, aggressive). One of my constraints was to not use sound and it started to become difficult here. 

At first, I added a flashing effect to the sawtooths themselves when they alerted and when they became aggressive. This worked well but had two problems. First, it wasn't visible when the player wasn't looking at them. Sound is audible even outside of your viewport, this wasn't. Second, it felt pretty...goofy? A little too much like a game.

My second, accepted, attempt was to visualize soundwaves. Sawtooths let out a small wave of sound when alerting and a bigger one when turning aggressive. 

This is great. It allows the player to anticipate that *something* is about to happen with the creature. And as an added benefit, it's visible even when the sawtooth is not currently in the line of vision.

## Obscured Vision
First, I added a linearly increasing darkness as the player heads down into the kelp. Just makes it feel more ominous.

Secondly, the kelp itself obscures the player's vision. In the 3d Subnautica the player's vision is totally blocked by the kelp. This allows critters to hide in it. Totally blocking vision in 2d is very frustrating as the kelp becomes a literal wall that blocks all vision beyond it. The concession here was just to reduce the distance the player can see beyond the kelp. Still a hazard but not frustrating.

## Reason to Descend
There are two reasons the player might want to descend. One is simply to explore. While this isn't a strictly mechanical reason it is very real. Entire games are based around purely a desire to explore. To support this I continued to add "wonder" as per the first area. Mainly in the visually appealing kelp forest.

But some players do want a mechanical reason to explore. Subnautica has progression through crafting. And deeper biomes are required to get new resources to craft more. 

That system is not in keeping with "simplest possible mechanic" to provide wonder. So I added a score at the top of the screen that tracks the player's maximum depth achieved without dying. Sometimes the old magic works.

## Misc
Fish and fish flocks generally avoid kelp. No guarantee but they prefer not to be near it. Keeps the area clean to focus on new threat of the sawtooths. They also add a minor sense of unease since the comforting colorful boys are less present.

# Lessons
## "Play -> Change -> Play" Is The Only Loop That Matters
Without rapid iteration we are nothing. I think everyone "knows" this but very few people live it. And that makes sense, the larger the game gets the harder it is to rapidly test something. It can literally be weeks from conception to playable.

This project has made me even more confident that rapid iteration is all that matters even if it means reducing your mechanic to throwaway code on a solid colored grid just to validate it.

## Mechanics Can Generate Sub-Mechanics
This was expected. Some mechanics won't work without others. Picture it as an iceberg with the player-visible mechanic implying others. 

What is important here is making sure that any mechanic you work on is **directly supporting the moment and its emotions**. 

I spent the vast majority of this project making the sawtooths behave in interesting and predictable ways with the kelp. They hide, peek, and lunge at the player. 

But this was absolutely not the simplest way to create trepidation in the area. Simply having the sawtooths render behind kelp while moving about fairly randomly has 90% of the effect for 5% of the cost. I am enormously grateful that I found that out in a grid based domain over the course of 3 days and not in 3d over 3 weeks!