# Week 1: Setup

## Join our Slack
Using your RMIT email address, navigate to https://cc-studio-2020.slack.com/ and sign up/join the conversation. This is where you will be able to communicate with me and each other. This is a service I use day to day for work and freelance projects so it will be the fastest way to get in touch with me, otherwise, send me an email.

## Download Sublime
If you have a preferred code editor, feel free to use it but for our class I will be using Sublime. [Download Sublime Text 3 here](https://www.sublimetext.com/3)

## Download this package to get started
[Download this folder "my-empty-sketch"](/template)
This is where we'll start, locally on our machines to hopefully prevent any incompatabilities *fingers crossed*. First download the above and then we'll go into what each thing is after that.

## Join the openProcessing class
[Join the openProcessing classroom](https://www.openprocessing.org/class/64609). You will be supplied with a code to join the classroom in class. Please use an obvious name and your RMIT email when signing up. This is where we will be submitting our weekly tasks and as a result, sharing what we’ve all been making.

## p5 Editor
There is an [online editor](https://editor.p5js.org/) that we may have to use during class this semester depending on how your machine is handling the above process.

# What on earth was all that about up there?!

## Welcome to Creative Coding
Congratulations, you have taken the dive! Welcome to big, bad and exciting world of creative coding. It is a large and ever-evolving landscape. 

It's normal to feel nervous if this is your first time coding. We will treat this class like any other studio class. We will make, experiment, discuss and evolve our ideas together AND most importantly leave noone behind. This studio is made to allow you to be as creative or as technical as you would like.

We've had students make little drawing machines, sound reactive installations, body reactive visuals, machine learning experiments and my personal favourite generative design and art.

Some common names that you may come across are things like:
- Processing/p5.js
- openFrameworks
- vvvv
- Cinder
- Max MSP
- Pure Data

This semester we will be covering Processing; a programming language for learning how to code within the context of the visual arts. We will be writing with a Javascript library called p5.js and submitting our weekly sketches via openProcessing.

Maybe a table might be easier to show you how these pieces fit.

Processing | Processing.js | openProcessing | p5.js | Javascript |
--- | --- | --- | --- | --- |
Created in 2001, as a language for learning how to code within the context of the visual arts. It runs on your Desktop. It is a programming language based on Java. This is the OG we know and love. | Created in 2008 and has since been sidelined(works but has noone to maintain or improve it). Can run on the web. It was made to run Processing sketches in the browser. It's also used as a base to run Processing code inside of openProcessing which highlights some incompatabilities. | Created in 2009 as a method of sharing your sketches and creating an online Processing community with visuals! Runs online. Online community where you submit your sketches to a class and can upload and share your sketches. | The newest of the bunch, released in 2014 and has the most work and effort going into it currently. It runs in the browser and there is an online editor(that we may use). p5.js is a Javascript library based on Processing. | JavaScript, often abbreviated as JS, is a programming language that runs in your browser. JavaScipt is the language - p5.js is a Javscript library. So we will be writing Javascript using the p5.js library.

Hopefully, we're all still here AND we're ready to go!


# Week 1: Introduction to Processing

## Sketching with code
The concept of a “sketch” is fundamental to Processing and as you can see we have named our empty template, "my-empty-sketch". It introduces a new way of looking at code to encourage the ability to "sketch" with code. As a designer, one of the things I had to unlearn when I started creative coding was letting myself "sketch" and "play" rather than having a definite visual I wanted to produce to the pixel. As I'm sure, you will also find - if you want a predefined static visual, you could probably get there quicker with something like Photoshop or Illustrator. The advantages of creative coding is being able to push beyond what you can already imagine - and rather collaborate WITH the computer and let it surprise you.

[Ben Fry's address](https://youtu.be/9IOTFZLYtqU)
"I want people to be impatient with the tools that are readily available to them... I'm less interested in someone creating the next Photoshop, but I do want them to create the tool that **is** the Photoshop they need for the project that they're actually creating at the time... We've been too willing to use the tools that have been provided to us created by companies who's primary interest is their bottom line and not necessarily the artefacts we create with their products."

[Lauren's voice - from 5:00](https://youtu.be/smXEYs_Bcpc)
"This slide has the word 'learn' in here which is really important to me...starting out you can see these people making code and you think oh I had to go to some elite univeristy, or work at a big company or be some kind of expert and I'm never going to get there... the whole basis of this is about learning. The idea of Processing is to make learning to code a little easier, a little bit more accessible to people that maybe don't relate to just printing out numbers to a command line... And this idea of making mistakes. Sometimes those screw ups become the most interesting part of your project... That's what's special about this group here. We are able to appreciate those mistakes and turn that into something wonderful."

Now Processing is only one community of programming artists - but you will discover a lot more and find that computer art goes back as soon as we started to look at what computers could do.

**Here's are some more video inspirations:**
- [A Box of Chaos: The Generative Artist's Toolkit by Benjamin Kovach](https://www.youtube.com/watch?v=kZNTozzsNqk&t=1s)
- [Code goes in, Art comes out - Tyler Hobbs](https://www.youtube.com/watch?v=LBpqoj2nOQo)
- [Vera Molnar on Computer Art](https://www.youtube.com/watch?v=BCZNNZGz5YI)

## Saving a file

## The first square
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

## Co-ordinates

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

## Sequence, colour and fill

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
What if we wanted to add another rectangle? One with a stroke and one without? Have a go.

## Using the p5.js reference
We will go into depth about shapes next week - but for the next exercise we're going to look at circles and/or ellipses. Now it may seem that "coders" just seem to type things in that they've memorised but a big part of coding is looking up the reference docs as there is simply too much to just "remember". 
[View p5.js' reference docs](https://p5js.org/reference/)

Let's find how to create a circle or ellipse.
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
```javascript
ellipse(x-coordinate of centre point, y-coordinate of centre point, ellipse width, ellipse height)
```

# Weekly exercise
So that's enough blabbering. Let's start by trying!

![Image title](url)

## Week 1 sketch
Week | Exercise |
--- | --- |
1 | ... |

# Uploading your weekly exercises
1. Go to [openProcessing](https://www.openprocessing.org/) and log in.
2. Navigate to **“Sketches”** and select **“Create a Sketch”**.3. On the far right panel, make sure your “mode” is set to **“Processing.js”**. This will save you from having to translate your code into Javascript manually(most of the time!).4. Copy and paste your code from Processing to the light grey box and hit **Save**.5. Go to “My Feed” and navigate to **“Classes”**.6. Scroll down to the week that you want to submit for and hit **“Add Sketch”**.7. Select your newly uploaded sketch and hey presto, we’ve submitted our first weekly exercise :)8. Make sure that **“Who can see it”** is set to **Anyone** or **Me & My Classes** in addition to **“Hide Source Code”** being set to **Off**.
