# Week 2

## Pivot
I've been thinking and reflecting a lot this week on the course ahead of us and I want to shift the exercises and examples a little to better reflect the things I learnt about you all in Week 1. 

There's always a tricky balancing act with teaching coding but a lot of the class seemed super enthusiastic on coding and advancing your knowledge, so we'll push more heavily in that direction using contemporary examples on how I've approached some projects. Therefore we'll be focusing less on the discourse element of our class, and focus more heavily on creating fun experiments to make this class more interactive.

I am planning to add in the following playful coding exercises into our lesson plan and update the summary accordingly:
- [Generative Posters/Typography](https://www.instagram.com/opencollab.mel/)
- [Live coding visuals](https://www.instagram.com/p/CDkfUkiHPHP/)
- [Machine Learning with StyleGAN and Snapchat](https://www.instagram.com/p/CBy4vXenvBD/)
- [Machine Learning with illustrations](https://www.instagram.com/p/CDA4kE2He6q/)

This will mean that we will move to coding locally on our computer, as openProcessing can be restrictive, and just use openProcessing as our gallery upload. This means that if you're working outside of openProcessing, we will upload a 1-2 minute screen capture of our visuals and upload the code as a zip. This will also give you a better sense of coding a commerical project like you would for a client.

### Let's see how this works.
Let's navigate to openProcessing.

1. Select the button "Create a sketch"
2. Open the side menu via the three dots or "kebab" icon
3. Navigate to "Files"
4. Upload your video as an .mp4 file called "video". [Asset download here](https://drive.google.com/drive/folders/1TzZcjKjFJ1pK_BgR-xPHUy1vdVeD9TVV?usp=sharing)
5. Copy in the below:

```javascript
let vid;

function setup() {
	createCanvas(900,900);
	background(0);
	vid = createVideo(['video.mp4'],vidLoad);
	vid.size(900, 900);
}

function draw() {
}

function vidLoad() {
  vid.loop();
  vid.volume(0);
}
``` 
**Code Description:**
Create a canvas that is 900 wide by 900 high with a black background. Create a video type variable with the file 'video.mp4' and assign it to the variable vid. Once the video finishes loading, call the function vidLoad which defines the video to play on loop with a volume of 0.

So there's a bunch of stuff there that may be new. Such as, what is a variable? And how do you define it? And how do we get this up and running on our computers.

## STUDIO: Variables, Movement and Color
### Download this zip if you haven't already
[Download this folder "my-empty-sketch"](https://drive.google.com/file/d/1vtYeOFjw6v_PfgIaUhCQf71ly9JIdjtl/view?usp=sharing)

### Data Types
Let's start with data types. In order for the computer to understand what kind of value it’s dealing with, you need to tell the computer what “type” of variable you’re going to be giving it. In a language like Processing you would write this:
```processing
int numberILike = 20;
```
This says that the variable called "numberILike" is an integer(whole numbers) and it's value is equal to the whole number 20;

However, in p5.js, because its JavaScript, we would define that same variable like this:
```javascript
let numberILike = 20;
``` 

But this doesn't mean that we're just ignoring data types. It's important when we start using this data, that we're aware of its type so that any calculations we do remain to make sense. 

The main data types that you’ll be dealing with at this stage are:

```javascript
//Number - floats have a decimal point and integers are whole numbers. They are considered the data type "Number". The difference becomes more important if and when you need to start rounding numbers or providing levels of accuracies in calculations.
let floatNumber = 2.01;
let intNumber = 20;

//String: A string is a sequence of characters. 
let sentenceString = "I am a sentence.";

//boolean - this one has only two values: true and false.
let trueOrFalse = true;

//And we have some special ones for the p5 library.
//p5.Color - You guessed it, a data type for handling colours. 
let crimsonRed = color(220,20,60);
let crimsonRed = color('#DC143C');
let crimsonRed = color('crimson');
let crimsonRed = color('hsl(348, 97%, 47%)');
let crimsonRed = color('hsb(348, 98.48%, 92.59%)');

//p5.Image - a canvas backed representation of an image. Can display .gif, .jpg and .png.
let imageDataType = loadImage('data/image.jpg');

//p5.Font - loads an opentype font file (.otf, .ttf) from a file or a URL, and returns a PFont Object
let myFont = loadFont('data/inconsolata.otf');
``` 

Note the lack of "u" in colour (this is a common type error when your code doesn’t run for us in Australia).

If you take another look at the [p5 reference](https://p5js.org/reference/), you'll notice that [image()](https://p5js.org/reference/#/p5/image) will show the data type of each parameter.

```javascript
image(img, x, y);

// img is the data type p5.Image
// x is the data type Number
// y is the data type Number
``` 

You will notice that majority of the shape parameters accept the "Number" data type - so this can be a float or an integer. Most of the time, you will need to make sure when doing calculations that you aren’t adding a String to a float for example - this will either not work or come up with something strange.

### Quick exercise
We're going to play a game. Answer along in your head.

What data type am I?

```javascript
let typeOne = 32.2;
let typeTwo = "60";
let typeThree = 60.0;
let typeFour = true;
let typeFive = 4;
let typeSix;
let typeSeven = "";
``` 

Now when you're confident - add this to your setup():
```javascript
print(typeof typeOne);
print(typeof typeTwo);
print(typeof typeThree);
print(typeof typeFour);
print(typeof typeFive);
print(typeof typeSix);
print(typeof typeSeven);
``` 

### Global variables and local variables
Let’s get our trusty circle back. We want what’s called a "global" variable that will increase each time the function draw() is called. This will create what I term the “smudge” effect.
```javascript
//I am a global variable, I'm available for every part of the sketch. And my data type is a float.
let x = 50.0;

function setup(){
  createCanvas(300,300);
}

function draw(){
  ellipse(x, 50, 50, 50); 
  //Increment variable x by 1
  x++;
}
``` 

A local variable is contained within a function and is only available in this function. Therefore, in the below program, the function setup() does not know about x. Let’s see what happens when you use a local variable...
```javascript
function setup(){
  createCanvas(300,300);
}

function draw(){
  //I am a local variable, I belong to draw() and only draw() knows about me!
  let x = 50.0;
  ellipse(x, 50, 50, 50); 
  //Decrement variable x by 1
  x--;
}
``` 

Eep! Nothing - snooze! This is because everytime you call the function draw() it sets x to 50.0 and decrements it by 1. Repeat. Local variables will be useful soon. However, for now, make sure you’re declaring your variables at the top of your program, outside of any function.

Now let's say we don't want to "smudge" the ellipse, we want to give the impression that the ellipse is moving across the screen.
```javascript
let x = 50.0;

function setup(){
  createCanvas(300,300);
}

function draw(){
  background(255);
  ellipse(x, 50, 50, 50); 
  x++;
}
``` 

### Quick exercise
Find two different 2D primitives(aka shapes) and increment/decrement their position and size using global variables. To smudge or not to smudge, I'll leave that up to you.

## Movement
BUT where do the shapes go?! Let's look at some common things you'll probably want to do. If you have any other ideas, shout out - let's work them out together!

### Conditionals
To get some more interesting movements, we need something called "conditionals". Conditionals are like questions we're asking our sketches. Is this true? If it is then do A - if it's something else do B. Like one of those choose-your-own-adventure books.

In this case, we're going to use the if statement to check if a statement is true.

### Looping behavior
```javascript
let x = 50.0;
let ellipseSize = 100;

function setup(){
  createCanvas(300,300);
}

function draw(){
  background(255);
  ellipse(x, 100, ellipseSize, ellipseSize); 
  //check if the ellipse has touched the far side of the canvas
  //if true: reset x to the start
  //otherwise continue
  if (x > width-ellipseSize/2){
  	x = ellipseSize/2;
  }
  
  x++;
}
``` 

### Ping Pong
```javascript
let x = 50.0;
let ellipseSize = 100;
let dir = 1;

function setup(){
  createCanvas(300,300);
}

function draw(){
  background(255);
  ellipse(x, 100, ellipseSize, ellipseSize); 
  //check if the ellipse has touched the right or left side of the canvas
  //if true: change the direction of the increment/decrement
  //otherwise continue
  if ((x > width-ellipseSize/2)||(x < ellipseSize/2)){
  	dir = dir*-1;
  }
  
  x+=dir;
}
``` 

### Smoooooothing with sin()
When I need something to move smoothly, I turn to my friend sin(). Now you may remember this little friend from trigonometry class and I definitely won't try to rehash that. 

But all you need to know is that it does what we did up there with Ping Pong by using the function sin(). This returns us a number moving back and forth between 1 and -1 and when plotted on a graph, gives us these beautiful wave forms.

```javascript
let ellipseSize = 100;
let angle = 0;

function setup(){
  createCanvas(300,300);
  noStroke();
}

function draw(){
  background(255);
  //converts degrees to radians
  let ang = radians(angle);
  //calculates the x position of the ellipse
  let x = width/2 + ellipseSize * sin(ang);

  fill(0);
  ellipse(x, height/2, ellipseSize, ellipseSize);
	
  fill(255);
  ellipse(width/2, height/2, ellipseSize, ellipseSize); 
  
  //increment our angle each loop
  angle += 2;
  
  //demonstrating values between -1 to 1
  print(sin(ang));
}
``` 

As we see here, there are different ways to do similar things and many other alternatives. There is no right or wrong answer here. They're all valid explorations. 

### Easing
In a similar vein, is the idea of easing. Now if you look at the things around in the world moving and stopping and starting, you'll realise that your ellipse incrementing by 1 each time is quite mechanical. It's consistantly moving at a static speed. Where if we think of our ellipse as a human running and about to run into a wall, we wouldn't see a human just run towards and into a wall at a steady incrementing speed would we?

Let's think of the number zero as the moon. And our destination is the moon. So we want to slow this ellipse down over time until it reaches a speed of 0(the moon).
```javascript
let x = 0;
let ellipseSize = 100;
let speed = 8;
let easing = 0.97;
		
function setup(){
  createCanvas(300,300);
}

function draw(){
  background(255);
	
  fill(0);
  ellipse(x,height/2,ellipseSize,ellipseSize);
	
  if (x > width-ellipseSize/2){
    x = width-ellipseSize/2;
  }

  speed *= easing;
  x+=speed;	
}
``` 

# DISCOURSE: Expression
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: Colours and Arrays
## Colours
Now let's dig deeper in the world of colours. If you haven't already had some fun with random colouring, here's one I prepared earlier, prepare your eyes!
```javascript
function setup(){
  createCanvas(900,900);
  background(0);
  noStroke();
}
function draw(){
  background(random(255), random(255), random(255));
  fill(random(255), random(255), random(255));
  ellipse(width/2+200,height/2,500,500);
  fill(random(255), random(255), random(255));
  ellipse(width/2,height/2+200,500,500);
  fill(random(255), random(255), random(255));
  ellipse(width/2-200,height/2,500,500);
  fill(random(255), random(255), random(255));
  ellipse(width/2,height/2-200,500,500);
}
``` 
Now, unless you’re intentionally after this eye-bleeding aesthetic, this can be a little overwhelming for most. Step two in our journey of creative coding is organising the chaos.

We’re going to focus on some colour techniques to better curate what the computer produces. Now, I’m not going to bore you(or myself) with colour theory but rather, let’s talk about three ways to produce better colours.

### Color tip #1: Limit your values
By default, Processing accepts RGB values. These are represented by three numbers, each between 0-255 inclusive, telling the computer how much red, green and blue you want. These values are added together, to create an RGB colour. Therefore, if we’re saying:
```javascript
fill(random(255), random(255), random(255), random(255));
``` 
We’re pretty much telling the computer take any RGB value of any alpha value and print it to the screen. Let’s move that chunk of code to another function called mousePressed() and add some transparency. mousePressed() is a p5 function that runs everytime you hit your mouse.

```javascript
function setup(){
  createCanvas(900,900);
  background(255);
  noStroke();
}

function draw(){ 
  //removing the code from here to function mousePressed()
}

function mousePressed(){ 
  background(random(255), random(255), random(255));
  fill(random(255), random(255), random(255),random(255));
  ellipse(width/2+200,height/2,500,500);
  fill(random(255), random(255), random(255),random(255));
  ellipse(width/2,height/2+200,500,500);
  fill(random(255), random(255), random(255),random(255));
  ellipse(width/2-200,height/2,500,500);
  fill(random(255), random(255), random(255),random(255));
  ellipse(width/2,height/2-200,500,500);
}
``` 

Now, this technique will eventually spit out something good - but it may take 1 mouse press or 100 mouse presses. We want to aim for something a little more reliable.

So by design, if we limit the pool of values that the computer can take from, we limit the amount of random freedom we’re giving the computer to produce a colour. This is something human vision can do much easier than teaching a computer what is and isn’t aesthetically pleasing.

So let’s look at a little Agnes Martin colouring.

```javascript
function setup(){
  createCanvas(900,900);
  background(255);
  noStroke();
}

function mousePressed(){ 
  //agnes pale blue white 240,247,247
  background(random(200,247), random(230,250), random(230,250));
  //agnes pale blue 219,227,227
  fill(random(200,220), random(210,230), random(215,235),random(50,150));
  ellipse(width/2+200,height/2,500,500);
  //agnes pale pink 237,223,212
  fill(random(220,240), random(230,240), random(210,220),random(50,150));
  ellipse(width/2,height/2+200,500,500);
  //agnes pale yellow 239,234,209
  fill(random(235,245), random(220,250), random(200,220),random(50,150));
  ellipse(width/2-200,height/2,500,500);
  //agnes pale gray 225,235,233
  fill(random(210,230), random(230,240), random(230,240),random(50,150));
  ellipse(width/2,height/2-200,500,500);
}
``` 
Now you will notice, that most of the generated colours aren’t so random, and therefore - feel a little more human-selected than computer-selected. Not perfect, but not so hectic...

Tweak colours until you're happy with how things are looking. You're looking for enough variation that the computer can surprise you but not enough surprise that your eyes are bleeding.

### Color tip #2: Change the colour mode
Even though we could technically look at every value within our limited RGB values to curate them - it would take a long time. Therefore, when it comes to manipulating colour, the HSB colour mode is more human friendly. HSB stands for Hue, Saturation and Brightness, which makes a lot more sense than trying to think about how much Red, Green and/or Blue is in a colour.

[Here's a bigger explanation on HSB](https://learnui.design/blog/the-hsb-color-system-practicioners-primer.html)

You'll notice that this is a link to the Learn UI blog. This is also a very handy tip to keep in your back pocket when balancing interface colours, I'm so bad at colours and I use this all the time!

The idea is that you pick a "saturation" and/or "brightness" and alter the "hue" to make a colour palette. It's surprisingly effective. It's also a great way to build up a systematic colour system if you're building out a style guide. 

This is also an interesting read about [Building an accessible colour system part 1](https://uxdesign.cc/my-struggle-with-colors-52156c664b87) and [part 2](https://uxdesign.cc/my-struggle-with-colors-part-ii-ed71bff6302a) for any budding interface designers/front end web devs out there. This talks about building a colour system that takes into account contrast levels to better support communities living blind or with a vision impairment.

Anyway, I digress. 

When thinking of HSB colours, first think of where you want to be on the colour spectrum. 

**Hue**
Values run from 0 to 360 - running through red, orange, yellow, green, blue, purple, magenta and looping back around to red.

**Saturation**
Values run from 0 to 100 - running from no saturation to highly saturated

**Brightness**
Values run from 0 to 100 - running from black to super bright

Let's just play with some colours.
```javascript
function setup(){
  colorMode(HSB,360,100,100,100);
  createCanvas(900,900);
  background(random(210,240), random(60,80), random(90,100));
  noStroke();
}

function draw(){
}

function mousePressed(){
  background(random(210,240), random(60,80), random(90,100));
  fill(random(30,60), random(60,80), random(90,100));
  ellipse(width/2+200,height/2,500,500);
  fill(random(10,20), random(60,80), random(90,100));
  ellipse(width/2,height/2+200,500,500);
  fill(random(20,30), random(60,80), random(90,100));
  ellipse(width/2-200,height/2,500,500);
  fill(random(0,60), random(60,80), random(90,100));
  ellipse(width/2,height/2-200,500,500);
}
```

Now you should start catching yourself, changing the random values of a hue, saturation or brightness level. Do you feel more in control of your random colours now?

### Quick exercise
Let’s try something. We want a colour palette of different shades and tints of pink and blue. How would you go about randomising these shades and tints?

### Color tip #3: Just pick some
These are oldies but goodies. Choose your colours beforehand - shock horror 😱! If you’re like me and find colours terrifyingly hard, here are some tools that you may or may not have encountered to make our lives easier:

The super fast color schemes generator https://coolors.co/
An AI colour generator http://khroma.co/
Search by colour through other designers’ work for inspiration via [Dribble](https://dribbble.com/colors/6c16c7) or [Designspiration](https://www.designspiration.net/) 

Another tip when I'm super stuck. I begin to look at a photo or an illustration that use colour in the way that I am trying to and I sample colours directly from there. 

### Quick exercise
Select a colour. Now, make a palette of four other colours to complement your chosen colour. You’ll use these colours in the next section.

## Arrays
The next stage in our Creative Coding journey is being able to make a colour palette for our artwork that we can draw upon. The way that we are going to do this is to create an Array of colours. What is an Array you might ask? Well, I’m glad you asked...

An Array is yet another datatype which can store a list of “things”. The “things” can be any datatype from a Number to a String and sometimes even MORE arrays. In our case, we’ll be using the datatype color to create a palette we can draw upon during our sketch.

To make an Array of colors, we need to globally define it at the top of our sketch, assign a variable name(colorList) and store a list of items.
```javascript
colorList = [item 0, item 1, item 2, item 3, item 4];
```

We describe the first item in an array as having an index of 0. The second item is therefore at index 1, the third at index 2 and so on...

Now, we’re going to replace each "item" with a different colour in the list. Use your colours from the above exercise and pay close attention to syntax here.

```javascript
let colorList;

function setup(){
  colorMode(HSB,360,100,100,100);
  createCanvas(900,900);
  colorList = [color(0,100,100), color(20,100,100), color(60,100,100)];
}

function draw(){
}
```

Now we’ve made our colour palette, we want to grab the first "colour" in the array, also known as the 0th item. To do this, instead of explicitly stating a colour, we state:

```javascript
let colorList;

function setup(){
  colorMode(HSB,360,100,100,100);
  createCanvas(900,900);
  colorList = [color(0,100,100), color(20,100,100), color(60,100,100)];
  noStroke();
}

function draw(){
  background(colorList[0]);
  fill(colorList[1]);
  ellipse(width/2, height/2, 800,800);
}
```

Or perhaps we want to get out a random colour from our palette each time we click?

```javascript
let colorList;

function setup(){
  colorMode(HSB,360,100,100,100);
  createCanvas(900,900);
  colorList = [color(0,100,100), color(20,100,100), color(60,100,100)];
  noStroke();
}

function mousePressed(){
  background(random(colorList));
  fill(random(colorList));
  ellipse(width/2, height/2, 800,800);
}
```

### Quick exercise
Draw a couple of shapes on the screen and change the colours of shapes using the colours in your array/palette.

## Save your images
The last step this week in curating our sketches, is to be able to save our canvas into an image when we’re happy with it. You can use this to create static images for Task 1. To save an image when we hit a key on our keyboard, let’s try the following:

```javascript
let colorList;

function setup(){
  colorMode(HSB,360,100,100,100);
  createCanvas(900,900);
  colorList = [color(0,100,100), color(20,100,100), color(60,100,100)];
  noStroke();
}

function mousePressed(){
  background(random(colorList));
  fill(random(colorList));
  ellipse(width/2, height/2, 800,800);
}

function keyPressed(){
  save("myImage.jpg");
}
```

Now we've set up a basic mechanism and structure. Click the canvas until you're happy with a result, then hit any key to save your favourite combinations.

## Week 02 Exercise
We've learnt a lot this week about movement, expression and colour. Let's put it all into action by using a colour palette inspired by Mark Rothko. Using shapes, transparency and a user defined colour palette, select one of the following human conditions to illustrate: "innocence", "gratitude", "friendship", "tragedy" or "ecstasy".