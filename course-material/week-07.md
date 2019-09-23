# Week 07: Extensions
Time to travel deeeeeeep down the rabbit hole! 
The good news is that you pretty much have all the coding fundamentals you need for now to reach for your coding stars. ⭐⭐⭐

It's totally okay if you're not 100% on all the things we went through. Coding is like any other skill, it takes practice and exercise but if at any point you get stuck, please reach out because we can solve it together :)

## Extension exercises
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

![Alexander Calder inspired sketch](https://media.giphy.com/media/SqwuZVZ9U31VlkCsYn/giphy.gif)

```processing
void setup(){
  size(900,900);
  colorMode(HSB,360,100,100);
  background(10,8,90);
  noFill();
  frameRate(10);
}

void draw(){
  background(10,8,90); 
  float vertexY = 150;
  beginShape();
    for(int v = 0; v < 9; v++){
      //random(400,500) value for x 
      //y to increase by 50
      float vertexX = random(400,500);
      float ellipseX = random(70,200);
      float ellipseY = random(50);
      vertex(vertexX,vertexY);
      
      if (random(1) < 0.3){
        //line 1
        line(vertexX,vertexY,vertexX+ellipseX/2,vertexY);
        fill(20,100,80);
        ellipse(vertexX+ellipseX/2,vertexY,random(20,50),random(20,50));
        noFill();
        line(vertexX,vertexY,vertexX-ellipseX/2,vertexY);
        fill(20,100,80);
        ellipse(vertexX-ellipseX/2,vertexY,random(20,50),random(20,50));
        noFill();
      } else if (random(1) > 0.7){
        //line type 2
        line(vertexX, vertexY,vertexX+ellipseX,vertexY-ellipseY);
        fill(20,100,80);
        ellipse(vertexX+ellipseX,vertexY-ellipseY,random(20,50),random(20,50));
        noFill();
      } else {
        line(vertexX, vertexY,vertexX-ellipseX,vertexY-ellipseY);
        fill(20,100,80);
        ellipse(vertexX-ellipseX,vertexY-ellipseY,random(20,50),random(20,50));
        noFill();
      }
      vertexY += random(50,100);
    }
  endShape();
}
```

## Extension Two: Sol LeWitt
Now to really get our brain working. In the work of Sol LeWitt's *wall drawings*, he provides instructions for a team to execute directly onto a wall's surface. This means, depending on where this is installed and the team that installs it, the visual outcome of his instructions could be different.

Can you try to "Look! Really look" at this instruction? What do you see and interpret?

> One one wall, intersecting non-symmetrical bands of parallel lines 36"(90 cm) wide, in four directions and colours.

Sketch out some ideas and try to use the process we've been using in class to create your own interpretation with code.

## Extension Three: M.C Escher
For this one I'm going to give you a little head start because there's a little upfront research into Escher's tessellations that may not be obvious at first glance.

"A regular tessellation is a pattern made by repeating a regular polygon. A regular polygon is one having all its sides equal and all it's interior angles equal. So there are only 3 kinds of regular tessellations - ones made from squares, equilateral triangles and hexagons." 
*http://www.funmaths.com/fun_math_projects/what_is_a_tessellation.htm*

We also see parrallograms, rectangles and diamonds in Escher's works.

Using these base grids, we can create our own creatures and geometries that will also be repeatable.

### Let's get out our grid paper.

Starting with a simple square pattern, let’s start drawing our custom tile! Also, for ease, let’s stick to simple, straight lines for now.

1. Draw a line on one side
2. Slide it to the opposite side and repeat exactly
3. Now repeat step 1 & 2 for the remaining side
4. Now look for recognisable figures

### Coding time

Using beginShape() and endShape(), start to draw in your vertex(x,y) coordinates. I promise it will be worth it! I know I always mix up my x and y coordinates, so sometimes I find it easier to write them down on paper first and then copy them in.

```processing
void setup() {
  size(595, 860);
  colorMode(HSB, 360, 100, 100);
}

void draw() {
  background(0,0,100);
  stroke(0,0,0);
  fill(0,0,100);
  beginShape();
    vertex(20,20);
    vertex(40,20);
    vertex(40,10);
    vertex(50,10);
    vertex(60,30);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(100,40);
    vertex(110,50);
    vertex(110,70);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,110);
    vertex(50,90);
    vertex(40,90);
    vertex(40,100);
    vertex(20,100);
    vertex(20,70);
    vertex(30,70);
    vertex(30,50);
    vertex(20,40);
    vertex(20,20);
  endShape(CLOSE);
}
```

Move your tile drawing to it's own function so we can easily do it again and again.
```processing
void setup() {
  size(595, 860);
  colorMode(HSB, 360, 100, 100);
}

void draw() {
  background(0,0,100);
  tile(color(0,0,100));
}

void tile(color f){
  stroke(0,0,0);
  fill(f);
  beginShape();
    vertex(20,20);
    ...
  endShape(CLOSE);
}
```
Once we've got a shape, how would we repeat this tile to the surface of the screen?

```processing
void setup() {
  size(595, 860);
  colorMode(HSB, 360, 100, 100);
}

void draw() {
  background(0,0,100);
  for(int y = 0; y < 10; y++){
    for(int x = 0; x < 7; x++){
      pushMatrix();
      translate(80*x,0);
      tile(color(0,0,100));
      popMatrix();
    }
    translate(0,80);
  }
}

void tile(color f){
  stroke(0,0,0);
  fill(f);
  beginShape();
    vertex(20,20);
    ...
  endShape(CLOSE);
}
```

Let's alternate colours with modulo.
```processing
int counter = 0;

void setup() {
  size(595, 860);
  colorMode(HSB, 360, 100, 100);
}

void draw() {
  background(0,0,100);
  for(int y = 0; y < 10; y++){
    for(int x = 0; x < 7; x++){
      pushMatrix();
      translate(80*x,0);
      if (counter % 2 == 0){
        tile(color(0,0,100));
      } else {
        tile(color(0,0,0));
      }
      popMatrix();
      counter++;
    }
    translate(0,80);
  }
}

void tile(color f){
  stroke(0,0,0);
  fill(f);
  beginShape();
    vertex(20,20);
    ...
  endShape(CLOSE);
}
```

Extensions - there's a bunch more extensions where I go into different shapes, reflection tessellation and tile division if you're liking this train of thought. [See extensions here](https://drive.google.com/file/d/1hO4atW1oKEEEEzgbT9eQzt-mWIyeflJo/view?usp=sharing)

## Week 7 sketch
Week | Exercise |
--- | --- |
7 | Pick one of the above exercises and see how you could extend it further? Maybe you want to add some interactivity? Maybe you want to customise colours? Maybe you want to do something completely different? |
