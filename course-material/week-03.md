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
