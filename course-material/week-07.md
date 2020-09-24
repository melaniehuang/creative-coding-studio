# Week 7
Exploration adventure time! The next couple of weeks, alongside creating your beautiful visualisations - we're going to explore some random creative coding fields of thought that will hopefully broaden your horizons on the potential we have with design and code for creativity.

# DISCOURSE: Code as performance
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: Live Coding!
We're going to step away from p5 this week and look at Livecodelab.net. Via Livecodelab we're able to code visuals and sound in our browser.

There is a super great step through guide here:
https://livecodelab.net/play/index.html#bookmark=introTutorial

And you'll notice the syntax is very similar to what we're doing in p5. If you are feeling fairly comfortable with p5 - use this cheat sheet and start making! 

Primitives
```
line
line 1.25

rect
rect 0.2, 0.5
rect 0.5

box
box 0.5
box 0.4,0.2,1

ball
ball 2
ball 1,1,2

peg
peg 2.25
peg 2,1,0.5
```

To colour our primitives abd vbackground:
```
fill 255,255,255
noFill
stroke 255,255,255
noStroke
background 0,0,255

//or maybe we use lights on our shapes
ambientLight 255, 255, 0
```

To animate and move and scale our primitives:
```
move 0,1,0
scale 1,0,1
rotate frame/100
rotate time/2
rotate pulse
rotate wave

pushMatrix
popMatrix
```

Repetition
```
//do it...
10 times
100 times
200 times
```

Conditionals
```
if frame%20==0
  peg 1
else if frame % 10==0
  rotate frame/10
  peg 0.5
else 
  rect 0.5
```

Gradients
```
simpleGradient (color 252,82,120),(color 106,130,251), (color 50,130,251)
```

Animation styles
```
animationStyle motionBlur
animationStyle paintOver
```

And for the finale!
Sound!
https://livecodelab.net/play/index.html#bookmark=trythemall
```
bpm 72
// leave this one as base
play 'tranceKick'  ,'-x-x ---x'
play "beep" + int(random 8) ,'x'
play "lowFlash", '-x-x xxx-'
play "toc" + int(random 8) ,'x'
play "tap" + int(random 4) ,'x-x-'
```

Now if you want to dive deeper - here are the keys to the some of the system ie. the reference docs:
https://github.com/davidedc/livecodelab/blob/master/docs/reference.md

And for inspiration - have a look under Demos, here are some of my faves:
https://livecodelab.net/play/index.html#bookmark=rose
https://livecodelab.net/play/index.html#bookmark=lava
https://livecodelab.net/play/index.html#bookmark=movingBlocks
https://livecodelab.net/play/index.html#bookmark=zfight

And here's one I prepared earlier.
```
bpm 50
play "tic", '-x-x'
play "glass"  ,'x--- x---'
play "cosmos", 'x--x'
play 'tranceKick'  ,'-x-- ---x x--- --xx'
play 'tense', '---x ---- ---x --xx'
play 'lowFlash', '---x ---- ---- ----'

rotate time*2
simpleGradient (color 252,82,120),(color 106,130,251), (color 50,130,251)
animationStyle motionBlur
noStroke()

20 times with i
	scale time%2
	move noise(20)
	if frame%30==0
		fill 252,82,120
		ball 0.5
	else if frame%5==0
		rotate -time*2
		fill 50,130,251
		peg 0.5
	else
		fill 106,130,251
		box 10,20,2
```

Now if making music has got you excited, you can also choose to look into Sonic Pi which will give you a lot more options for the sound component.
[Sonic Pi](https://sonic-pi.net/)


## Week 07: Live 3D Visuals
Sound, Visuals, Sound AND Visuals - it's up to you. Your task this week is to build 1 x 20 second demo on livecodelab.net or p5/Sonic Pi/p5.sound. 
In livecodelab.net there's nowhere to save your code, so I suggest when you get something you like - save it somewhere like a text file like I've done here ^ or even on openProcessing as "comments". 

When you're happy with it - record your sound and/or screen and upload that video to openProcessing. Don't forget to include your code, commented out up the top.

If you're unsure how to do this, revisit "Let's see how this works." in [Week 2](https://github.com/melaniehuang/creative-coding-studio/blob/master/course-material/week-02.md).

