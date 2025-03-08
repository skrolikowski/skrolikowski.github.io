---
title: "Hop It & Profit"
author: shane
description: A grid based game where the player must reach the goal while avoiding obstacles.
categories: [Projects, Professional]
# tags: [typescript, javascript, python, game-dev, casino]

image:
    path: /assets/img/projects/hoh/hopit/00.jpg
    alt: This project was developed by House of How for DraftKings. All rights to the game and its assets belong to DraftKings.
  
toc: true
comments: false
published: true
hidden: true
---

### Overview
While working at House of How, I contributed to a goal style game developed for DraftKings called Hop It & Profit. My role focused on front-end development, specifically responding to real-time game state changes provided through server responses.

A grid based game where the player makes a wager, and then progresses towards the goal while avoiding obstacles. If the player hits an obstacle, they lose their wager; however each row they progress earns a multiplier on their wager. They can cash out at an time or continue for higher rewards.

### Information
- **Client** - DraftKings (via [House of How](https://houseofhow.com/))
- **Timeline** - Oct. 2021 - Jan. 2022
- **Platform** - Web Browser
- **Genre** - Casino / Gambling
- **Tech Stack** - TypeScript/JavaScript, Python

[Demo](https://casino.draftkings.com/games/5e413a6d-d52b-4ade-81d9-9e9d8e794762/draftkings-hop-it--profit/demo)

![](/assets/img/projects/hoh/hopit/01.jpg){: w="200" .normal }
![](/assets/img/projects/hoh/hopit/02.jpg){: w="200" .normal }
![](/assets/img/projects/hoh/hopit/04.jpg){: w="200" .normal }
![](/assets/img/projects/hoh/hopit/03.jpg){: w="200" .normal }
![](/assets/img/projects/hoh/hopit/05.jpg){: w="200" .normal }
![](/assets/img/projects/hoh/hopit/06.jpg){: w="200" .normal }


### Contributions
My role focused on front-end development, specifically responding to real-time game state changes provided through server responses.



{%
  include embed/video.html
  src='assets/video/HIP_07.mp4'
  types='mp4'
  title='Demo video'
  autoplay=true
  loop=true
  muted=true
%}

The game had a two theme mechanic where the player could swap between two unique themes.

{%
  include embed/video.html
  src='assets/video/HIP_08.mp4'
  types='mp4'
  title='Demo video'
  autoplay=true
  loop=true
  muted=true
%}


### Challenges
__The first challenge...__ was creating a responsive layout that would work on both portrait & landscape orientations. Since the player could press on game tiles to move the character, the clickable areas had to resize in response to screen size changes.

__The second challenge...__ had to do with the amount of animations needed to run at once, especially on mobile. The first approach I used was animating spritesheets via CSS, but lead to choppy animations and was eventually scrapped for [Spine](https://esotericsoftware.com/).

__The third challenge...__ was integrating an input field over the game canvas. The input field was used to allow the player to enter any bet amount they wished. There were issues with how the field wouldn't receive focus on some browsers or displayed odd behaviors on others. The solution was to create a custom input field that would receive focus and allow the player to enter their bet amount.





