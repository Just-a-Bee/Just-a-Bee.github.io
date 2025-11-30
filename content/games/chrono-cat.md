+++
date = '2024-04-06T11:31:36+01:00'
draft = false
title = 'Chrono Cat'
tags = ['Godot', 'GDScript']
+++
## Overview
Chrono Cat was made as a small personal project in 2024

Chrono cat is a short Sokoban-Style puzzle game inspired by games like Baba is You. It features a unique "rewind" mechanic which allows you to send objects back in time. Can you help Chrono Cat take a nap in all five levels?

This is my most polished project, with a focus on a clean user experience, smooth animations, and quality of life features like saved progress and a settings menu.

{{< include-html "static/html/cat-widget.html" >}}
## Gameplay
Solve tricky puzzles to help Chrono Cat get to her bed
![image](/Chrono-Cat/puzzle.png)
Use Chrono Cat's rewind ability to send objects back through time!
![image](/Chrono-Cat/rewind.GIF)

## Development
As one of my first serious game projects, I spent a lot of time getting this one right. At one point it had so many issues I just decided to start from scratch and remake the whole thing in Godot 4. This was a great decision, as I had learned a lot from my mistakes and wound up with a much cleaner and simpler codebase. 

I made all of the code, assets, and animations myself, and reached out to my friend Isaiah for the music.

As a big fan of puzzle games this project means a lot to me and I would love to revisit it and make it into something more someday. 

## Code

One of my favorite features to implement was the 'Undo' feature. After every move the player makes, the current state is saved in an array called the 'Undo Array'. Then when we want to undo (or restart) we just restore the game states from the Undo Array.

```
# function to undo the most recent move
func undo():
	if undo_array.size() > 0:
		restore_state(undo_array[-1])
		undo_array.pop_back()
		sfx.play_undo()
#function to restart the level
func restart():
	if undo_array.size() > 0:
		restore_state(undo_array[0])
		undo_array.clear()
		sfx.play_restart()
# function to revert to a previous state
func restore_state(state:Array):
	if rewinding:
		cancel_rewind()
	var restore_positions = state[0] # first entry of state is the position of every actor
	var restore_rewinds = state[1] # second entry is each actor's rewind array
	var restore_rewind_uses = state[2] # third entry is number of rewind uses
	
	# move every actor to its previous position
	actor_dictionary.clear()
	for restore_position in restore_positions:
		var restore_actor = restore_positions[restore_position]
		if restore_actor.active == false:
			restore_actor.restore()
			restore_actor.active = true
		actor_dictionary[restore_position] = restore_actor
		restore_actor.move(map_to_local(restore_position), true)
	
	# set the rewind array for every actor to the previous one
	rewind_dictionary.clear()
	for actor in restore_rewinds:
		rewind_dictionary[actor] = restore_rewinds[actor].duplicate()
	
	# set the number of rewind uses to previous amount
	rewind_uses = restore_rewind_uses
```

If I were making this today, the states would be stored as structs, rather than arrays where each index corresponds to a specific value.
## Credits
Game by [Abby Smith](/about/)

Music and sounds by [Isaiah Sugar](http://isaiahsugar.com)

Made in [Godot](https://godotengine.org/license)

**[The code is available on my GitHub page](https://github.com/Just-a-Bee/Chrono-Cat)**