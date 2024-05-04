# introduction

hiya it's Sera~ :o  
let's talk about slope mechanics - how they work and their effects on the ball.

just to be clear, this will NOT be about how to "count breaks".  
however, just so you don't leave totally empty-handed on that regard, i'd recommend learning some variation of the mycella method ;p  
that is, move your aim until you "maximize" the slope, get some number from that, then move back to the aiming point, and figure what's your "aiming point slope" by multiplying that maximum-slope by the angle difference between the maximum-point and the aiming-point. not super easy to explain, but that's the fundamental principle, i.e. `effective slope = maximum slope * angle`)

# slope components

at this point, "everyone" already knows that slopes have a x-component and y-component.  
some examples (values obtained by accessing the game memory, season4-like old hit bar view):

| ![0.08x](https://i.imgur.com/ltZCYp8.png) | ![0.08y](https://i.imgur.com/3edZNVN.png) | ![0.08x, 0.08y](https://i.imgur.com/UKbZ1tc.png) |
|-------------|-------------|-|
| **0.08x, 0.00y** | **0.00x, 0.08y** | **0.08x, 0.08y** |

# y-component

let's start with the good news: the y-component is COMPLETELY irrelevant for calculation.  
it doesn't even have any influence on power (video):

[![slope-y video](https://img.youtube.com/vi/Yw9XEveIh8w/0.jpg)](https://www.youtube.com/watch?v=Yw9XEveIh8w)  
(the small difference between results is because the aim wasn't perfectly the same for every shot, so we have a very very small slope x-component)

thus, the **0.00x, 0.08y** example is calculated in exactly the same way as 0 slope. so, what DOES the y-component do?  
as you move your aim, the y-component turns into x-component, and the other way around. if you turn 90 degrees, the x-component and the y-component will be switched (all x becomes y, and all y becomes x) :o  
in practical terms, the y-slope can also be really annoying in that it makes the slope harder to guess ;(

# x-component

if the y-component doesn't do anything, that must mean all the slope influence in your shots comes from the x-component.  
that is indeed the case :o the x-component will ALWAYS have an effect on both aim and power (thus, if your calculations don't change anything in power according to the slope, they're ~~wrong~~ inaccurate).

just like wind, slope also influences the trajectory throughout the entirety of the shot.

## slope influence on aim

since both slope and wind influence the trajectory throughout the entirety of the shot, it seems like a good idea to relate slope influence to wind influence.  
the formula that i use is to calculate the influence of slope on aim is:

``x-component * final hwi * % * constant``

**x-component:** slope x-component at the final aiming point, some would call that the "mycella result".  
the scale (breaks, pixels, aliens) doesn't matter, as long as you are using the appropriate constant for your scale.

**final hwi:** wind influence used for the shot, after considering height and whatever are your favourite drugs to use in the process of figuring it out.

**%:** % power that's going to be used for the shot.  
like, if you'll use 94% power, multiply by 0.94

**constant:** a number that depends on your shot and the scale that you're using to measure the x-component. basically, the point is to relate the value of 1 x-component to the wind influence.  
thus, if you count by pixels or aliens, you'll use a different constant to someone who's counting breaks (but, in the end, the result of `constant * x-component` should always result in aiming by the same amount, of course).  
the constant varies according to the shot type and power - like, the 3w-constant will be lower than the 2w-constant, and the 1w-334 constant will be greater than the 1w-266 constant.


## slope influence on power

the influence of slope on power will also change according to drive, shot type and % (though this % effect is MUCH smaller).  
slope will ALWAYS send your ball further 👀 (except for cobra and spike, where it has like no effect, just like terrain also doesn't have like any effect on power)

there's also a small variation in the influence according to the amount of breaks - the more breaks we have, the less each individual break counts.  
like, for 1w dunk 332y 20spin 100% the first break is worth 0.075y, but at 10 breaks, each break is worth only ~0.068y :o

the margin of error for power calculations is relatively wide, so i didn't bother too much.  
it's just important to know that those things exist~


## random example (why not)

**video**  
[![slope demo video](https://img.youtube.com/vi/uTjE33t8kxc/0.jpg)](https://www.youtube.com/watch?v=uTjE33t8kxc)

### first step: mycella (to find out the x-component)
~16.1 breaks (converted to oldschool breaks scale)  
angle difference between maximum-x and aiming point: approximately 62.7 degrees

``x-component = 16.1 * cos 62.7`` ``= 7.4``

### second step: x-component * final hwi * % * constant
``7.4 * 1.020 * 0.9278 * 0.3321`` ``= 2.331y``  
this constant (0.3321) is meant for use with this scale and this shot ONLY. if you count by pixels, you'll get another result for the x-component and thus you should also use a different constant (but the end result should still be 2.331y)..

then don't forget to add the wind, of course

### slope influence on power

i don't know, discount ``7.4 * 0.075 * 0.926 * 0.99278`` ``= 0.51y`` off the distance.  
that's ``x-component * how much the first break is worth * effect of having many breaks * % effect``  
absolutely no clue how good the effect values are, i just got some little bits of data and made up some formulae randomly. they work pretty well, don't ask

good luck -.( ' ~ ' ).- if you have any questions, too bad, that's it


## so what?

there's a lot of flat out wrong information circulating around.  
now well, the beauty of it is that you can compensate one mistake with another, and that can make things work for your immediate purposes <3  
but if you want consistent slope data that doesn't change across different shots and drives, this is the way to go~



## BONUS: peeking at the game memory

this part is up for those who.. are curious? wanna develop their own "assists"?  
well, whatever.  

in fact, there are two values in the game memory that represent the slope values. however, both values represent *both* a x-component and a y-component, according to the angle difference between our aiming-point and the hole's "zero-point".

**important:** the hole's zero-point was defined by the map creators when they created the hole (basically the central point in the modeling software XD), it's rarely on the pin. so, for the most part, this is NOT like the wind angle that we use for calculations, and unfortunately there's no reasonable way to find it without gm commands or memory access T_T

many consider `v1` to be `slope-x` and `v2` to be `slope-y`, but i don't like those names, because both values have a x-component and a y-component (that changes according to our aim).  
it's probably easier to understand with an example:

```
v1: 0.042  v2: 0.134     angle difference: 71.9

v1x: v1 * cos(a)   |   0.04 * 0.31 = 0.013
v1y: v1 * sin(a)   |   0.04 * 0.95 = 0.040
v2x: v2 * sin(a)   |   0.13 * 0.95 = 0.127
v2y: v2 * cos(a)   |   0.13 * 0.31 = 0.042

vx: (v1x+v2x) * 100 | (0.013+0.127) * 100 = 14.0
vy: (v1y+v2y) * 100 | (0.040+0.042) * 100 = 8.2
```

for more examples, watch my auto-slope video :o https://www.youtube.com/watch?v=l6VGsviUL1M

this was all done for scientific purposes. also, for some mysterious reason, some private servers actually allow these kinds of memory readings as a matter of policy (like, it's totally allowed).
so uh, do with that what you will~

that's it, good luck :)  
if you have any questions, too bad, i don't really care all that much :c  
you could join the [dead discord server](https://discord.gg/2UYHA2W85d) or just find me elsewhere i guess~
