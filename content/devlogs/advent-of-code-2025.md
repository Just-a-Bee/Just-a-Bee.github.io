+++
date = '2025-12-31T13:05:00+01:00'
draft = false
title = 'Advent of Code 2025'
tags = ["C++", "Open Source"]
+++

I participated in Avent of Code this year! I used C++ for my solutions as I am most familiar with it. I solved 19/24 of the puzzles in the end. 

## My Favorite Puzzle
I thought [day seven](https://adventofcode.com/2025/day/7) was a lot of fun. In the puzzle, a laser is being split as it travels along a bunch of different points, and you have to count how many times it gets split. The trick is that after solving part one, it is changed so that you have to count the number of possible paths the laser can take. Originally I tried to just reuse my part one solution, keeping a list of each point the laser could be at but allowing duplicates this time to account for multiple paths. This proved to be dramatically too slow. Instead I had to pivot to counting the number of ways the laser could have reached that position and storing that value along with the position to avoid having to process it multiple times.

It was fun having to optimize a data structure for speed and efficiently solve the problem, especially because I don't often encounter situations where speed is a concern in my projects.

[The code can be viewed on my Github Page.](https://github.com/Just-a-Bee/AdventofCode2025)
Unfortunately, my SSD died and I hadn't pushed my changes past day 9 so that code is gone forever.