---
title: "Getting Angles Between Two Objects with `atan2`"
category: codex
layout: codex-entry
tags: [pico8, math, dev]
---

## Goal

Fire a projectile between two objects. The projectile should be "aimed" at the target object, but should not track the target if it moves. 

## Solution

![Playable Example](/assets/p8/atan2.png)

<a href="/assets/p8/atan2.html" data-modal>Playable Example</a> - [GitHub](https://github.com/pixelrip/p8-codex/blob/main/atan2.p8)

## How it Works

We have two objects in the game. In this case the orange guy and the red guy. First things first, we'll need a way to get the **angle** from the orange guy (`src`) to the red guy (`tgt`).

```lua

function get_angle(src,tgt)
	local y2=tgt.pos.y  
	local x2=tgt.pos.x  

	local y1=src.pos.y  
	local x1=src.pos.x 

	return atan2(y2-y1,x2-x1)
end

```

I won't (ok, can't) explain what [atan2()](https://www.lexaloffle.com/dl/docs/pico-8_manual.html#ATAN2) does exactly, but I do know that if we give it the `y` distance between our objects, followed by the `x` distance, we'll get the **angle** between the two objects 
(something between 0 to 1). Trig, right?

So next we create a bullet object that has an **angle** and **speed**:

```lua

function fire_bullet(src,tgt)
	local bt={}
	bt.spr=3
	bt.x=src.x
	bt.y=src.y
	
	bt.ang=get_angle(src,tgt)
	bt.speed=2
		
	add(bullets,bt)	
end

```

With the **angle** and **speed** attached to each bullet in the `bullets` table we just need to make sure they move using `sin()` and `cos()` on the `x` and `y` on every frame. 

```lua

-- in our update()
for bt in all(bullets) do
	bt.x += sin(bt.ang) * bt.speed 
	bt.y += cos(bt.ang) * bt.speed
end

```


I hear you saying "what the hell do `sin()` and `cos()` have to do with moving bullets on an angle?" Good question! I did my best to explain that here: [Sin and Cos for Movement](/codex/sin-and-cos/).


