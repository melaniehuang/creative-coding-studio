# Week 08: Extensions

It’s time for a sketch UPGRADE! We are ready to start adding libraries - which means lots
more cool things! Libraries are a collection of additional functions that we can join onto our
sketch to make our sketch more awesome.

Today we’ll be focusing on two main things you may want to play with: Microphone Input
and Sound output .

Importing a library into Processing is easy peasy: Sketch > Import Library > Add Library
Once you become a bit more comfortable with libraries, you can also branch out to
Contributed Libraries that other people have made.

## Processing types

Although the libraries in Processing work, it’s a lot easier to handle sound and video if we
switch over to p5.js for this instance. This is because p5.js already comes with built in
functions and libraries for this. This class has introduced you to a myriad of
Processing-related bits and pieces so here is a summary(in timeline order):

**Processing**
Created in 2001, as a language for learning how to code within the context of the visual arts.
It runs on your Desktop. It is a programming language based on Java. This is the OG we know and love.

**Processing.js**
Created in 2008 and has since been sidelined(works but has noone to maintain or improve it). Can run on the web. It was made to run Processing sketches in the browser. It's also used as a base to run Processing code inside of openProcessing which highlights some incompatabilities.

**openProcessing**
Created in 2009 as a method of sharing your sketches and creating an online Processing community with visuals! Runs online. Online community where you submit your sketches to a class and can upload and share your sketches.

**p5.js**
The newest of the bunch, released in 2014 and has the most work and effort going into it currently. It runs in the browser and there is an online editor(that we've been using). p5.js is a Javascript library based on Processing.

There is a time and place for all these things and as you start to build out your sketch, you
can investigate what is appropriate especially in regards to Processing vs. p5.js.

## Introducing p5.js
p5.js is a Javascript library based on Processing which means, it’s way more friendly when
you’re trying to do things in the browser because Javascript is one of the core technologies
of the big, bad, world wide web.

So let’s first write something we know how to write out in Processing - in p5.js.
https://editor.p5js.org/

If you haven't used the online editor before, make sure you Sign up or you won't be able to save your code. So what are the main differences?

### 1. Functions are simply “function” followed by its name. 
**Processing**
```processing
void setup(){
}
void draw(){
}
```
**Javascript(p5.js)**
```javascript
function setup(){
}
function draw(){
}
```

### 2. createCanvas(w,h) replaces size(w,h)
**Processing**
```processing
void setup(){
  size(900, 900);
}
void draw(){
}
```
**Javascript(p5.js)**
```javascript
function setup(){
  createCanvas(900,900);
}
function draw(){
}
```

### 3. Variables are declared as var no matter their data type. However, always be sure to keep track of what each variable’s data type is because this is still important.
**Processing**
```processing
int number = 10;
color[] col = new color[10];
void setup(){
  size(900, 900);
}
void draw(){
  for (var i = 0; i < col.length; i++){
  }
}
```
**Javascript(p5.js)**
```javascript
var number = 10;
var col = [];
var cLength = 10;
function setup(){
  createCanvas(900,900);
}
function draw(){
  for (var i = 0; i < cLength; i++){
  }
}
```

### 4. Sometimes things don’t load in order for Javascript so you’ll need to start using the function preload for preloading files before your sketch runs.
**Processing**
```processing
PImage img;
void setup(){
  img = loadImage("file.jpg");
  size(900, 900);
}
void draw(){
  image(img, 0, 0);
}
```
**Javascript(p5.js)**
```javascript
var img;
function preload(){
  img = loadImage("file.jpg");
}
function setup(){
  size(900, 900);
}
function draw(){
  image(img, 0, 0);
}
```

### 5. p5.js is in itself a library and therefore comes with some functions that Processing does not have(yay!). For instance, we now have touch events in addition to mouse and key events! This means we can get our sketches working on our mobile.
**Processing**
```processing
PImage img;
int number = 10;
color[] col = new color[10];
void setup(){
  img = loadImage(file.jpg);
  size(900, 900);
}
void draw(){
  for (var i = 0; i < col.length; i++){
  }
}
void mousePressed(){
  //do something
}
```
**Javascript(p5.js)**
```javascript
var img;
var number = 10;
var col = [];
var cLength = 10;
function preload(){
  img = loadImage(file.jpg);
}
function setup(){
  createCanvas(900,900);
}
function draw(){
  for (var i = 0; i < cLength; i++){
  }
}
function touchStarted(){
  //do something when you press the mouse OR touch a mobile screen
}
```

This list of specific differences could get relatively large so let’s just try an example and see
how we go.

```processing
boolean s;
color c = color(255,255,0);

void setup(){
  background(0,0,255);
  size(375,600);
  s = true;
}

void draw() {
  fill(c);
  ellipse(mouseX, mouseY, 50,50);
}

void mousePressed() {
  if (s) {
    c = color(255,255,0);
    s = false;
  } else { 
    c = color(255,0,0);
    s = true;
  }
}
```
**Exercise**
Convert this Processing sketch into Javascript with p5.js. Get this sketch working both in
the p5.js editor on your Mobile and Desktop.

# Studio
Okay, that's enough from me - go forth and try some tutorials that interest you. I've added some example tutorials in Week 9's notes. Let's do some coding!

## Week 8 sketch
Week | Exercise |
--- | --- |
8 | Pick a tutorial you like and see how you can extend it further. Simple :) If you're finding the coding easy, focus on trying to extend it more. If you're finding the creativity easy, focus on a harder coding challenge. All I ask is that you try something you haven't done before. |
