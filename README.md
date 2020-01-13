# hack-a-thing-1-98-souls

# Description
Attempted to learn Unity3D to create a basic roguelike game.

# Who did what
I did everything.

# What I learned
A surprising amount. Unity is an extraordinary beast, with particular programming paradigms to it that have been enlightening in terms of creating dynamic, persistent and interactive systems (as games tend to be). I also learned exactly how important assets are (as a programmer, they're generally not my job, so I tend to scoff and leave them for the designers to deal with). Moreover: the value of Epsilon. Read more below.

# What didn't work
Epsilon and floating point, as a practical matter, causes great suffering in its wake. The bug that current holds up my program - and which I am wracking my brain trying to solve - is as follows. The problem is that the animation of the player's movement hangs, and as a result refuses to accept any new input while the animation is still ongoing. The reason the animation hangs is due to the mechanism of smooth animation: every increment of time, it moves the object from its current location in the direction of its target location. The movement's distance is determined by the size of the increment and the proportion of distance it must move. Once the "current location" of the object comes within Epsilon of the target location, the animation ceases (having finished movement, essentially).

The issue, as one might imagine, is that the object currently overshoots the target location by an incredibly small value that is still greater than epsilon, thus not breaking the loop. On the next loop, the animator re-evaluates its location, and moves backwards the same amount, landing it in its pre-final location - which then, on the next cycle, goes back to the final-but-past-epsilon location, sticking in a loop.

I am currently at a loss as to what to do with this bug - whether it's best to adjust epsilon (sounds VERY DANGEROUS) or to figure out if there's some fundamental problem with the initial conditions/animation scheme.

# Credits
I followed and made modifications on the [Unity 2D roguelike tutorial](https://learn.unity.com/project/2d-roguelike-tutorial).