# Week 8 + 9

UPDATE: The way that we were going to train our own machine learning model was via the recommended Google Colaboratory. Turns out a new update to the service means that we don't have enough provided RAM to do this :( - and the paid upgrade is only available in the US currently so I can't even train it on your behalf. 

HOWEVER, this is only one of three exercises we're going to look at over the next two weeks.

## Prep for Studio
If you want to try making your own Kusama inspired Lens with me - download Lens Studio, but note the Mac version is 1.3GB:
[Download here - 1.3GB](https://lensstudio.snapchat.com/download/)

We will be using Version 3.1. If you're having issues with download limits or speed - you can always come back to this when you've downloaded it successfully. The whole class will be available as a recording so you can watch along now and code along later.

Whilst that is hopefully downloading...

Today we're going to very very very small tasters into the world of Machine Learning. This can seem intimidating and IS an entire field of mountains to climb however, we're going to skim the surface together, make some neat stuff and hopefully get a taste of Machine Learning from a creative aspect.

For context, Machine Learning is definitely a component of my current practice as a designer however I work in collaboration with developers to deliver projects - and lucky for me we have a Machine Learning expert in our team of three. I am however super passionate about exploring this field creatively so when I get time, I like to make little experiments or follow along examples to explore what's possible. I prefer making it rather than just reading about it!

If Machine Learning is something you're interested in or after these two weeks, become interested in exploring - then I will also provide some extension links for you to explore in your own time.

If you only learn ONE thing in this studio, I want it to be this: With a little design and code, you can make almost anything.

Time and time again, I cannot even tell you how often these demos that seem like a once off and a spur of the moment thought - evolve into commissioned projects because I built that thing once, or I tried that library once, or I had a funny idea... Don't let "a real project" get in the way of just creating things and giving yourself room to explore and extend your craft.

# DISCOURSE: Obsession and Space
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: DEMO 1 Snapchat ML
Now this class comes directly from Lens Studio who have a really great collection of guides and templates to help us make our own Community Lens.

**[View full guide to making a Style Transfer lens here](https://lensstudio.snapchat.com/templates/ml/style-transfer/)**

Because it's not currently possible to get a Colab Pro account to beef up our RAM to teach our own models, here's one I trained earlier, in June, wow things move fast!
- [new_model.onnx](https://drive.google.com/file/d/1nkEYlHqnIGgrmWpcsg6NmpcFUYMTNMxR/view?usp=sharing)

1. Open Lens Studio and go to Templates
2. Under the filter Category, select Machine Learning
3. Open the template called Style Transfer.
4. Drag your pre-trained model "new_model.onnx" into your Resources panel. A settings panel will appear, select Import.
5. Click on "ML Component" in the Objects panel.
6. In the Inspector, look for the field "Model". Click on the input field and select your uploaded model "new_model". Select Ok.
7. In your Preview panel, you can select different sample test images/videos or even a live webcam view. Have a look at what the different enrivornments look like!
8. Now we've made our first lens!

# STUDIO: DEMO 2 Transfer Learning - Kusama or Turrell?
Because I really really really want to give you the possibility of personalising a model yourself - I've ad-libbed this next section with the help of Daniel Shiffman.

Let's try it out together! Now what are we doing?
We're going to train our model to "learn" the difference between a Turrell and a Kusama 😱 with Teachable Machine, ml5 and p5. 

What is that you say? You want to choose your own artists?! Yes!! Please do! Or if you're not art-inclined, you can choose any two objects or animals or "things" you can Google search! You can have more than two recognised things, but let's start here first.

## Training our own model

The first thing we need to do is go here and select "Image Project":
https://teachablemachine.withgoogle.com/train

1. Rename "Class 1" to be the title of your first "thing".
2. Rename "Class 2" to be the title of your second "thing". 
3. Upload relevant images for each "thing" and hit "Train Model".
4. Once finished training, hit "Export" and the deafult tab should be "Tensorflow.js".
5. Low and behold if you look a little further down there is a "p5.js" tab with a code snippet you can copy! Let's paste this into an empty project.

## Testing with our webcam
First, make sure your web server is running. If you don't know how - revisit the Week 5 studio class.

Now arrange your code as such:
- index.html - I merged it with our empty template for you:
```html
<!DOCTYPE html>
<html lang="">

  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Empty Example</title>
    <link rel="stylesheet" href="style.css">
    <script src="/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@latest/dist/ml5.min.js"></script>
    <script src="sketch.js"></script>
  </head>

  <body>
    <div>Teachable Machine Image Model - p5.js and ml5.js</div>
  </body>

</html>
```

- sketch.js
```javascript
// everything inside of this script tag <script type="text/javascript">
  
  // Classifier Variable
  let classifier;
  // Model URL should be your URL
  let imageModelURL = 'https://teachablemachine.withgoogle.com/models/m_BMR3hu0/';
  
  // Video
  let video;
  let flippedVideo;
  // To store the classification
  let label = "";

  // Load the model first
  function preload() {
    classifier = ml5.imageClassifier(imageModelURL + 'model.json');
  }

  function setup() {
    createCanvas(320, 260);
    // Create the video
    video = createCapture(VIDEO);
    video.size(320, 240);
    video.hide();

    flippedVideo = ml5.flipImage(video);
    // Start classifying
    classifyVideo();
  }

  function draw() {
    background(0);
    // Draw the video
    image(flippedVideo, 0, 0);

    // Draw the label
    fill(255);
    textSize(16);
    textAlign(CENTER);
    text(label, width / 2, height - 4);
  }

  // Get a prediction for the current video frame
  function classifyVideo() {
    flippedVideo = ml5.flipImage(video)
    classifier.classify(flippedVideo, gotResult);
    flippedVideo.remove();

  }

  // When we get a result
  function gotResult(error, results) {
    // If there is an error
    if (error) {
      console.error(error);
      return;
    }
    // The results are in an array ordered by confidence.
    // console.log(results[0]);
    label = results[0].label;
    // Classifiy again!
    classifyVideo();
  }
```

Now let's find even more images of our "things", to test this with. Open all those images up on your computer so you have a bunch of images visible.

If everything has gone to plan, if you point your webcam at the images, we should be able to detect whether it is the first "thing" or second "thing" via the label on the bottom!

## Testing with an image
Now in Shiffman's video, he extends this to emojis(which are simply just text) - but we are going to extend into images. So let's say we don't have a webcam we can simply point at other images... Let's upload an image and classify that!

1. Move those images into your data folder.
2. And now instead of classifying a still image from our video, we're going to classify an image from our data folder.

```javascript
// Teachable Machine(edited)
// The Coding Train / Daniel Shiffman
// https://thecodingtrain.com/TeachableMachine/1-teachable-machine.html
// https://editor.p5js.org/codingtrain/sketches/PoZXqbu4v

// The image
let img;

// For displaying the label
let label = "waiting...";
// The classifier
let classifier;
let modelURL = 'https://teachablemachine.withgoogle.com/models/m_BMR3hu0/';


// STEP 1: Load the model!
function preload() {
  classifier = ml5.imageClassifier(modelURL + 'model.json');
  img = loadImage("data/style_image.png");
}

function setup() {
  createCanvas(640, 520);
  // STEP 2: Start classifying
  classifyImage();
}

//Function to classify the image
function classifyImage() {
  classifier.classify(img, gotResults);
}

function draw() {
  background(0);

  // Draw the image
  image(img,0,0,600,400);

  // STEP 4: Draw the label
  textSize(32);
  textAlign(CENTER, CENTER);
  fill(255);
  text(label, width / 2, height - 16);
}

// STEP 3: Get the classification!
function gotResults(error, results) {
  // Something went wrong!
  if (error) {
    console.error(error);
    return;
  }
  // Store the label and classify again!
  label = results[0].label;
  classifyImage();
}
```

And here we have it! Our own artwork detector or THING detector!

# STUDIO: DEMO 3 Illustrations with PoseNet

This one is mainly illustration work so you will need something like Adobe Illustrator or I can recommend that Sketch also works. If this isn't possible for you - never fear you can play with the live demos of a girl or boy with a webcam or an image! [Live demos](https://pose-animator-demo.firebaseapp.com/)

Okay we're not even coding for this one - shock horror!

**[Learn about Pose Animator here](https://blog.tensorflow.org/2020/05/pose-animator-open-source-tool-to-bring-svg-characters-to-life.html?utm_source=newsletter&utm_medium=email&utm_campaign=TensorFlow2020Q3newsletter&utm_term=pose_animator&max-results=20)**

## Custom illustrations

**[Learn to use custom illustrations](https://github.com/yemount/pose-animator#animate-your-own-design)**

(This is taken from the above tutorial - https://github.com/yemount/pose-animator#animate-your-own-design)
1. Animate your own design
2. Download the [sample skeleton SVG here](https://github.com/yemount/pose-animator/blob/master/resources/samples/skeleton.svg).
3. Create a new file in your vector graphics editor of choice. Copy the group named ‘skeleton’ from the above file into your working file. Note: Do not add, remove or rename the joints (circles) in this group. Pose Animator relies on these named paths to read the skeleton’s initial position. Missing joints will cause errors. However you can move the joints around to embed them into your illustration. See step 4.
4. Create a new group and name it ‘illustration’, next to the ‘skeleton’ group. This is the group where you can put all the paths for your illustration.
5. Flatten all subgroups so that ‘illustration’ only contains path elements. Composite paths are not supported at the moment. The working file structure should look like this:
```
    [Layer 1]
    |---- skeleton
    |---- illustration
          |---- path 1
          |---- path 2
          |---- path 3
```
6.Embed the sample skeleton in ‘skeleton’ group into your illustration by moving the joints around.
7. Export the file as an SVG file.
8. Open [Pose Animator camera demo](https://pose-animator-demo.firebaseapp.com/camera.html). Once everything loads, drop your SVG file into the browser tab. You should be able to see it come to life :D

# Week 08 + 09: Open Submission
What are YOU inspired to create?
1. Interested in creating another Snapchat Lens'? Use another template and guide and customise it to be your own!
2. Interested in diving deeper into Machine Learning? Watch a video on ml5 or Runway and explore an alternative way to use machine learning. Create something.
3. Interested in illustration or animation? What could you film your own character doing? Where could you extend and play with this demo?
4. Not really vibing with Machine Learning? Be free! Pick any Coding Train/p5/Javascript tutorial and extend it. Make sure to reference it in your code.