---
layout: post
title: D/Generation - Entities
slug: d-generation-part-3
excerpt: D/Generation game clone development journal - part 3.
image: /assets/collections/dgen-03.png
series: dgen
categories: ['game-clones', 'series']
tags: ['game-dev', 'programming']
stats:
  items:
  - label: Code
    value: "[Release - v0.1.0](https://github.com/skrolikowski/Genoq/releases/tag/v0.1.1)"
---


## Introduction

Last [part]({% link _projects/egen-part-3.md %}) we set up a grid, which is essentially just a mapping system used for locating a cell in our isometric world. We'll use this for loading level maps and the level editor. You can find  the code for the previous article [here](https://github.com/skrolikowski/Genoq/releases/tag/v0.1.0).

The topic of this section is regarding entities and their attributes. I'll also touch on accepting user input so we can move our entities around the world.

### Entity-Component Systems

[Entity Component System] (ECS) is the design pattern that attempts to sidestep traditional class hierarchies and use a more componentized approach. I like to think of it like a food buffet where the Entities are plates and Components are the food selections. Attaching Components to Entities adds additional behavior or functionality to that entity. For example, attaching a `Physics` Component to an entity causes the entity to now obey the laws of physics. Some Components are empty classes that solely serve as a tag for Systems.

Systems are continuously running, manipulating entity attributes or performing other tasks. Systems can be categorized as follows:

* **Update System** - performs updates on zero or more Entities.
* **Draw System** - renders zero or more Entities (or other content).
* **Entity Process System** - acts upon a specific set of Entities.

Finally there's the World, which encapsulates everything and performs the following tasks:

- Manages Entities (i.e. creating a new Entity, removing an Entity).
- Retrieves Entities with a specific combination of Components for Systems.
- Triggers every System once a frame.

...

One flaw in using class hierarchies is the attributes or methods of a parent class may or may not have any value in the inherited classes. A solution would be further dichotomize your hierarchies, but may create complications down the road. 

Some advantages to this approach:

- **Improved data locality** - [This article](http://gameprogrammingpatterns.com/data-locality.html) goes over the topic better than I could. Essentially our game entity and their attributes will be stored in arrays for efficient query/processing for the CPU.
- **Expandability** - The ability to add/remove components or systems down the road should be relatively simple.

> At the time of writing this article, in order to use [MonoGame.Extended] ECS module you'll will need to reference the pre-release packages instead (v3.6.1). Please review [this section](http://docs.monogameextended.net/NuGet-Pre-Release/){: target="blank"} from their wiki for instructions.

## Time to Code



## Further Reading

- [Data Locality](http://gameprogrammingpatterns.com/data-locality.html)

{% include wiki-footer.html %}