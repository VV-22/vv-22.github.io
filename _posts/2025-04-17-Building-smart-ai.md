---
permalink: "/building-smart-ai"
description: "Occupancy maps and behavior trees!"
title: "Building a (kinda) smart AI for my Game AI course"
date: "2025-04-17"
layout: post
---

## Preface

When I registered for CS 5150 at Northeastern University, I had absolutely no idea that it would be one of the most fun classes I've ever had! Not only did I learn a LOT about games, AI and how they work in tandem, but I also got the chance to work with like-minded people and build something that was "fun" (atleast to build :)). Huge shoutout to Prof. Damian Isla, who's knowledge is something I'm constantly amazed by!

Over the course of 4 months, I built pathfinding algorithms (A-star and Dijkstra), spatial functions (Line-of-sight, hold-position and flee), behavior trees(shoot-when-in-line-of-sight, charge-at-player), occupancy maps (perception) and a two-man final project that was a culmination of all we had learnt.

The following content discusses about the approaches we took and some rambling on the choices I made.

## Premise

The idea is to create a third-person hunter style game within a closed environment (A house). The core gameplay loop is to assassinate NPCs by building fear in them. “Fear” can be built by different external stimuli such as noise, vision, etc (refered to as "Events"). We decided to go with Unreal Engine 5 for the game, as we had a solid foundation from the course's assignments to model the AI's perception and behavior. [^a]

{%include youtubePlayer.html youtube_id="bNCdHk-QD9M"%}

## Event System

The external stimuli mentioned in the premise was realized using an "event-system". When an event is triggered, all NPCs in a specified radius are alerted about the event, after which they walk up to the place to investigate it. The game has (at the time of writing this) 4 events that can be triggered.

- Door-knock: Smallest radius.
- Footsteps: small radius.
- Radio: Medium radius.
- Clock: Highest radius.

This event system is built by checking for sphere-overlaps when triggered.

## Perception System

When the NPC is aware of the player, it chases the player, and searches when he is out of line-of-sight and hearing-radius. This is done using a perception system with spatial functions and occupancy maps. Each one of these warrants a project of its own, but the basic rundown is as follows.

Each NPC has an "Awareness" meter that specifies how aware the NPC is of the player. A value of 0 indicates that it is not aware and a value of 1 indicates that the NPC is fully aware of the player and knows his current position. The perception system works closely with occupancy maps to track the position of the player once it's awareness decreases from 1.

### Occupancy maps

An occupancy map keeps track of the probability of the player's position across the entire level. Essentially, it is a 2-dimensional grid of a probability distribution, and is updated every frame to track where the player's most likely position is. In this game, we implemented a occupancy map with 2 sources of input -  line-of-sight and hearing radius. The basic outline of the logic is:

```

// Runs every frame
// Awareness has bounds [0,1]
Perception:
    If player is in line of sight or can be heard:
        Increase awareness.
    else:
        Decrease awareness.

    If NPC awareness is 1:
        Set probability of occupancy-map to 1 at the player's location
        Run behavior from behavior-tree. (In this case, it would try to attack the player.)
    else:
        Update-occupancy-map
        get the point with highest probability
        Run behavior from behavior-tree. (In this case, it would search for the player.)


Update-occupancy-map:
    create two maps: vision-map[row, col] and sound-map[row,col]
    for each traversible position in the level:
        if(point is in line-of-sight and player is not seen)
            cull probability at this point in the vision-map
        if(point is in hearing-radius and player is not heard)
            cull probability at this point in the sound-map
    redistribute culled probabilities in both the vision and sound maps.
    Add two maps together, then divide by the maximum value of the summation to create a new probability distribution.
    Replace the existing occupancy map with the new probability distribution.

```

With the perception system outlined above being implemented, the NPC has emergent behavior where it actively tracks the position of the player using line of sight and sound and searches for the player when it no longer sees or hears him. The video below showcases a basic version of the perception system, using only line of sight. I implemented this as part of the course.

{% include youtubePlayer.html youtube_id="TDkoXHjpTd0" %}

## AI-Behavior tree

In order to build a well-defined behavior for the NPC, we used behavior trees. For the uninitiated, behavior trees are a super-easy way to build complex behavior without needing to manage each behavior individually. Unreal Engine provides a standard way to do so, and by playtesting, we ended up with the following tree:

![Behavior-tree](/assets/img/behavior-tree.png)


The AI has 4 "states" it can be in:

- Passive: At this state, the NPC is unaware of the player. It has a specifc patrol route defined by a spline, and it follows that path. The movement is done using Dijkstra's algorithm, with path-smoothing.
- Investigate: The NPC has currently heard some event happening in the world. This "event" can be a door knock, a grandfather clock falling down, or just the character hearing the player sprint. When the NPC hears these events, its' "fear" increases and it goes to investigate the event. 
- Afraid: The NPC reaches this state if it's fear is maxed out. This corresponds to it being "paralyzed", at which point the player can walk up to and assassinate the NPC.
- Attack: The NPC is aware of the player, and is charging at the player at this state. If the NPC is able to catch the player, the player loses and the game ends. The player can duck behind cover or out-run the NPC, but the NPC is clever and tracks the player. This is done using the occcupancy map and perception system mentioned above.

## Future plans and finishing thoughts

There is still quite a lot of stuff to improve. Right now, the player can cheese through the game by just running all the time. While that might not make for fun gameplay, making a complex perception system that tracks the player's likeliest position was way more fun than it sounds.

When I get time, we plan to add much more closed maps, enemies with different behaviors and different player abilities.

My very thanks to Prof. Damian for his invaluble advice, and to my teammate Utkarsh, without whom this game's premise could never be put in words.

[^a]: [Github](https://github.com/VV-22/CS5150-final)