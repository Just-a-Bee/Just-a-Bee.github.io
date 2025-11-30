+++
date = '2025-06-12T11:31:36+01:00'
draft = false
title = 'Tank Game'
tags = ['C++', 'Raylib']
+++

## Overview

![image](/Tank-Game/Game.PNG)

This was a small C++ project using the Raylib graphics library, mostly made to practice my C++ and see what it's like making a game without an engine. I focused on implementing 'Design Patterns', mostly based on the diagrams from [Refactoring Guru](https://refactoring.guru/design-patterns)

It features menu screens, collision detection, powerups, a scoring system, and an implementation of AStar pathfinding. The graphics and gameplay are quite simple, as it's intended as more of a technical project.
## Design Patterns

Within the main function I implemented the State pattern, creating a state machine that runs the game's main logic. The main function holds a reference to a GameState and calls its process() function every frame, which then has different functionality based on its type.
![image](/Tank-Game/State_Machine.PNG)

The menus utilize the command pattern to have simple buttons that can have different behaviors without having to be different classes and to simplify the menu code.
![image](/Tank-Game/Command_Pattern.PNG)

The Player and the Enemies feature the strategy pattern. Each Tank has a TankController which controls its behaviors. This way any child class of Tank can utilize the behavior from any TankController.
![image](/Tank-Game/Strategy_Pattern.PNG)

Finally, the singleton pattern is used for the GameData class, which stores info like the current score and the game's high scores. This information needs to be retained when changing states and only needs to exist in one place, so it made sense to store it here.
![image](/Tank-Game/Singleton.PNG)


## Credits
Game by [Abby Smith](/about/)

Made using the [Raylib](https://www.raylib.com/) graphics library

**[The code is available on my GitHub page](https://github.com/Just-a-Bee/TankGame)**