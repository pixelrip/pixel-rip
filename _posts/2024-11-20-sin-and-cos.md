---
title: "Sin and Cos for Movement"
category: codex
layout: codex-entry
tags: [pico8, math, dev]
---

## Goal

Move an object at a given speed and angle using `sin()` and `cos()` for the x and y values.

## Solution

![Playable Example](/assets/p8/movement-diagonal.png)

<!-- The HTML and accompanying JavaScript are compiled from PICO-8. If you are looking to better understand the example source code, ignore these and look at the linked .P8 file in PICO-8 or your favorite IDE. -->
<a href="/assets/p8/movement-diagonal.html" data-modal>Playable Example</a> - [Source Code
](/assets/p8/movement-diagonal.p8)


## How it Works

It is fairly straightforward to get and object to move along an X and Y axis. Let's say you have an object `player` with `x` and `y` coordinates. Some simple math like this would move that player:

```lua

player.x += 1 --increase x position; moves right
player.x -= 1 --decrease x position; moves left
player.y += 1 --increase y position; moves down
player.y -= 1 --decrease y position; moves up

```

But what happens when an object needs to move on the diagonal? It turns out PICO-8's [sin()](https://www.lexaloffle.com/dl/docs/pico-8_manual.html#SIN) and [cos()](https://www.lexaloffle.com/dl/docs/pico-8_manual.html#COS) functions are suited to this. 

Unsurprisingly, a deep understanding of the trigonomety behind these functions eludes me--but I'll leave that to the mathematicians. What I do know is that we can use these functions move an object in any direction with an **angle** and a **speed**.

```lua

angle = 0.125 
speed = 2.5

```

You'll rightly think of an **angle** as a value between 0 and 360°, but in PICO-8  our `sin()` and `cos()` functions need a decimal value in the 0-1 range to represent an angle. If you picture a full 360° circle on a PICO-8 screen, then 0 (or 0°) represents a `down`, and 0.5 (or 180°) represents `up`.

![Angles around a circle](/assets/img/angles.png)

A further breakdown:

- 0.25 is 90° (left)
- 0.375 is 135° (up and left)
- 0.5 is 180° (up) 
- 0.625 is 225° (up and right)
- and so on until...
- 1 is 360° (down, again)

The **speed** is the distance on the screen (pixels) that the object will move per frame. 

So, to make something move on a diagonal, we pass the **angle** into the `sin()` function for `x` (and the `cos()` function for the `y`) then multiply the **speed**.

```lua

angle = 0.125
speed = 2.5

obj.x += sin(angle) * speed
obj.y += cos(angle) * speed

```



## Thanks

Episode 24 of the [Lazy Devs' "Making a Shmup" Tutorial](https://www.youtube.com/watch?v=JQrroRRKbbk&list=PLea8cjCua_P3Sfq4XJqNVbd1vsWnh7LZd&index=24) has a fantastic breakdown of the usefulness of `sin()` and `cos()` for moving on angles. 
