+++
date = '2025-10-24T13:05:00+01:00'
draft = false
title = 'Starting my Game Studio Project'
+++

Recently I've started working on my Game Studio 3 project for my university course. I'm working with an amazing group and very excited to be coming together to make a game.

The concept we settled on is a First-Person Metroidvania inspired by Metroid Prime, but taking notes from more modern shooters like Ultrakill, and Metroidvanias like Hollow Knight. Currently, we're still deep in the ideas stage, coming up with enemy concepts, areas to explore, and upgrades, as well as writing the story.

In order to make our ideas a reality, we're using Unreal Engine 5. I am responsible for the gameplay programming, UI programming, and likely more as we move along with the project and have more things to implement.

I've just started on the Inventory system, which keeps track of what items the player has collected. This is used for giving the player the right stats/abilities, and for saving that information. Later there will be a menu that displays these items and describes them.

The inventory contains a map of items to integers in order to keep track of the quantity. (Some items, such as health upgrades, the player will be able to collect more than one of) 
![image](/Devlogs/Inventory.PNG)
When a new item is collected, we check if its class matches the class of an already collected item, if so we just increment that item. Then the item's "Get Collected" function is called, which is what actually implements the item's behaviour.

I'm very happy with the direction of this project, and look forward to sharing more as it comes along.