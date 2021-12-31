# introduction

how difficult could power calculation be?? very, in fact.  
in theory, calculating power is actually easily the most difficult part :o  

luckily, the acceptable margin of error is, like, very wide.  
the beam can save you, the hole is quite large and all <3

let's start by thinking about the factors that influence power: **terrain**, **slope**, **wind** and **height**.  
ah, there's also **spin** :o


# terrain

terrain is EASY <3  
you just add to the distance some value you get from some table, and that's it.

example of a terrain table, i got it from some random excel by Suphanut:  
![suphanut table](https://i.imgur.com/tKlzzcR.png)

**HEY NOOB!!!!** if you thought that the 95% rough discounted 5% off your total power (like, `280y*0.95 = 266y`), that is **ABSOLUTELY NOT** the case.  
you just look at the table and add the value to your distance.  
like, if the hole is at 250y and you'll use a tomahawk from some 95% rough, you'll add 4y to your distance `= 254y`.

is that really all there is to it? for the vast majority of cases, yes.  
HOWEVER, at a certain power %, the terrain influence starts to get lower, which means that when you want to dunk non-fairways with a very low power % (like 30%), using the standard values will make you overshoot it.  
i have seen streamers struggling with that on wind hill ;(

unfortunately, i can't go into too many details because i haven't tested that much.
at a glance, 80% to 100% definitely behaves normally, and up to 60% that effect is probably relatively irrelevant, if it even exists (like, less than 0.1y).  
however, at 30%, we are already dealing with at least 0.5y difference at a 95% rough :o


# slope

yes, slope does have influence on power.  
i already wrote about that in my [slope theory article](https://github.com/sera-pangya/illuminati-zone/blob/main/slope-theory.md), it's all explained there 👀

basically, having a slope with a x-component will ALWAYS send the ball further, and the influence for each break depends on how many breaks there are (more breaks = slightly less influence).  
using less % power will also very slightly lower the influence for each break.

that effect is considerably important when you are dunking at nearly full power, or when there are a lot of breaks.  
thus, if your calculations don't consider that, you may have problems dunking distances over 300y~


# wind

everyone knows that one, it's `wind * angle * influence`. is that it? yes, it is.  
however, obviously, the difficult part here is figuring out the wind influence.

here's something very FUN and INTERESTING: the wind influence is higher on the distance-axis, compared to the aim-axis (except for spikes, where it's the opposite).  
in other words.. if your hwi (horizontal wind influence) is 1.0, your "vwi" (influence of wind on power) will be greater than 1.0.  
greater by how much? that depends on your shot and on the power %.

i'll paste some dunk 1w 332+0 values that i collected, just to give some idea:

| % | 100 | 95 | 90 | 85 | 80 | 75 | 70 | 65 | 60 | 55 | 50 | 40 | 30 |
| --- | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| **hwi** | 1.359 | 1.118 | 0.919 | 0.756 | 0.625 | 0.519 | 0.433 | 0.364 | 0.307 | 0.262 | 0.224 | 0.165 | 0.121 |
| **vwi** | 1.467 | 1.213 | 1.004 | 0.835 | 0.697 | 0.585 | 0.495 | 0.422 | 0.362 | 0.312 | 0.271 | 0.206 | 0.156 |

as one can see from that data, the vwi is approximately 8% higher than the hwi at 100%, and that difference keeps increasing until it's 40% higher (!) at 10% power.

so well, that's pretty crazy. is that all? no, that's not all.  
there's another highly mysterious effect: the more "backwards" the wind is, the stronger it is.  
really strange? i agree, watch my demo and if you're lucky you'll get it: https://www.youtube.com/watch?v=yKBZao6-_20

generally speaking, that effect is relatively irrelevant (about ~2% difference on the vwi for dunks on strong winds).  
however, for spikes, it can get up to 5% difference for 7-wind :o considering how spike wind influences are relatively pretty high, the difference between doing that or not can be higher than 0.5y!  
that effect applies to EVERY shot.


# height

that's also an easy one, you just do `height * H`. right?  
for those who don't know, H is a value that represents the influence of each 1m on power.  
like, if you have a H of 0.8 and -20 height, you'll discount `0.8 * 20` out of the distance `= 16y`.

to start off, i'll post tonycheese's diagram that he made before 2010 (!) and i post on like half my articles:
![tonycheese](https://i.imgur.com/4ZVUdnm.png)


there are two very important takeaways from that diagram:
- **%** changes the H
- **the height itself** changes the H

**first important thing:** as power % gets lower, H increases (note how the arc at 80% is more influenced by height).  
any exceptions? only when using drugs, like, dunk using 20% or less power, or cobra shots.

**second important thing:** the more + the relative height is, the higher the H. the reasoning is similar.  
if i recall correctly, the only exception is also the cobra shot in + heights~ nice

in that sense, the greatest mistake in the tutorials published by our great predecessors was to not give any solutions as to how to adjust the H according to the height itself (and most didn't even mention the issue).  
that's the main reason as to why many old excels included special calculations for, like, ice spa hole 17, or you could find notes like "+1 caliper pink wind 16" :o  
even for those that knew that this effect existed, it was difficult to put some precise numbers to it. however, most new excels already can put pretty accurate values to it~

to give an example of how that works practically, i'll paste some dunk 1w 332+0y 20-spin H-values that i collected.  
**power %** column, **height** row:

|     | +25m | +20m | +15m | +10m | +5m | +1m | -1m | -5m | -10m | -20m | -30m | -40m | -80m |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **100%** | 0.687 | 0.644 | 0.608 | 0.576 | 0.550 | 0.530 | 0.520 | 0.502 | 0.483 | 0.449 | 0.420 | 0.395 | 0.320 |
| **95%** | 0.954 | 0.869 | 0.805 | 0.752 | 0.708 | 0.680 | 0.670 | 0.638 | 0.610 | 0.561 | 0.520 | 0.486 | 0.387 |
| **90%** | 1.360 | 1.177 | 1.057 | 0.968 | 0.898 | 0.850 | 0.830 | 0.794 | 0.752 | 0.683 | 0.628 | 0.583 | 0.457 |
| **85%** |  | 1.620 | 1.381 | 1.229 | 1.120 | 1.050 | 1.010 | 0.964 | 0.906 | 0.814 | 0.742 | 0.684 | 0.527 |
| **80%** |  | 2.400 | 1.805 | 1.540 | 1.370 | 1.270 | 1.220 | 1.148 | 1.070 | 0.949 | 0.858 | 0.786 | 0.597 |
| **75%** |  |  | 2.406 | 1.909 | 1.638 | 1.490 | 1.440 | 1.342 | 1.241 | 1.086 | 0.974 | 0.886 | 0.664 |
| **70%** |  |  | 3.607 | 2.360 | 1.960 | 1.700 | 1.670 | 1.540 | 1.410 | 1.215 | 1.083 | 0.980 | 0.725 |
| **65%** |  |  |  | 2.917 | 2.274 | 2.000 | 1.900 | 1.728 | 1.568 | 1.342 | 1.184 | 1.067 | 0.782 |
| **60%** |  |  |  | 3.720 | 2.632 | 2.260 | 2.120 | 1.916 | 1.723 | 1.460 | 1.280 | 1.147 | 0.832 |
| **55%** |  |  |  |  | 3.016 | 2.520 | 2.340 | 2.096 | 1.867 | 1.564 | 1.363 | 1.217 | 0.875 |
| **50%** |  |  |  |  | 3.450 | 2.780 | 2.590 | 2.264 | 2.000 | 1.660 | 1.436 | 1.278 | 0.911 |

**those values are only for dunk 1w 332+0y 20-spin!!!!!!**  
generally speaking, lower drives will have higher H-values, and the H-values will be greater for 1w than for 2w, etc~


# spin

most people have already seen, in some form, adjusting the spin for dunks.  
why do that? well that's an easy question, more backspin = more reach. in many cases, the difference between two calipers will be too large (like, nearly 1y), and then it's useful to use spin to simulate "half calipers".

so, let's move on to a more difficult question: how much is 1 spin worth?  
as always, that depends on your shot and the % power. it also depends on the spin itself :o  
at low %s, one spin is worth MUCH less. also, the more backspin you put in, the higher the value of 1 spin.

as an example, here are some values for 1w dunk 332y (difference 20 spin to 21 spin):

| % | 100 | 95 | 90 | 85 | 80 | 75 | 70 | 65 | 60 | 55 | 50 | 40 | 30 | 20 | 10 |
| :-: | :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |  :-: |
| **spin** | 0.73 | 0.68 | 0.63 | 0.56 | 0.49 | 0.43 | 0.37 | 0.32 | 0.27 | 0.23 | 0.20 | 0.14 | 0.10 | 0.06 | 0.03 |

that means 21 spin goes 0.73y further than 20 spin at 100% power and 0 height.

also, as said before, the more backspin, the higher the value of each 1 spin.  
so, in this case, the difference of 20 to 21 is 0.73y, but the difference of 0 to 1 spin is 0.62y 👀

besides that, adding more backspin also results in a slight increase in wind influences (see this video by BooN https://www.youtube.com/watch?v=cVKGVM-hlwE).  
a quick and dirty approximation is 1% increase for 1 backspin~

also, decimal spin and curve exist, down to arbitrary precision. if you can manipulate down to that level of precision, you should take advantage of it for even more precise fine-tuning.

are there any exceptions? yes, cobra beam impact.  
cobra is like completely unaffected by spin before it lands, which makes it impossible to fine-tune power with spin like we can do with other shots. of course, that doesn't stop being relevant for cobra roll-ins, since spin will still influence the ball's trajectory after it bounces.  
unfortunately, it's very important to fine-tune power for cobra beam impact. calculating cobra sucks.

aah, we can wrap this up with a sorta related note: adding curve will make the ball go less far (for any shot).  
in other words, when you add curve, you'll lose some amount of distance that's proportional to the amount of curve added.  
that's one of the reasons (but not the main one) why dunks with curve are difficult.


# adding it all together

so, now that i know how each factor works in isolation, i can just add them all up and we have Good Power Calculation. right??

let's say we start with the distance. then let's consider some random values..
first, we add `+4.0` for the terrain.  
after that, we consider that result (after terrain) to decide which H to use, and calculate `height * H`, add `+6.0` for the height.  
after that, we consider that new result (after terrain and height) to decide on the wind influence, and calculate `wind * angle * influence`, add `+5.0` for the wind.

thus, our power result will be `distance + 4.0 + 6.0 + 5.0`. right? no.  
what's the problem? the problem is that all those factors influence the power result, but when you change the power, that will also change our H and wind influence. circular reference 👀

in this example, we considered our H for the % that we would use considering distance + terrain, but then we added another 11y to the distance!
obviously that's going to result in a relatively large difference on the final % and, as a consequence, on the H.  
the same thing applies for the wind - the higher the %, the higher the vwi.

how do we even deal with that? good luck <3  
one possibility is to just brute force it, test ALL the possible %s and see which % comes the closest. that allows us to know for a fact that we are using the correct values.  
another way is to apply some sort of correction in the H and vwi estimations.

if using the "corrections" method, it's probably best to start with the factors that are least influenced by the %.
the order is terrain, slope, wind, height.


# final thoughts

many of the explained effects aren't considered even in very good excels, which proves that the allowed margin of error for power calculation is indeed very wide (and that those effects are relatively small, for the most part).

in practical terms, there are two things that are most important:
- reasonable approximations for H (according to height and %)
- reasonable approximations for the order in which you add the factors

that's it, good luck :)  
if you have any questions, too bad, i can't really answer everyone's questions T_T  
maybe join Our humble [discord server](https://discord.gg/2UYHA2W85d), if you're lucky you'll get answers~
