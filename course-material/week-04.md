# Week 4: Images and text

## Uploading an image

We will learn more about the fabulous ways of manipulating an image in Week 7/8/9 but for now we will learn simply how to upload an image.

Last week we learnt about some common datatypes like **String** and **int**. In order to upload an image, we will use an image datatype called **PImage**. Note the capital “P” and “I” - computers don’t care about “what you meant to type” - they’re black and white and therefore, extremely case-sensitive.

## Local image
Make a folder called “data” where your Processing sketch is stored. Place your image file inside here. Processing can display .gif, .jpg, .tga, and .png images.

![](image url)

```processing
//Declare your variable
PImage artwork;

void setup(){
  size(300,300);
  //Load ‘artwork’ from file path
  artwork = loadImage("data/calder.jpg");
}

void draw(){
  //Draw ‘artwork’ to canvas + optionally give a width and height
  image(artwork,0,50,250,200);
}
```


