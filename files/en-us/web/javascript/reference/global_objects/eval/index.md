
Home  ›  Games  ›  Javascript Game
10 Simple Javascript Game Codes Free
Written By Ahmad Ansori  04 March 2020  1 Comment

Konten [Tutup]
Understanding JavaScript
10 Simple Javascript Game Codes Free
1. Flappy Bird Game Using JavaScript and HTML5
Here is the game code for Flappy Bird
The following tutorial makes a game Flappy Bird
2. Simple Code Snake Game Using Javascript
Here is the game code for Snake
Here is a video tutorial for creating a snake game 
3. Tetris game in JavaScript
Here is the game code for Tetris
Here is a video to make a tetris game
4. Quiz App With JavaScript
Here is the game code for Quiz
Video making quiz game application
6. Suwit Jawa 2.0 Using Javascript
Here is the game code for Suwit Jawa
The following video tutorial for making Javanese Suwit game
7. Code Ping Pong Game Using JavaScript
Here is the game code for Ping Pong
The following is a video tutorial for making ping pong games
8. Code Memory Game JavaScript
Here is the game code for Memory
Next is a video tutorial for creating memory games
Next is a video tutorial for creating memory games
9. Hangman Game using Javascript
Here is the game code for Hangman
Next is a tutorial on making a hangman game
10. Bubble Shooter Using Javascript
Here is the game code for Bubble Shooter
video tutorial on making the Bubble Shooter game
Conclusion
10 Simple Javascript Game Codes Free
10 Simple Javascript Game Codes Free- On this occasion I will share the code to make a simple game with the Javascript programming language. The game code can later be your reference material for making other simple games.

Before you continue do you already know what is javascript programming ?, if you don't know yet, please read the brief summary below.

Understanding JavaScript
JavaScript is one of the most widely used programming languages in the past twenty years. JavaScript programming can be learned quickly and easily, and we can use it for various purposes, for example from increasing the functionality of a site to creating game applications and web-based applications. In addition, there are thousands of themes and JavaScript applications that you can use for free and all of this is thanks to several sites, such as Github.com.

Baca Juga: Tempat Wisata di Nganjuk untuk Mengisi Akhir Pekan

10 Simple Javascript Game Codes Free
The following is a collection of simple javascript games but has very interesting functions and can be a reference material, these games include:

1. Flappy Bird Game Using JavaScript and HTML5
Flappy Bird is a game that uses 2D display. The aim is to direct the flying bird, named "Faby", which moves continuously to the right, between sets of pipes like Mario. If a player touches the pipe, they lose. Faby quickly flaps every time the player taps the screen, if the screen doesn't knock, then Faby falls due to gravity. Each pair of pipes he navigates yields one player point, with a medal awarded for a score at the end of the match. No medals are awarded for scores less than ten. Bronze medals are awarded for scores between ten and twenty. To receive a silver medal, players must reach 20 points. Gold medals are given to those whose value is higher than thirty points. Players who reach a score of forty or higher receive a platinum medal.

Here is the game code for Flappy Bird
Code index.html


<!DOCTYPE html>

<html>

  <head>

    <title>Flappy Bird using JS | by learnWD</title>

  </head>

  <body>

   <h3>flappyBird by LearnWD</h3>

  

   <canvas id="canvas" width="288" height="512"></canvas>

  

   <script src="flappyBird.js"></script>

  </body>

</html>

Code flappyBird.js 



var cvs = document.getElementById("canvas");

var ctx = cvs.getContext("2d");

// load images

var bird = new Image();

var bg = new Image();

var fg = new Image();

var pipeNorth = new Image();

var pipeSouth = new Image();

bird.src = "images/bird.png";

bg.src = "images/bg.png";

fg.src = "images/fg.png";

pipeNorth.src = "images/pipeNorth.png";

pipeSouth.src = "images/pipeSouth.png";



// some variables

var gap = 85;

var constant;

var bX = 10;

var bY = 150;

var gravity = 1.5;

var score = 0;

// audio files

var fly = new Audio();

var scor = new Audio();

fly.src = "sounds/fly.mp3";

scor.src = "sounds/score.mp3";

// on key down

document.addEventListener("keydown",moveUp);

function moveUp(){

    bY -= 25;

    fly.play();

}

// pipe coordinates

var pipe = [];

pipe[0] = {

    x : cvs.width,

    y : 0

};

// draw images

function draw(){

  

    ctx.drawImage(bg,0,0);

  

  

    for(var i = 0; i < pipe.length; i++){

      

        constant = pipeNorth.height+gap;

        ctx.drawImage(pipeNorth,pipe[i].x,pipe[i].y);

        ctx.drawImage(pipeSouth,pipe[i].x,pipe[i].y+constant);

            

        pipe[i].x--;

      

        if( pipe[i].x == 125 ){

            pipe.push({

                x : cvs.width,

                y : Math.floor(Math.random()*pipeNorth.height)-pipeNorth.height

            });

        }

        // detect collision

      

        if( bX + bird.width >= pipe[i].x && bX <= pipe[i].x + pipeNorth.width && (bY <= pipe[i].y + pipeNorth.height || bY+bird.height >= pipe[i].y+constant) || bY + bird.height >=  cvs.height - fg.height){

            location.reload(); // reload the page

        }

      

        if(pipe[i].x == 5){

            score++;

            scor.play();

        }

      

      

    }

    ctx.drawImage(fg,0,cvs.height - fg.height);

  

    ctx.drawImage(bird,bX,bY);

  

    bY += gravity;

  

    ctx.fillStyle = "#000";

    ctx.font = "20px Verdana";

    ctx.fillText("Score : "+score,10,cvs.height-20);

  

    requestAnimationFrame(draw);

  

}

draw();

Files Images and Sound:  Images | Sound

The following tutorial makes a game Flappy Bird


2. Simple Code Snake Game Using Javascript
The following code to make a simple snake game with JavaScript:


Here is the game code for Snake


<canvas id="gc" width="400" height="400"></canvas>

<script>

window.onload=function() {

    canv=document.getElementById("gc");

    ctx=canv.getContext("2d");

    document.addEventListener("keydown",keyPush);

    setInterval(game,1000/15);

}

px=py=10;

gs=tc=20;

ax=ay=15;

xv=yv=0;

trail=[];

tail = 5;

function game() {

    px+=xv;

    py+=yv;

    if(px<0) {

        px= tc-1;

    }

    if(px>tc-1) {

        px= 0;

    }

    if(py<0) {

        py= tc-1;

    }

    if(py>tc-1) {

        py= 0;

    }

    ctx.fillStyle="black";

    ctx.fillRect(0,0,canv.width,canv.height);



    ctx.fillStyle="lime";

    for(var i=0;i<trail.length;i++) {

        ctx.fillRect(trail[i].x*gs,trail[i].y*gs,gs-2,gs-2);

        if(trail[i].x==px && trail[i].y==py) {

            tail = 5;

        }

    }

    trail.push({x:px,y:py});

    while(trail.length>tail) {

    trail.shift();

    }



    if(ax==px && ay==py) {

        tail++;

        ax=Math.floor(Math.random()*tc);

        ay=Math.floor(Math.random()*tc);

    }

    ctx.fillStyle="red";

    ctx.fillRect(ax*gs,ay*gs,gs-2,gs-2);

}

function keyPush(evt) {

    switch(evt.keyCode) {

        case 37:

            xv=-1;yv=0;

            break;

        case 38:

            xv=0;yv=-1;

            break;

        case 39:

            xv=1;yv=0;

            break;

        case 40:

            xv=0;yv=1;

            break;

    }

}

</script>
