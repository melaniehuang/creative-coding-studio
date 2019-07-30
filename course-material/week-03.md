# Week 3: Shapes and movement

## Shapes Glorious Shapes
There are SO many different shapes we can create.

With your experience drawing rectangles and ellipses from week 1 - give some of these 2D primitives a whirl! If you get stuck, just punch in random numbers and spot the difference! With very little knowledge of coding, you can still visually discern what the numbers and parameters may stand for.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  //line(x1, y1, x2, y2);
  line(100,100,600,100);
  
  //triangle(x1, y1, x2, y2, x3, y3);
  triangle(300,400,500,200,450,550);
  
  //quad(x1, y1, x2, y2, x3, y3, x4, y4);
  quad(50, 450, 300, 550, 200, 700, 50, 600);
}
```

But let's say we're a little more ambitious and we want to make a big spikey explosion type shape?! Let's draw our own shapes!

The first thing we need to do is type beginShape(); and endShape(); - This tells Processing "Hey Processing, the next few vertices that I specify, will be vertexes for my shape.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  beginShape();
    //vertex(x,y);
  endShape();
}
```

Now we add in each x and y value for each vertex of our shape. This can be a strenuous task however it does start to pay off once you can start manipulating those shapes with code.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  beginShape();
    //vertex(x,y);
    vertex(200,50);
    vertex(230,120);
    vertex(260,40);
    vertex(300,100);
    vertex(350,60);
    vertex(360,140);
    vertex(450,120);
    vertex(380,180);
    vertex(460,210);
    vertex(360,250);
    vertex(380,400);
    vertex(260,270);
    vertex(220,350);
    vertex(220,250);
    vertex(170,320);
    vertex(210,200);
    vertex(100,240);
    vertex(180,150);
    vertex(120,80);
    vertex(210,150);
    vertex(200,50);
  endShape(CLOSE);
}
```

Then we've also added the paramater "CLOSE" to indicate that we want a closed shape. So we can make this strobe explosion! Warning: eyes. Hide the ugly stroke with noStroke(); in setup().

```processing
void setup(){
  size(900,900);
  background(255);
  noStroke();
}

void draw(){
  background(random(120,255),0,0);
  fill(random(150,255));
  beginShape();
    //vertex(x,y);
    vertex(200,50);
    vertex(230,120);
    vertex(260,40);
    vertex(300,100);
    vertex(350,60);
    vertex(360,140);
    vertex(450,120);
    vertex(380,180);
    vertex(460,210);
    vertex(360,250);
    vertex(380,400);
    vertex(260,270);
    vertex(220,350);
    vertex(220,250);
    vertex(170,320);
    vertex(210,200);
    vertex(100,240);
    vertex(180,150);
    vertex(120,80);
    vertex(210,150);
    vertex(200,50);
  endShape(CLOSE);
  ellipse(600,620,500,500);
}
```

### Exercise
Try to create your own unique shape. How can you manipulate it?

There are also a bunch of different [beginShape()](https://processing.org/reference/beginShape_.html) parameters you can discover like beginShape(TRIANGLE_STRIP);. Perhaps you also want a contour ie. [beginContour()](https://processing.org/reference/PShape_beginContour_.html). NB: The vertex of shapes goes clockwise, the vertex of a contour goes counter-clockwise.

## Movement
Now that we're confident with shapes, let's try and make something move.

Up to this point we have been “hard coding” values into our program. This means when we draw a rect(10,10,100,100);, our program is drawing a rectangle on top of itself again and again and AGAIN. Boring!

By replacing the value with a variable and incrementing/decrementing that variable each time our program calls the function draw(), we can start to add movement to our shapes.

Before we dive into what a “variable” can be - let’s try this:

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  ellipse(mouseX, mouseY, 50, 50); 
}
```

Now we have some crazy drawing tool that draws the current position of your mouse’s x-coordinate and y-coordinate. If we want it to appear like the ellipse is moving, we draw the background at the start of the draw() loop.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  background(255);
  ellipse(mouseX, mouseY, 50, 50); 
}
```

Now we just have an ellipse following our mouse x and y. This is because we're essentially drawing a background on top of the previous frame.

mouseX and mouseY are examples of a system variable. This is a variable that Processing understands already. But of course, we can make our own variables!

## Variables
First off, we need to talk about **data types**. In order for the computer to understand what kind of value it’s dealing with, you need to tell the computer what “type” of variable you’re going to be giving it. The main ones you’ll be dealing with at this early stage are:

**float**: Floating-point numbers, e.g. numbers that have a decimal point.
**int**: Integers, whole numbers aka numbers without a decimal point
**char**: Characters, typographic symbols such as A, d, and $. A char stores letters and symbols in the Unicode format(a computer standard for the consistent encoding, representation, and handling of text)
**String**: A string is a sequence of characters.
**color** - You guessed it, a datatype for handling colours. Note the lack of “u” in colour (this is a common type error when your code doesn’t run for us Aussies).

You will notice that majority of the shape parameters accept the “float” data type. Most of the time, you will need to make sure when doing calculations that you aren’t adding a **String** to a **float** for example - this will either not work or come up with something strange.

For example, this will not work:

```processing
float x = 2.342;
int y = 1;
int p = x + y;
println(p);
```

The console will read “cannot convert from float to int”. 
But this **will** work.

```processing
float x = 2.342;
int y = 1;
float p = x + y;
println(p);
```

And this **will** work but not produce the most expected result. ie. p = 2.3421 :/

```processing
String x = "2.342";
int y = 1;
String p = x + y;
println(p);
```

So even through we may "know" as humans, there's a way of adding those two numbers together ie. 2.342 + 1 = 3.342. Or perhaps in the first example if it needed to be an **int** value - we'd round to the closest integer therefore 2.342 + 1 would round to 3. Our computers aren't humans like that - we have to be more specific in Processing.

But enough theory, we’ll learn by doing!

## Global variables and local variables
Let’s get our trusty circle back. We want what’s called a “global” variable that will increase each time the function draw() is called. This will create what I term the “smudge” effect.

```processing
//I am a global variable, I'm available for every part of the sketch.
float x = 50.0;

void setup(){
  size(300,300);
}

void draw(){
  ellipse(x, 50, 50, 50); 
  //Increment variable x by 1
  x++;
}
```

A local variable is contained within a function and is only available in this function. Therefore, in the below program, the function setup(); does not know about x. Let’s see what happens when you use a local variable... 

```processing
void setup(){
  size(300,300);
}

void draw(){
  //I am a local variable, I belong to draw() and only draw() knows about me!
  float x = 50.0;
  ellipse(x, 50, 50, 50); 
  //Decrement variable x by 1
  x--;
}
```

Nothing! This is because everytime you call the function draw(); it sets x to 50.0 and decrements it by 1. Repeat.

Local variables will be useful soon. However, for now, make sure you’re declaring your variables at the top of your program, outside of any function.

### Exercise
Make a global variable called ‘s’ and use it to increment or decrement the size of your ellipse! 

## Joan Miró
A close friend of Alexander Calder was [Joan Miró](https://en.wikipedia.org/wiki/Joan_Mir%C3%B3), a Spanish painter, sculptor, and ceramicist. Though [divided by an ocean and World War II](https://www.nytimes.com/2017/04/20/arts/design/miro-calder-and-a-convergence-of-constellations.html), they created continued on remarkably like-minded trajectories. And if you like one, I can guarentee you'll probably like the other ;)

Take a look at [Dog Barking at the Moon(1926)](https://www.joan-miro.net/dog-barking-at-the-moon.jsp). Take a look at how strange yet somewhat familiar the dog looks! Or take a look at [Painting(1933)](https://www.joan-miro.net/painting-1933.jsp) and look at the human figures! Or even deeper still, [Le Fermier et son epouse(The Farmer and his wife)(1936)](https://www.joan-miro.net/le-fermier-et-son-epouse.jsp) with two dancing human bodies and collection of animals.
