# Introduction to p5.js!
Reference code &amp; materials for a 2-hour pre-conference workshop introducing [p5.js](https://www.p5js.org) at [Strangeloop 2022](https://www.thestrangeloop.com/).

We will be working with the [p5.js web editor](https://editor.p5js.org/). Please create an account there to save your code.

Topics covered:

* drawing: shapes, fill, stroke, strokeWeight
* variables: declarations, assignments, scope, updating
* functions: setup and draw
* user input: mouse movement, mouse press
* conditionals: if/else
* map: math!
* animation: move, bounce
* loops: repeats, grids

[Collection of examples for all topics](https://editor.p5js.org/kjhollen/collections/sNFpUWpsH) in the p5.js editor.

## drawing: shapes, fill, stroke, strokeWeight

First, we'll practice the basics of drawing with shapes and working with the p5.js coordinate system.

```
  // 0-255 grayscale
  stroke(255);

  // line (x1, y1, x2, y2)
  line(10, 20, 190, 20);

  // red, green, blue 0-255
  fill(54, 104, 204);

  // no outline
  noStroke();

  // rect (x, y, w, h) where x, y is top left
  rect(210, 20, 80, 160);

  // ellipse(x, y, w, h) where x, y is in the center
  ellipse(100, 200, 100, 100);
```
[Run example: simple colors and shapes](https://editor.p5js.org/kjhollen/sketches/eZsNSfDq2)

**Practice exercise**: Make the canvas 300x300 pixels. Using only two colors, make a composition using at least 8 circles. Consider how you can make more complex shapes by overlapping circles in various ways.

**Practice exercise**: Make the canvas 100x100 pixels. Using only black and white (no grayscale yet!), create a sketch that draws a leaf. Note: make the background black or white, too.

## variables ##

Use variables to store and/or update information. There are many "types" of data you can store in a variable, but to keep things simple for now, we'll focus on numbers.

```
let x = 100; // declare a variable, x, and assign it a value (100)
line(x, 50, x, 350); // use the variable, x, to draw a line at x = 100
```

Variables declared with `let` can be updated and assigned a new value.

```
x = x + 20; // adds 20 to x (previously 100), and reassigns the new value (120) to x
line(x, 50, x, 350); // this time, use the variable to draw a line at x = 120
```

[Run full example: declaring, assigning, & using variables](https://editor.p5js.org/kjhollen/sketches/rzyFfs_io)

Where should you declare & assign your variables? Unfortunately, there's not a simple answer to this question: it depends on what you want to do. So far, to keep things simple, we've been declaring our variables right before we use them in the `draw()` function. You may also want to have some variables in what's called the global scope:

```
let x = 100;

function setup() {
  createCanvas(600, 600);
}

function draw() {
  background(0);
  stroke(255);
  strokeWeight(5);
  
  line(x, 50, x, 350);
  // x = x + 1;
}
```
The global scope is outside of either the `setup()` and `draw()` functions. When you're getting started, it can be nice to keep your variables at the top of the code for easy reading. Notice there's a line here that's commented out. What happens when you uncomment it? Why?

[Run full example: global variable](https://editor.p5js.org/kjhollen/sketches/tBIXNbKfb)

p5.js also has some built-in variables that can be used for creating interactive sketches. For example, the `mouseX` and `mouseY` variables hold the current (x,y) location of the mouse.

```
// draws a line from the center of the canvas to the mouse
function setup() {
  createCanvas(600, 600);
  background(0);
}

function draw() {
  stroke(255);
  line(300, 300, mouseX, mouseY);
}
```
[Run example: drawing a line from the center of the canvas to the mouse](https://editor.p5js.org/kjhollen/sketches/QiDnC-Anc)

## simple user interaction: `mouseIsPressed` variable &amp; conditionals

The built-in variable `mouseIsPressed` contains one of two values, `true` or `false`, indicating whether or not a button on the mouse is currently pressed. Considering our previous example, we can modify our code to only draw when the user presses the mouse by using this variable with an `if` statement:

```
function setup() {
  createCanvas(600, 600);
  background(0);
}

function draw() {
  stroke(255);
  if (mouseIsPressed == true) { // only draw if mouse button pressed!
  	line(300, 300, mouseX, mouseY);
  }
}
```
[Run example: simple drawing program with user interaction](https://editor.p5js.org/kjhollen/sketches/o_2NLjl-h)

**Practice exercise**: Create a simple drawing program where the user can draw by pressing the mouse. If you feel stuck, try to start with something simple, like drawing a circle where the user clicks, then add on more shapes. Try to do something unexpected. 

**Practice exercise**: For an added challenge, try to create a drawing program that has two different tools that the user can access by pressing 2 different keys on the keyboard. Think about how you might add variables and use the [`key`](https://p5js.org/reference/#/p5/key) or [`keyIsPressed`](https://p5js.org/reference/#/p5/keyIsPressed) variables, or even the [`keyPressed()`](https://p5js.org/reference/#/p5/keyPressed) function to achieve this.

## resources / what's next?

looking for more tutorials? try these!

* [p5.js reference](https://p5js.org/reference/) - list of all p5.js functions, with examples
* [p5.js forums](https://discourse.processing.org/c/p5js) - a good place to ask questions and get help
* [book: getting started with p5.js](https://www.amazon.com/Make-Interactive-Graphics-JavaScript-Processing/dp/1457186772) - by Lauren McCarthy, Casey Reas, and Ben Fry
* [intro to programming in p5.js](https://www.youtube.com/playlist?list=PLT233rQkMw761t_nQ_6GkejNT1g3Ew4PU) - by xin xin
* [the coding train: foundations of programming in javascript](https://www.youtube.com/watch?v=yPWkPOfnGsw&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA) by Dan Shiffman
