+++
date = '2025-05-02T11:43:25+01:00'
draft = false
title = 'Tank Game'
tags = ['C++', 'Open Source']
+++

## Overview

This is a C++ only project made using the Raylib graphics library.

The goal of this project was to practice C++ development and make a 3D game without relying on a game engine. To accomplish this, I followed [design patterns](https://refactoring.guru/design-patterns) such as using a state machine to handle the main game loop, and using the strategy pattern to add behavior to my actors in-game. I also had to implement an actor manager that process and draws the game objects each frame, as well as a physics system, and A* pathfinding.

## Gameplay
Learn how to play
![image](/tank/howto.PNG)
Fight off enemy tanks
![image](/tank/screenshot.PNG)
Go for a high score!
![image](/tank/score.PNG)

## Code
The code for this project is very clean with a lot of clever abstractions to keep things simple.

For example, this is the entirety of the main function:
```
int main(void) {

	// Open window
	InitWindow(SCREEN_WIDTH, SCREEN_HEIGHT, "Tank Game");
	SetTargetFPS(60);

	// Declare the current state, start in TitleState
	GameState* currentState = new TitleState;
	currentState->enterState(); // Call the state's enter function

	// Main game loop, called every frame
	while (!WindowShouldClose()) {
		currentState->nextFrame(); // Tell current state to process and render the next frame
		GameState* changeState = currentState->shouldChangeTo(); // Ask if the state should be changed
		if (changeState) { // Change to changeState if it has a value
			currentState->exitState();
			delete currentState;
			changeState->enterState();
			currentState = changeState;
		}
	}

	// Deallocate pointers
	delete currentState;
	delete GameData::getInstance(); // Singleton needs to be deleted

	return 0;
}
```
This state machine holds a reference to a "Game State" object and calls its "next frame" function to render each frame of the game. This modular strategy allows the game to change between wildly different modes, as the current state has complete control over what happens each frame, while allowing easy switching to other states through the "should change to" function. 

## Credits
Created by [Abby Smith](/about/)
 and [Isaiah Sugar](http://isaiahsugar.com) using [Godot Game Engine](https://godotengine.org/license)

**[You can download the project here](/Downloads/TankGame.zip)**

**[The code is available on my GitHub page](http://github.com/Just-a-Bee/TankGame)**