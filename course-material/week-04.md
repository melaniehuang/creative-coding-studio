# Recap!
So we've learnt some very core fundementals about Processing and there's been a lot of information thrown at you - so let's do a quick recap of the bits that we've covered.

### Core sketch flow
```processing
void setup(){
  //This runs once at the start
}

void draw(){
  //Then this runs over and over again	
}
```

### Adding comments and references
```processing
// This will add a comment and tell the computer to skip this line.
// Mostly useful for when you want to add a reference to your inspiration:
// Introduction to Runway: Machine Learning for Creators (Part 2)
// https://www.youtube.com/watch?v=7btNir5L8Jc
```

### Looking up the Processing reference to find things
[Processing's reference docs](https://processing.org/reference/)

### Drawing shapes
Coordinates start at the top left (0,0) and x increases to the right, y increases to the bottom.

```processing
//To draw a shape we can use predefined 2D primitives:
rect(x,y,w,h);
ellipse(x,y,w,h);

//Or create our own:
beginShape();
  vertex(x,y);
  vertex(x2,y2)
endShape();
```

Filling and colouring those shapes:

```processing
//We define the colours of our shape BEFORE we draw the shape
fill(255,220,100);
stroke(200,20,100);
rect(x,y,w,h);
```

Adding some randomness:

```processing
void setup(){
  size(300,300);
}

void draw(){
  ellipse(random(width), random(height), 50,50);
}
```

### Variables and movement

We learnt about predefined systems variables like:
```processing
mouseX
mouseY
width
height
```

And about making our own both globally...

```processing
//global variables
float xPosition = 100;

void setup(){
  size(300,300);
}

void draw(){
  println(xPosition);
  xPosition++;
}
```
and locally...

```processing
void setup(){
  size(300,300);
  //local variable xPosition
  float xPosition = 200;
  println(xPosition);
}

void draw(){
  //a different local variable xPosition
  float xPosition = 100;
  xPosition++;
  println(xPosition);
}

//They don't know about each other because they live in different functions.
```

And then we used this knowledge to make a circle move.

```processing
float xPosition = 10;

void setup(){
  size(300,300);
}

void draw(){
  ellipse(xPosition, height/2, 50,50);
  xPosition++;
}
```

And then we briefly touched on "if statements" to stop the circle from falling off the screen and drawing backgrounds to prevent the smudge effect.

```processing
float xPosition = 10;

void setup(){
  size(300,300);
}

void draw(){
  background(0);
  ellipse(xPosition, height/2, 50,50);
  xPosition++;
  
  if (xPosition > width){
    xPosition = 0;
  }
}
```

# Week 4: Images and text

## Uploading an image
We will learn more about the fabulous ways of manipulating an image in Week 7/8/9 but for now we will learn simply how to display an image.

Last week we learnt about some common datatypes like String and int. In order to display an image, we will use an image datatype called PImage. Note the capital “P” and “I”. Computers don’t care about “what you meant to type”. They’re black and white and therefore, extremely case-sensitive. Make sure to include the capitals.

## Local image
Make a folder called “data” where your Processing sketch is stored. Place your image file inside here. Processing can display .gif, .jpg, .tga, and .png images.

![](image url)

You can now tell the computer where you've stored it.

```processing
//Declare your new variable
PImage artwork;

void setup(){
  size(300,300);
  //Tell the computer where your image lives
  artwork = loadImage("data/calder.jpg");
}

void draw(){
  //Draw ‘artwork’ to canvas + optionally give a width and height
  image(artwork,0,50,250,200);
}
```

So now we have an image displaying in the sketch, let's do something interesting with it!

What we're going to do now, is copy a block of pixels from one place to another.

```processing
/* source and destination where:
dh	int: destination image height
sx = X coordinate of the source's upper left corner
sy = Y coordinate of the source's upper left corner
sw = source image width
sh = source image height
dx = X coordinate of the destination's upper left corner
dy = Y coordinate of the destination's upper left corner
dw = destination image width 
dh = destination image height */
copy(sx, sy, sw, sh, dx, dy, dw, dh);
```

Let's see a practical example.

I've loaded an image that fills the entire canvas and I want to use bits of the image to tile across my sketch. Let's say I think that the top left hand corner is an interesting part of the canvas?

```processing
//Declare your variable
PImage artwork;

void setup(){
  size(300,300);
  //Load ‘artwork’ from file path
  artwork = loadImage("data/calder.jpg");
}

void draw(){
  //Draw ‘artwork’ to canvas + optionally give a width and height
  image(artwork,0,0,400,300);
  //copy the top left hand corner of (0,0) with a width of 100px and height of 100px
  //copy TO (100,0) and display it with a width of 100px and height of 100px
  copy(0, 0, 100, 100, 100, 0, 100, 100);
}

```

Try to make your own gridded pattern using parts of an image.

```processing
PImage artwork;

void setup(){
  size(300,300);
  artwork = loadImage("data/calder.jpg");
}

void draw(){
  image(artwork,0,0,400,300);
  //copy the top left hand corner of (0,0) with a width of 100px and height of 100px
  //copy TO (100,0) and display it with a width of 100px and height of 100px
  copy(0, 0, 100, 100, 100, 0, 100, 100);
  copy(0, 0, 100, 100, 200, 0, 100, 100);
  
  copy(200, 100, 100, 100, 100, 100, 100, 100);
  copy(200, 100, 100, 100, 0, 100, 100, 100);

  copy(100, 200, 100, 100, 0, 200, 100, 100);
  copy(100, 200, 100, 100, 200, 200, 100, 100);
}

```

Now maybe we want to bring back our trusty friend, random().
Because copy expects a parameter type of (int, int, int, int, int, int, int, int) we will need to convert the random float value to an int.

```processing
//Give me a random value between 0 and width, then convert that float number to be an integer
int(random(width)

//Give me a random value between 0 and height, then convert that float number to be an integer
int(random(height)
```

```processing
PImage artwork;

void setup(){
  size(300,300);
  artwork = loadImage("data/calder.jpg");
  //Move image drawing to setup as you only want to draw the image once
  image(artwork,0,0,400,300);
}

void draw(){
  //Now copy!
  copy(int(random(width)), int(random(height)), 30, 30, int(random(width)), int(random(height)), 30, 30);
}
```

Pretty! Or maybe we want to copy a smaller version onto itself.

```processing
PImage artwork;

void setup(){
  size(300,300);
  artwork = loadImage("data/calder.jpg");
  image(artwork,0,0,300,300);
}

void draw(){
  copy(0,0,300,300,25,25,250,250);
}
```

What can you do? Play around a bit more with the copy() function and see what you can create.

## Add some text
Just like drawing images and shapes, we can also draw text to screen. Remember that variable type String that we semi-glazed over. Well let's put that type into practice now, and while we're at it, we'll look at char also.

A char is a single character. Computers represent these as numbers. For instance, 65 is the character capital 'A'.

```processing
char letter = 'A';

void setup(){
  println(letter);
}

void draw(){
}
```

```processing
char letter = 65;

void setup(){
  println(letter);
}

void draw(){
}
```

They will both print out the letter A. Now this gives us the nifty ability to increment through the entire character set like we would increase numbers.

```processing
char letter = 65;

void setup(){
  println(letter);
}

void draw(){
  letter++;
  println(letter);
  
  if (letter == 'Z'){
    letter = 65;
  }
}
```

A String is like a sentence. 

```processing
String sentence = "Calder";

void setup(){
  println(sentence);
}

void draw(){
}
```

Note the difference between using 's' for char and "s" for String.
We can then print the char or String to the screen.

```processing
char letter = 'C';
String sentence = "Calder";

void setup(){
  size(400,400);
  background(0);
  fill(255); 
  text(letter, 50,50);
  text(sentence, 100,200);
}

void draw(){  
}
```

Let's merge this new knowledge into our artwork copy exercise! And change the size and alignment of our text.

```processing
PImage artwork;
String artistName = "CALDER";

void setup(){
  size(500,500);
  background(255);
  artwork = loadImage("data/calder.jpg");
  image(artwork,50,50,400,400); 
  
  //Change text colour to black
  fill(0);
  //Change text size to 100px
  textSize(100);
  //Change text alignment to CENTER, instead of the default LEFT
  textAlign(CENTER);

  //print text to screen once
  text(artistName,width/2,465);
  text(artistName,width/2,110);
}

void draw(){
  copy(50,50,400,400,50+50,50+50,300,300);
}
```

And now the finishing touch, how do we not use a horrible system typeface!

1. Go to the Processing menu and select Tools > Create Font
2. Select a typeface you like, set the size and click "Ok"

This will create a file in your "data" folder called "fontname-100.vlw"
Take note of what this is called as you will need it in just a second.

Just like images have their own variable type, PImage - fonts have their own variable type called PFont.

```processing
PImage artwork;
String artistName = "CALDER";
//Declare your font type
PFont SupriaCondensed;

void setup(){
  size(500,500);
  background(255);
  artwork = loadImage("data/calder.jpg");
  image(artwork,50,50,400,400); 

  //Tell the computer where your font file is and load the font file into the sketch
  SupriaCondensed = loadFont("data/SupriaSans-CondHeavy-100.vlw");
  //Select this PFont to display text with
  textFont(SupriaCondensed);

  fill(0);
  textSize(100);
  textAlign(CENTER);

  //adjust the placement of your text
  text(artistName,width/2,465);
  text(artistName,width/2,110);
}

void draw(){
  copy(50,50,400,400,50+50,50+50,300,300);
}
```

And then maybe, we're just having fun and we want to copy THAT image again onto itself?!

```processing
PImage artwork;
String artistName = "CALDER";
//Declare your font type
PFont SupriaCondensed;

void setup(){
  size(500,500);
  background(255);
  artwork = loadImage("data/calder.jpg");
  image(artwork,50,50,400,400); 

  //Tell the computer where your font file is and load the font file into the sketch
  SupriaCondensed = loadFont("data/SupriaSans-CondHeavy-100.vlw");
  //Select this PFont to display text with
  textFont(SupriaCondensed);

  fill(0);
  textSize(100);
  textAlign(CENTER);

  //adjust the placement of your text
  text(artistName,width/2,465);
  text(artistName,width/2,110);
}

void draw(){
  copy(50,50,400,400,50+50,50+50,300,300);
  copy(artwork,0, int(random(height)), width, 5, 0, int(random(height)), width, 5);
}
```

## Week 2 sketch
Week | Exercise |
--- | --- |
4 | Make a mosaic with image and text using the copy() function. Which image and what the text says is completely up to you. Push yourself out of the box of what you can imagine and design and have fun with it. The next couple of weeks are going to be all about experimentation and playfullness to explore the possibilities and opportunities of creative coding to expand your creative practice.|




