# Twin Shot

## Authors
Idit Halevi & Thai Ben Hamo 

If you have any questions or encounter any issues with this project, feel free to contact us at idit8886@gmail.com, we'll be more than happy to help!

## Gameplay Video
### Watch Twin Shot in Action
[![Twin Shot Gameplay](https://img.youtube.com/vi/29HNc-V0FuA/0.jpg)](https://youtu.be/29HNc-V0FuA)

## About Twin Shot
Twin Shot is a game developed using the SFML graphics library, incorporating object-oriented programming principles and design patterns. The player controls an archer equipped with unlimited arrows, aiming to clear each level of enemies.

The game includes two types of enemies:
- A randomly moving enemy.
- A flying enemy with smart movement patterns.

Players can use arrows not only to eliminate enemies but also to stick them into walls, allowing the player to reach difficult areas. The player has three lives, and losing all of them ends the game. 

Each level contains power-ups, such as:
- **Speed Boost**: Increases movement speed temporarily.
- **Invincibility**: Grants temporary immunity from enemies.
- **Extra Life**: Restores one lost life.

Players earn points by collecting coins, which appear for a limited time. The game features a high score table and a level selection menu that allows progression to previously reached stages (as long as the game window remains open). 

Levels are loaded from an external file.

## Getting Started
Follow these instructions to set up and run the game on your local machine.

## Prerequisites

- Visual Studio ([2022 version](https://www.sfml-dev.org/download/sfml/2.6.0/))
- C++ development environment set up in Visual Studio
- SFML library installed and configured ([SFML Installation Guide](https://www.sfml-dev.org/download/sfml/2.6.0/))

### How to Run

1. Clone the repository:

```bash
git clone https://github.com/iditha/Twin-Shot-Game-.git
```

2. Open the project in Visual Studio.
3. Ensure SFML is installed and linked properly.
4. Build the solution to restore any dependencies.
5. Run the project using Visual Studio.```

## How to Play
- Move: Left and Right Arrow Keys
- Jump: Up Arrow Key
- Shoot Arrow: Spacebar

### Gameplay Rules
- Players must eliminate all enemies to complete a level.
- If an enemy touches the player, they lose a life.
- Falling off a platform results in losing a life and respawning at the level’s starting point.
- Power-ups appear for a limited time.
- Coins provide points and appear briefly.
- Levels are structured in external files, allowing easy customization.

## Tiles and Objects
### Game Elements
- **Player (`P`)**: The archer controlled by the player.
- **Walls (`#`)**: Static obstacles that block movement.
- **Coins (`$`)**: Collectible items that increase the score.
- **Gifts (`G`)**: Power-ups providing temporary boosts.
- **Random Enemies (`&`)**: Move randomly on the level.
- **Flying Enemies (`*`)**: Follow smart movement patterns.
- **Empty Space (` `)**: Free area where the player and objects can move.

## Creating Custom Levels
Levels are stored in the `resources` folder as text files (e.g., `Level1.txt`, `Level2.txt`, etc.). To add a new level:
1. Create a new file with the next sequential number (e.g., `Level5.txt`).
2. Define the board layout using specific characters for objects and enemies.
3. Ensure each file starts with:
   ```
   <rows> <columns> 
   ```
4. Update the CMake configuration by adding:
   ```cmake
   configure_file ("Level5.txt" ${CMAKE_BINARY_DIR} COPYONLY)
   ```
5. Follow the format of existing levels when designing new ones.

Here’s an example of a level layout:

```
12 22
#                    #
###                  #
          #  &  $#  ##
   *      ########
     $
    #######     G
#$        #    ###
##        #     *
  P $     #     #   &
######    #     ######
#                    #
#                    #
```


## Source Code Structure

### Core Game Mechanics

- `Controller.cpp`, `Controller.h`: Manages the main game loop, handles user input, and manages transitions between game states.
- `Level.cpp`, `Level.h`: Handles level management, including loading levels and updating game objects.
- `CollisionHandling.cpp`, `CollisionHandling.h`: Manages collision detection and responses.
- `Resources.cpp`, `Resources.h`: Singleton for managing textures, sounds, and music assets.

### Characters

- `Player.cpp`, `Player.h`: Manages player behavior and interactions.
- `Enemy.cpp`, `Enemy.h`: Base class for enemy behavior.
- `FlyingEnemy.cpp`, `FlyingEnemy.h`: Specialized logic for flying enemies.
- `RandomEnemy.cpp`, `RandomEnemy.h`: Specialized logic for randomly moving enemies.

### Game Objects

- `Arrow.cpp`, `Arrow.h`: Represents the player's projectile.
- `Wall.cpp`, `Wall.h`: Static obstacles within levels.
- `Coin.cpp`, `Coin.h`: Collectible items that add to the player's score.
- `Gift.cpp`, `Gift.h`: Base class for power-ups.
- `SpeedGift.cpp`, `SpeedGift.h`: Power-up that temporarily increases player speed.
- `LifeGift.cpp`, `LifeGift.h`: Power-up that grants an extra life.
- `BubbleGift.cpp`, `BubbleGift.h`: Power-up that makes the player invincible for a short duration.

### User Interface

- `Menu.cpp`, `Menu.h`: Manages the main menu, including buttons and commands.
- `InfoBar.cpp`, `InfoBar.h`: Displays current score, lives, and other HUD elements.
- `MenuCommand.cpp`, `MenuCommand.h`: Handles specific actions in the game menus.
- `HelpMenuCommand.cpp`, `HelpMenuCommand.h`: Manages the help section of the menu.
- `LevelsMenuCommand.cpp`, `LevelsMenuCommand.h`: Handles level selection via the menu.

### Animation and States

- `Animation.cpp`, `Animation.h`: Manages sprite animations for game objects.
- `AnimationData.h`: Contains animation frames and sprite data.
- `MovingState.cpp`, `MovingState.h`: Handles the player's movement state.
- `JumpingState.cpp`, `JumpingState.h`: Manages the player's jumping behavior.
- `FallingState.cpp`, `FallingState.h`: Controls the player's falling state.
- `StandingState.cpp`, `StandingState.h`: Represents when the player is idle.
- `PlayerState.h`: Base class for managing different player states.

### Utilities and Helpers

- `Factory.h`: Template class for creating game objects using the Factory design pattern.
- `Clock.cpp`, `Clock.h`: Manages game timing and intervals.
- `Direction.cpp`, `Direction.h`: Handles directional logic for movement.
- `Macros.h`: Contains game-wide constants and macros.

## Design Patterns Used

The game follows several design patterns to ensure maintainability and scalability:

- **Singleton Pattern**: Used in `Resources` to manage assets efficiently.
- **Factory Pattern**: Implemented in `Factory.h` to dynamically create game objects.
- **State Pattern**: Manages complex player states (jumping, moving, falling).
- **Observer Pattern**: Updates UI elements in response to game events.

## Acknowledgments
Special thanks to our instructors and colleagues for their support throughout the development of this project.




