+++
date = '2025-01-15T11:43:37+01:00'
draft = false
title = 'Bigfoots Big Break'
tags = ['Godot', 'GDScript']
+++

## Overview

Bigfoot's Big Break was made in three days for the GoedWare Game Jam Limited Color Palette in January 2025.

Based on the theme "Two points of view", you are venturing into the woods in search of Bigfoot. Equipped with your trusty camera drone, you can look around the forest yourself and get a bird's-eye view. Track down Bigfoot and snap some pictures for the newspaper.

It placed 11th out of 83 entries.

{{< include-html "static/html/bigfoot-widget.html" >}}

## Gameplay

Use the split screen view to search for bigfoot from two points of view at a time
![image](/Bigfoot/Splitscreen.png)
Take pictures of your surroundings, using either perspective
![image](/Bigfoot/picture.GIF)
Get your evidence collection scored
![image](/Bigfoot/evidence.png)
*Is that Bigfoot?*

## Code

Scoring the pictures was an interesting challenge in this one.

The picture variable is a dictionary that holds information like its score, a list of reasons for its score (which is displayed at the end), and the actual texture of the picture.

The score is calculated based on a series of checks that each can give you bonus points, such as the subject being very close, or looking at the camera.
```
# picture scoring is done based on current transform of actors
func score_picture(picture, taker):
	
	var taker_dir = -taker.camera.get_global_transform().basis.z
	var distance
	var dot

	# calculate distance and dot product of subjects
	var distance_nessie = nessie.global_position - taker.camera.global_position
	var dot_nessie =  taker_dir.dot(distance_nessie.normalized())
	
	var distance_bigfoot = bigfoot.global_position + Vector3(0,bigfoot.height/2,0) - taker.camera.global_position
	var dot_bigfoot = taker_dir.dot(distance_bigfoot.normalized())
	
	# figure out who the picture is of
	var subject = null
	if distance_nessie.length() < MAX_PICTURE_RANGE && dot_nessie > MAX_ANGLE_TOLERANCE && nessie.hidden == false:
		subject = nessie
		distance = distance_nessie
		dot = dot_nessie
	elif distance_bigfoot.length() < MAX_PICTURE_RANGE && dot_bigfoot > MAX_ANGLE_TOLERANCE:
		subject = bigfoot
		distance = distance_bigfoot
		dot = dot_bigfoot

	# if no subject, picture doesn't score anything
	if subject == null:
		picture["strings"].push_back("Bad.")
	else:
		var subject_look_dir = subject.get_global_transform().basis.z
		var looking_at_camera = -taker_dir.dot(subject_look_dir)
		var score = 0
		
		# subject is in picture
		score += 1
		picture["strings"].append("Good: +1")
		
		# add bonus for getting picture of nessie
		if subject == nessie:
			score += 3
			picture["strings"].append("Nessie: +3")
			nessie.stop_showing()
		
		# add bonus based on distance
		if distance.length() < 5:
			score += 2
			picture["strings"].append("Very close: +2")
		elif distance.length() < 15:
			score += 1
			picture["strings"].append("Quite close: +1")
		# add bonus based on angle
		if dot > .98:
			score += 2
			picture["strings"].append("Dead on: +2")
		# add bonus if subject is looking at the camera
		if looking_at_camera > .8:
			score += 2
			picture["strings"].append("Say Cheese: +2")
		# add the score to the picture
		picture["score"] = score
```

These pictures are then held in an array and shown to the player at the end along with their total score.

## Feedback

This game did quite well in the jam, managing to place 11th overall, however we were held back because a lot of players didn't understand how to play. Another problem is that the best playstyle was to just use the drone and ignore the other 'Point of View', so we didn't make good use of the theme.

To fix these issues we made a few changes. First, the drone spawns in closer to the ground so it doesn't crash as easily when you try to start flying it. It also has a limited range so that you have to move the player character around as well. 

I also recorded sounds for Bigfoot to make while he's walking around, to make him easier to find, and improved his AI so he doesn't get stuck as much. 

## Credits
Code by [Abby Smith](/about/)

Art, shader programming, and audio by [Isaiah Sugar](http://isaiahsugar.com)

Made in [Godot](https://godotengine.org/license)

**[The code is available on my GitHub page](https://github.com/Just-a-Bee/bigfoot)**