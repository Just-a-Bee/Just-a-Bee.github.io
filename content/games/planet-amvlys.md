+++
date = '2026-05-23T11:43:25+01:00'
draft = false
title = 'Planet Amvlys'
tags = ['Unreal Engine 5']
+++

## Overview

Planet Amvlys was created as part of my Games Programming course at the University of East London. I was the lead programmer in an interdisciplinary team of students who produced this game in Unreal Engine 5 from September 2025 - May 2026.

My work was focused on gameplay systems programming, while also covering UI and audio programming. I created all menus, player abilities, progression systems, puzzle elements, the cutscene system, the save/load system and more. Overall, I learned a lot about team management, and full-scale UE5 development on this project.

{{< include-html "static/html/amvlys-widget.html" >}}
## Gameplay

![image](/Amvlys/title.png)
![image](/Amvlys/level.png)
Explore the mysterious planet

![image](/Amvlys/upgrades.png)
Unlock unique upgrades

![image](/Amvlys/boss.png)
Fight threatening bosses
## Code

On this project I created an "Activators" system. Actors with the "Activator" component can be used to affect "Activated" actors, such as doors, cutscene triggers, elevators, or moving platforms. 

![image](/Amvlys/activator.GIF)

On Begin Play, the activated component iterates over it's activators, binding their status changed event to an event dispatcher. Then, whenever an activator's status changes the activated component is notified and can change its status accordingly. Because this system is based in composition, these behaviours can be applied to any object. A moving platform can activate only while the player is in a certain area, or a door can only open when all four buttons are pressed, or anything else that requires multiple actors to send simple signals to each other in this way.

I developed this system to make it easy for my level designer to create unique environmental puzzles with drag-and-drop components and instance editable variables. No code necessary! This allowed for faster iteration times during level design, as well as designers making complex puzzles in levels without programmer assistance.

## Feedback

During development, I collected playtest feedback multiple times. These were invaluable for perfecting the player experience. This lead to many bugs being identified, as well as new programming challenges from desired quality of life features. 
After our first playtest I added "Coyote Time" to the player character, which allows jumping for a short time after walking off a ledge. This prevents players from falling when they press the jump button just a bit too late. Then, a bug was discovered: pressing jump twice in quick succession lead to a normal jump, followed by a coyote time jump, gaining extra height. To fix this, I prevented the activation of coyote time when leaving the ground after jumping.
Many other issues were identified and solved thanks to playtest feedback, and most playtesters enjoyed the gameplay.

## Further Development

We are continuing development on this game for some time, so it is not released quite yet. We're planning to submit to the [Gamebridge](https://gamebridge.uk/) showcase in June, which I am very excited for.

## Credits
Created by [Abby Smith](/about/), Ben Baker, Taylor Webb, Stephen Liu, Shaynun-Nakai Grant, and Narcis Ghiocel