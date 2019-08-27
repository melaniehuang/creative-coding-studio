# Week 6: Loops and repetition

So we’ve been drawing shapes, changing colours and composing our designs. It’s time to look at how the computer can help us with the things that the computer is great at and our human math-ing is not so great at. Let’s start by simply drawing a circle:

```processing

color[] colorList = new color[5]; 
void setup(){
  size(900,900);
  noStroke();
  colorMode(HSB,360,100,100);
  colorList[0] = color(199,100,90);
  colorList[1] = color(186,58,90);
  colorList[2] = color(9,78,94);
  colorList[3] = color(322,34,100);
  colorList[4] = color(13,24,100);
}

void draw(){
}

void mousePressed(){
  background(colorList[int(random(5))]);
  fill(colorList[int(random(5))]);
  ellipse(50,50,100,100);
}
```

So now let’s say we want to draw a row of circles, we could copy and paste line 19 and 20 over and over again, calculating the new coordinates and filling up the row. Bearable, but now what if you want to draw 100 smaller circles?! So this is where the for loop comes to the rescue. The for loop is denoted in the following way:

```processing 
for (init; test; update) { 
  statements
} 
```
1. The init statement is run.
2. The test is evaluated to be true or false.
3. If the test is true, jump to step 4. If the test is false, jump to step 6.
4. Run the statements within the block.
5. Run the update statement and jump to step 2.
6. Exit the loop.

If this looks overwhelming, don’t worry. It’s quite straight forward once we talk in human words.

init =  “Computer, start the variable’s value here,...”
test =  “...keep running the statements until this is false”
Update =  “...and each time, update the value.”

Therefore, let’s step through what we know:
1. Our canvas is 900px wide 
2. Our circles are 100px wide
3. Therefore, we need 9 circles to fill a row. 

**init - “Computer, start the variable i at the value 0”**
```processing
for (int i = 0; test; update){ 
  //statements
} 
```
**test - “...keep running the statements until i <  9 is false...”**
```processing
for (int i = 0; i < 9; update){ 
  //statements
}
```
If we want 9 circles in a row, each time we run the loop of statements, we want to increment the circle’s x value by 100px so that we’re not drawing 9 circles on top of one another. Therefore, we need to add a little maths to the circle’s x value.

**update - “...and each time, increment i by 1.”**
```processing
for (int i = 0; i > 9; i++){ 
  ellipse(50+(100*i),50,100,100);
}
```
So let’s give it a shot:

```processing
color[] colorList = new color[5]; 

void setup(){
  size(900,900);
  noStroke();
  colorMode(HSB,360,100,100);
  colorList[0] = color(199,100,90);
  colorList[1] = color(186,58,90);
  colorList[2] = color(9,78,94);
  colorList[3] = color(322,34,100);
  colorList[4] = color(13,24,100);
}

void draw(){
}

void mousePressed(){
  background(colorList[int(random(5))]);
  for (int i = 0; i < 9; i++){  
    fill(colorList[int(random(5))]);
    ellipse(50+(100*i),50,100,100);
    println(i);
  }
}
```

**Exercise**
1. Can you work out why sometimes some circles are missing?
2. Now, can you work out how to repeat this row of 9 circles nine times down the canvas?
Hint: A loop can contain a loop! 

```processing
color[] colorList = new color[5]; 

void setup(){
  size(900,900);
  noStroke();
  colorMode(HSB,360,100,100);
  colorList[0] = color(199,100,90);
  colorList[1] = color(186,58,90);
  colorList[2] = color(9,78,94);
  colorList[3] = color(322,34,100);
  colorList[4] = color(13,24,100);
}

void draw(){
}

void mousePressed(){
  background(colorList[int(random(5))]);
  for (int i = 0; i < 9; i++){  
    for (int j = 0; j < 9; j++){
      fill(colorList[int(random(5))]);
      ellipse(50+(100*i),50+(100*j),100,100);
    }
  }
}
```

Let’s have a look at a way we can improve this loop. Let’s say we want to be able to change the size of the circles and the size of the canvas, but always draw enough circles to fill the canvas.

```processing
color[] colorList = new color[5]; 
int ellipseSize = 20;

void setup(){
  size(400,650);
  noStroke();
  colorMode(HSB,360,100,100);
  colorList[0] = color(199,100,90);
  colorList[1] = color(186,58,90);
  colorList[2] = color(9,78,94);
  colorList[3] = color(322,34,100);
  colorList[4] = color(13,24,100);
}

void draw(){
}

void mousePressed(){
  background(colorList[int(random(5))]);
  
  for (int i = 0; i < width; i+=ellipseSize){ 
    for (int j = 0; j < height; j+=ellipseSize){ 
      fill(colorList[int(random(5))]);
      ellipse((ellipseSize/2)+i, (ellipseSize/2)+j,
      ellipseSize,ellipseSize);
    }
  }
}
```

**Exercise: Can you explain the new loop in plain English?**
```processing
for (int i = 0; i < width; i+=ellipseSize){ 
  for (int j = 0; j < height; j+=ellipseSize){ 
    fill(colorList[int(random(5))]);
    ellipse((ellipseSize/2)+i,(ellipseSize/2)+j,ellipseSize,ellipseSize);
  }
}
```
**init:** - "Computer, start the variable ______ at the value ______"
**test:** "...keep running the statements until ______"
**update** - "...and each time, increment/decrement ______ by ______."

To test the sketch, change the size of the ellipse and the size of the canvas.
Isn’t that nicer than specifying and respecifying every coordinate, every time?

## Keyboard and Mouse Inputs
So let’s talk this week about conditional statements that will help give more structure to our sketches. Let’s say on keyPressed() we want to draw 20 ellipses to the screen.

```processing
color[] colorList = new color[5]; 

void setup(){
  size(900,900);
  background(255);
  noStroke();
  colorMode(HSB,360,100,100);
  colorList[0] = color(199,100,90);
  colorList[1] = color(186,58,90);
  colorList[2] = color(50,90,100);
  colorList[3] = color(322,34,100);
  colorList[4] = color(13,24,100);
}

void draw(){
}

void keyPressed(){
  for(int i =0; i < 20; i++){
    fill(colorList[int(random(5))]);
    ellipse(random(width),random(height), 10,10);
  }
}
```

This should be fairly familiar to you. Now let’s say we want to define what happens when the ‘m’ key is pressed. The first thing we’re going to need is a conditional statement known as an if statement.

## If/Else statement
So some of you may have already ventured into the land of if statements but if you haven’t don’t worry - it’s fairly straight forward. We want the computer to do the following:

On key press, run the function keyPressed() and…
...if the key is ‘m’(for magic), execute the following statements
...else, execute the following statements instead.

This is represented like this:
```processing
void keyPressed(){
  if (key == 'm'){
    //Execute these statements
  } else {
    //Execute these statements
  } 
}
```

You can even chain it like this:
```processing
void keyPressed(){
  if (key == 'm'){
    //Execute these statements
  } else if (key == ‘1’){
    //Execute these statements
  } else {
    //Execute these statements
  }
}
```
**Exercise: Can you make this work in the previous code?**
We only want the key ‘m’ to trigger the drawing of the 20 colourful confetti.

```processing
color[] colorList = new color[5]; 

void setup(){
  size(900,900);
  background(255);
  noStroke();
  colorMode(HSB,360,100,100);
  colorList[0] = color(199,100,90);
  colorList[1] = color(186,58,90);
  colorList[2] = color(50,90,100);
  colorList[3] = color(322,34,100);
  colorList[4] = color(13,24,100);
}

void draw(){
}

void keyPressed(){
  if(key == 'm'){
    for(int i =0; i < 20; i++){
      fill(colorList[int(random(5))]);
      ellipse(random(width),random(height), 10,10);
    }
  }
}
```

## Relational operators
Another thing you may have noticed is that there are TWO equal signs.
```processing
if (key == 'm')
```

This is what’s known as a Relational Operator; an operator that checks if items are related to one another. In this case, we’re asking the computer to check the “equality” of key and the letter ‘m’ . Some other Relational Operators you might recognise are:
**!=** inequality
**<** less than
**<=** less than or equal to
**>** greater than
**>=** greater than or equal to

**Exercise: Change the equality operator to the inequality operator in your sketch.**
Now change it back to equality.

## Logical Operators
So given we’re checking for == (equality), the key m is not the same as the key M to the computer. Let’s first see what it’s doing. Run your sketch again and type ‘m’ and then ‘M’.  

If we want to trigger our colours on m or M, or any other key in fact, then we will need a logical operator. Instead of just checking for m, we want to check for m OR M.

We could do the following:
```processing
void keyPressed(){
  if (key == 'm'){
    //Execute these statements
  } else if (key == ‘M’){
    //Execute these statements
  } else {
    //Execute these statements
  }
}
```
However, if we want ‘m’ and ‘M’ to execute the same statements, it’s a waste of breath for the computer. So, we bring in a logical operator...

**||** or
```processing
//if the key is m OR M:
if (key == 'm' || key == 'M'){
  //Execute these statements
} 
```

**!** not
```processing
//if the key is NOT m or NOT M:
if (!(key == 'm') || !(key == 'M')){
  //Execute these statements
} 
```

**&&** and
```processing
//If the key is m AND the canvas width is 900px
if (key == 'm' && width == 900){
  //Execute these statements
} 
```

**Exercise:Try these different variations in your sketch.**
Can you get ‘m’ OR ‘M’ to draw confetti and ‘s’ OR ‘S’ to change the size of the confetti?

### Special Keys
The last missing piece of the puzzle is for situations where you want to use keys that aren’t letters, numbers or punctuation. We have to be a little careful here as depending on where you run the code also depends on what else the system might execute with that “special” key.

Some keys require key and some require keyCode checks:
value | variable check |
--- | --- |
a-z, A-Z | key |
" " (space) | key |
ENTER | keyCode |
BACKSPACE | keyCode |
ESC | keyCode |
UP, DOWN, LEFT, RIGHT | keyCode |

So for the ‘special’ keys that need keyCode. We’d do the following:
```processing
void keyPressed(){
  background(colorList[int(random(5))]);
  if (keyCode == UP){
    //execute these statements
  } else {
    //execute these statements
  }
}
```

## Let’s look at some practical uses.
### Multiple keys for different uses
```processing
int ellipseSize = 2;

void setup(){
  size(900,900);
  background(255);
  noStroke();
}

void draw(){
  fill(0);
  ellipse(random(width),random(height), ellipseSize,ellipseSize);
}

void keyPressed(){
  if (key == ' '){
     for (int i = 0; i < 100; i++){
       ellipse(random(width),random(height), ellipseSize,ellipseSize);
     }
   } else if (keyCode == UP){ 
     ellipseSize++;
   } else if (key == 'r' || key == 'R'){
     ellipseSize = 2;
   }
}
```

**Exercise: Can you describe what’s happening here?**
Add a new command: If a user presses to DOWN key, decrease the size of the ellipse.

### Using arrow keys to increment and decrement color values
```processing
color currentColor;
int h = 359;
int t = 100;
boolean countUp = false;

void setup(){
  size(900,900);
  background(0);
  colorMode(HSB,360,100,100,100);
  noStroke();
}

void draw(){
  currentColor = color(h,75,90,t);
  fill(currentColor);
  ellipse(random(width),random(height), 10,10); 
}

void keyPressed(){
  if (keyCode == UP && h >= -1 && h <= 359){
    h++;
  } else if (keyCode == DOWN && h >= 0 && h <= 360){
    h--;
  }  
  
  if (keyCode == RIGHT && t >= -1 && t <= 99){
    t++;
  } else if (keyCode == LEFT && t >= 0 && t <= 100){
    t--;
  }  
}
```

## Type a pattern
Can you work out what’s going on here?







