# Week 05: Colours and palettes

By now, I would assume that most of you are going to town with random colours. It’s fun, so if you haven’t, here’s one I prepared earlier(prepare your eyes!):

```processing
void setup(){
  size(900,900);
  background(0);
  noStroke();
}
void draw(){
  background(random(255), random(255), random(255));
  fill(random(255), random(255), random(255));
  rect(random(900), random(900),100,100);
  fill(random(255), random(255), random(255));
  ellipse(width/2, height/2,random(150,200),random(150,200));
}
```

Now, unless you’re intentionally after this eye-bleeding aesthetic, this can be a little overwhelming for most. Step two in our journey of creative coding is organising the chaos.

This week we’re going to focus on some colour techniques to better curate what the computer produces. Now, I’m not going to bore you(or myself) with colour theory but rather, let’s talk about three ways to produce better colours.

## Color tip #1: Limit your values

By default, Processing accepts RGB values. These are represented by three numbers, each between 0-255 inclusive, telling the computer how much red, green and blue you want. These values are added together, to create an RGB colour. Therefore, if we’re saying:

```processing
fill(random(255), random(255), random(255), random(100));
```

We’re pretty much telling the computer take any RGB value of any alpha value and print it to the screen. Let’s generate a combo each time we press our mouse.

```processing
void setup(){
  size(900,900);
  background(255);
  noStroke();
}

void draw(){ 
}

void mousePressed(){ 
  background(random(255), random(255), random(255));
  fill(random(255), random(255), random(255),random(100));
  ellipse(width/2+200,height/2,500,500);
  fill(random(255), random(255), random(255),random(100));
  ellipse(width/2,height/2+200,500,500);
  fill(random(255), random(255), random(255),random(100));
  ellipse(width/2-200,height/2,500,500);
  fill(random(255), random(255), random(255),random(100));
  ellipse(width/2,height/2-200,500,500);
}
```

Now, this technique will eventually spit out something good - but it may take 1 mouse press or 100 mouse presses. We want to aim for something a little more reliable.

So by design, if we limit the pool of values that the computer can take from, we limit the amount of random freedom we’re giving the computer to produce a colour. This is something human vision can do much easier than teaching a computer what is and isn’t aesthetically pleasing.

*Note:* mousePressed() still requires the draw() function to exist even if there’s nothing there.

So let’s try it again with limited values:

```processing
void setup(){
  size(900,900);
  background(255);
  noStroke();
}

void draw(){ 
}

void mousePressed(){ 
  background(random(220,250), random(210,250),random(200,250));
  fill(random(200,250), random(200,250), random(200,250), random(200,250));
  ellipse(width/2+200,height/2,500,500);
  fill(random(200,250), random(200,250), random(200,250), random(200,250));
  ellipse(width/2,height/2+200,500,500);
  fill(random(200,250), random(200,250), random(200,250), random(200,250));
  ellipse(width/2-200,height/2,500,500);
  fill(random(200,250), random(200,250), random(200,250), random(200,250));
  ellipse(width/2,height/2-200,500,500);
}
```

Now you will notice, that most of the generated colours aren’t so random, and therefore - feel a lot more human-selected than computer-selected. Not perfect, but better...

Tweak colours until you're happy with how things are looking. You're looking for enough variation that the computer can surprise you but not enough surprise that your eyes are bleeding.

## Colour tip #2: Change the colour mode

Even though we could technically look at every value within our limited RGB values to curate them - it would take a long time. Therefore, when it comes to manipulating colour, the HSB colour mode is more human friendly. HSB stands for Hue, Saturation and Brightness, which makes a lot more sense than trying to think about how much Red, Green and/or Blue is in a colour.

The standard HSB values are:
