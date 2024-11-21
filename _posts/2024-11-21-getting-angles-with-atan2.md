---
title: "Getting Angles Between Two Objects with `atan2`"
category: codex
layout: codex-entry
tags: [pico8, math]
---

{{ page.date | date: "%Y-%m-%d" }} in [codex](/codex/)

## Goal

Fire a projectile between two objects. The projectile should be "aimed" at the target object, but should not track the target if it moves. 

## Solution

![Playable Example](/assets/p8/atan2.png)

<a href="/assets/p8/atan2.html" data-modal>Playable Example</a> - [GitHub](https://github.com/pixelrip/p8-codex/blob/main/atan2.p8)

## How it Works

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

I won't (ok, can't) explain what [atan2](https://www.lexaloffle.com/dl/docs/pico-8_manual.html#ATAN2) does exactly, but I do know that if we give it the y distance between our objects, followed by the x distance, we'll get the angle between the two objects (something between 0 to 1). Trig, right?

Once we have an angle, we just create a bullet and give it the x (sin) and y (cos) velocity with that angle. 

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

At this point you might be like "Hold on, what? Velocity? Sin? Cos?"

Yeah sorry about that, more math. It might be helpful to step back and take a look at these two items from the [codex](/codex):

1. TODO: Moving objects with velocity
2. TODO: Sin and Cos




