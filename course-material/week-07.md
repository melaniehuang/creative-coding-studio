# Week 07: Extensions
Time to travel deeeeeeep down the rabbit hole! 
The good news is that you pretty much have all the coding fundamentals you need for now to reach for your coding stars. ⭐⭐⭐

It's totally okay if you're not 100% on all the things we went through. Coding is like any other skill, it takes practice and exercise but if at any point you get stuck, please reach out because we can solve it together :)

## Extension exercices
So this week and the next couple of weeks we're going to jump around into a whole bunch of different exercises that will hopefully inspire you to extend your assignments somehow.

This week we will focus on specific exercises inspired by the three artists: Calder, Escher & LeWitt. The following weeks will be more freeform, asking you to explore topics and subjects you're interested in extending into.

Let's go!

## Extension One: Calder
So let's say we want to make a sketch inspired by Calder's mobiles? And to make it a little easier for ourselves, let's make a static version of his mobiles.

![Alexander Calder exhibition at National Gallery of Victoria 2019](https://github.com/melaniehuang/creative-coding-studio/blob/master/course-material/images/week-07-001.jpg)

**Step 1. Look! Really look.**
- What can you see when you look at this photo?
- What do you like and what do you dislike?
- Can you break it down into shapes? 
Let's write it out on the board.

**Step 2. Focus on a small goal and then build slowly.**
- Pick a starting point.
- Then pick our next thing to do.
- Then pick our next thing to do. 
What might we code first?

**Step 3. Evaluate and experiment. Repeat.**
- Was something too big or was something too small?
- Did the code not do what you expected? Was it better that way?
Start to get a feel of this collaboration with your computer. If you find a moment of inspiration, follow it. If you get stuck, try something else and maybe that will inspire a solution to the previous problem.

As I try to always reiterate in class, creative coding is **NOT** trying to simply draw a static image with code. You can already do this in Photoshop or Paint. The magic comes within the collaboration between you and the computer.

Let's try to create this together.
![Alexander Calder inspired sketch](https://github.com/melaniehuang/creative-coding-studio/blob/master/course-material/images/week-07-002.gif)

## Extension Two: Sol LeWitt
Now to really get our brain working.

In the work of Sol LeWitt's wall drawings, he provides instructions for a team to execute directly onto a wall surface. This means, depending where this is installed, the visual outcome of his instructions will be different.

Can you try to "Look! Really look" at this instruction? What do you see and interpret?

"One one wall, intersecting non-symmetrical bands of parallel lines 36"(90 cm) wide, in four directions and colours."

Sketch out some ideas and try to use the process we've been using in class to create your own interpretation with code.

## Extension Three: M.C Escher
This one I'm going to give you a little head start because there's a little upfront research into Escher's tessellations that may not be obvious at first glance.

"Regular" tessellation describes a tessellation where all the shapes are the same and tileable.
There are six different "regular" tessellations that have been discovered:
Square, Rectangle, Parrallogram, Diamond, Triangle, Hexagon

Using these base grids, we can create our own creatures and geometries that will also be repeatable.

Let's get out our grid paper.
Starting with a simple square tile, grab your grid worksheets and let’s start drawing! Let’s stick to straight lines for now.

1. Draw a line on one side
2. Slide it to the opposite side and repeat exactly
3. Now repeat step 1 & 2 for the remaining side
4. Now look for recognisable figures

Now comes the tedious-ish part.

Using beginShape() and endShape(), start to draw in your vertex(x,y) coordinates. I promise it will be worth it! I know I always mix my x and y coordinates, so sometimes I find it easier to write them down on paper first and then copy them in.

Once we've got a shape, how would we repeat this tile on screen?
<exercise>

Let's alternate colours with modulo.
<exercise>

Extensions - there's a bunch more extensions where I go into different shapes, reflection tessellation and tile division if you're liking this train of thought.

## Weekly task
Pick one of the above exercises and see how you could extend it further? Maybe you want to add some interactivity? Maybe you want to customise colours? Maybe you want to do something completely different?
