Midterm Project MD 

For this project I followed the rubric, and also utizlied Chat GPT to help with this assignment. 

Since I used Chat GPT, I wanted to treat the AI as an interactive teacher, instead of just asking it answers, I tried to engage with the ideas, ask questions with clarification, as well as making sure the AI is explaining everything in a step by step basis so I learn. 

I began the project by writing some initial code on my own, based off tour code along from our last session. I shared it and asked "I will attach the rubric and the code i do have already written"

This was the code I had written. 



let myFirstSound;

function preload() {
  soundFormats('wav', 'mp3');  
  myFirstSound = loadSound('Hat 1 .wav', soundLoaded);
}

function setup() {
  createCanvas(400, 200);
  textSize(20);
  textAlign(CENTER, CENTER);
  text("Move your cursor to the 'Preview' section\nPress 'P' to play sound", width / 2, height / 2);
}

function soundLoaded() {
  console.log("Sound successfully loaded!");
}

function keyPressed() {
  console.log("Key pressed:", key);
  if (key.toLowerCase() === 'p') {
    playCustomSound();
  }
}

function playCustomSound() {
  if (myFirstSound.isLoaded()) {
    myFirstSound.play();
    console.log("Sound played.");
  } else {
    console.log("Sound not loaded yet.");
  }
}

let mySecondSound;

function preload() {
  soundFormats('wav', 'mp3');  
  mySecondSound = loadSound('Kick 1 .wav', soundLoaded);
}

function setup() {
  createCanvas(400, 200);
  textSize(20);
  textAlign(CENTER, CENTER);
  text("Move your cursor to the 'Preview' section\nPress 'O' to play sound", width / 2, height / 2);
}

function soundLoaded() {
  console.log("Sound successfully loaded!");
}

function keyPressed() {
  console.log("Key pressed:", key);
  if (key.toLowerCase() === 'o') {
    playCustomSound();
  }
}

function playCustomSound() {
  if (mySecondSound.isLoaded()) {
    mySecondSound.play();
    console.log("Sound played.");
  } else {
    console.log("Sound not loaded yet.");
  }
}

Chat GPT pointed out to me that in JS you cannot have multiple functions with the same name, since the later ones would overwrite the earlier ones.   I learned that I need to combine them all into single function (preload,setup,keypressed)

I was able to get all the sounds loaded in, but I couldn't press the keys I set to sample the sounds.  It was explained to me that some browsers block sound playback until I interact with the actual web page.  I learned to use the mousepressed function to enable sound.  

From there I started getting console errors.  TypeError: Cannot read properties of undefined (reading backround)

I shared the full console log, with the prompt of "now nothing is working, I attached a screenshot as well as the console error for us to troubleshoot"  This helped me learn that p5 JS  functions like background or texr can only run after setup is complete.  We fixed this by adding a flag (canvasready = true) to ensure the canvas was intialized.  This was a big Aha! moment 

From there came some embarassing user error moments.  One of my samples, the kick drum, would repeat multiple times.  My inital thought was that somewhere along this process, I either A. entered the code in wrong, or B. Was prompting the AI wrong.  I asked "The kick sound is still playing like 4 or 5 times when I press O one time Is it because loadCount=3?"  This wasn't the case.  It was user error, due to me not double checking the actual audio file, assuming it was a one shot sample.  

It was suggested by Chat that I could trim the audio sample, but I wanted to learn something new, so I asked if it's possible to write code that will make it so it only plays 1 second of the sample.  This led me to understand how to slice playback using p5's optional.play parameters. 

sound.play(0, 1, 1, 0, 1); // play from 0s for 1 second

From there technically the final code was completed.  I tested it and it worked!!  I was initally going to just finish there, but then I thought what if it had a little bit of UI? I asked chat to write code that I could paste in to give it a more colorful UI, it did this but I also asked if it could explain to me the functions, conditions, and other JS code that it was using to achieve this, so next time I could understand how to execute it.  This led to a breakdown of how draw () creates animation loop how helper functions make reusable visuals, how state variables control color, and how settimeout resets visuals.  I believe i will need more practice with this last UI part, but I just did that end piece for fun! 

At the end I asked for a recap where it explained exactly where i went wrong, what i could have done better and also what i could be doing to reinforce the material.  I was shown my mistakes ie. duplicate function names and space in file names, reminded about the order of loading and setup, debugging techniques like checking console logs, and asking WHY and not just how... 

At the end, I feel like I understood JS a bit more, and I also learned a lot about utizlizing AI to write code.  This stuff is like gibberish to me, and it's amazing that with the help of computers and technology, someone like myself, who is awful with this kind of things, can achieve success.  

Here is the final code used for the midterm project 

let sound1, sound2, sound3;
let loadCount = 0;
let canvasReady = false;
let clickToEnable = false;

// Button visual states
let playingP = false;
let playingO = false;
let playingL = false;

function preload() {
  soundFormats('wav', 'mp3');
  sound1 = loadSound('timbale.wav', onSoundLoad); // 'P'
  sound2 = loadSound('kick.wav', onSoundLoad);    // 'O'
  sound3 = loadSound('hat.wav', onSoundLoad);     // 'L'
}

function setup() {
  createCanvas(400, 200);
  textSize(16);
  textAlign(CENTER, CENTER);
  canvasReady = true;
  background(30);
  text("Loading sounds...", width / 2, height / 2);
}

function onSoundLoad() {
  loadCount++;
  console.log(`Sound ${loadCount} loaded`);

  if (loadCount === 3 && canvasReady) {
    background(30);
    text("Click to enable sound, then press P / O / L", width / 2, height / 2);
  }
}

function mousePressed() {
  if (loadCount === 3) {
    clickToEnable = true;
    background(30);
    text("Press P, O, or L to play sounds", width / 2, height / 2);
  }
}

function keyPressed() {
  if (!clickToEnable) {
    console.log("Click the canvas first to enable sound.");
    return;
  }

  let keyLower = key.toLowerCase();

  if (keyLower === 'p') {
    playingP = true;
    playFullSound(sound1);
    setTimeout(() => (playingP = false), 300);
  } else if (keyLower === 'o') {
    playingO = true;
    playOneSecond(sound2);
    setTimeout(() => (playingO = false), 300);
  } else if (keyLower === 'l') {
    playingL = true;
    playFullSound(sound3);
    setTimeout(() => (playingL = false), 300);
  }
}

function playFullSound(sound) {
  if (sound.isPlaying()) {
    sound.stop();
  }
  if (sound.isLoaded()) {
    sound.play();
    console.log("Full sound played.");
  }
}

function playOneSecond(sound) {
  if (sound.isPlaying()) {
    sound.stop();
  }
  if (sound.isLoaded()) {
    let duration = sound.duration();
    console.log("kick.wav duration:", duration);
    console.log("Playing 1 second from the start.");
    sound.play(0, 1, 1, 0, 1);
  } else {
    console.log("Sound not loaded yet.");
  }
}

// ---------- UI Drawing ----------
function draw() {
  background('#1e1e1e');

  drawButton(width / 4, height / 2, 'P', playingP ? '#00e0ff' : '#444');
  drawButton(width / 2, height / 2, 'O', playingO ? '#ff00aa' : '#444');
  drawButton((width * 3) / 4, height / 2, 'L', playingL ? '#00ff77' : '#444');

  // Title text
  fill(255);
  noStroke();
  textSize(18);
  textAlign(CENTER, TOP);
  text("Click to enable sound. Then press P, O, or L", width / 2, 10);
}

function drawButton(x, y, label, fillColor) {
  fill(fillColor);
  stroke(255);
  strokeWeight(2);
  rectMode(CENTER);
  rect(x, y, 80, 80, 12); // round square

  fill(255);
  noStroke();
  textSize(32);
  textAlign(CENTER, CENTER);
  text(label, x, y);
}

LINK: 🔧 [View/edit the project in the p5.js editor](https://editor.p5js.org/arnoldsallan/full/gaeb9husL)