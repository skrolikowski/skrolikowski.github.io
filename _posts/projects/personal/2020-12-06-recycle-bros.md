---
title: Recycle Bros.
author: shane
description: Pink and Yellow, two ambitious recycle bots in a 96x96 resolution world; A 96x96 screen resolution arcade game.
categories: [Projects, Personal]
tags: [game-dev, love2d, arcade, game-jam]
image: /assets/img/projects/personal/RB_Cover.png

toc: true
comments: false
published: true
hidden: true
---

## Overview
You play as two robot brothers, Pink and Yellow tasked  with sending incoming recyclables to their next location... wherever that may be, and collecting points along the way. You are given only 3 misses before your boss shuts you down and labels you as a recyclable.

The goal is simple. Beat your top score and have fun!

### Information
- **Release Date** - Dec. 6th, 2020
- **Platforms** - Mac / Win
- **Genre** - Action/Arcade.
- **Theme** - Retro
- **Limitation** - 96x96 screen resolution.
- **Team**
  - Me - Lead Designer/Programmer
  - [Kai](https://kaidesu.com/) - Lead Artist/Programmer

[Github](https://github.com/skrolikowski/recycle-bros)
| [itch.io](https://skrolikowski.itch.io/recycle-bros)
| [Post-Mortem](https://skrolikowski.itch.io/recycle-bros/devlog/201623/designing-recycle-bros)

![](https://img.itch.zone/aW1hZ2UvODQyNTc2LzQ3MjM3NjAucG5n/794x1000/Ui%2BHBb.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvODQyNTc2LzQ3MjMzMjMucG5n/794x1000/fqyrSb.png){: w="250" .normal }
![](https://user-images.githubusercontent.com/355659/100678775-c3188200-3322-11eb-87ab-bcbc120f24e6.png){: w="250" .normal }
![](https://user-images.githubusercontent.com/355659/100913505-b90f9400-3486-11eb-938c-5fbed0e11b1e.png){: w="250" .normal }

## Design
Prior to the announcement of the limitation (96x96 screen resolution) it was my intent to make a game based on an old
[Game & Watch](https://nintendo.fandom.com/wiki/Mario_Bros._(Game_%26_Watch)) handheld title I would spend HOURS playing in my youth.

![Game & Watch multiscreen Mario Bros. handheld](https://www.mobygames.com/images/shots/l/972690-game-watch-multi-screen-mario-bros-dedicated-handheld-screenshot.png)
_Image courtesy of [MobyGames](https://www.mobygames.com/)_

Below are some early prototypes of the game.
We later changed the the conveyor belt design so items have a chance of falling down to another belt.

## Mechanics
The game moves in 'ticks' of slowly decreasing durations between when items are spawned.
It's up to the player to control both bots to bridge the gaps so the items can cross safely to their destination.
If 3 items are lost the game is over.

The goal of the game is to see how far you can get beating your previous top scores.

## Technologies Used
- [Love2D](https://love2d.org/) - Game Framework.
- [Aesprite](https://www.aseprite.org/) - Sprite Animations.
- [Pyxel Edit](https://pyxeledit.com/) - Creating the Tilesheet.
- [Tiled](https://www.mapeditor.org/) - Level Design/Map Making.
- [Sublime Text 3](https://www.sublimetext.com/3) - Text Editor.