---
layout: wiki
title: Unit Testing with xUnit and Visual Studios
excerpt: This article will detail how to setup xUnit within your Visual Studio's project.
image: /assets/covers/pexels-photo-546819.jpeg
categories: ['tutorials']
tags: ['unit-testing', 'visual-studios', 'pragmatic', 'programming', 'c#', '.net']
difficulty: easy
---

## Introduction

This article explains how to setup [xUnit] to use in your [Visual Studio]'s project and create the two main different unit test types in [xUnit]. Also, we'll set it up so we can run our tests within [Visual Studio]'s Test Explorer.

Unit Testing is just one or many approaches to testing your software. The term *unit* can be thought of as a function or a code block that represents a single idea. These tests are good for making sure the fundamental logic is guaranteed to be in place and working.

Interested in learning more about the [benefits of unit testing]?

## Setup

* Create or open an existing project.
* Right-click the project root from within the **Solution Explorer** tab.
* Select *Add > New Project...*

{% include utils/image.html src="/assets/collections/VS2017_AddProject.PNG" %}

* Look for *xUnit Test Project (.Net Core)* under the Visual C# language menu.
* Create a new project and name your new project (use whatever naming convention suites you).

{% include utils/image.html src="/assets/collections/VS2017_xUnit.PNG" %}

* So now you should have a regular project and an xUnit project under one solution.

{% include utils/image.html src="/assets/collections/VS2017_SolutionExplorer_xUnit.PNG" %}

> **Note**: By selecting *xUnit Test Project (.Net Core)* when creating a new tests project all the NuGet packages were automatically installed and linked up. If you ever create a regular console project you can always go back and add the xUnit packages manually.

## Writing Unit Tests

...


## Terminology

* **Project** - with regards to Visual Studio, a folder containing a single `.csproj` file.
* **Solution** - with regards to Visual Studio, a folder containing a single `.sln` file, plus one or more project  folders.

## Further Reading

* [Getting Started with xUnit.net](https://xunit.github.io/docs/getting-started/netfx/visual-studio#write-first-theory){: target="_blank"}
* [Benefits of Unit Testing]

[Visual Studio]: https://visualstudio.microsoft.com/
[xUnit]: https://xunit.github.io/
[Open/Close Principle]: https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle
[Test Driven Development]: https://en.wikipedia.org/wiki/Test-driven_development
[benefits of unit testing]: {% link _posts/2019-01-30-benefits-of-unit-testing.md %}

{% include wiki-footer.html %}