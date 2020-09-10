# Week 5

# WE MADE A ZINE!
Well done everyone - I thoroughly enjoyed reading about your inspirations and process for Task 1 and together we've created this collaborative zine for 2020.

[Download to print me here!](https://drive.google.com/file/d/1pLwcrPmzh-zDMFQmUikkXoDZf8lJA66r/view?usp=sharing)

It is formatted for an A5 double sided booklet :) I'm glad we have this momento of where we all started this semester. 

So now we've had a little bit of a break, it's time to start thinking about Task 2 & 3 and what we're going to make.

To recap the [assignment](https://github.com/melaniehuang/creative-coding-studio/blob/master/course-files/2020-assessment-criteria.pdf)...

```markdown
Create an interactive sketch with code. The only requirements are as follows:
- You are required to have an input that affects the visuals or sounds of your sketch, ie. no static sketches
- You are required to explore and connect data and visuals in a meaningful way
- You are required to research and explore artists and designers, whether past or present, to inspire and push forward your ideas
```

To kick us off, we're going to talk this week about storytelling - and storytelling through the medium of design and code. 
Then in our studio portion, we'll learn how to bring data into the visuals we want to create.


# DISCOURSE: Storytelling
Every best effort will be made to record and upload these in a timely matter however due to technology issues this may not always be possible. This will be a record of this portion of the class for later reference but please do not rely on these as your only source. It's best to show up to class.
- [Zoom recording will be uploaded here](https://drive.google.com/drive/folders/1x1sPNrUC-WDVlskrmzzX-wktnjgXGy2i?usp=sharing)
- [Slides available here](https://drive.google.com/drive/folders/1Tt7AbCijBW1Rt7hgZ5EJ3xZjVOBFKdjX?usp=sharing)

# STUDIO: Libraries and Data

## What is data?
So firstly, what do we mean by "data"? Let's think about the examples we just saw:
- political data such as the positive/negative percentages of news headlines
- community opinion data on an idea such as "An innocent person in prison or 10 guilty people on the streets?"
- the data from a performance, maybe you want to track your dance moves on camera?
- personal stories as data such as Gabori's works about her experiences, perhaps you want to collect your own observations about your own life?
- maybe you want to find an existing data set and tell a story from a different angle like I did with the Coronavirus dataset?
- maybe you want to create your own dataset? How many hours did you spend in front of a screen? How many people did you talk with in a day? Nicolas Felton does a visual [annual report](http://feltron.com/FAR11.html) of his data each year.

## Finding data
There are so many places to look for inspiration and data:
- [Information is Beautiful](https://informationisbeautiful.net/)
- [Australian Bureau of Statistics](https://www.abs.gov.au/browse?opendocument&ref=topBar)
- [Open Weather API](https://openweathermap.org/api)
- [Well-formatted COVID data](https://github.com/pomber/covid19)
- [City of Melbourne Data](https://data.melbourne.vic.gov.au/)
- [Email a tree, Urban Tree data](http://melbourneurbanforestvisual.com.au/)
- [New York Times 2019 in Visual Stories and Graphics](https://www.nytimes.com/interactive/2018/us/2018-year-in-graphics.html)
- [Fathom](https://fathom.info/projects/)
- [Ri Liu](https://ri.id.au/)
- [Kaggle](https://www.kaggle.com/datasets)
- [Periscopic](https://periscopic.com/)
- [Domestic Data Streamers](https://domesticstreamers.com/)
- [Dear Data](http://www.dear-data.com/theproject)
- [Cool Infographics](https://coolinfographics.com/)
- [Marvel Cinematic Universe](https://graphics.straitstimes.com/STI/STIMEDIA/Interactives/2018/04/marvel-cinematic-universe-whos-who-interactive/index.html)

Or you can make your own, you just need a trusty spreadsheet!

## Using data
So  today we're going to look at how to use a simple dataset. 
The most common data files you'll come across on the web are:
- [JSON files](https://p5js.org/reference/#/p5/loadJSON)
- [CSV files](https://p5js.org/reference/#/p5/loadTable)
- [XML files](https://p5js.org/reference/#/p5/loadXML) 
- [plain text files](https://p5js.org/reference/#/p5/loadStrings)

p5.js has different but similar ways of handling each of these particular files and if you're interested in visualisations - I recommend that you start to explore more file types as you will need them for particular datasets.

Our friend, Daniel Shiffman does some great videos on this that I will link here(there's a whole playlist):
- [10.1: Introduction to Data and APIs in JavaScript - p5.js Tutorial](https://www.youtube.com/watch?v=rJaXOFfwGVw)

Today, we're going to run through how to get data from a simple CSV file.

### Accessing files
Please make sure you're using Chrome for this tutorial. 

One thing you will encounter with JavaScript is that it does not have direct access to local files due to security and privacy. This is different to what you may be used to when you were using html and css. If you used html in the past and referenced something locally on your computer, let's say:

```html
<img src="data/chicken.png"></img>
```

It would work. But now if you did something like this in your JavaScript file:

```javascript
let imgChicken = loadImage("data/chicken.png");
```

You would get an error in your console(Option+CMD+J) saying something like "Fetch API cannot load file. URL scheme must be "http" or "https" for CORS request."

Once we push our files onto the web, this will no longer be an issue but while we're experimenting locally on our computers, we will need to create a simple environment to "mock" our sketch locally. There are so many ways to do this, but the easiest I've found is to add an extension to Chrome called [Web Server for Chrome](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb?hl=en).

1. Hit the "Add to Chrome" button.
2. Confirm that you want to "Add Web Server for Chrome" by hitting "Add app".
3. A new tab will open with a yellow icon and the name "Web Server". Click on this.
4. A new window will open with a purple header called "Web Server for Chrome". Select "Choose folder" and navigate to the directory that contains your "index.html" page.
5. The folder title should now appear next to the button. "Current:" + your folder name
6. Under the heading "Web Server URL(s)", there should be a blue underlined link beginning with "http://...". Click on this to open your "index.html" page in Chrome.
7. Now we're ready to rumble!
8. If you come back to this and need to start your server again. Go to this [URL](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb) and select "Launch app". Or type into Chrome "chrome://apps/" and there should be a shortcut there.

### CSV data
So first thing's first: [Download this CSV file](https://drive.google.com/file/d/1RaiHSx_Awp0QEkc1V9uIsLN7EV0a48uv/view?usp=sharing).

If you open this CSV file up in your text editor, you'll be able to see a bunch of data relating to the Top 24 Parmas in Melbourne, as ranked by [Parma Daze](https://www.parmadaze.com/) - and before you say it... you're welcome 🐔

1. [Download parma data](https://drive.google.com/file/d/1RaiHSx_Awp0QEkc1V9uIsLN7EV0a48uv/view?usp=sharing).
2. Using our ["my-empty-sketch" template](https://drive.google.com/file/d/1vtYeOFjw6v_PfgIaUhCQf71ly9JIdjtl/view?usp=sharing), move the *.csv file into your folder called data. 
3. Make sure that your server extension is running and let's load the table of data via [loadTable()](https://p5js.org/reference/#/p5/loadTable).

```javascript
let table;

function preload(){
  // loadTable(filename, [extension], [header], [callback], [errorCallback])
  // We're telling p5 that the data is located at 'data/parmadaze-top24.csv', the file is a csv file and it contains a header row which is the first row of the file: rank,pub,address,coordinates,latitude,longitude,date,score containing all the headings.
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
}
```

So if we're getting a green screen and there's no errors in our console - we're looking good.

If you're stuck with a white screen with the word Loading... displayed, then make sure you have your Web Server extension running and your file is named correctly and in the right location.

Let's look at this more closely - what is [loadTable()](https://p5js.org/reference/#/p5/loadTable) doing? The loadTable() function is reading in the contents of our file and storing it as a p5.Table object so that it understands that the data of the file is formatted in predictable ways with rows, columns and optionally a "header" labelling our content types.

After our data file is loaded, we can access it with the following functions:
- [getColumn('columnName')](https://p5js.org/reference/#/p5.Table/getColumn)
- [getRow(index)](https://p5js.org/reference/#/p5.Table/getRow)
- [getString(row,column)](https://p5js.org/reference/#/p5.Table/getString)
- [getNum(row,column)](https://p5js.org/reference/#/p5.Table/getNum)


### getColumn()
Let's get all the data from the column called 'pub'. This will give us a list of the all the pubs' names.
```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  print(table.getColumn('pub'));
}

function draw() {
  background(0,255,0);
}
```

Now if we open up our console(Option+CMD+J) in Chrome, we should get the following:
```
Array(23)
```
and if you click on it to expand the array, you should see:
```
Array(23)
    0: "The Birmingham Hotel"
    1: "The Wandi Pub"
    2: "The Park Hotel"
    3: "The Cheeky Pint"
    4: "The Imperial Hotel"
    5: "The Wolf & I"
    6: "The Town Hall Hotel"
    7: "Easey's @ The Bottom End"
    8: "Hardimans Hotel"
    9: "The Duke"
    10: "The Portland Hotel & James Squire Brewhouse"
    11: "The Exchange Hotel"
    12: "The Workers Club"
    13: "The Stone Hotel"
    14: "The Local Taphouse"
    15: "The Royston Hotel"
    16: "Robert Burns Hotel"
    17: "The Lord Newry Hotel"
    18: "The Cricketers Arms"
    19: "The Napier Hotel"
    20: "College Lawn Hotel"
    21: "The Railway Club Hotel"
    22: "The Notting Hill Hotel"
```

### getRow()

Or maybe we want to access an entire row? Let's say we know that the CSV is ordered by rank - so we just want to see all the details for the highest ranked parma establishment. 

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  print(table.getRow(0));
}

function draw() {
  background(0,255,0);
}
```

Now if we open up our console(Option+CMD+J) in Chrome, we should get the following:
```
n.default.TableRow {arr: Array(8), obj: {…}, table: n.d…t.Table}
```
...and if you click on it to expand the "obj", you should see:
```
n.default.TableRow {arr: Array(8), obj: {…}, table: n.d…t.Table}
    obj:
      address: "333 Smith St, Fitzroy"
      coordinates: "-37.7991046,144.9818822"
      date: "14.1.16"
      latitude: "-37.7991046"
      longitude: "144.9818822"
      pub: "The Birmingham Hotel"
      rank: "1"
      score: "9.1"
```

### getNum() and getString()
So now let's get the "score" of the No. 1 ranked pub parma and use that data.

First we get the data and print it in the console to make sure it's the piece of data we were expecting.

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  let score = table.getNum(0,'score');
  print(score);
}
```

Great. 9.1 should be printing over and over in your console.
Let's try and get the address?

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  let address = table.getNum(0,'address');
  print(address);
}
```

Now what is printing out?
```javascript
333
```
333?! Why isn't it printing out the full address? 
So if we look back at the code:
```javascript
let address = table.getNum(0,'address');
```

We've asked the computer to get a Number. So it tried...and got a Number 🤦‍

Remember we spoke about data types - String, Number, Boolean etc? Well, CSV files are just a bunch of values separated by commas assumed to be String values.

So let's revisit our code again and instead - now that we know that addresses are Strings not Numbers - getString():

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  let address = table.getString(0,'address');
  print(address);
}
```

Woohoo! Now we should be seeing in our console(again, Option+CMD+J)- we will see the address that we were originally expecting. It's again an example of needing to check what we assume to be "true". One of the annoying things about JavaScript is that sometimes it tries it's best to reinterpret what we may have "meant" so it doesn't error at all - it just assumes. 

So we can now get String and Number values - let's use it to influence our ellipse size:
```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  //scores are currently out of 10, let's make the score out of 100
  let score = table.getNum(0,'score')*10;
  ellipse(windowWidth/2, windowHeight/2, score, score);
  text(table.getString(0,'address'),windowWidth/2, windowHeight/2);
} 
```

And now let's get each pub's score and address... can you guess how we can repeat through each row and get out the score?

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  for (let i = 0; i < table.getRowCount(); i++){
    let score = table.getNum(i,'score')*10;
    ellipse(50+i*50, 50, score, score);
    text(table.getString(i,'address'),50+i*50, 150+(i*30));
  }
} 
```

And let's add a line to join the ellipse to the address.

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  for (let i = 0; i < table.getRowCount(); i++){
    let score = table.getNum(i,'score')*10;
    ellipse(50+i*50, 50, score, score);
    text(table.getString(i,'address'),50+i*50, 150+(i*30));
    line(50+i*50, 50,50+i*50,150+(i*30));
  }
} 
```

So GREAT! Now we have data coming through and ways to access them. It's looking a bit bleh and there's not enough difference between the scores to see it in any meaningful way. Let's look at the data more closely, by looking at the "header" row, to see what else we can use:
```
Our header row contains the following column names:
rank
pub
address
coordinates
latitude
longitude
date
score
```

So perhaps instead of just a static x,y position of (50+i*50,50), we want the ellipse to be where it is located on a real map. So let's grab out the longitude and latitude.
```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  for (let i = 0; i < table.getRowCount(); i++){
    let score = table.getNum(i,'score')*10;
    ellipse(table.getNum(i,'longitude'), table.getNum(i,'latitude'), score, score);
  }
} 
```

Hmmmm, that's really no good at all. Can you see a little cluster of ellipses in the top left? Let's take a look at the actual data. What are the values of these longitudes and latitudes between?

The first pub "The Birmingham Hotel" is located at (-37.7991046,144.9818822). And the others also seem fairly similar. We need a way to transform these coordinates so it sits nicely over the entire width and height of the canvas. 

Introducing [map()](https://p5js.org/reference/#/p5/map):
```javascript
map(value, start1, stop1, start2, stop2);
//value = Number: the incoming value to be converted
//start1 = Number: lower bound of the value's current range
//stop1 = Number: upper bound of the value's current range
//start2 = Number: lower bound of the value's target range
//stop2 = Number: upper bound of the value's target range
```

So if we wanted to map our value 'longitude' and 'latitude' values, we need to work out what the upper and lower bounds of our values are. I've prepared this earlier by looking at Google's longitude and latitude of the Melbourne area:
```javascript
//longitude of area: (144.8, 145.4)
//latitude of area: (-37.7, -38)
```

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(0,255,0);
  for (let i = 0; i < table.getRowCount(); i++){
    let score = table.getNum(i,'score')*10;
    let mappedLongitude = map(table.getNum(i,'longitude'),144.8,145.4,0,windowWidth);
	  let mappedLatitude = map(table.getNum(i,'latitude'),-37.7,-38,0,windowHeight);
    ellipse(mappedLongitude, mappedLatitude, score, score);   
  }
} 
```

And now instead of associating the score to the size, let's use colour instead.
Let's break it into 6 different colours ranging from red(HOT CHICKEN PARMA ALERT-DROP EVERYTHING AND GO GET ONE) to a yellow gold(a significant chicken parma - worth a visit) colour.
```javascript
<8.0: rgb(253,255,179,50)
8-8.25: rgb(255,238,153,80)
8.25-8.5: rgb(255,217,153,80)
8.5-8.75: rgb(255,191,128,100)
8.75-9: rgb(255,158,102,100)
>9.0: rgb(255,123,75,150)
```

To do this, let's use an if/else statement: 
```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  noStroke();
}

function draw() {
  background(255);
  for (let i = 0; i < table.getRowCount(); i++){
    let score = table.getNum(i,'score');
    if (score <= 8.0){
      fill(253,255,179,50);
    } else if (score <= 8.25 && score > 8.0){
      fill(255,238,153,80);
    } else if (score <= 8.5 && score > 8.25){
	    fill(255,217,153,80);
	  } else if (score <= 8.75 && score > 8.5){
      fill(255,191,128,100);
    } else if (score <= 9.00 && score > 8.75){
      fill(255,158,102,100);
    } else if (score > 9.0){
      fill(255,123,75,150);
    }

    let mappedLongitude = map(table.getNum(i,'longitude'),144.8,145.4,0,windowWidth);
	let mappedLatitude = map(table.getNum(i,'latitude'),-37.7,-38,0,windowHeight);
    ellipse(mappedLongitude, mappedLatitude, 60,60);   
  }
} 
```

And because we can, let's print out each pub's name and change the background to something darker:

```javascript
let table;

function preload(){
  table = loadTable('data/parmadaze-top24.csv', 'csv', 'header');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  noStroke();
}

function draw() {
  background(59,42,0);
  for (let i = 0; i < table.getRowCount(); i++){
    let score = table.getNum(i,'score');

    if (score <= 8.0){
      fill(253,255,179,50);
    } else if (score <= 8.25 && score > 8.0){
      fill(255,238,153,80);
    } else if (score <= 8.5 && score > 8.25){
	    fill(255,217,153,80);
	  } else if (score <= 8.75 && score > 8.5){
      fill(255,191,128,100);
    } else if (score <= 9.00 && score > 8.75){
      fill(255,158,102,100);
    } else if (score > 9.0){
      fill(255,123,75,150);
    }

    let mappedLongitude = map(table.getNum(i,'longitude'),144.8,145.4,0,windowWidth);
	  let mappedLatitude = map(table.getNum(i,'latitude'),-37.7,-38,0,windowHeight);
    ellipse(mappedLongitude, mappedLatitude, 50,50);   
    text(table.getString(i,'pub'),mappedLongitude, mappedLatitude);
  }
} 
```

And now we've made our first visualisation!

The next steps on our visualisation journey is to tackle [using APIs](https://www.youtube.com/watch?v=ecT42O6I_WI&list=PLRqwX-V7Uu6a-SQiI4RtIwuOrLJGnel0r&index=5) and [using JSON](https://www.youtube.com/watch?v=_NFkzw6oFtQ&list=PLRqwX-V7Uu6a-SQiI4RtIwuOrLJGnel0r&index=2) which you might encounter depending on what data you're trying to use.

For now, let's just let the whole CSV data visualisation above sink in.

## Week 05: Stories with data
This week is about research! 

Option A: Hunt for a dataset that contains something interesting to you or if you prefer, come up with some ideas for what you'd like to visualise and then find some data to go along with it. You're looking for data that is preferably formatted as CSV, JSON or has an API. If the dataset you found is not a CSV, ping me and I can point you in the right direction to get started and break through that barrier!

Option B: Make your own dataset that tells your story - maybe you start to collect some of your personal stats or you look at the Rotten Tomatoes scores of your favourite comedies. To collect your data, start with an empty spreadsheet in something like Google Sheets/Excel, put your "header" names in the top with data underneath and when you're done - "Export as a CSV". Then put it through a [CSV Linter](https://csvlint.io/) to make sure it's compliant. Now your data is read to use!

Option C: Already started Task 2? Start to think about how you could you incorporate a dataset into your project? Have a look at some static values or colours you are using - could you turn that into something more meaningful? Could your use of random() be less "random" and more intentional?

Your task this week is to find a dataset and to turn that data into visuals. Just like we did today. Of course this doesn't have to be your final sketch - just a start.
- Your data file must have at least 10 rows of data.
- Your sketch must call in that data, in some way, to influence the visuals we are seeing.

You will expand on this dataset in the semester for your final visualisation. Don't worry, you're not completely locked in if you find another dataset that interests you - but we want to start to put this work in practice. 