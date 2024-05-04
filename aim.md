# introduction

after reading all those complications with power, it's relatively easier to understand aim :o however, the amount of error allowed is much lower.

what are the factors that influence your aim? wind and slope.  
height also influences indirectly, by changing the influences of those factors.


# wind

as the ancients already knew, the wind effect is `wind * angle * influence`. of course, the difficult part (theoretically) is figuring out what the influence is.  
so, which factors influence the influence (heh)? the general principle is that, the more time the ball is up in the air, the more it is influenced (it's not JUST that, but that's pretty intuitive).

thus, let's repeat the obvious conclusion: the higher the power % the more influence we have, and the more downhill the relative height the more influence we have.  
with regards to the %, starting at some point, the influence starts to decrease VERY rapidly:

| % | 100 | 95 | 90 | 85 | 80 | 75 | 70 | 65 | 60 | 55 | 50 | 40 | 30 | 20 |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **hwi** | 1.357 | 1.120 | 0.921 | 0.758 | 0.627 | 0.519 | 0.434 | 0.365 | 0.308 | 0.262 | 0.223 | 0.166 | 0.121 | 0.084 |

height is way more complex. i'll just post some hard data (1w dunk 332+0, as always) and let the reader take their own conclusions~  
the values represent the relative effect that height has on hwi (like, if the hwi for 100% at 0m is 1.3590, the hwi for 100% at +10m will be `1.3590 - 0.1016 = 1.2574`)

|  | +25m | +20m | +15m | +10m | +5m | +1m | -1m | -5m | -10m | -20m | -40m | -80m |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **100%** | -0.2763 | -0.2121 | -0.1542 | -0.1016 | -0.0486 | -0.0097 | 0.0096 | 0.0480 | 0.0881 | 0.1707 | 0.3245 | 0.5732 |
| **95%** | -0.3068 | -0.2329 | -0.1670 | -0.1100 | -0.0514 | -0.0097 | 0.0096 | 0.0480 | 0.0914 | 0.1780 | 0.3342 | 0.5893 |
| **90%** | -0.3438 | -0.2539 | -0.1800 | -0.1155 | -0.0547 | -0.0105 | 0.0104 | 0.0514 | 0.0964 | 0.1847 | 0.3437 | 0.6009 |
| **85%** |  | -0.2811 | -0.1911 | -0.1205 | -0.0585 | -0.0113 | 0.0113 | 0.0504 | 0.0992 | 0.1889 | 0.3486 | 0.6048 |
| **80%** |  | -0.3213 | -0.2056 | -0.1253 | -0.0601 | -0.0113 | 0.0112 | 0.0516 | 0.1005 | 0.1909 | 0.3486 | 0.6037 |
| **75%** |  |  | -0.2217 | -0.1286 | -0.0603 | -0.0113 | 0.0113 | 0.0537 | 0.1025 | 0.1917 | 0.3485 | 0.5992 |
| **70%** |  |  | -0.2618 | -0.1349 | -0.0616 | -0.0113 | 0.0113 | 0.0533 | 0.1020 | 0.1904 | 0.3438 | 0.5901 |
| **65%** |  |  |  | -0.1413 | -0.0630 | -0.0113 | 0.0113 | 0.0530 | 0.1012 | 0.1880 | 0.3390 | 0.5799 |
| **60%** |  |  |  | -0.1558 | -0.0637 | -0.0113 | 0.0113 | 0.0525 | 0.1002 | 0.1849 | 0.3325 | 0.5690 |
| **55%** |  |  |  |  | -0.0643 | -0.0112 | 0.0112 | 0.0530 | 0.0998 | 0.1832 | 0.3277 | 0.5585 |
| **50%** |  |  |  |  | -0.0648 | -0.0113 | 0.0112 | 0.0531 | 0.0991 | 0.1809 | 0.3213 | 0.5486 |
| **40%** |  |  |  |  | -0.0711 | -0.0129 | 0.0112 | 0.0510 | 0.0959 | 0.1745 | 0.3084 | 0.5287 |
| **30%** |  |  |  |  |  | -0.0113 | 0.0113 | 0.0518 | 0.0954 | 0.1718 | 0.3020 | 0.5166 |
| **20%** |  |  |  |  |  | -0.0128 | 0.0113 | 0.0520 | 0.0952 | 0.1703 | 0.2988 | 0.5102 |
| **10%** |  |  |  |  |  | -0.0130 | 0.0128 | 0.0540 | 0.0969 | 0.1710 | 0.2988 | 0.5110 |


# slope

just like wind does, slope also influences the ball's trajectory for the entirety of its traveling time. thus, the slope influence is also affected by height.  
however, besides that, slope influence is also strongly directly affected by the power %.  
like, if you'll dunk at 60%, the slope influence will also be only 60% of what it would otherwise be (multiply by 0.6).

i go into more detail about slopes in my [slope theory article](https://github.com/sera-pangya/illuminati-zone/blob/main/slope-theory.md), maybe worth a read, maybe not~

the tldr about slopes on aim is that, since slope and wind are affected by the same things, i like to relate one to the other by using a constant.  
thus, my slope formula is `slope * final hwi * % * constant`.

what's that "constant" about? it's basically a value that relates your slope counting method to the hwi.  
like, if you count by pixels, you'll use a different constant to those who count breaks.  
in any case, the final result of the slope formula on aim should always be the same, of course.


# spin

repeating what was said on the power part, putting more backspin also results in a slight increase in wind influences [(see BooN's video)](https://www.youtube.com/watch?v=cVKGVM-hlwE).  
you can roughly estimate it as an 1% increase per spin~ (that value also varies according to conditions).  

interestingly enough, that ends up meaning that (in most cases) using 30 frontspin will result in having to aim less than using 30 backspin, even though 30 frontspin will require a considerably higher % :o  
i don't really like it much though, as the sharper landing arc means you get a bit less leeway with power, but it's still kinda cool.


# turning effect

so, is that it? yes, but no.

let's say that you're doing some calculations for some relatively ridiculous conditions, and you get a result of 69 PB (!).  
when you move 69 PB, the angle will have changed, probably even quite considerably so (depending on how far the hole is).

if you aren't accounting for it, this effect can be quite dangerous in situations where the wind influence is high, or the wind isn't too lateral.  
this is also very dangerous in situations with ugly slopes, since the "effective slope" can change very quickly. like, aiming at the hole you have 8.6 breaks, but after aiming it's now 9.4 breaks..

so, you can either consider that somehow during calculation, or recalculate everything after aiming.  
it's just important to know that it is a thing that exists~


# final thoughts

wind and slope influence decrease VERY quickly as you use less % power, so dunking with low %s is extremely efficient.  
the only drawback is that you don't get many pangs ;(

why are slopes terrifying? on one hand, it's difficult to read the slope correctly out of the user interface and, to make things worse, most excels use inaccurate formulae for slopes.  
that ends up resulting in quite understandable slopephobia 👀

**protip:** the EASY way to get 18 chips is to just get dunk everything you can with low %s :) as it can be seen, the influences are ridiculously lower, which GREATLY increases your allowed margin of error.  
you can misread the wind by a few degrees with medium wind, get the slope wrong by quite a bit and it still works \o/

that's it, good luck :)  
if you have any questions, too bad, the game is unfair and broken and now that's also your problem.  
you could join the [dead discord server](https://discord.gg/2UYHA2W85d) or just find me elsewhere i guess~
