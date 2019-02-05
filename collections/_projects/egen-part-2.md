---
layout: post
title: D/Generation - Game World
slug: d-generation-part-2
excerpt: D/Generation game clone development journal - part 2.
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
---

### Before we start...

Before going further, I would like to establish some tools for when things go south. In other words, it would be nice to have the ability to log information in case we need to debug a section of code. Also, I want to get unit testing setup in order to open up test driven development options.

I've written step-by-step instructions for setting these up:

* [Logging w/log4net]({% link _wiki/tutorials/logging.md %})
* [Unit Testing]({% link _wiki/tutorials/unit-testing-xunit.md %})

## Game World

D/Generation is an isometric action puzzler. You will move the character room-by-room, floor-by-floor blasting your way through an array of enemies, while saving NPCs in the process. Let's break this statement down:

#### Isometric

Our game world will be built on top of an isometric grid; each cell being 64x64. While visually our game will look 3D (isometric), as far as our collision detection and other systems are concerned it's 100% 2D. Therefore, our system will work in the cartesian coordinates, but rendering entities will first be converted to their respective isometric coordinates.

#### Action Puzzler

The game will challenge the player through hostile enemies, traps, and puzzles. Towards the beginning of the game the player will come across his first weapon: a laser. The laser is used as an offensive attack, as well as, toggling a walls switch across the room.

#### Room-by-Room, Floor-by-Floor

The player will traverse through a series of rooms to progress to the next floor. Each floor provides different and more difficult challenges. The viewport will only show one room at a time: the room the player is currently in. Every time the player enters a new room, the room state will be saved and next room's state will be loaded. The reason we are saving each room's state:

* **Story progression** - When the player picks up a key in one room, it shouldn't reappear next time the player revisits the room.
* **Clearing rooms shouldn't respawn enemies** - D/Generation's focus was more on puzzles over action, so once a room was cleared the enemies should no longer appear.

#### Saving NPCs

The player will come across non-hostile NPCs that require rescue. After clearing the room the player could then proceed to assist the NPC in escaping. Saved NPCs rewarded the player with an extra life.

Later in the game the player will come across hostile enemies disguised as non-hostiles.

## Grid Implementation

Our `Grid` will contain a `List<Cell>` to hold each `Cell`. Each `Cell` will represent a 64-unit cube in the world. Some `Cell`s will be occupied with a static game entity or unoccupied for dynamic entities to move over. Furthermore, other `Cell`s will not be rendered at all. These `Cell`s will work to create the shape of the floor.

### Grid

<script src="https://gist.github.com/skrolikowski/11d64a71178fdd82cd5af16c356ca3b9.js"></script>

The `Grid`'s job is to contain the `Cell` objects, and provide querying capabilities. This is a good start, but will need to be expanded upon for our purposes.

### Cell

<script src="https://gist.github.com/skrolikowski/cb379049261619301bc110dc79138a2d.js"></script>

Each `Cell` knows enough information to provide information of where it is in the game world. Notice how everything is set once in the constructor as opposed to every time it's called. Obviously, we are signing the agreement to never change the `Size` of a `Cell`. This is fine in our case.

### Making It Isometric

Imagine you are floating above a 64x64-unit cell (pictured on the left). This will be our true world coordinate system. Now imagine that you are staring eye-level at the cell as if you were the green triangle. Now you move up 120 degrees and are now looking at the isometric view (pictured on the right).

{: .text-center .p-3 }

<img src="/assets/collections/Cartesian-vs-Isometric-01.svg" width="75%">

The following is code for finding the origin position of each cell in the grid:

```csharp
// C#

float unit     = cell.width / 2;
float halfUnit = unit / 2;

int x = (col - row) * unit;
int y = (col + row) * halfUnit;
```

However, this is only half the conversion. In order to draw a polygon we must provide the renderer every vertex position. The following code shows how to obtain each vertex (relative to it's origin):

```csharp
// C#

float unit     = cell.width / 2;
float halfUnit = unit / 2;

List<Vector2> vertices = new List<Vector2>
{
	new Vector2( 0,    0       ),  // Origin
	new Vector2( unit, halfUnit),
	new Vector2( 0,    unit    ),
	new Vector2(-unit, halfUnit)
};
```

### Adding Depth

The next step is to add the illusion of 3D by turning the grid cells into cubes. We'll do this by expanding our list of `vertices`. Below is a diagram of what our isometric cube will look like in relation to it's origin point. Notice that I chose to grow the cube up (negative direction).  This is because I want to think of the game floor to be at level 0.

{: .text-center .p-3 }

<img src="/assets/collections/Isometric-Cube.svg" width="75%">

The following code shows the 4 new vertices:

```csharp
// C#

vertices.Add(vertices[0].Translate(0, unit * -depth));
vertices.Add(vertices[1].Translate(0, unit * -depth));
vertices.Add(vertices[2].Translate(0, unit * -depth));
vertices.Add(vertices[3].Translate(0, unit * -depth));
```

What's happening here is we are building off of the existing polygon by adding an isometric `unit * -depth`. Depth here represents how many isometric units above/below we are translating. The idea behind this is we now have the ability to not only query a cell by row and col, but also how high or low above the game floor.

Below is another diagram to re-iterate the measurements of our iso-cube:

{: .text-center .p-3 }

<img src="/assets/collections/Isometric-Measurements.svg" width="75%">

### Putting It All Together

<script src="https://gist.github.com/skrolikowski/cb379049261619301bc110dc79138a2d.js"></script>

And finally, the result is an 8x8 IsoGrid:

{: .text-center .p-3 }

<img src="/assets/collections/IsoGrid.png" width="75%">

## Conclusion

We've just created the foundation for our game world. Each isometric cell (or more) will represent a `Node`, which will be introduced in the next section when we cover the [Entity Component System].

One topic we may need to revisit is the drawing order. Essentially what might happen is we may witness sprites overlapping when they shouldn't depending on which order they are drawn. Approaches to fix this are referred to as the z-sorting or depth-sorting. We'll have to tackle this when later on down the road.

## Further Reading

* [Creating Isometric Worlds: A Primer for Game Developers](https://gamedevelopment.tutsplus.com/tutorials/creating-isometric-worlds-a-primer-for-game-developers--gamedev-6511)
* [Drawing isometric boxes in the correct order](http://shaunlebron.github.io/IsometricBlocks/)

{% include wiki-footer.html %}