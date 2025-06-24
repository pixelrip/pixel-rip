---
title: "A Very Basic Example of Collision Detection"
category: codex
layout: codex-entry
tags: [pico8, dev]
---

## Goal

Figure out if two objects in a 2D plane "collide." 

## Solution

![Playable Example](/assets/p8/collision.png)

<!-- The HTML and accompanying JavaScript are compiled from PICO-8. If you are looking to better understand the example source code, ignore these and look at the linked .P8 file in PICO-8 or your favorite IDE. -->
<a href="/assets/p8/collision.html">Playable Example</a> - [Source Code](/assets/p8/collision.p8)


## How it Works

This approach to detecting collisions doesn't ask "are these two objects colliding?" as much as it asks **"are these two objects definitely 100% NOT colliding?"**

How do we do that? With any two objects we can ask 4 quick questions to find out if the objects are definitely **not** colliding. 

Question 1: Is the top of Object A **lower** in 2d space than the bottom of a Object B? 

![First Check](/assets/img/collision-check-1.png)

If the answer is yes, these objects can not possibly be touching. If the answer is no, we don't know for certain that they are touching, so we move on to question 2. 

Question 2: Is the right side of Object A further left than the left side of Object B?

![Second Check](/assets/img/collision-check-2.png)

Again, if yes then there is no possible way they could be colliding. If no, we move on. I imagine you can see where this is going.

Question 3: Is the bottom of Object A higher than the top of Object B?

![Third Check](/assets/img/collision-check-3.png)

Question 4: Is the left side of Object A further right than the right side of Object B?

![Fourth Check](/assets/img/collision-check-4.png)

If all four of these checks pass, we know for certain these two objects are definitely 100% NOT colliding. If one of these checks does not pass, we can assume the opposite. 

## Coding It

First things first, we define two objects, with an `x` and `y` position--but we'll go one step further and define some hitbox coordinates based on the size of the sprite. 

```lua

player={
    spr=1, --sprite number
    x=60,  --x position on screen
    y=100, --y position on screen
    hb={
        x1=1,
        y1=0,
        x2=6,
        y2=7 }  -- hitbox
}

enemy={
    spr=2,
    x=60,
    y=100,
    hb={
        x1=0,
        y1=0,
        x2=7,
        y2=7}
}

```

The hitbox is simply four coordinates identifying where in the sprite we want to make "collidable." In my example both sprites are 8x8. The enemy sprite fills that entire 8x8 space, so I want everything from 0 to 7 in both directions to be collidable. The player sprite is slightly narrower, so I only want everything from 1 to 6 on the `x` to be part of the hitbox. Maybe this sketch will help that make sense?

![Sketch of Hitbox Coordinates](/assets/img/hitbox-example.png)

Once we have our objects, we need to keep an eye on them every frame to see if they collide. In my example I have this baked into my main `_update` function. So every frame `collided` will return true or false as to whether two objects are colliding (in this case player and enemy). If they do collide, I'm just going to increment a variable called `collisions`. 

```lua

function _update()
	...

	-- check for collisions
	if collided(enemy,player) then
	 collisions+=1
	end
end

```

How does `collided()` know what to do? The function calculates the boundaries of both objects (top, bottom, left, right) by adding each object's position to its hitbox coordinates. Then it applies our four questions as conditional checks—if any of these checks return true, we know the objects aren't colliding and can immediately return false. Only if all four checks fail do we conclude the objects must be colliding.

```lua 

function collided(a,b)
	-- find top,bot,lef,rig
	local a_top=a.y+a.hb.y1
	local a_bot=a.y+a.hb.y2
	local a_lef=a.x+a.hb.x1
	local a_rig=a.x+a.hb.x2
	
	local b_top=b.y+b.hb.y1
	local b_bot=b.y+b.hb.y2
	local b_lef=b.x+b.hb.x1
	local b_rig=b.x+b.hb.x2

	-- rule out collsions
    if(a_top>b_bot) return false
    if(b_top>a_bot) return false
	if(a_lef>b_rig) return false	
	if(b_lef>a_rig) return false
	
	return true
end

```
