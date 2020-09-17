# Week 6
This week we're going to extend our idea of "data" - and use sound as our data and our medium.
Sound is a funny beast and I'll be honest, I always forget about sound. Even when I was designing interactive installations, we always forgot about sound until the very last minute - so now I try to bring it into my practice where I can. Don't forget, you can add sound!

For this week, we're going to talk about some wonderful creative practitioners that extend this notion of sound as a medium and then we're going to get our hands dirty and dive into adding libraries to our p5 toolkit, namely looking at the p5.sound library.

# DISCOURSE: Sound as a medium
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: Libraries and sound

## Meta-libraries
It’s time for a sketch UPGRADE! We are ready to start adding libraries - which means lots more cool things! Libraries are a collection of additional functions that we can join onto our sketch to make our sketch more awesome. That's right, libraries for our p5.js library!

Libraries are wonderful ways to extend projects in specific directions. And p5.js and Javascript both have a TONNE of libraries! See here at [p5.js Libraries](https://p5js.org/libraries/).

### Types of libraries
There are two types of libraries: Core Libraries and Community Libraries. Core libraries are maintained by the p5.js team, community libraries are maintained by "the community". There's not a lot of difference here, but sometimes the community libraries become out of date or not in sync with new versions of p5.

### Installing p5.sound
1. Using our ["my-empty-sketch" template](https://drive.google.com/file/d/1vtYeOFjw6v_PfgIaUhCQf71ly9JIdjtl/view?usp=sharing), open up your **index.html** file.
2. Paste in the following in between your <head></head> tags, underneath your reference to p5.min.js: 
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.1.9/addons/p5.sound.js" integrity="sha512-KxzVm+IqxNNq0+SzT/zzd5PHxY4LPrN+v5gZJ6+JKqjeU3Cr4y/djAg5eNlKDWurn1SeKZpql/yeOMWblMSzOg==" crossorigin="anonymous"></script>
```
It should look something like this:
```
<!DOCTYPE html>
<html lang="">

  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Empty Example</title>
    <link rel="stylesheet" href="style.css">
    <script src="p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.1.9/addons/p5.sound.js" integrity="sha512-KxzVm+IqxNNq0+SzT/zzd5PHxY4LPrN+v5gZJ6+JKqjeU3Cr4y/djAg5eNlKDWurn1SeKZpql/yeOMWblMSzOg==" crossorigin="anonymous"></script>
    <script src="sketch.js"></script>
  </head>

  <body>
  </body>

</html>
```
3. Now we can use the p5.sound functions!

## Using our microphone
First thing is first, let's turn on our Web Server again. If you've forgotten how to - navigate your way to "Apps" in Chrome and hit "Web Server". If this is not installed yet, you'll have to go back to [Week 5](https://github.com/melaniehuang/creative-coding-studio/blob/master/course-material/week-05.md) and follow the steps for installation.

So let's start with a black background with a white ellipse in the centre and then open up the Web Server URL in Chrome. This should but the link in your Web Server extension under "Web Server URL(s)". Mine is http://127.0.0.1/8887.

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0);
  ellipse(windowWidth/2, windowHeight/2, 200,200);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

Great, what a beautiful circle. Now let's say we want to read in the volume of our microphone input and use that to affect the background colour of our sketch. 

The first hurdle that we need to overcome that is specific to the browser - is that you need to have a user "initiate" audio. Gone are the days where you could auto-play on loop annoying songs to your visitors. p5.sound has a way to handle this. 

We are going to create a variable for our canvas and then set it up so that when a user clicks on the canvas, it gives the sketch permission to access a user's microphone.

```javascript
function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
}

function draw() {
  background(0);
  ellipse(windowWidth/2, windowHeight/2, 200,200);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

Now let's create a variable called "mic" to set the Audio In to the user's microphone.

```javascript
let mic;

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  mic = new p5.AudioIn();
  mic.start();
}

function draw() {
  background(0);
  ellipse(windowWidth/2, windowHeight/2, 200,200);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

If you refresh the page and click the canvas, you should see a red dot in the tab bar. This means, your microphone is on!
Now the last piece of the puzzle is to read in the volume - or in p5.sound language, it's the Amplitude. Let's name another new variable called amplitude and call in p5.Amplitude:

```javascript
let mic;
let amplitude;

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  mic = new p5.AudioIn();
  mic.start();
  amplitude = new p5.Amplitude();
}

function draw() {
  background(0);
  ellipse(windowWidth/2, windowHeight/2, 200,200);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```
Now we have this set up - let's get the "level" of our mic input. [getLevel()](https://p5js.org/reference/#/p5.Amplitude/getLevel) returns the volume of the sound source and returns a number between 0 and 1.

```javascript
let mic;
let amplitude;

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  mic = new p5.AudioIn();
  mic.start();
  amplitude = new p5.Amplitude();
}

function draw() {
  let micLevel = mic.getLevel();
  print(micLevel);
  background(0);
  ellipse(windowWidth/2, windowHeight/2, 200,200);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```
Let's open up our console, and don't forget to click the canvas. Now its time to SING or CLAP at our computer! You should see an increase as you sing or clap! Now let's use it in our sketch more visibly:

```javascript
let mic;
let amplitude;

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  mic = new p5.AudioIn();
  mic.start();
  amplitude = new p5.Amplitude();
}

function draw() {
  let micLevel = mic.getLevel()*255;
  background(micLevel);
  ellipse(windowWidth/2, windowHeight/2, 200+micLevel,200+micLevel);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

Hurray! So now what?!

## Using a sound file
So let's say instead of a microphone - we wanted to read in a sound file instead?
p5.sound can do that too! Let's [download](https://drive.google.com/file/d/1wjGVwbK5cyLQznXlF0IQNz9nrza-HXyC/view?usp=sharing) this sound clip I prepared earlier, or if you have an mp3 on hand you can use your own. Move this file into the data folder. This sound clip is from Uoon I - Alva Noto & Ryuichi Sakamoto (Vrioon). If you're using your own file, make sure to be aware of the file size. Sound files can get quite large and your sketch won't run until it has loaded. 

So we load the sound in our preload function just like we would load an image file.
Instead of start() - we use play() and instead of calling getLevel() on the mic, we're calling getLevel on the Amplitude.

```javascript
let sound;
let amplitude;

function preload(){
   sound = loadSound('data/sound-clip.mp3'); 
}

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  sound.play();
  amplitude = new p5.Amplitude();
}

function draw() {
  let soundLevel = amplitude.getLevel()*255;
  background(soundLevel);
  ellipse(windowWidth/2, windowHeight/2, 200+soundLevel,200+soundLevel);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

## Getting freaky with gradients
As I look at this example I remember an experience I had in a [James Turrell](https://mona.net.au/stuff-to-do/unseen-seen) chamber. If you're in Hobart, I suggest you witness this. If you haven't seen a Turrell before, he is a master of Light and Space. His use of colour and perception is extraordinary and I've always wanted to create a sound reactive gradient. So today is the day!

Now you may expect like in most programs, there's a function to do fill and a function to do gradient - but not in p5.js. However, rather than seeing this as "impossible" we're just going to learn how to draw gradients ourselves.

So if you think about what a gradient is... 
It's a colour slowing blending into another colour right?

What p5.js DOES have is a function called [lerpColor()](https://p5js.org/reference/#/p5/lerpColor). Let's give this one a whirl and because we're now dreaming in colour, let's change the colour mode too.

lerpColour() blends two colours together and finds the colour at "amt" specified between 0 and 1. So if the amt was 0.1, the colour would be closed to c1 and if the amt was 0.9, the colour would be closer to c2:
```javascript
lerpColor(c1, c2, amt)
```

```javascript
let sound;
let amplitude;
let from;
let to;

function preload(){
   sound = loadSound('data/sound-clip.mp3'); 
}

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  colorMode(HSB,360,100,100,100);
  from = color(345,57,94,100);
  to = color(273,57,94,100);
  sound.loop();
  amplitude = new p5.Amplitude();
  noStroke();
}

function draw() {
  let soundLevel = amplitude.getLevel();
  let interval = lerpColor(from, to, soundLevel);
  let interval2 = lerpColor(from, to, soundLevel-0.2);
  background(interval);
  fill(interval2);
  
  ellipse(windowWidth/2, windowHeight/2, 200,200);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

Okay so what's going on here? Can you figure it out?

And now for our final trick... I'm just going to leave this here:
```javascript
let sound;
let amplitude;

let from;
let to;

let toMin;
let toMax;

function preload(){
   sound = loadSound('data/sound-clip.mp3'); 
}

function setup() {
  let cnv = createCanvas(windowWidth, windowHeight);
  cnv.mousePressed(userStartAudio);
  sound.loop();
  amplitude = new p5.Amplitude();

  colorMode(HSB,360,100,100,100);
  from = color(345,57,94,100);
  toMin = color(273,57,94,100);
  toMax = color(320,57,94,100);
  noStroke();
}

function draw() {
  let soundLevel = amplitude.getLevel();
  background(from);

  for (let i = 1.0; i > 0.1; i-=0.01){
    let internalColor = lerpColor(toMin,toMax,soundLevel);
    let gradientBase = lerpColor(internalColor,from,i);
    fill(gradientBase);
    ellipse(windowWidth/2,windowHeight/2,i*1000,i*1000);
  }
}
```

Can you work our how to do radial gradients from looking at this code? What about linear gradients? Have a think!


## Week 06: Sound to visuals
Your task this week is to make your own interpretation of this sonic gradient. Where can you take it? How can you evolve it?
Please don't just change the colour and submit it - that's not making it your own! Play with colour, play with sound - just like all the artists we saw this week.