# Week 3: Shapes and movement

## Shapes Glorious Shapes
There are SO many different shapes we can create.

With your experience drawing rectangles and ellipses from week 1 - give some of these 2D primitives a whirl! If you get stuck, just punch in random numbers and spot the difference! With very little knowledge of coding, you can still visually discern what the numbers and parameters may stand for.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  //line(x1, y1, x2, y2);
  line(100,100,600,100);
  
  //triangle(x1, y1, x2, y2, x3, y3);
  triangle(300,400,500,200,450,550);
  
  //quad(x1, y1, x2, y2, x3, y3, x4, y4);
  quad(50, 450, 300, 550, 200, 700, 50, 600);
}
```

But let's say we're a little more ambitious and we want to make a big spikey explosion type shape?! Let's draw our own shapes!

The first thing we need to do is type beginShape(); and endShape(); - This tells Processing "Hey Processing, the next few vertexes that I specify, will be vertexes for my shape.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
  beginShape();
    //vertex(x,y);
  endShape();
}
```

Now we add in each x and y value for each vertex of our shape. This can be a strenuous task however it does start to pay off once you can start manipulating those shapes with code.

```processing
void setup(){
  size(900,900);
  background(255);
}

void draw(){
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

Then we've also added the paramater "CLOSE" to indicate that we want a closed shape. So we can make this strobe explosion! Warning: eyes.

```processing
void setup(){
  size(900,900);
  background(255);
  noStroke();
}

void draw(){
  background(random(120,255),0,0);
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
  ellipse(600,620,500,500);
}
```

**Try to create your own unique shape. How can you manipulate it?**
There are also a bunch of different [beginShape()](https://processing.org/reference/beginShape_.html) parameters you can discover like beginShape(TRIANGLE_STRIP);. Perhaps you also want a contour ie. [beginContour()](https://processing.org/reference/PShape_beginContour_.html).

## Joan Miró
A close friend of Alexander Calder was [Joan Miró](https://en.wikipedia.org/wiki/Joan_Mir%C3%B3), a Spanish painter, sculptor, and ceramicist. Though divided by an ocean and World War II, they created continued on remarkably like-minded trajectories. And if you like one, I can guarentee you'll probably like the other ;)

Take a look at [Dog Barking at the Moon(1926)](https://www.joan-miro.net/dog-barking-at-the-moon.jsp). Take a look at how strange yet somewhat familiar the dog looks! Or take a look at [Painting(1933)](https://www.joan-miro.net/painting-1933.jsp) and look at the human figures! Or even deeper still, [Le Fermier et son epouse(The Farmer and his wife)(1936)](https://www.joan-miro.net/le-fermier-et-son-epouse.jsp) with two dancing human bodies and collection of animals.
