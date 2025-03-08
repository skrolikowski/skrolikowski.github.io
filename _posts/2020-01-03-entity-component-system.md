---
title: Entity Component System
description: This article will cover the topic of the Entity Component System design pattern.
categories: ['design-patterns']
tags: ['design-patterns', 'entity-component-system']

toc: false
published: false
comments: false
---

## Design

### World

The world is what ties it all together, with the following jobs:

* Creating Entities.
* Attaching/detaching Components from Entities.
* Telling the System's to update/draw.
* Filtering out Entities based on Component ownership.

#### Filtering Entities

When it comes time to act upon a System, the System will require a list of Entities to act upon. Whether it be to draw an Entity or update it's Component information, we only need the Entities that the current System is responsible for. An example of this is a *MoveSystem*. This System will only need Entities with *Transform* and *Body* Components.

### Entities

Entities on their own are usually just an ID. The World is responsible for tying Entities and Components together. Your framework may have an actually Entity class, which acts as a query into if a Component is associated with the Entity or not.

### Components

A Component is nothing more than zero or more attributes with a common relation.  You can think of it as a state machine for individual attributes. For example, a *HealthComponent* can have `_health` and `_maxHealth` variables. The System responsible for maintaining Entity health will receive input from other Components (i.e. PhysicsComponent) whether an Entity's health values should be updated and updates accordingly. If the `_health` value reaches 0 then we can trigger the Entity's death state.

It's also important to note that Components can be left empty, and thus act as a tag for the System. An example of this would be a *PlayerComponent*. This component has no viable attributes, but can act as an identifier for finding the player Entity within a System.

It's possible to add private helper functions to a Component, but it's usually just variables and/or enums.

#### List of Useful Component

{: .table .table-striped .w-75 .mx-auto }

| Component                 | Description                                                  |
| ------------------------- | ------------------------------------------------------------ |
| **HealthComponent**       | _`health` & `_maxHealth` attributes, delimiter values for incrementing/decrementing health based on a status effect. |
| **StatusEffectComponent** | You may have status effects Entities can contract. This can be a bit array of status the Entity currently has. |
| **PlayerComponent**       | Variable-less Component used for tagging the Player Entity.  |
| **TransformComponent**    | `_position`, `_rotation`, and `_scale`                       |
| **TrackingComponent**     | Is an Entity within range of tracking? What are it's tracking behaviors? |
|                           |                                                              |

### Systems

When it comes time to act upon a set of Entities, the System will request only the Entities it is capable of updating, based on Component criteria. For example, a MovementSystem (the system responsible for moving entities) will only need to act upon Entities that can move. Stationary entities will be ignored, thus eliminating unnecessary processing time.

Different Systems will usually conform to an interface to detail a System's main processing responsibilities.

* **DrawSystem** - System for loading content and drawing.
* **UpdateSystem** - System for initializing data and updating Component attributes.

#### List of Useful Systems

{: .table .table-striped .w-75 .mx-auto }

| System              | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| **InputSystem**     | Updatable System responsible for updating **TransformComponent** variables. |
| **RenderSystem**    | Drawable System responsible for drawing Entities.            |
| **MovementSystem**  | Updatable System responsible for transforming Entity's position, scale, and rotation. |
| **CollisionSystem** | Updatable System responsible for checking collision information and triggering a response. |
|                     |                                                              |

## Advantages

#### Data Locality

When your CPU is processing thousands of lines of code, the time it takes to request data from memory vs it's own cache can be vast. To our perspective one [cache miss] vs [cache hit] is unnoticeable, but when there are many cache misses it can lead to noticeable differences. This topic has lead to more optimized coding practices, including what can be called *data locality* or *data-oriented design*.

Organizing data in a way that the CPU can access it more affectively (in it's local cache vs RAM) can minimize cache misses.

#### Usability

There is an argument for expandability when it comes to using Entity-Components over the traditional class hierarchy approach. For example, you may need to add additional functionality that could directly or indirectly affect another class in the hierarchy, with Entity-Component you can easily add or remove fun  [example needed].

Another example involves altering Entities mid-game. For example, say your game has introduced several power-ups. It integrate this into a class hierarchy could become a challenge depending on the size and complexity of the code. With Entity-Components, it's possible to add (and remove) Entity attributes with a new Component class and attachment to that Entity.

## Disadvantages

It can be difficult to know where to get started coming from a traditional class hierarchy background. Fortunately there are many examples online to get you started:

* [MonoGame.Extended.Entities - C#](https://github.com/craftworkgames/MonoGame.Extended/tree/develop/Source/MonoGame.Extended.Entities)
* [Artemis ODB - Java](https://github.com/junkdog/artemis-odb/wiki)

The idea of [data encapsulation] can disregarded since all Entities can share one or many Components with other Entities. It is still possible to use inheritance, but not recommended.

## Further Reading

* [Evolve Your Hierarchy](http://cowboyprogramming.com/2007/01/05/evolve-your-heirachy/) - Refactoring Game Entities with Components.
* [Data-Oriented Design](http://gamesfromwithin.com/data-oriented-design) - why you should considering organizing your data.
* [Data Locality](http://gameprogrammingpatterns.com/data-locality.html) - more on why you should consider organizing your data.
