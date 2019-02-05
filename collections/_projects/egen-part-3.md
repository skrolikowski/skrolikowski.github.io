layout: post
title: D/Generation - Entities
slug: d-generation-part-3
excerpt: D/Generation game clone development journal - part 3.
image: /assets/collections/dgen-03.png
series: dgen
categories: ['game-clones', 'series']
tags: ['game-dev', 'programming']
stats:

  - label: Title
    value: E/Generation
  - label: Language
    value: C#
  - label: Frameworks
    value: ".Net Framework, MonoGame, MonoGame.Extended"

____

Last article we setup the game world, which was essentially just a grid.

## Entity Component System

An [Entity Component System] (ECS) is the design pattern I plan on using for the game. The basic idea behind Entity-Components is to sidestep class hierarchies and build our game entities buffet-style; adding only the necessary attributes (i.e. Components). Some entities will move, while others will be stationary. Some entities will have AI, while others won't. The ECS approach attempts to un-bloating every entity with functionality it may or may not need.

Some advantages we should benefit from:

- **Improved data locality** - [This article](http://gameprogrammingpatterns.com/data-locality.html) goes over the topic better than I could. Essentially our game entity and their attributes will be stored in arrays for efficient query/processing for the CPU.
- **Expandability** - The ability to add/remove components or systems down the road should be relatively simple.

### Entities



| Game Objects                               |
| ------------------------------------------ |
| Player                                     |
| Enemies                                    |
| Projectiles                                |
| Environment (e.g. walls, doors, furniture) |

## Further Reading

- [Data Locality](http://gameprogrammingpatterns.com/data-locality.html)

{% include wiki-footer.html %}