+++
date = '2026-02-10T13:05:00+01:00'
draft = false
title = 'Unreal Engine Skill Tree'
tags = ['Unreal Engine 5']
+++

I've added a skill tree to my Unreal Engine project where the player can unlock various upgrades. Each item features its own tree with unique options to allow for unique player expression.

## Overview
Clicking on an item in the inventory screen opens its skill tree. From here the player can select upgrades and unlock them for a specific cost. There is support for upgrades that are only available after purchasing the ones before them, as well as upgrades that are incompatible with each other, where only one of them can be purchased.

Here we can see the skill tree for the blaster item. The main choice is between the Rapid Fire upgrade and the Charge Shot. These options will appeal to different players and provide an interesting choice that is satisfying to see the result of. After these upgrades are subsequent increases to their effectiveness, either by increasing fire rate or increasing damage.

## How it Works
This system required some weird solutions to problems, as unreal engine doesn't support child classes of Widget Blueprints (Which are used for user interface menus) very well. I wanted the individual skill trees to share a base skill tree class, but have their own editable buttons. This way, the layout would be easy to edit and configure per tree. However, when creating a child of a Blueprint, the components of the parent class aren't available to reference, edit, or add children to. To remedy this, the base Skill Tree class has a reference to a canvas panel which is set by the child class during its beginplay function giving the base class access to the individually edited skill trees.

When an upgrade is purchased, the index of that upgrade is passed to the corresponding inventory item, which contains functionality to apply each upgrade. I could have had each upgrade be its own class with unique functionality to apply, but in UE5 blueprints, this would require a seperate file for each one, which would quickly become difficult to manage. Instead each item just has an unlock upgrade function with a switch statement for each upgrade.

The user interface itself also has very smooth functionality. Switching between each skill tree happens smoothly without errors, and upgrades indicate when can be or have been purchased by changing color. The descriptions are displayed on the side and are unique to each upgrade. 
