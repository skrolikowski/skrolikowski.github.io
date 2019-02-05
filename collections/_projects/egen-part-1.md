---
layout: post
title: D/Generation - Introduction
slug: d-generation-part-1
excerpt: D/Generation game clone development journal - Part 1.
image: /assets/collections/dgen-03.png
series: dgen
categories: [game-clone, series]
tags: [game-dev, programming]
stats:
  - label: Title
    value: E/Generation
  - label: Language
    value: C#
  - label: Frameworks
    value: ".Net Framework, MonoGame, MonoGame.Extended"
thumbnails:
  footer: Images from MobyGames
  thumbs:
    - /assets/collections/dgen-01.png
    - /assets/collections/dgen-02.png
    - /assets/collections/dgen-03.png
    - /assets/collections/dgen-04.png
    - /assets/collections/dgen-05.png
---

## What is D/Generation?

[D/Generation] is a game that came out in the early 90s. It had an isometric display and pleasant visuals. I came across it in a variety pack, and it soon became a game I frequented. According to the Wikipedia article:

> The game takes place in a slightly cyberpunk futuristic setting in 2021. A French company called Genoq has developed a series of new genetically engineered bioweapons, which have run out of control and taken over Genoq's Singapore lab. The main character is a courier making an emergency delivery by jetpack of an important package to one of Genoq's top researchers, Jean-Paul Derrida (a name likely inspired by the philosophers Jean-Paul Sartre and Jacques Derrida), and who is happily oblivious to the carnage until the lab's doors lock behind him. His customer is ten floors away, all of them crawling with bioweapons. - [Wikipedia](https://en.wikipedia.org/wiki/D/Generation)
{: .quote}

Your job is to lead the player through a maze of rooms, moving from floor-to-floor, each floor increasing in difficulty. The player is faced with several obstacles including, laser barriers, room puzzles, and the crazed bioweapons. Along the way, you will find several weapons and items to assist you. Early on the player obtains a laser gun, which neutralizes most bioweapons, and assists you in toggling triggers across the room.

Additional features & mechanics:

* The player's own laser can bounce off walls, and fortunately can't kill you.
* You will come across friendly NPCs you can save to gain lives.
* Most entities (including you) will be destroyed with one hit, other entities will require a grenade to neutralize them.
* Parts of the story will reveal itself through items in the game and dialogue exchanges.

## Gaming Frameworks Used

#### MonoGame

[MonoGame] is a gaming Framework Class Library (FCL) providing tools for setting up an application window, accessing the keyboard, mouse, and gamepads,  and play audio files.

#### MonoGame.Extended

[MonoGame.Extended] extends upon MonoGame providing several useful modules including like Animation, Camera, GUI, and Particles. These are features that I might revisit and build myself, but for now it's nice to have a head start.

## Game Specifications

#### Screen manager

I want the game to be able to have a title screen, menu screen, game screen, pause screen, and settings screen (and probably more). This will allow us to switch between the screens in an easy fashion, while saving the state of the leaving screen.

**MonoGame.Extended** has such a tool, which will be used at first. With that said, I'd like to dedicate an full article in this series or a separate tutorial. The  goal would be to investigate it's inner workings, providing some  usage examples.

* **Title** - this is sort of what sells the game, so we'll need to make it special with some awesome graphics and explosions.
* **Menu** - the player can start a new game or continue from a saved state.
* **Game** - this will be where the player spends most of their time playing the game.
* **Pause/Settings** - this screen can only be accessed from the *Game* screen. We can make use of MonoGame.Extended's GUI module to create a character/game settings interface.

{% include utils/image.html src="/assets/collections/DGen Screens.svg" %}


#### Physics

I'm going to group collision detection/response, acceleration and velocity all together under game physics. Fortunately MonoGame.Extended has a Collision module, however the documentation is somewhat lacking. Therefore, we'll probably go into that topic at a later date.

When it comes to collision detection, there are lots of stuff to consider. Considering D\Generation was a room-based adventure game, and there weren't many entities on the screen at one time, it doesn't seem reasonable to overcomplicate things. So we may just go with a simple axis-aligned bounding-box strategy.

> **Side note**: If you're looking for a more efficient approach you can research [narrow vs broad phase collision detection](https://www.toptal.com/game/video-game-physics-part-ii-collision-detection-for-solid-objects).

### Entities

We'll need a way to manage all the game entities in our world. The world will be responsible for keeping a list of all the game entities, perform collision detection, and notifying them to update/draw themselves. We may also want to provide a way to access a specific entity or groups of entities (through a tagging system?)

* **AI** - this includes pathfinding, steering behaviors, and finite state machine.
* **Rooms** - I'm not a fan of respawning enemies, so we will need to keep track of each room's state.

### Dialogue System

During the game you'll come across friendly NPCs, which you will have dialogues with where they will provide you with useful information like revealing parts of the story or giving you a password to access a locked room. We will be using [MonoGame.Extended]'s GUI module for this.

{% include utils/image.html src="/assets/collections/dgen-04.png" %}

### Assets

Since I don't have much experience creating graphics for games, I'll probably be using either [Kenney Assets](https://kenney.nl/assets) and/or [AssetForge](http://assetforge.io/). I am no artist, so it may look crude but I'll try to create as appealing asset as I can.

## Conclusion

My goal is to make a game clone of the old 90s game [D/Generation]. I want to keep a journal of my journey to give you some insight on how I do game programming. It should be noted that I am no expert and will make mistakes (and probably correct them at a later date), or I will completely redo a section of the game functionality just cause I believe it could be done better.

I hope you gain something from this series. Enjoy!

## Further Reading

* [.Net Framework]{:target="_blank"}
* [MonoGame]{:target="_blank"}
* [MonoGame.Extended]{:target="_blank"}
* [Collision Detection for Solid Objects](https://www.toptal.com/game/video-game-physics-part-ii-collision-detection-for-solid-objects){:target="_blank"} - detailed article discussing narrow vs broad phase collision detection and different strategies.
* [Collision Detection](http://www.jeffreythompson.org/collision-detection/table_of_contents.php){:target="_blank"} - cool article with examples and visuals.


*[GUI]: Graphical User Interface
*[FCL]: Framework Class Library


[D/Generation]: https://en.wikipedia.org/wiki/D/Generation)
[.Net Framework]: https://docs.microsoft.com/en-us/dotnet/framework/ ".Net Framework"
[MonoGame]: http://www.monogame.net/	"MonoGame"
[MonoGame.Extended]: https://github.com/craftworkgames/MonoGame.Extended "MonoGame.Extended"