# Week 3

# DISCOURSE: Mathematics and Art
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: Repetition

## Tessellation
Now, we're all going to take a breath in this week as Escher's ability to absorb mathemathical concepts aesthetically is no mean feat!

So as we saw on Slide 7 of Escher's symmetries, he used 1 of 6 regular polygons - this is known as "regular symmetry":
- Square
- Rectangle
- Parallelogram
- Diamond
- Triangle
- Hexagon

Discovering that these shapes could tesselate was never going to be enough for Escher. Today, we will learn how to create an Escher-inspired creature for our exercise.

Starting with a simple square tile, let's attempt our first tile: https://www.icloud.com/keynote/0_U39fuJNXWEiqZN4XP6ZIICg#Grids

I have added a collaborative grid paper tile with your name on it so let’s start drawing! Let’s stick to straight lines for now.

### Quick exercise
1. Draw line/s on one side.
2. If you have multiple lines, group and slide it to the opposite side to repeat exactly.
3. Now repeat step 1 & 2 for the other side. Draw line/s on the remaining left hand side.
4. Group and slide to opposite side to repeat exactly.
5. Escher at this point would then look and refine for recognisable figures.

You can come back to this if you run out of time. Use the shape I've prepared for you if you want to proceed.

If you've created your own shape, whip out your pencils(and erasers, this involves some concentration) and mark out all the vertex coordinates. There’s a lot of numbers and if you’re anything like me, I always confuse my x and y order.

Tip: Start with pencil and paper first then input the vertices into the sketch in bulk.

```javascript
function setup() {
  createCanvas(120,120);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  stroke(0,0,0);
  fill(0,0,100);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
``` 

## Functions
setup() and draw() are both functions that p5 offer as part of the library. As we've spoken about, functions are simply mini programs that we can tell to run.

Everything else you’re calling(rect(), beginShape() etc.) are also functions that come as part of the language. 

However, we have the POWER to create our own functions. Let’s move our shape to its own function, specify the tile’s fill colour as a parameter and change the canvas size to 595 x 860.

Hint: This will mean we can change the colour of each tile! ♥️

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  tile(color(0,0,100));
}

function tile(c) {
  stroke(0,0,0);
  fill(c);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
``` 

So, everything looks relatively the same - however, we now have the power to do this…

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  tile(color(0,0,100));
  translate(80,0);
  tile(color(0,0,0));
}

function tile(c) {
  stroke(0,0,0);
  fill(c);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
```

Now you should have two tiles that should tessellate exactly - we’re getting somewhere! More on translations later.

### Quick exercise
To test your tile function, use the translate(x,y) function like the exercise to create 4 tiles that fit together perfectly :)

x will depend on your shape’s width, it should be somewhere between 60-90. 

## Translations in Processing/p5.js
You would’ve noticed a new function: 
```javascript
translate(x,y);
```
The translate function translates your sketch’s coordinate system. This is accumulative each time you call translate(). Every time draw() is called, the coordinate system resets back to default.

So the first time we draw our tile, the coordinate system is set at it's normal position of (0,0).

In the previous example, we asked the sketch to translate (0,0) to (80,0). So now where:
- x used to equal 80, it now equals zero
- x used to equal 90, it now equals 10
- x used to equal 100, it now equals 20... and so on.

Words are failing us so let’s look at the example.

Inside of the tile() function, the first vertex is always drawn at (20,20):
```javascript
...
  beginShape();
    vertex(20,20);
  ...
  endShape(CLOSE);
...
```

It isn't until we call translate() in draw() that the coordinate system shifts 80px to the right.
```javascript
function draw() {
  background(0,0,90);
  //(0,0) is still (0,0)
  tile(color(0,0,100));
  //Move (0,0) to (80,0)
  translate(80,0);
  //First vertex of tile is now drawn at the new (20,20)
  tile(color(0,0,0));
}
```

Notice that we're never changing the coordinates of the tile itself. We're moving the coordinate system instead.

This takes a while to get your head around especially when you start looking at scale() and rotate(). But for now just remember. **We're moving the coordinate system not the shape.**

## Push and Pop
Next thing to add to our kit, push and pop!
```javascript
push(); //Begin separate coordinate system
pop(); //End separate system and reset to prior
```
This gives us the ability to reset the coordinate system whenever we need to. Hold this thought, we'll use it in the next section.

## Repetition
Now we could manually translate and draw every tile until we fill the screen but that seems like a lot of effort… instead, let’s use the computer for something it is great at - repetition.

Introducing the for loop: 
```javascript
for (init; test; update){ 
  statements
} 
```
1. The init statement is run.
2. The test is evaluated to be true or false.
3. If the test is true, proceed to step 4. If the test is false, jump to step 6.
4. Run the statements within the block.
5. Run the update statement and jump to step 2.
6. Exit the loop.

This may look overwhelming, but it’s quite straightforward once you look at an example. Here comes our friend push() and pop() also.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  for(let i = 0; i < (width/80)+1; i++){
    push();
    translate(80*i,0);
    tile(color(0,0,100));
    pop();
  }
}

function tile(c) {
  stroke(0,0,0);
  fill(c);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
```

1. Start i at 0.
2. Is the test ( i < (width/80)+1 ) true? 
3. If test is true, proceed to 4. If false, jump to 6.
4. Run statements in block.
5. Increase i by 1.
6. Exit the loop.

Holy moley! It’s a miracle!

Now we also want the tiles to fill the entire width. So, let’s do a separate translate outside of the loop to move the first tile off the screen.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  translate(-40,0);
  for(let i = 0; i < (width/80)+1; i++){
    push();
    translate(80*i,0);
    tile(color(0,0,100));
    pop();
  }
}

function tile(c) {
  stroke(0,0,0);
  fill(c);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
```

## Inception time: A loop within a loop
Now we want to loop on that loop to fill the canvas in the y direction:

```javascript
for (init1; test1; update1){ 
  for (init2; test2; update2){ 
    statements
  } 
}
```

Let's write a loop within a loop.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  translate(-40,-40);
  for(let y = 0; y < (height/80)+1; y++){
    for(let i = 0; i < (width/80)+1; i++){
      push();
      translate(80*i,80*y);
      tile(color(0,0,100));
      pop();
    }
  }
}

function tile(c) {
  stroke(0,0,0);
  fill(c);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
```

And for our final trick, let's alternate colors like Escher did. Introducing modulo "%":

```javascript
% //Modulo checks the remainder when one number is divided by another.
```
So if we were to check if (n % 2 == 0) is true, it will be true every second time ie. alternating true, false.

Using the conditional statements we learnt last week, let's put this into practice. 

First we need to keep track of the variable n, let's create a variable called "counter".
```javascript
let counter = 0;
```
Then every time we loop through our nested loop(a loop within a loop), we increment counter by 1;
```javascript
counter++;
```

Then we check "counter" for its remainder when divided by 2. All together, it should look a little like this:

```javascript
let counter = 0;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
}

function draw() {
  background(0,0,90);
  translate(-40,-40);
  for(let y = 0; y < (height/80)+1; y++){
    for(let i = 0; i < (width/80)+1; i++){
      push();
      translate(80*i,80*y);
      if(counter%2==0){
        tile(color(0,0,100));
      } else {
        tile(color(0,0,0));
      }
      pop();
      counter++;
    }
  }
}

function tile(c) {
  stroke(0,0,0);
  fill(c);
  beginShape();
    vertex(20,20);
    vertex(30,10);
    vertex(30,20);
    vertex(40,20);
    vertex(40,10);
    vertex(60,20);
    vertex(60,40);
    vertex(80,30);
    vertex(80,20);
    vertex(100,20);
    vertex(110,30);
    vertex(100,50);
    vertex(120,50);
    vertex(110,70);
    vertex(90,50);
    vertex(90,80);
    vertex(100,70);
    vertex(100,100);
    vertex(80,100);
    vertex(80,110);
    vertex(60,120);
    vertex(60,100);
    vertex(40,90);
    vertex(40,100);
    vertex(30,100);
    vertex(30,90);
    vertex(20,100);
    vertex(20,70);
    vertex(10,80);
    vertex(10,50);
    vertex(30,70);
    vertex(40,50);
    vertex(20,50);
    vertex(30,30);
    vertex(20,20);
  endShape(CLOSE);
}
```

My oh my. I'm just going to let that mind bending sit with you. 

## Week 03
Create your own Escher-inspired pattern. 

- Option A(for the daring): Try an alternative tesselation type, there's Alternative Translation A and B in the grid paper shared slides.
- Option B(for the extra daring): There are diagrams explaining alternative shapes that Escher used. Try a different shape.
- Option C(for if you're feeling more creative): Expand your shape by working with the inside of the shape. Divide it into multiple parts or imagine your own creatures like Escher did.