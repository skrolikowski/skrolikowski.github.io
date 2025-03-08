---
title: How To Get Started
author: shane
description: Getting started in game development can be hard. This article tries to eliminate some of the anxiety and provide tips on getting started.
categories: [Game Development]
tags: [game-dev]

image:
  path: /assets/img/covers/pexels-photo-1373100.jpeg
  alt: Photo by Kevin Bidwell from Pexels

pin: true
toc: true
comments: false
published: true
---

## Where Do I Start?

It was probably about 2 years ago when I became serious about (becoming good at) game development. Prior to this I'd conceptualize or read some inspiring article, but it never went past the idea. The purpose of this article (and future articles on the topic) is to share my experiences as complete beginner, self-taught game developer.

With that said, I do have 10+ years of programming experience (mainly PHP/JavaScript) and I have taken at least 2 courses on the topic. However, I don't consider homework assignments to be adequate when compared to real world experiences. Sitting down and saying, "I'm going to build a great game" is hard, even for the more experienced. For those of us that inspire to enter the field, this is especially difficult since we have no idea where to start.

Coming from a limited background, I wanted to share a couple tips from my experiences starting out on my own.

### Clear Your Mind

The first thing to do is throw out all your great game ideas. Stop thinking about the last great game you played and stop saying, "I want to make a game just like that." You'll need to think smaller. Think Pong.

What I found helpful was to go through (this [list](http://inventwithpython.com/blog/2012/02/20/i-need-practice-programming-49-ideas-for-game-clones-to-code/)). Try building each game, one-by-one from scratch (with the help of a game framework, of course). At first you'll have no idea what you're doing, but eventually you'll build confidence in your abilities and soon start to do it like it's second nature.

### Picking A Language

I'd say this comes down to a few factors:

1. **Choose what's comfortable** - considering most programming languages follow similar semantics, but differ in syntax, pick a language you are comfortable with. Focusing on one won't hinder you from easily learning another later <small>(of course going from python to c++ is more difficult that the opposite)</small>.
2. **Based on a framework?** - I started with Lua/Love2D, then experimented with C++/OpenGL, and now trying C#/MonoGame.Extended. Bottom line is you may choose the framework, or the framework may choose you.
3. **Using a game engines?** - some game engines (i.e. Unity, Godot) allow you to code in several different languages, while others don't.

### Framework vs From Scratch

If you're just getting started, you'll definitely want to choose a framework.

#### Yes, Please!

Your anxiety will subside and you'll become more confident. You may even find yourself exploring the library files to see what's happening behind the scenes. Then you'll venture into creating your own framework.

Below is a list of frameworks with their corresponding language:

- [Lua](https://www.lua.org/)/[Love2D](https://love2d.org/) - Love2D provides you with several modules to build a 2D game. Plus it has a large, active community.
- [Python](https://www.python.org/)
  - [pyglet](https://pyglet.readthedocs.io/en/pyglet-1.3-maintenance/)
  - [pygame](https://www.pygame.org/news)
- [C#](https://docs.microsoft.com/en-us/dotnet/csharp/)/[MonoGame](http://www.monogame.net/)[Extended](https://github.com/craftworkgames/MonoGame.Extended)

#### No, thank you.

Choosing to build a framework from scratch is a multi-faceted journey into many topics causing you to wish you would have paid attention in school. Regardless, it'll definitely push you to your limits and you will learn lots from it. Some topics include:

- **Physics**

  - **Forces** - Acceleration and environmental factors. Do you want gravity in your world? How will your entities interact with surfaces? In the air?
  - **Collision Detection/Response** - You could use brute force tactics or more efficient broad vs narrow approaches for detection. Learning how to detect collision can be grueling on the CPU, especially when you have thousands of calculations running every fraction of a second.

- **Input/Events** - Do you want to handle just keyboard events? How about mouse or gamepad?

- **Particles** - Not necessary but allows you to add cool effects (e.g. flames, explosions)

- **Math**

  - **Vectors** - Using a [Euclidian Vector](https://en.wikipedia.org/wiki/Euclidean_vector) as opposed to individual x, y (and z) variables opens you up to the wonderful properties of [vector math](https://mathinsight.org/vector_introduction). For example, how do you find the direction from an *origin* to a *target*?

    Simple: ```target - direction = direction vector```

  - **Matrix** - When it comes to 3D, you'll want to understand what matrices are used for and how multiplication works.

### Conclusion

This is just an introduction to my beginning journey into game development. The intent was to help ease the anxiety and to get you started in your adventure. I hope to continue on this topic and create many more articles in the future.

### Further Reading

- [List of Game Engines](https://en.wikipedia.org/wiki/List_of_game_engines)
- ["I Need Practice Programming": 49 Ideas for Game Clones to Code](http://inventwithpython.com/blog/2012/02/20/i-need-practice-programming-49-ideas-for-game-clones-to-code/)
- [A list of Game Development resources to make magic happen](https://github.com/mbrukman/awesome-gamedev).

---
Photo by [Photo by Kevin Bidwell from Pexels](https://www.pexels.com/photo/game-cartridges-1373100/)