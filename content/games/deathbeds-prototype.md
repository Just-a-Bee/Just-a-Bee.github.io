+++
date = '2026-05-23T11:43:25+01:00'
draft = false
title = 'Deathbeds Prototype'
tags = ['Unreal Engine 5']
+++

## Overview

Deathbeds is an isometric wave survival game made in Unreal Engine 5 that I am working on as a freelance programmer. This prototype was made in 1 week to demonstrate the basic idea for the game.

As the sole programmer on the project I am responsible for all technical systems design and implementation. This includes an inventory/upgrades system, tank character controllers, enemy AI and pathfinding, wave spawning, and more. While this version is a simple prototype, there are more features planned for the finished game that I will continue developing.

{{< include-html "static/html/deathbeds-widget.html" >}}
## Gameplay

![image](/Deathbeds/fight.png)
Fight enemy tanks
![image](/Deathbeds/collect.png)
Collect upgrades
![image](/Deathbeds/prepare.png)
Prepare for your next run

## Code

The main feature of this game is its 'Components' system. During a run, enemy tanks have a chance to drop an item called a component. They have various effects, such as increasing your speed, damage, or health. Before each run, the player may choose three of these components to equip. 

The main goals when implementing this system were to keep the code lightweight and simple, to support a small project with limited scope, while allowing for unique functionality, and descriptions. I also wanted to keep implementation of new items and maintenance of current items easy and accessible to non programmers.

To support this, items are stored as the structure "S_Item", which only has two members: its Rarity (E_Rarities) and its Type (E_ItemTypes). These two values can be used to retrieve an "S_ItemData" structure, which contains information like the item's Name, Description, and Icon. These Item Data values are stored in a Data Table, so that any developer can easily change things like an item's name, or the icon it shows in the inventory. This table also stores the Value of each item, which represents how effective it is (e.g. a Health Increase item with a value of 1.5 multiplies the player's health by 1.5), allowing designers to balance item effectiveness without going deep into any code or blueprints.

![image](/Deathbeds/data.PNG)

This system is very effective for the needs of the project. It's lightweight and allows for easy creation of new items, and makes it easy for other developers to collaborate in making unique content for Deathbeds.
## Further Development

Development on this project is continuing, hopefully to a Steam release. Feel free to follow along!
## Credits
Game Design and 3D Art by Oscar Lowe, Programming by Abby Smith
Made in Unreal Engine 5