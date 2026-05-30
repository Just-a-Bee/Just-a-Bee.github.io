+++
date = '2026-05-23T13:05:00+01:00'
draft = false
title = 'Implementing Advanced Strategy AI'
tags = ['Raylib', 'C++']
+++

## Overview

For my Games Programming dissertation at the University of East London, I made a strategy game demo that features an advanced enemy AI. The goal of this project was to make multiple AI opponents in a tactics strategy game with imperfect information (fog-of-war prevents players from seeing their opponents actions). I then be conducted a playtest against human players to test the skill level of the AI opponents. This will determine which AI's strategy is the most effective, and how effective it is.

## Castle Conquest
![image](/Devlogs/Diss/diss-image-1.PNG)
The game features multiple units to command, castles to take over, and a system for buying new units to expand your army. The aim of this design is to create a game that is complicated enough to allow for varied strategies, but simple enough to be understood by new players.

## The AI
There are two completed AI players for this game. I aimed to complete much more advanced AI agents, but the game had a much more complicated decision space than anticipated, so simpler AI became the way to go. The first finished AI uses Minimax, which scores each potential action and picks the best one. Afterwards I implemented Hierarchical Portfolio Search, which selects good actions based on "partial player" strategies, then picks the best combination of those actions. You can read more about this in [the full paper](/Devlogs/Diss/AI-Dissertation.pdf).

## Code
[The code is available on my University Github Page](https://github.com/Abby-Smith-UEL/stategydemo)
