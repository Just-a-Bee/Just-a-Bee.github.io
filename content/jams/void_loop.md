+++
date = '2025-08-08T11:43:25+01:00'
draft = false
title = 'void loop()'
tags = ['Godot', 'GDScript']
+++

## Overview

void loop() was made for the GMTK Game Jam 2025 in four days.

Following the theme "Loop" the player is tasked with stopping a recursive function call before The Program crashes. The game is set inside a computer program where you play as Integer and fight your way through a random series of rooms. After each room, you add a line of code to the recursive function to improve your chances of winning.

It placed 184th for creativity out of 9,584 entries.

{{< include-html "static/html/loop-widget.html" >}}

## Gameplay
Stop Boolean before it's too late!

Fight enemies!
![image](/Loop/combat.png)

Choose powerful upgrades!
![image](/Loop/upgrades.png)

Add them into the code!
![image](/Loop/code.png)

## Code

Within the code, a real recursive function makes all of this work:
```
func loop():
	# get our current block and update the code window
	var block = loop_arr[current_block]
	code_window.increment_sprite_offset()

	# execute our block and wait for it to finish
	block.execute()
	if not block.is_finished:
		await block.finished

	# reset our block and increment current_block
	block.reset()
	current_block += 1

	# if that was the last block, restart "loop"
	if current_block >= loop_arr.size():
		current_block = 0
		code_window.set_sprite_offset(0)
		await get_tree().create_timer(Block.line_execute_time).timeout
	
	# if stack count is too high lose the game
	if stack_count > 16:
		lose()
	
	# if loop isn't paused, continue executing
	if do_execute_loop:
		loop()
```

This iterates over an array of 'code blocks' (the lines added to the function in game) and executes each one. It was important to me that there is a real recursive function happening within the code to make the game more real. Although, it does stop recurring when the function pauses after you defeat all the enemies.

I also had to implement a randomly generated array of rooms to fight through, various enemy AIs, and the upgrade menu UI. Overall it was a very fun project to work on!

## Credits
Created by [Abby Smith](/about/)
 and [Isaiah Sugar](http://isaiahsugar.com) using [Godot Game Engine](https://godotengine.org/license)

**[The code is available on my GitHub page](https://github.com/Just-a-Bee/gmtk-2025)**