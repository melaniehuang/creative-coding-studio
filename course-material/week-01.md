# Let's talk assignments

## Brief:
A museum has commissioned you to create a response to one or more artists in their major upcoming exhibition _Masters of Seeing_. The exhibition will feature the work of three individuals - sculptor Alexander Calder, graphic artist MC Escher and conceptual pioneer Sol Lewitt.

The museum is asking for visual, animated content that is inspired by key themes and ideas of either the artists’ life or work to use around the museum through print, digital and/or exhibition design. These visuals **must** be made with code as it is the desire of the curator to present a visual language both as a response to the exhibition but also one which speaks to a modern way of “seeing”.

The museum encourages both playful and experimental exploration of any treatments you see fit and are open to your concepts and personal reflections on the chosen artists’ work.

The project will be broken up into three stages for assessment:
- Task 1: Concept (30%)
- Task 2: Build (40%)
- Task 3: Final presentation (30%)

This studio will also involve a mandatory physical visit to the National Gallery of Victoria to see Alexander Calder’s exhibition in Week 2 where you will start to collect your initial inspirations.

## Task 1: Concept (30%)
Research one or more of the artists’ life and/or work to uncover and construct two clearly defined concepts for your proposed visuals.

**Mandatory items**
- Process journal documenting inspiration and ideas(500 words with accompanying images)
- Two clearly presented concepts in process journal (200 words each with accompanying images/sketches)

**Assessment criteria**

- 3 x Weekly code sketches with references in comments(20pts)
- Documentation of research and inspiration in process journal(40pts)
- 2 x Clearly defined concepts in process journal(40pts)

Due date: Fri 9 Aug 2019, 11pm AEST
Reminder: No assessments will be accepted without a cover sheet

## Task 2: Build (40%)
After a collaborative consultation with your client(slash lecturer), you will be provided with ideas and areas to explore for your deliverables. This may be a single concept, or perhaps a combination of the two for you to explore further. Your task is to expand upon your ideas in Task 1, in order to build the final visuals for the exhibition.

**Mandatory items**
- Process journal documenting inspiration and ideas(500 words with accompanying images)
- Interactive sketch demonstrating proposed final visuals

**Assessment criteria**
6 x weekly code sketches with references in comments(12pts)
Interactive sketch demo(12pts)
Process journal documenting any development or research leading to final sketch(16pts)
Please be sure to include all developments of your interactive sketch as part of this documentation
Check-in: 18 September 2019 (In class)

Due date: 4 October 2019, 11pm AEST
Reminder: No assessments will be accepted without a cover sheet

## Task 3
Present and mock your ideas for the final visuals and how they could be used at the museum for the exhibition
- and -
Prepare a 10-minute presentation on your inspiration, process and final outputs. Use plenty of large images and tell your story. This is not meant to be a stiff or professional presentation, just a chance to share your work amongst peers. Have fun with it!

As an additional part of this assessment, each student will also be required to ask and be asked a question at the end of each presentation. This is an opportunity for the class to discover more about your inspiration and process.

**Mandatory items**
- Accompanying slides and live demo
- 10 minute presentation in front of class
- 1 answer to a question asked by a peer + 1 question for a peer’s presentation
- Final process journal and visuals

**Assessment criteria**
- Presentation (60pts)
- Answer(5pt) and question(5pt)
- Final process journal and visuals (30pts)

Presentation: Wed 16 + 23 Oct, 9:30am-12:30pm (In class)
Due date: 26 October 2019, 11pm AEST

# Week 1: Setup

## Join our Slack
[Join our Slack channel](https://comm2753-cc.slack.com/) using your RMIT email address. This is where you will be able to communicate with me and each other. This is probably the fastest way to get in touch with me, otherwise, send me an email.

## Download and install Processing 
[Download the latest version of Processing here](https://processing.org/download/). We'll be working with a mixture of Processing and p5.js(Javascript) in class but when you're on your laptop/desktop - this is where we will be writing our code. For now, this is fine - but later on in the semester we may want to use the online editor which I've linked below.

## Join the openProcessing class
[Join the openProcessing classroom](https://www.openprocessing.org/class/59891)
You will be supplied with a code to join the classroom in class. Please use an obvious name and your RMIT email when signing up. This is where we will be submitting our weekly tasks and as a result, sharing what we’ve all been making. It can be a little incompatible sometimes - but we'll work through it :)

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
[A Box of Chaos: The Generative Artist's Toolkit by Benjamin Kovach](https://www.youtube.com/watch?v=kZNTozzsNqk&t=1s)
[Code goes in, Art comes out - Tyler Hobbs](https://www.youtube.com/watch?v=LBpqoj2nOQo)

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

Can you describe what is happening in this sketch in plain english?
Change some numbers and it should become fairly obvious :)

You’ll also notice here that I have included these lines: _//This runs once_ and _//This runs on repeat_. This is what’s known as commenting - the characters **//** that precede the comment tell the computer to ignore this line. You will be using comments to add any inspiration or references you may have used for your sketches.

### !! This part is a super important bit !!
You will find a LOT of inspiration online and naturally watch a tonne of tutorials to learn throughout the semester. I dare you to get through the entire semester without watching one of Daniel Shiffman's Coding Train videos. As Lauren McCarthy eloquently said, learning is part of the process. *However* - you **MUST** put your sources in your code commented at the top of your code. It doesn't need to be complex, just something like this so I can tell where their ideas end and yours begin:

```
// Coding Challenge #11: 3D Terrain Generation with Perlin Noise in Processing
// https://www.youtube.com/watch?v=IKB1hWWedMk
```

Try adding your own comments.

An important thing to also realise at this point is that the computer, unlike the English language, can’t assume what you were supposed to say. Therefore, if there’s a character out of place, the code won’t run. 

This:
```
//
```
is not the same as this:
```
\\
```
or this:
```
/ /
```

Check those commas, brackets and semicolons! Don’t worry too much about this, you will naturally get better at checking for these things the more you write code.

## Co-ordinates

To tell the computer where to draw something, you will need to give it an x and y coordinate. You may remember these bad boys from maths class but in Computer Graphics, it’s a little different. 

The top left corner (x,y) is (0,0). The x coordinates increase to the right, the y coordinates INCREASE moving down the canvas.

```
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
```
//rect(x, y, width, height);
rect(0, 0, 200, 200);
```

By default, rect() accepts the x & y position of the rectangle’s top left corner.
Now, let’s add some colour!


## Sequence, colour and fill

So to add a fill to the rectangle, we need to add a line _above_ our rect() function:
```
fill(169,225,250);
```

By default, Processing interprets your numbers as RGB colours - the amount of red, green and blue you want to mix into a single colour. When we write something like:
```
fill(255);
```
the computer is actually interpreting that to be:
```
fill(255,255,255); 
```

**Try the following:**
```
void setup(){
  size(900,900);
  background(248,250,169);
}

void draw(){
  fill(169,225,250);
  rect(400,400,100,100);
}
```

Under **Tools > Colour Selector**, you can choose your own RGB colours. We will delve more into colours and what the numbers all mean later in the semester. For now, just copy and paste the R, G and B values as comma-separated numbers like the example above.

In addition, let’s remove that awful black stroke. By default:
``` 
stroke(0); 
```
is applied to all 2D Primitives. In the setup() function, include the line:
```
noStroke();
```

What if we wanted to add another rectangle? One with a stroke and one without? Have a go.


## Uploading your weekly exercises

1. Go to [openProcessing](https://www.openprocessing.org/) and log in.
2. Navigate to **“Sketches”** and select **“Create a Sketch”**.
3. On the far right panel, make sure your “mode” is set to **“Processing.js”**. This will save you from having to translate your code into Javascript manually(most of the time!).
4. Copy and paste your code from Processing to the light grey box and hit **Save**.
5. Go to “My Feed” and navigate to **“Classes”**.
6. Scroll down to the week that you want to submit for and hit **“Add Sketch”**.
7. Select your newly uploaded sketch and hey presto, we’ve submitted our first weekly exercise :)
8. Make sure that **“Who can see it”** is set to **Anyone** or **Me & My Classes** in addition to **“Hide Source Code”** being set to **Off**.
 
