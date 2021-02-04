# introduction

heya~ let's start by going back to the fundamentals..

the inputs to a power calculation are **power**, **height** and **wind**. the output is the % you have to hit (a caliper, if we may).  
we all already intuitively understand how power works (let's forget all actual existing formulae for a moment).

we know that, the higher the % you hit, the higher the wind influence is going to be, and the less the effect of height on distance (the so-called "H+/H-") is.

so, it turns out that those inputs influence each other.  
when you add the wind influence to the distance, you're changing the power that you have to hit.. but, in turn, that also changes the wind influence itself.  
same thing for height - we already knew from [tonycheese's awesome mspaint diagram](https://i.imgur.com/ZEKbwVW.jpg) (back before 2010!) that the ball's arc changes according to the power you hit.

# what

so, in the end, you have to balance three variables which influence each other, which is actually incredibly annoying. how do you even "solve" this properly?  
for literally over 99% of material that i can find (e.g. excel calculators), the answer is "you don't".  
you just do the steps in an order that's good enough and then fix it with magical steps, like "multiply by 1.25 (or 1.24, ...) for backwards wind".

how can one fix it? if only we magically knew which power to use in advance, we could already calculate power with the correct parameters from the beginning.  
it turns out that i don't really know how to solve that (i'm actually NOT a maths nerd, believe it or not), but we can "pseudo-solve" it by employing brute force.

the idea is basically: test a bunch of power inputs, compare the power input to the distance result, and take the best one.  
you can make the process faster and less ugly with like a binary search and such stuff.

# why

so, why do that?  
for one, it's clearly the "proper" way to do things, considering that we know for a fact that we are using the proper H-value and wind influence.  
and, on that last point.. it's really nice to already know the proper wind influence from the power step. that means you don't need to do another full wind influence calculation for aim.

i've been using this method to figure both power and hwi in one go, and it's been working pretty much perfectly, as far as i can tell.  
when i miss, i feel like it's just my fault.

see you around~
