# Week 4

Congratulations! By now, you would've handed in your first assignment AND challenged yourself with the fundementals of coding. So this is great news! We have all the building blocks we need in place. Now we can use them!

Each week we're going to see some related inspiration and attempt to create something new. A new experiment, a new toy, a new area to tinker so hopefully you can see how these fundementals can live in the outside world and maybe perhaps in or as an extension to your already growing portfolio. 

# DISCOURSE: The early pioneers
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: Generative Poster Design
We're going to create a poster that can be manipulated with a set of sliders. We're also going to learn a little html & css to get you thinking about how all the pieces fit together and to explore variable typefaces together!

Let's start with getting an interesting background happening. We're dedicated this class to Vera Molnar so let's use a blend of her works as inspiration:
- [Cycle of Structure de Quadrilatère, 1985](https://www.artsy.net/artwork/vera-molnar-cycle-of-structure-de-quadrilatere)
- [Structure A, 1988](https://www.artsy.net/artwork/vera-molnar-structure-a)

## Poster Design
### Background 
For our background we're going to draw randomised wonky quadrilaterals with a stroke and no fill. We're going to layer those quads and increase the amount of them as we go down the canvas. Let's just start and see what emerges.

I want a portrait orientated poster at 595 x 860px with a black background.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
}
```

### Quadrilaterals 
Now we add a [quad()](https://p5js.org/reference/#/p5/quad). If you haven't drawn a quad before, check out the reference but here is the syntax with each (x,y) set being each of the four corners.
```javascript
quad(x1, y1, x2, y2, x3, y3, x4, y4);
```
```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  quad(5,5,45,5,45,45,5,45);
}
```

We are using quad() instead of rect() so we can have some fun over each corner. Let's add some randomness to the corners, just a little.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();  
  quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));
}
```

And already we can see a Molnar square!

Let's flex our function skills from last week and make this into a custom function.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  molnarQuad();
}

function molnarQuad(){
  quad(5+random(-5,5),5+random(-5,5), 45+random(-5,5),5+random(-5,5), 45+random(-5,5),45+random(-5,5), 5+random(-5,5),45+random(-5,5));
}
```

Now that we have our own function to make these quads, let's define how many quads we want draw on top of each other. We're going to give our function a parameter of s and then put it in a loop. 

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  molnarQuad(2);
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
	  quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));  	
	}
}
```

Remember these from last week? :) For Loops. Now look what happens when we change the number from 2 to 20.
```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  //changing from 2 to 20
  molnarQuad(20);
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

### Back to the grid
Let's put this wonky quad tile into a grid like we did with Escher's tesselations.

```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  for(let y = 0; y < 5; y++){
  	for(let i = 0; i < 5; i++){
      push();
      translate(i*60,y*60);
    	molnarQuad(2);
    	pop();
  	}
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

Let's see what happens when we now modify molnarQuad(2) to molnarQuad(y+1):


```javascript
function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  for(let y = 0; y < 5; y++){
  	for(let i = 0; i < 5; i++){
      push();
      translate(i*60,y*60);
    	molnarQuad(y+1);
    	pop();
  	}
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

### Quick exercise
Have a play around with the numbers, see what you can create.
Maybe you want to try a different shape or set of numbers... In the spirit of Molnar's Imaginary Machine - maybe let the computer surprise *you*!

## Adding sliders
Let's explore adding some UI to this poster. So our goal is to use some standard HTML inputs like a "slider" and connect the value of the slider to a variable within our sketch. 

We're going to explore this via the p5 library under the category of [DOM](https://p5js.org/reference/#group-DOM). This collection of functions gives us the ability to manipulate html and css on the page from our "sketch.js" file. 

Let's see this in action:
```javascript
let slider1;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 
  //create a slider with values from 2-20, start the slider at 5.
  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  for(let y = 0; y < 5; y++){
    for(let i = 0; i < 5; i++){
      push();
      translate(i*60,y*60);
      molnarQuad(y+1);
      pop();
    }
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

So now we have a slider at the bottom of the screen. If you move the slider handle around, nothing happens. That's because we haven't connected it to anything. Let's connect it to the amount of Molnar quads we want in our grid.

```javascript
let slider1;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 

  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  for(let y = 0; y < slider1.value(); y++){
    for(let i = 0; i < slider1.value(); i++){
      push();
      translate(i*60,y*60);
      molnarQuad(y+1);
      pop();
    }
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

And now let's make a second slider that alters the space between the quads.

```javascript
let slider1;
//Create a second variable for the second slider
let slider2;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 

  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');

  //create slider2 and its properties
  slider2 = createSlider(20, 120, 60);
  slider2.position(170, 880);
  slider2.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  //let's pull out the value 60 as a variable that will be controlled by slider2
  let grid = slider2.value();
  for(let y = 0; y < slider1.value(); y++){
    for(let i = 0; i < slider1.value(); i++){
      push();
      //now let's use the variable grid here
      translate(i*grid,y*grid);
      molnarQuad(y+1);
      pop();
    }
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

## sketch.js vs. index.html
Now let's say we want to add some text. We could simply do something like this:
```javascript
let slider1;
//Create a second variable for the second slider
let slider2;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 

  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');

  //create slider2 and its properties
  slider2 = createSlider(20, 120, 60);
  slider2.position(170, 880);
  slider2.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  //let's pull out the value 60 as a variable that will be controlled by slider2
  let grid = slider2.value();
  for(let y = 0; y < slider1.value(); y++){
    for(let i = 0; i < slider1.value(); i++){
      push();
      //now let's use the variable grid here
      translate(i*grid,y*grid);
      molnarQuad(y+1);
      pop();
    }
  }
  fill(0,0,100);
  noStroke();
  text("Hello there world!", width/2, height/2);
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

However, I want to explore variable typefaces with you today. And for that - we will need to use some css. What's the difference, you may ask?

When you type in:
```javascript
text(str, x, y);
```
We're asking the program to print the words "Hello there world" into the sketch on the HTML canvas that p5.js uses to render the graphics that you are drawing to screen. This means, the text is not what we call "live" text. "Live" text can be selected on a webpage, copy and pasted, can adjust itself to screen sizes, can be read by screen readers for people living with a vision impairment and the list goes on... 

### Quick exercise
Try and select the text to copy and paste it. Can you?

This may seem like a small nuance but when you start to build and design websites, we want to avoid fixed sizes for a digital landscape that comes in many screen sizes and resolutions. Besides, variable text sizing is not supported by the p5 DOM functions at the moment and its fun, so let's explore that further.

## HTML + CSS
First step, let's put some text on our website. We're going to open two unexplored files today, index.html and style.css.

Our html file determines what is being shown on the page and the css styles that page. When we write code to "sketch.js":
1. The webpage "index.html" loads the file "sketch.js" and the library "p5.js".
2. The p5.js library then reads "sketch.js" and knows how to render it as a html canvas object. 

Open up your **index.html** file in your text editor and in between our body tags:
```
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vera Molnar</title>
    <link rel="stylesheet" href="style.css">
    <script src="p5.min.js"></script>
    <script src="sketch.js"></script>
  </head>
  <body>
    <div class="grid-container">
      <div class="grid-item">MACHI</div>
      <div class="grid-item">NEIMA</div>
      <div class="grid-item">GINAI</div>
      <div class="grid-item">RE</div>
    </div>
    <div class="grid-container2">
      <div class="grid-item2">VERA MOLNAR</div>
      <div class="grid-item2">B. 1920</div>
      <div class="grid-item2">ARTIST</div>
    </div>
  </body>
</html>
```

Now let's see the text. Try and select it! Hurray! We have selectable text. Let's make it look not so basic. Open your **style.css** file in your directory and copy and paste the following:

```
html, body {
  height: 100%;
}

body {
  padding: 0;
  margin: 0;
  //background colour
  background-color: #100f0f;
  //text colour
  color: #fff;
}

canvas{
  //positioning the canvas to the very top
  position:absolute;
  top:0;
  //and moving it in the "z" space, behind everything
  z-index: -5;
}
```

So now we can see some changes. We've changed:
- the colour of the background
- the colour of the text
- the position of the canvas
- the viewing order of the canvas(moving it to the back)

Now let's mess about with the fonts.

## Google Fonts + HTML/CSS
Let's navigate to [Google Fonts](https://fonts.google.com/). Google Fonts is a catalog of well made web fonts that are free and open source. 

There's a checkbox labelled "Show only variable fonts" where you can see all the variable fonts available. Variable fonts on the web are a fairly new concept and are definitely not in common use however I suspect this will change soon. In any case, it's a good topic to start to think about and play around with.

If you want to use one of these variable fonts, go ahead and download it however many of them can only be altered in "weight". We're going to alter the "width" and "weight" of our poster text for our class today so we're going to use [Amstelvar](https://googlefonts.github.io/fluid/#wave).
- Download this font file here: https://github.com/TypeNetwork/Amstelvar/blob/master/fonts/Amstelvar-Roman%5Bwdth%2Cwght%2Copsz%5D.ttf

You can also find some fun variable fonts with fun variations [here](https://v-fonts.com/).

Now we want to load this font from our computer and use it on our poster. 
1. Let's select "Download" in the middle right or if you're on Google Fonts, select "Download family". 
2. Navigate to your Downloads folder and find the ttf file: "Amstelvar-Roman[wdth,wght,opsz].ttf".
3. Copy and paste this file into the folder called "data".
4. Open up your style.css file and declare this at the top:
```
@font-face {
  font-family: 'Amstelvar-Var';
  src: url('data/Amstelvar-Roman[wdth,wght,opsz].ttf');
}
```
5. Now let's change the fonts of our text inside the [class](https://www.w3schools.com/cssref/sel_class.asp) .grid-item and .grid-item2. Beneath the "canvas{}", write the following:
```
.grid-item {
  width:100%;
  font-family: 'Amstelvar-Var';
  font-variation-settings: 'wdth' 400, 'wght' 98;
  font-size: 150px;
  padding: 20px;
}

.grid-item2 {
  width:100%;
  font-family: 'Amstelvar-Var';
  font-variation-settings: 'wdth' 400, 'wght' 98;
  font-size: 18px;
  padding: 20px;
}
```
6. And the last touch, let's sort out this grid. We're going to use some basic [CSS Grid Layouts](https://www.w3schools.com/css/css_grid.asp):
```
.grid-container {
  display: grid;
  grid-template-columns: 500px;
  grid-template-rows: 150px 150px 150px 150px;
  padding: 10px;
}

.grid-container2 {
  position:absolute;
  top:760px;
  display: grid;
  grid-template-columns: 300px 100px 100px;
  grid-template-rows: 140px;
  padding: 10px;
}

.grid-item {
  width:100%;
  font-family: 'Amstelvar-Var';
  font-variation-settings: 'wdth' 400, 'wght' 98;
  font-size: 150px;
  padding: 20px;
}

.grid-item2 {
  width:100%;
  font-family: 'Amstelvar-Var';
  font-variation-settings: 'wdth' 400, 'wght' 98;
  font-size: 18px;
  padding: 20px;
}
```
If you want to read any further into html and css - there's many many many tutorials and resources online. I've linked some reference pages for you above. In addition, Daniel Shiffman also does wonderful playlist of videos on his Coding Train channel on [HTML/CSS/DOM](https://www.youtube.com/watch?v=URSH0QpxKo8&list=PLRqwX-V7Uu6bI1SlcCRfLH79HZrFAtBvX) which is exactly the area we're playing in today but he goes in depth into what is where and why.

Phew! Okay now that that's sorted, let's see the magic!

## Variable type in action
We're going to make a third and forth slider now to control the width(wdth) and the weight(wght) of our type. Here goes nothing!
```javascript
let slider1;
let slider2;
//Let's make some new variables
let slider3;
let slider4;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 

  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');

  slider2 = createSlider(20, 120, 60);
  slider2.position(170, 880);
  slider2.style('width', '100px');

  //New sliders with new properties
  slider3 = createSlider(75, 125, 75);
  slider3.position(310, 880);
  slider3.style('width', '100px');

  slider4 = createSlider(100, 900, 100);
  slider4.position(450, 880);
  slider4.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  let grid = slider2.value();
  for(let y = 0; y < slider1.value(); y++){
    for(let i = 0; i < slider1.value(); i++){
      push();
      translate(i*grid,y*grid);
      molnarQuad(y+1);
      pop();
    }
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

Okay now we have our sliders. Let's attach their values to font weight and widths. There's a few parts here so let's go slow. What we are now going to, in Javascript, is ask the program to: 
1. "Select" all the elements with the class "grid-item" in our index.html file. 
2. Get the values from slider3 and slider4 and format them in a way that the program can understand.
3. Change the css on each of those elements with the values from slider3 and slider4.

Step 1: Select the elements
```javascript
  //We ask the computer to select all the elements in our index.html file with the class ".grid-item"
  let gridItems = selectAll('.grid-item');
```
Step 2: Format values
```javascript
  //We create a custom string variable with all the values we need
  let varSetting = "'wdth' +"+slider3.value()+", 'wght' "+slider4.value();
```
Step 3: Change the css on each of those selected elements with the variable we've just created.
```javascript
  //Using a loop we change every selected item
  //gridItems.length gets the "length" of the array gridItems - how many elements have been selected?
  //For each element we change the css style of "font-variation-settings" to the string we prepared "varSetting"
  for(let g = 0; g < gridItems.length; g++){
    gridItems[g].style('font-variation-settings', varSetting);
  }
```

Now let's put it all together and give it a go!
```javascript
let slider1;
let slider2;
//Let's make some new variables
let slider3;
let slider4;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 

  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');

  slider2 = createSlider(20, 120, 60);
  slider2.position(170, 880);
  slider2.style('width', '100px');

  //New sliders with new properties
  slider3 = createSlider(75, 125, 75);
  slider3.position(310, 880);
  slider3.style('width', '100px');

  slider4 = createSlider(100, 900, 100);
  slider4.position(450, 880);
  slider4.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  let grid = slider2.value();

  let gridItems = selectAll('.grid-item');
  //"'wdth' "+slider3.value()+", 'wght' "+slider4.value()+";""
  let varSetting = "'wdth' " + slider3.value() + ", 'wght' " + slider4.value();
  for(let g = 0; g < gridItems.length; g++){
    gridItems[g].style('font-variation-settings', varSetting);
  }

  for(let y = 0; y < slider1.value(); y++){
    for(let i = 0; i < slider1.value(); i++){
      push();
      translate(i*grid,y*grid);
      molnarQuad(y+1);
      pop();
    }
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

### Quick exercise
Let's say we want to do the bottom text also. How would you do it?

```javascript
let slider1;
let slider2;
//Let's make some new variables
let slider3;
let slider4;

function setup() {
  createCanvas(595,860);
  colorMode(HSB, 360, 100, 100);  
  background(0,0,0); 

  slider1 = createSlider(2, 20, 5);
  slider1.position(30, 880);
  slider1.style('width', '100px');

  slider2 = createSlider(20, 120, 60);
  slider2.position(170, 880);
  slider2.style('width', '100px');

  //New sliders with new properties
  slider3 = createSlider(75, 125, 75);
  slider3.position(310, 880);
  slider3.style('width', '100px');

  slider4 = createSlider(100, 900, 100);
  slider4.position(450, 880);
  slider4.style('width', '100px');
}

function draw() {
  background(0,0,0); 
  stroke(0,0,100);
  noFill();
  let grid = slider2.value();

  let gridItems = selectAll('.grid-item');
  let varSetting = "'wdth' " + slider3.value() + ", 'wght' " + slider4.value();
  for(let g = 0; g < gridItems.length; g++){
    gridItems[g].style('font-variation-settings', varSetting);
  }

  let gridItems2 = selectAll('.grid-item2');
  for(let g = 0; g < gridItems2.length; g++){
    gridItems2[g].style('font-variation-settings', varSetting);
  }

  for(let y = 0; y < slider1.value(); y++){
    for(let i = 0; i < slider1.value(); i++){
      push();
      translate(i*grid,y*grid);
      molnarQuad(y+1);
      pop();
    }
  }
}

function molnarQuad(s){
  for(let i = 0; i < s; i++){
    quad(5+random(-5,5),5+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5),45+random(-5,5),5+random(-5,5),45+random(-5,5));    
  }
}
```

## Week 04: Love Posters

Select an artist, designer, creative or maybe just someone in your life that you love. Your task this week is to make a poster in their honour using the magic triangle of 3 rules & 3 sliders:
1. 595 x 860px in a portrait orientation
2. Black and white only
3. Must include a variable typeface

In addition to the above rules: it also must contain 3 sliders that control 3 seperate elements of the poster.