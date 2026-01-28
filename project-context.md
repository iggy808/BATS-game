# Project Context

## Background
- I was contracted to create a game that can embed itself within Kartra, a commerical platform for educators to create curriculums.
- The game needs to be fully playable within Kartra, and can only use java script.
- A sample of an implementation can be found in this project's `src-demo.html` file.

## Constraints
- Using Kartra places some restrictions on our game's development:
  - All visual and audio assets must be stored as base-64 encoded strings, as `const` javascript variables.
    - This means any .jpg or .mp3 files used must be converted to base-64 encoded strings to be consumed by the game logic.
  - External calls to CDNs are prohibited (except for the call to fetch the Phaser-JS library).

## Kartra User Flow
- The user will navigate Kartra and our game as follows:
1. User completes lecture on Kartra (out of our domain, this is irrelevant to game development)
2. User is presented our game

## Game Structure
- The game is in 2D.
- The game is split into two parts:
1. Scenario Navigation
2. Timed match three game

### Game Structure - Scenario Navigation
- It is easiest to describe how the scenario navigation portion of the game works with an example:
  - The player character (a child) is standing outside of a barber shop, accompanied by their guardian.
  - The player is presented with the guardian's initial prompt:
    - "Hey! Let's go into the barber shop."
  - The player is then presented with two dialogue options:
    - `Enter the shop`
    - `Run away`
  - One of these options is correct (`Enter the shop`), and the other option is incorrect (`Run away`).
  - If the user selects the incorrect option, the guardian gently responds, "Come on friend, let's go to the shop!", and the player is presented with the same previous dialogue options.
  - The scene only progresses if the player selects the correct dialogue option.

- Speaking more abstractly, the scenario navigation scene is a sequence of dialogue options. One option is correct, the other is incorrect. Users can only progress the scenario by selecting the correct option.

### Game Structure - Timed Match Three Game
- After the player successfully completes the scenario, they are rewarded with a fun match three style game.
- The player has two minutes of free play time, called a `Brain Break`, wherein they will play the match three game.
- The time should be shown to the user in the upper-right-hand portion of the screen.
- After the time is up, they are presented with a button that says "Continue Lesson"

  