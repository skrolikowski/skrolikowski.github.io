---
title: Slot Raider
author: shane
description: You are a gambling adventure, but in this adventure it may cost your life! Spin to win.. or lose your life...
categories: [Projects, Personal]
tags: [game-dev, love2d, arcade, game-jam]
image: https://img.itch.zone/aW1hZ2UvMTkwNTc0OC8xMTIxMjY3OS5naWY=/794x1000/07gaDq.gif

toc: true
comments: false
published: true
hidden: true
---

## Overview
Slot Raider is a _roguelike/slots_ style game developed for the [Juice Jam II](https://itch.io/jam/gdb-juice-jam-ii) game jam.
The player's goal is to survive for as long as possible while collecting coins, purchasing restorative items, while avoiding traps.
The overal theme of the jam was _juiciness_, which is how visually pleasing a game responds to the player's input.

### Information
- **Release Date** - Feb. 5th, 2023
- **Platforms** - Mac / Win
- **Genre** - Roguelike/Slots
- **Game Jam** - [Juice Jam II](https://itch.io/jam/gdb-juice-jam-ii)
- **Theme** - _juiciness_, Paying the Price

[Github](https://github.com/skrolikowski/juice-jam-ii)
| [itch.io](https://skrolikowski.itch.io/slot-raider)
| [Dev Log](https://skrolikowski.itch.io/slot-raider/devlog/485671/behind-slot-raider)

---

## Design
The game was inspired by my recent experience with slot games, combined with my passion for roguelikes.


![](/assets/img/projects/personal/slot-raider/00.jpg){: w="200" .normal }
![](/assets/img/projects/personal/slot-raider/01.jpg){: w="200" .normal }
![](/assets/img/projects/personal/slot-raider/02.jpg){: w="200" .normal }
![](/assets/img/projects/personal/slot-raider/03.jpg){: w="200" .normal }
![](https://img.itch.zone/aW1hZ2UvMTkwNTc0OC8xMTIxMjY1My5naWY=/794x1000/GTNZg5.gif){: w="200" .normal }
![](https://img.itch.zone/aW1hZ2UvMTkwNTc0OC8xMTIxMjY3My5wbmc=/794x1000/WT2FEp.png){: w="200" .normal }

## Mechanics
The player must continually spin the slots, collecting coins, and absorbing damage. The coins can be used to purchase health potions or a single-usage shield.

Three or more matching symbols reap a reward, some grant coins, while others affect the player's health. The game ends when the player runs out of health; the amount of coins collection represnts the player's score.

## Challenges

### Balancing
The most challenging part was balancing the difficulty by adjusting number of trap symbols, health potions, and earning coins to progress. The symbols occurances were based on weighted chances, and play-tested to ensure the player could earn enough coins to buy health potions, but not too offer a challenge.

### Jam Theme
A slot game naturally meets the needs of both themes, _juiciness_ and _paying the price_. I focused on first creating a simple slot mechanic that could be expanded upon later to add triggers for visual/sound events. I relied on assets and tools found on itch.io to create the effects.
