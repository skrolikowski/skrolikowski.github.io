---
title: "Conquest: Combat Demo ~ Revised"
description: "Combat Demo for a work-in-progress turn-based strategy game: Conquest"
categories: [Projects, Personal]
# tags: [game-dev, love2d, arcade, game-jam]
image: /assets/img/projects/personal/conquest-combat-revised/04.jpg

toc: true
comments: false
published: true
hidden: true
---

## Overview
__Conquest: Combat Demo ~ Revised__ was developed for the [Post Jam "Jam" #9](https://itch.io/jam/post-jam-jam-9), in which participants were tasked in revising an existing game jam submission.
The game is turn-based combat strategy game where the player controls a small army battling it out against the computer;
the goal is for the player to strategically move their army across the battlefield to defeat the enemy army or capture their flag.

The original predecessor being [Conquest: Combat Demo](https://skrolikowski.itch.io/conquest-combat-demo), was developed a month earlier for the [DOS Games July 2024 Jame](https://itch.io/jam/dos-games-july-2024-jam).

![](https://img.itch.zone/aW1hZ2UvMjk2MjIwOS8xNzcyMDM1NC5naWY=/original/uKzjPF.gif){: .center}

### Information
- **Release Date** - Sep. 10th, 2024
- **Platforms** - HTML5
- **Genre** - Turn-based Strategy
- **Game Jam** - [Conquest: Combat Demo ~ Revised](https://skrolikowski.itch.io/conquest-combat-demo-revised)
- **Theme** - Revise another jam submission

[Github](https://github.com/skrolikowski/conquest_combat)
| [Demo](https://skrolikowski.itch.io/conquest-combat-demo-revised)

---

## Design
The game is inspired by a mini-game of a childhood favorite of mine: [Conquest of the New World](https://www.gog.com/en/game/conquest_of_the_new_world),
which focuses on Exploration, Colony Management, and Combat. I chose to focus on the combat aspect of the game.
I researched by studing the manual and playing the game and basically tried to emulate the combat system.

### Original
![](/assets/img/projects/personal/conquest-combat/01.jpg){: w="200" .normal }
![](/assets/img/projects/personal/conquest-combat/02.jpg){: w="200" .normal }
![](/assets/img/projects/personal/conquest-combat/03.jpg){: w="200" .normal }
![](/assets/img/projects/personal/conquest-combat/04.jpg){: w="200" .normal }

### Revised
![](https://img.itch.zone/aW1hZ2UvMjk2MjIwOS8xNzcyMDM1My5wbmc=/original/3mOA9k.png){: w="200" .normal }
![](/assets/img/projects/personal/conquest-combat-revised/01.jpg){: w="200" .normal }
![](/assets/img/projects/personal/conquest-combat-revised/02.jpg){: w="200" .normal }
![](/assets/img/projects/personal/conquest-combat-revised/03.jpg){: w="200" .normal }

## Mechanics
A turn-based strategy game where the player plays against a simple computer program.
Each player takes turns moving their units in a limited, chess-like fashion.
Attacks are made by selecting multiple units and attacking on a square of enemy units.
The game ends when the player defeats the enemy army or captures their flag.

### Morale, Panic & Retreat
Units taking damage can chance panicking, which will cause the unit to retreat a square; if the square is fully occupied they lose an additional hit point instead.
Panic chance is reduced by the Leader's charsima stat.

### Combined Arms & Flank Attacks
Combining an attack with multiple unit types, plus attacking from multiple sides can add bonus hit chance and damage.

### Varying Unit Types
There are three unit types: Footman, Rogue, and Musketeer, each with their advantages and limitations.
The Musketeer can attack from any distance in the same row, and can only stand on the home row.
The Rogue unit is able to move two squares or 1 square plus attack; great for flanking.
The Footman occupies less space on the battlefield, but moves slowly.

{%
  include embed/video.html
  src='assets/video/conquest-combat-00.mp4'
  types='mp4'
  title='Demo video'
  autoplay=true
  loop=true
  muted=true
%}

## Challenges
Biggest challenge was reverse engineering the game from the manual and playing the game.
The original game was released in 1996, and I haven't been able to find the source code.
Fortunately, the game manual was descriptive in all aspects of explaining the combat mechanics and unit types.

### Computer AI
Another challenge was creating a simple computer AI for the player to play against.
During the computer's turn, each unit would pick their best movement and/or attack.
Then they will be sorted by their strength, and actions would be taken until the computer ran out of moves.
If enough units were panicked and the Leader's charasma was low, the computer would retreat.