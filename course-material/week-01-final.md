# Week 1

## Studio introduction

### Join our Slack
Using your RMIT email address, navigate to https://cc-studio-2020.slack.com/ and sign up/join the conversation. This is where you will be able to communicate with me and each other. This is a service I use day to day for work and freelance projects so it will be the fastest way to get in touch with me, otherwise, send me an email. We will use this for our 1-1s in class.

### Download Sublime
If you have a preferred code editor, feel free to use it but for our class I will be using Sublime. [Download Sublime Text 3 here](https://www.sublimetext.com/3)

###  Download Chrome
We will be working in the browser so please make sure you are using [Google Chrome](https://www.google.com.au/chrome/). If you don't already use this browser, please download it. If you already have this browser, please make sure it's up to date.

### Download this zip to get started
[Download this folder "my-empty-sketch"](/template)
This is where we'll start, locally on our machines to hopefully prevent any incompatabilities *fingers crossed*. First download the above and then we'll go into what each thing is after that.

### Join the openProcessing class
[Join the openProcessing classroom](https://www.openprocessing.org/class/64609). You will be supplied with a code to join the classroom in class. Please use an obvious name and your RMIT email when signing up. This is where we will be submitting our weekly tasks and as a result, sharing what we’ve all been making.

### p5 Editor
There is an [online editor](https://editor.p5js.org/) that we may have to use during class this semester depending on how your machine is handling the above process.

### Let's get to know each other
In this class I've set up 1-1s for you and I however, I'd really love to get a spirit of collaboration and inspiration amongst one another. This will happen via the openProcessing submissions but also let's kick things off with a simple exercise.

Let's break for 10 minutes and then we will come back and share with each other:
- Name
- Have you coded before?
- Something that inspired you to take this studio or inspires your practice.

## Computers and Creativity
[Zoom recording will be uploaded here]()
[Slides available here]()

## Coding shapes

### An introduction to Creative Coding
Congratulations, you have taken the dive! Welcome to the exciting world of creative coding. It is a large and ever-evolving landscape. 

It's normal to feel nervous if this is your first time coding. We will treat this class like any other studio class. We will make, experiment, discuss and evolve our ideas together AND most importantly leave noone behind. This studio is made to allow you to be as creative or as technical as you would like. So if you are on the other side and you have coded before, use this as an opportunity to explore pathways you've always wanted to expand in or revisit existing concepts differently.

We've had students make little drawing machines, sound reactive installations, body reactive visuals, machine learning experiments and my personal favourite generative art.

Some common names that you may come across are things like:
- Processing/p5.js
- openFrameworks
- vvvv
- Cinder
- Max MSP
- Pure Data

This semester we will be covering Processing; a programming language for learning how to code within the context of the visual arts. We will be writing with a Javascript library called p5.js and submitting our weekly sketches via openProcessing.

Maybe a table might be easier to show you how these pieces fit.

Processing | Processing.js | openProcessing | p5.js | JavaScript |
--- | --- | --- | --- | --- |
Created in 2001, as a language for learning how to code within the context of the visual arts. It runs on your Desktop. It is a programming language based on Java. This is the OG we know and love. | Created in 2008 and has since been sidelined(works but has noone to maintain or improve it). Can run on the web. It was made to run Processing sketches in the browser. It's also used as a base to run Processing code inside of openProcessing which highlights some incompatabilities. | Created in 2009 as a method of sharing your sketches and creating an online Processing community with visuals! Runs online. Online community where you submit your sketches to a class and can upload and share your sketches. | The newest of the bunch, released in 2014 and has the most work and effort going into it currently. It runs in the browser and there is an online editor(that we may use). p5.js is a Javascript library based on Processing. | JavaScript, often abbreviated as JS, is a programming language that runs in your browser. JavaScipt is the language - p5.js is a Javscript library. So we will be writing Javascript using the p5.js library.

Hopefully, we're all still here AND we're ready to go!

### Sketching with code
The concept of a “sketch” is fundamental to Processing and as you can see we have named our empty template, "my-empty-sketch". It introduces a new way of looking at code to encourage the ability to "sketch" with code. 

### Learning to build vs. learning to use software
As a designer, one of the things I had to unlearn when I started creative coding was letting myself "sketch" and "play" rather than having a definite visual I wanted to produce to the pixel. 

As I'm sure you will also find - if you wanted a predefined static visual, you could probably get there quicker with something like Photoshop or Illustrator. The advantages of creative coding is being able to push beyond what you can already imagine - and rather collaborate WITH the computer and let it surprise you. We want to see code as an additional tool for our designs.

"I want people to be impatient with the tools that are readily available to them... I'm less interested in someone creating the next Photoshop, but I do want them to create the tool that **is** the Photoshop they need for the project that they're actually creating at the time... We've been too willing to use the tools that have been provided to us created by companies who's primary interest is their bottom line and not necessarily the artefacts we create with their products."
- [Ben Fry's address](https://youtu.be/9IOTFZLYtqU)

### The first square
Functions are like mini programs and the main two functions that exist in Processing are setup() and draw(). setup() runs once at the start of our sketch and draw() runs over and over again on repeat.

1. Name your sketch folder
2. Open the file "sketch.js" in Sublime.

Copy and paste in the following:
```javascript
//This runs once
function setup(){
  createCanvas(900,900);
  background(0);
}

//This runs on repeat
function draw(){
  rect(400,400,100,100);
}
```

3. Save the file.
4. Open "index.html" in Google Chrome.

Can you describe what is happening in this sketch in plain english?
Change some numbers and it should become fairly obvious :)

You’ll also notice here that I have included these lines: _//This runs once_ and _//This runs on repeat_. This is what’s known as commenting - the characters **//** that precede the comment tell the computer to ignore this line. You will be using comments to add any inspiration or references you may have used for your sketches.

### Quick exercise
Can you add your name in as a comment in this sketch?

### !! This part is a super important bit !!
You will find a LOT of inspiration online and naturally watch a tonne of tutorials to learn throughout the semester. I dare you to get through the entire semester **without** watching one of [Daniel Shiffman's Coding Train](https://www.youtube.com/user/shiffman) videos. As Lauren McCarthy eloquently said, learning is part of the process. *However* - you **MUST** put your sources in your code commented at the top of your code. It doesn't need to be complex, just something like this so I can tell where their ideas end and yours begin:

```processing
// Coding Challenge #11: 3D Terrain Generation with Perlin Noise in Processing
// https://www.youtube.com/watch?v=IKB1hWWedMk
```

Try adding your own comments.

An important thing to also realise at this point is that the computer, unlike the English language, can’t assume what you were supposed to say. Therefore, if there’s a character out of place, the code won’t run. 

This:
```processing
//
```
is not the same as this:
```processing
\\
```
or this:
```processing
/ /
```

Check those commas, brackets and semicolons! Don’t worry too much about this, you will naturally get better at checking for these things the more you write code.

### Co-ordinates

To tell the computer where to draw something, you will need to give it an x and y coordinate. You may remember these bad boys from maths class but in Computer Graphics, it’s a little different. 

The top left corner (x,y) is (0,0). The x coordinates increase to the right, the y coordinates INCREASE moving down the canvas.

```javascript
(0,0)___________ (900,0)
|                      |
|                      |
|                      |
|                      |
|                      |
|                      |
|                      |
(0,900) ________ (900,900)
```

Therefore rect() accepts the following 4 parameters:
```javascript
//rect(x, y, width, height);
rect(0, 0, 200, 200);
```

By default, rect() accepts the x & y position of the rectangle’s top left corner.
Now, let’s add some colour!

### Sequence, colour and fill

So to add a fill to the rectangle, we need to add a line _above_ our rect() function:
```javascript
fill(169,225,250);
```

By default, Processing interprets your numbers as RGB colours - the amount of red, green and blue you want to mix into a single colour. When we write something like:
```javascript
fill(255);
```
the computer is actually interpreting that to be:
```javascript
fill(255,255,255); 
```

**Try the following:**
```javascript
function setup(){
  createCanvas(900,900);
  background(248,250,169);
}

function draw(){
  fill(169,225,250);
  rect(400,400,100,100);
}
```

We can pick own own RGB colours here: https://htmlcolorcodes.com/color-picker/
We will delve more into colours and what the numbers all mean later in the semester. For now, just copy and paste the R, G and B values as comma-separated numbers like the example above.

In addition, let’s remove that awful black stroke. By default:
```javascript
stroke(0); 
```
is applied to all 2D Primitives. In the setup() function, include the line:
```javascript
noStroke();
```

### Quick exercise
What if we wanted to add another square but of a different colour? Let's use Josef Albers' series Hommage to the Square as our inspiration.

"Though deceptively simple, the series transformed how artists approached color theory. The differently colored squares were introduced by Albers to help students and other artists to approach and study color experimentally."
https://publicdelivery.org/josef-albers-homage-to-the-square/

Take a look and choose one that appeals to you. Now try to recreate that on the screen. You can interpret this activity as you like.

### Using the p5.js reference
Now we will look for more shapes but how do I find out what shapes I can make? 

Now it may seem that "coders" just seem to type things in that they've memorised but a big part of coding is looking up the reference documentation as there is simply too much to just "remember". 
[View p5.js' reference docs](https://p5js.org/reference/)

### ellipse()
Let's find how to create a circle or as the function is called, an ellipse.
1. Search the page for what you think it might be called. In this case, circle() and ellipse().
2. Read the docs. It's really that straight forward in p5.js as they have done a lot of work to make the documentation as friendly as possible.
[circle()](https://p5js.org/reference/#/p5/circle)
[ellipse()](https://p5js.org/reference/#/p5/ellipse)

The two parts you're looking for are...

The **example** code - the one you can just copy, paste and manipulate:
```javascript
ellipse(56, 46, 55, 55);
```
and the **syntax** on how to use that function:
```javascript
ellipse(a, b, c, d)
/*	
a	- float: x-coordinate of the ellipse
b	- float: y-coordinate of the ellipse
c	- float: width of the ellipse by default
d	- float: height of the ellipse by default
*/
```

So in human terms, by default, this means:
- (a,b) is the coordinate of the ellipse's centre point
- c is the ellipse's width
- d is the ellipse's height

### Shapes Glorious Shapes
There are SO many different shapes we can create.

Now with your experience drawing rectangles and ellipses - give some of these 2D primitives a whirl! If you get stuck, summon your inner Lilian Schwartz and "just change the numbers and see what happens", sometimes the computer may show you something you didn't even know you were looking for. Even with limited knowledge of coding, you can still visually discern what the numbers and parameters may stand for.

```javascript
function setup(){
  createCanvas(900,900);
  background(255);
}

function draw(){
  //line(x1, y1, x2, y2);
  line(100,100,600,100);
  
  //triangle(x1, y1, x2, y2, x3, y3);
  triangle(300,400,500,200,450,550);
  
  //quad(x1, y1, x2, y2, x3, y3, x4, y4);
  quad(50, 450, 300, 550, 200, 700, 50, 600);
}
```

But let's say we're a little more ambitious and we want to make a big spikey explosion type shape?! Let's draw our own shapes!

The first thing we need to do is type beginShape(); and endShape(); - This tells Processing "Hey Processing, the next few vertices that I specify, will be vertices for my shape.

```javascript
function setup(){
  createCanvas(900,900);
  background(255);
}

function draw(){
  beginShape();
    //vertex(x,y);
  endShape();
}
```

Now we add in each x and y value for each vertex of our shape. This can be a strenuous task however it does start to pay off once you can start manipulating those shapes with code.

```javascript
function setup(){
  createCanvas(900,900);
  background(255);
}

function draw(){
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

Then we've also added the paramater "CLOSE" to indicate that we want a closed shape. So we can make this strobe explosion! Warning: eyes!! 

Hide the ugly stroke with noStroke(); in setup().

```javascript
function setup(){
  createCanvas(900,900);
  background(255);
  noStroke();
}

function draw(){
  background(0,0,0);
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
}
```

Now this is a great example. Perhaps we knew that something like random() would give us some random numbers to create a strobe... however what we may not have predicted is the way that this renders to the screen. Can you see the strange shadows forming inside the shape? Try focusing on one point and then moving your head.

These are the wonderful discoveries that we sometimes stumble across. This is the moment we become collaborators with the computer rather than simply just using the computer to output something determined.

### random()
So what was going on with random()?

```javascript
//You can use the function random() with 0,1 or 2 arguments.
//If you use it with 0 arguments, it will return a value between 0 up to (but not including) 1. ie. 0.34
random()

//If you use it with 1 argument, it will return a value between 0 up to (but not including) the number. ie. in this case, 4.53
random(5);

//If you use it with 2 arguments, it will return a value between the first number up to (but not including) the second number. ie. in this case, 2.08
random(1,3);

```

Each time the random() function is called, it returns an unexpected value within the specified range.

So when it comes to colours, if you're using the default colour system of RGB colours - we could create a strobe colour effect with the fill of our shape with the following line:
```javascript
fill(random(255));
```

So every time the function draw() runs, it will select a different number between 0 up to(but not including) 255.

### More inspiration

Have an explore of these examples to give you a feel for what's possible in p5.js.
https://p5js.org/examples/

Have a look on things other people are creating on openProcessing:
https://www.openprocessing.org/browse/#

# Week 1 sketch
Week | Exercise |
--- | --- |
1 | Create an ode to an ode. We see A. Michael Noll create his hommage to Picasso, Mondrian and Riley. Let's select one of Noll's [artworks](http://dada.compart-bremen.de/item/agent/16) to recreate or perhaps a Picasso, Mondrian or Riley. Add a comment with the initial artwork/s that inspired you and why you chose that piece. Add any other references you were inspired by. We want to include at least one primitive(shape) and one or more instances of the function random() on a value. |

### Uploading your weekly exercises
- Go to https://www.openprocessing.org/ and log in.
- Navigate to Sketches and select Create a Sketch.
- On the far right panel, make sure your "mode" is set to p5js. 
- Type in your code, or if you're writing this locally, copy and paste your code.
- Check that it's working as intended by selecting Play.
- Go to My Feed and navigate to Classes.
- Scroll down to the week that you want to submit for and hit Add Sketch.
- Select your newly uploaded sketch and hey presto, we’ve submitted our first weekly exercise :) - You can edit these all the way up to your assignment submission but I would advise that you try to do as we go whilst the content is fresh in your mind.
- Make sure that Who can see it is set to Anyone or Me & My Classes in addition to Hide Source Code is set to Off.