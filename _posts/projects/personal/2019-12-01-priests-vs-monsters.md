---
title: Priests vs Monsters
author: shane
description: Yet another Tower Defense Game...
categories: [Projects, Personal]
tags: [game-dev, love2d, arcade, game-jam]
image: /assets/img/projects/personal/PvM_Cover.png

toc: true
comments: false
published: true
hidden: true
---

## Overview
Can you survive a 10 wave onslaught? Each rounds last 60 seconds, with increasing difficulty.
Spend magic to summon Priests in warp (light brown) tiles.
Don't allow the Monsters to destroy your sacred Banner.
Monsters are Bound to their path and can fall to their deaths into the void, but they have limited Leap skills to jump across gaps.

### Information
- **Release Date** - Dec. 1st, 2019
- **Platforms** - Mac / Win
- **Genre** - Tower Defense
- **Theme** - Leaps & Bounds

[Github](https://github.com/skrolikowski/game-off-2019)
| [itch.io](https://skrolikowski.itch.io/priests-vs-monsters)

![](https://img.itch.zone/aW1nLzI3MzI2ODAucG5n/315x250%23c/wQWSO3.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTI1MzMxLzI3Mjg0NTAucG5n/794x1000/IKapVd.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTI1MzMxLzI3Mjg0NTEucG5n/794x1000/1QQ%2Brg.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTI1MzMxLzI3Mjg0NTcucG5n/794x1000/WbTMy1.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTI1MzMxLzI3Mjg0NTIucG5n/794x1000/cvVuu7.png){: w="250" .normal }


## Design
I've always wanted to make a tower defense game, and finally joined a [game jam](https://itch.io/jam/game-off-2019) to motivate myself to make my first published game.
The timeline was a month, so it gave me plenty of time to gather assets, prototype, and build a small framework to use.
Love2D has a wealth of [community contributed libraries](https://github.com/love2d-community/awesome-love2d) that helped the game come to life.

## Mechanics
Monsters spawn in 10 waves of increasing difficulty.
Each wave a modifier is used to slightly increase the spawn rate.

The monsters follow a predefined path and use steering behaviors to flow through the map. 
Priest projectiles have knockback abilities to push the monsters into the void.

Priests can be added in select locations and fire projectiles into the waves of monsters.
Magic is awarded for each kill and can be used to summon more Priests.

#### Monster Types:
- **Skeleton** - Average health and movement speed
- **Skull** - Low health & fast movement
- **Vampire** - High health & slow movement

#### Priest Types (Towers):
- **Range** - Fast attack rate, medium attack strength. 
- **Trap** - Sustaining burn attack.
- **Heavy** - Slow attack rate, heavy attack strength.

## Challenges
I spent a lot of time adjusting the pathing so the monsters don't fall into the void like lemmings.
I believe it still does happen on occasion, but it still took a while to make the necessary adjustments.
The priest projectiles do give a knockback radius, so it is expected that monsters will indeed fall to their doom.
Just not voluntarily.

## Technologies Used
- [Love2D](https://love2d.org/) - Game Framework.
- [Sublime Text 3](https://www.sublimetext.com/3) - Text Editor.
