---
title: "Getting Direction Angles with `atan2`"
date: 2024-11-19
category: codex
layout: codex-entry
tags: [pico8, math]
github: nil
---

Todo: Embed goes here

## Goal

Fire a projectile between two objects. The projectile should be "aimed" at the target object, but should not track the target if it moves. 

## How it Works

- 

We have two objects in the game. In this case the orange guy and the red guy. First things first, we'll need a way to get the angle from the orange guy (src) to the red guy (tgt).

```lua

function get_angle(src,tgt)
	local y2=tgt.pos.y  
	local x2=tgt.pos.x  

	local y1=src.pos.y  
	local x1=src.pos.x 

	return atan2(y2-y1,x2-x1)
end

```

TODO: Explain ATAN2

In this case [atan2](https://www.lexaloffle.com/dl/docs/pico-8_manual.html#ATAN2) will 


Next, we have a function that creates a bullet object and adds to it our `bullets` table.

```lua

function fire_bullet(src,tgt)
	local ang=get_angle(src,tgt)
	local vx=sin(ang)*2
	local vy=cos(ang)*2
	
	local bt={}
	bt.spr=3
	bt.pos={
		x=src.pos.x,
		y=src.pos.y
	}
	bt.vel={
		x=vx,
		y=vy
	}
	
	add(bullets,bt)	
end

```

We calculate the x and y velocity with the `sin` and `cos` of our angle calculation.

TODO: Why / how?

