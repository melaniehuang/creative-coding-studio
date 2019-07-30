# Week 1: Setup

## Join our Slack
[Join our Slack channel](https://join.slack.com/t/creativecodin-9bj1428/shared_invite/enQtNzAzMDgzMzY3NTg0LWQ5NTRjNjcyZGZmZTU3ZGFlZWI0NDk2YjJiYzYzMjY2OTZlODYzNTQ4ZDYwNTEzNGQzODI0Mzg5ZTY1NTEzODc) using your RMIT email address. This is where you will be able to communicate with me and each other. This is probably the fastest way to get in touch with me, otherwise, send me an email.
This will be the link - for future reference: [https://cc-studio-2019.slack.com/](https://cc-studio-2019.slack.com/)

## Download and install Processing 
[Download the latest version of Processing here](https://processing.org/download/). We'll be working with a mixture of Processing and p5.js(Javascript) in class but when you're on your laptop/desktop - this is where we will be writing our code. For now, this is fine - but later on in the semester we may want to write Javascript in the online editor which I've linked below.

## Join the openProcessing class
~~[Join the openProcessing classroom](https://www.openprocessing.org/class/59891)
You will be supplied with a code to join the classroom in class. Please use an obvious name and your RMIT email when signing up. This is where we will be submitting our weekly tasks and as a result, sharing what we’ve all been making. It can be a little incompatible sometimes - but we'll work through it :)~~
**Edit: This was not working too well in the new computer labs. Let's park this for now and rather just zip up our Processing sketches for submissions.**

## p5 Editor
[Sign up for an account](https://editor.p5js.org/) to write your code in the browser. Create an account and press play. You can only save files when you're logged in. So to make sure you don't lose any work - make sure you're logged in. Once we start to do more intensive sketches that need more processing(mind the pun) power, we'll need to use the desktop editor that you installed above.

# Week 1: Introduction to Processing

## Sketching with code
The concept of a “sketch” is fundamental to Processing. It introduces a new way of looking at code to encourage the ability to “sketch” with code. 

[Ben Fry's address](https://youtu.be/9IOTFZLYtqU)
"I want people to be impatient with the tools that are readily available to them... I'm less interested in someone creating the next Photoshop, but I do want them to create the tool that **is** the Photoshop they need for the project that they're actually creating at the time... We've been too willing to use the tools that have been provided to us created by companies who's primary interest is their bottom line and not necessarily the artefacts we create with their products."

[Lauren's voice - from 5:00](https://youtu.be/smXEYs_Bcpc)
"This slide has the word 'learn' in here which is really important to me...starting out you can see these people making code and you think oh I had to go to some elite univeristy, or work at a big company or be some kind of expert and I'm never going to get there... the whole basis of this is about learning. The idea of Processing is to make learning to code a little easier, a little bit more accessible to people that maybe don't relate to just printing out numbers to a command line... And this idea of making mistakes. Sometimes those screw ups become the most interesting part of your project... That's what's special about this group here. We are able to appreciate those mistakes and turn that into something wonderful."

Now Processing is only one community of programming artists - but you will discover a lot more and find that computer art goes back as soon as we started to look at what computers could do.

**And here's some more video inspo:**
- [A Box of Chaos: The Generative Artist's Toolkit by Benjamin Kovach](https://www.youtube.com/watch?v=kZNTozzsNqk&t=1s)
- [Code goes in, Art comes out - Tyler Hobbs](https://www.youtube.com/watch?v=LBpqoj2nOQo)

## Saving a file
When we save our sketch file, Processing will save that sketch inside a folder of the same name. For the sketch to run smoothly, you will always need to keep that sketch file (*.pde) inside the folder. Like this:
**sketch_name > sketch_name.pde**
This is how the computer knows where to find your sketch and any files or parts you may reference in your sketch.

## The first square
Functions are like mini programs and the main two functions that exist in Processing are setup() and draw(). setup() runs once at the start of our sketch and draw() runs over and over again on repeat until you press stop. 

Try the following:

```processing
//This runs once
void setup(){
  size(900,900);
  background(0);
}

//This runs on repeat
void draw(){
  rect(400,400,100,100);
}
```

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

Can you describe what is happening in this sketch in plain english?
Change some numbers and it should become fairly obvious :)

You’ll also notice here that I have included these lines: _//This runs once_ and _//This runs on repeat_. This is what’s known as commenting - the characters **//** that precede the comment tell the computer to ignore this line. You will be using comments to add any inspiration or references you may have used for your sketches.

### !! This part is a super important bit !!
You will find a LOT of inspiration online and naturally watch a tonne of tutorials to learn throughout the semester. I dare you to get through the entire semester without watching one of [Daniel Shiffman's Coding Train](https://www.youtube.com/user/shiffman) videos. As Lauren McCarthy eloquently said, learning is part of the process. *However* - you **MUST** put your sources in your code commented at the top of your code. It doesn't need to be complex, just something like this so I can tell where their ideas end and yours begin:

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

```processing
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
```processing
//rect(x, y, width, height);
rect(0, 0, 200, 200);
```

By default, rect() accepts the x & y position of the rectangle’s top left corner.
Now, let’s add some colour!


## Sequence, colour and fill

So to add a fill to the rectangle, we need to add a line _above_ our rect() function:
```processing
fill(169,225,250);
```

By default, Processing interprets your numbers as RGB colours - the amount of red, green and blue you want to mix into a single colour. When we write something like:
```processing
fill(255);
```
the computer is actually interpreting that to be:
```processing
fill(255,255,255); 
```

**Try the following:**
```processing
void setup(){
  size(900,900);
  background(248,250,169);
}

void draw(){
  fill(169,225,250);
  rect(400,400,100,100);
}
```

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

Under **Tools > Colour Selector**, you can choose your own RGB colours. We will delve more into colours and what the numbers all mean later in the semester. For now, just copy and paste the R, G and B values as comma-separated numbers like the example above.

In addition, let’s remove that awful black stroke. By default:
```processing
stroke(0); 
```
is applied to all 2D Primitives. In the setup() function, include the line:
```processing
noStroke();
```

What if we wanted to add another rectangle? One with a stroke and one without? Have a go.

## Using the Processing reference
We will go into depth about shapes post exhibition - but for the next exercise we're going to look at circles and/or ellipses. Now it may seem that "coders" just seem to type things in that they've memorised but a big part of coding is looking up the reference docs as there is simply too much to just "remember". 
[View Processing's reference docs](https://processing.org/reference/)

Let's find how to create a circle or ellipse.
1. Search the page for what you think it might be called. In this case, circle() and ellipse().
2. Read the docs. It's really that straight forward in Processing as they have done a lot of work to make the documentation as friendly as possible.
[circle()](https://processing.org/reference/circle_.html)
[ellipse()](https://processing.org/reference/ellipse_.html)

The two parts you're looking for are...

The **example** code - the one you can just copy, paste and manipulate:
```processing
ellipse(56, 46, 55, 55);
```
and the **syntax** on how to use that function:
```processing
ellipse(a, b, c, d)
/*	
a	- float: x-coordinate of the ellipse
b	- float: y-coordinate of the ellipse
c	- float: width of the ellipse by default
d	- float: height of the ellipse by default
*/
```
So in human terms, by default, this means:
```processing
ellipse(x-coordinate of centre point, y-coordinate of centre point, ellipse width, ellipse height)
```

# Weekly exercise
So that's enough blabbering. Let's start by trying!
In celebration of our NGV visit next week, let's use an Alexander Calder mobile as inspiration.

![Alexander Calder, Gamma](https://github.com/melaniehuang/creative-coding-studio/blob/master/course-material/images/week-01-001.jpg)

Alexander Calder
American 1898–1976
_Gamma(1947)_
painted sheet metal and steel wire
147.3 x 213.3 x 94.4 cm
Collection of Jon Shirley
© 2019 Calder Foundation, New York/Copyright Agency, Australia

## Week 1 sketch
Week | Exercise |
--- | --- |
1 | Use Alexander Calder's work aestethically as your inspiration. Draw at least two different x 2D primitives to the screen in an interesting way. Use colour/s other than grayscale. Add your name as a comment at the top of the sketch for good practice. If you use any of his artworks or other tutorials as a reference, please include these also in your comments. If you do not use any particular artwork and/or other tutorials, please add a comment acknowledging that you "did not use any additional material" for inspiration. |

# Uploading your weekly exercises
1. Go to [openProcessing](https://www.openprocessing.org/) and log in.
2. Navigate to **“Sketches”** and select **“Create a Sketch”**.
3. On the far right panel, make sure your “mode” is set to **“Processing.js”**. This will save you from having to translate your code into Javascript manually(most of the time!).
4. Copy and paste your code from Processing to the light grey box and hit **Save**.
5. Go to “My Feed” and navigate to **“Classes”**.
6. Scroll down to the week that you want to submit for and hit **“Add Sketch”**.
7. Select your newly uploaded sketch and hey presto, we’ve submitted our first weekly exercise :)
8. Make sure that **“Who can see it”** is set to **Anyone** or **Me & My Classes** in addition to **“Hide Source Code”** being set to **Off**.
