+++
date = '2026-05-23T13:05:00+01:00'
draft = false
title = 'Implementing Advanced Strategy AI'
tags = ['Raylib', 'C++', 'Open Source']
+++

## Overview

For my Games Programming dissertation at the University of East London, I made a strategy game demo that features an advanced enemy AI. The goal of this project was to make multiple AI opponents in a tactics strategy game with imperfect information (fog-of-war prevents players from seeing their opponents actions). I then be conducted a playtest against human players to test the skill level of the AI opponents. This determined which AI's strategy is the most effective, and how effective it is.

In the end I had two separate AI strategies. One using Minimax (Scoring each potential move and choosing the highest scoring option) and one using Hierarchical Portfolio Search, which performed a deeper search on combinations of moves. The optimizations required to perform this deeper search involved pruning a large number of moves and not considering them at all. This resulted in the HPS AI performing worse as it would often miss very good moves in favor of the just-okay moves it considered.
## [Read the full paper](/Devlogs/Diss/AI-Dissertation.pdf)

## [Download the playtest game](/Devlogs/Diss/StrategyDemo.zip)

## Code
[The code is available on my University Github Page](https://github.com/Abby-Smith-UEL/stategydemo)
