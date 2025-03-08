---
title: Space Bum For Hire
description: Your friendly universe neighborhood Space Bum; 2D Platformer Action/Adventure.
categories: [Projects, Personal]
tags: [game-dev, love2d, arcade, game-jam]
image: https://img.itch.zone/aW1nLzI5MzI4MDAucG5n/original/Fn1MkX.png

toc: true
comments: false
published: true
hidden: true
---

This was a really casual 2-month game jam, I challenged myself to build a full game with a beginning and ending.
With a strong background of previously prototyping various AI behaviors, collision resolution, animation, it was finally time to put it all together.

I am very proud of the end result and am currently working on a [sequel](/blog/sb2-devlog-1/) in Unity.

### Information
- **Release Date** - Jan. 31st, 2020
- **Platforms** - Mac / Win
- **Genre** - 2D Platformer Action/Adventure.
- **Theme** - Outerspace [optional: narrative exporation]

[Github](https://github.com/skrolikowski/space-bum-for-hire)
| [itch.io](https://skrolikowski.itch.io/space-bum-for-hire)


![](https://img.itch.zone/aW1nLzI5MzI5OTUucG5n/315x250%23c/L0oASQ.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTU4ODA3LzI5MzI5MDUucG5n/794x1000/v4Ud2u.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTU4ODA3LzI5MzI5MTYucG5n/794x1000/5o8r0f.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTU4ODA3LzI5MzI5ODkucG5n/794x1000/JW%2Bd%2BV.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTU4ODA3LzI5MzI5ODgucG5n/794x1000/270BT5.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTU4ODA3LzI5MzMwMTkucG5n/794x1000/7Toqe2.png){: w="250" .normal }
![](https://img.itch.zone/aW1hZ2UvNTU4ODA3LzI5MzMwMTgucG5n/794x1000/Ir83%2Bl.png){: w="250" .normal }


## Design
The theme of **outerspace** was announced at the start of the jam, which was welcoming.
I'm a fan of sci-fi and always wanted to create an action/adventure with a anti-hero character.

The first step was coming up with an intro for Space Bum's entrance.

> Captain Jenny and the crew of the research vessel known as Starship Senturi are in a bit of a pickle. They've been sent to the planet OS9 to study a rare crystal, however they were given no warning there would be hostile life present. Without the means to defend themselves, a damaged ship, and limited comm capabilities who are they going to turn to...?

You are first met by Commander Scott who gives you your first quest.
From then on it's up to the player to traverse the levels, unlocking new quests and dialogues.

There's a large amount of platforming, which can be considered the biggest challenge to overcome for the player.

Being a fan of Space Quest games, I wanted to sprinkle a bit of humor into the dialogues.
When in gameplay and Space Bum steps within sight of an NPC a random dialogue option will be displayed.

## Game Mechanics

### Quests
To track progression for the game, the player would need to trigger specific events in order.
These events will unlock new dialogues and update the progression.

### Checkpoints
Every now and then the player will encounter checkpoints to save their progress in case of death.
This was to speed the gameplay along so the player didn't have to re-experience the cutscenes again.

### Interactive Game Menu
By Pressing [TAB] the player can use his P.E.T. (Personal Electronic Teleporter) to move to and from the Starship Senturi.
This is just an area to learn more about the game, your quests, and take part in a small parkour course with a reward.

![P.E.T.](/assets/img/projects/personal/SB4H-PET.gif)

### Collectibles
The player will need to conserve their ammo, however can find more along the way.
Some health items are available as well.

## Challenges

### RigidBody Physics
The first steps were to get a small engine setup for the game.
I wanted to use Love2D's [physics module](https://love2d.org/wiki/love.physics), mainly for the collision detection/resolution.
Although there are countless articles of how Box2D is terrible for platformers I thought it worked rather well.

You can see characters slide around, which is a side effect of using Box2D.
I actually liked it and kept it in.

### Moving Platforms
Sliding, clipping, hopping, it all goes wrong when trying to place a rigid body on a moving platform.
The common trick used here is to have the moving platform "host" and control the transform of the hosted entity.

## Technologies Used
- [Love2D](https://love2d.org/) - Game Framework.
- [Tiled](https://www.mapeditor.org/) - Level Design/Map Making.
- [Sublime Text 3](https://www.sublimetext.com/3) - Text Editor.