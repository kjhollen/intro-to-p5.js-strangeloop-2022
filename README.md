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

## getting started: the default sketch

When you start a new sketch in the p5.js editor, it has some template code to help you get started. This template code includes two functions: `setup()` and `draw()`.

- **`setup()`** runs exactly once, when your sketch first starts
- **`draw()`** runs after `setup()`, repeating at a rate of 60 frames per second until you close the tab or stop the sketch

In the default sketch, `setup()` is used to initialize the canvas and set its drawable size, while `draw()` just clears the background with a light gray color.

```
// runs first, and only once when sketch is started
function setup() {
  createCanvas(400, 400); // creates a drawing area of 400x400 pixels
}

// runs after setup() at a rate of 60 frames per second, by default
function draw() {
  background(220); // draws a light gray background over the whole canvas
}
```

## drawing: shapes, fill, stroke, strokeWeight

First, we'll practice the basics of drawing with shapes and working with the p5.js coordinate system. While we're just getting started, it may be convenient to add the `noLoop()` function to `setup()` to make `draw()` run only once.

p5.js provides some functions for drawing basic shapes, like circles, rectangles, lines, and triangles. You can also build complex shapes by drawing vertices directly, but sometimes it's easier to layer simple shapes or import an image in this case. To draw shapes on the canvas, we need to be able to describe where they are. Every shape needs a location as an (x,y) coordinate (or possibly multiple locations, for example, for a line where two endpoints are required). Some shapes may also need dimensions to describe their size.

```
  // line (x1, y1, x2, y2)
  line(10, 20, 190, 20);

  // rect (x, y, w, h) where x, y is top left
  rect(210, 20, 80, 160);

  // ellipse(x, y, w, h) where x, y is in the center
  ellipse(100, 200, 100, 100);
```
The color of lines or outlines can be controlled with the `stroke()` function. The interior color of shapes is controlled with `fill()`. If you want to turn off the outline or fill color, you can use `noStroke()` or `noFill()`.
```
  // 0-255 grayscale
  stroke(255);

  // red, green, blue 0-255
  fill(54, 104, 204);

  // no outline
  noStroke();
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

## advanced topics

If we have time, we'll work through some more advanced topics for creating generative and interactive works. If we run out of time, these can also be a great place to continue studying on your own!

### `map()`

[`map()`](https://p5js.org/reference/#/p5/map) is a useful function for scaling a variable from a known domain (set of inputs) to a desired output range. For example, you may want to use the current `mouseX` coordinate to control the size of a shape, or the brightness of a color. The `map()` function takes five (!) arguments: an input value to scale, the minimum number expected in the input, a maximum number expected in the input, the desired minimum output number, and finally the desired maximum output number. The `map()` function performs the scaling calculation so we don't have to, then returns the value so we can use/store it for later use. 

In this example, the variable circleSize will be 5 when mouseX is 0, or 100 when mouseX is 600, or 47.5 when mouseX is 300, etc:
```
// mouseX expected to be between 0 - 600, desired output is a circle size between 5 - 100  
let circleSize = map(mouseX, 0, 600, 5, 100);
```
And in this example, the variable fillColor will be 0 when mouseY is 0, or 255 when mouseY is 600, or 128 when mouseY is 300, etc:
```
// mouseY expected to be between 0 - 600, desired output is a color/tone so 0-255
let fillColor = map(mouseY, 0, height, 0, 255);
```

[Run example: scaling size & color with `map()`](https://editor.p5js.org/kjhollen/sketches/_Z1YEo_oc)

### animation

To animate shapes, we can use a variable to store their location and update the variable to move the shape. Recall our global variable example from earlier, where the variable x is updated every frame of the `draw()` function:

```
let x = 0;

function setup() {
  createCanvas(400, 400);
  stroke(255);
  strokeWeight(5);
}

function draw() {
  background(0);
  line(x, 0, x, height);
  
  // move to the right for next time.
  x = x + 1;
}
```
Eventually, the line animates off of the right side of the screen and never comes back! But, we can fix this by adding a conditional that checks if the line has gone off-screen and resetting the x-coordinate to start again at x = 0:

```
  if (x > width) {
    x = 0;
  }
```
[Run example: bouncing line animation](https://editor.p5js.org/kjhollen/sketches/uLuELnQwv)

**Practice exercise**: Update the example code to have the line bounce off the left side of the canvas, too. (Hint: you may also need to add a variable to control the direction or speed of the line - see [solution](https://editor.p5js.org/kjhollen/sketches/0tXQrIJ5a))

### Repetition with loops

When we learned about variables earlier, we saw an example that drew three lines using the same variable and updating its value:

```
  let x = 100;
  line(x, 50, x, 350);

  x = x + 20;
  line(x, 50, x, 350);

  x = x + 20;
  line(x, 50, x, 350);
```

There is some repeated code here. Imagine what this would look like if we want to draw 100 lines in this fashion! With this approach, we'd have to add 200 lines of code. Fortunately, loops provide a compact way to describe an action that should be repeated. The key elements are:

- an initialization: declaring a variable that will be used to count/update in the loop
- a condition: a test run on the loop variable to determine if the loop should continue
- an increment: an expression that updates the loop variable

The `for` loop provides a concise way to declare all three of the required elements:

```
  //  initialize; condition; increment
  for (let x = 20; x <= 580; x = x + 20) {
    line(x, 20, x, 580);
  }
```
[Run example: create a bunch of lines with a for loop](https://editor.p5js.org/kjhollen/sketches/Rp4-nKQJS)

### making grids with nested loops

In the previous example, we used a loop to draw a bunch of vertical lines across the screen by updating the x coordinate of the line in the loop. If we instead wanted to draw a series of shapes, like circles, we could update the code like this:

```
  for (let x = 100;  x <= 500; x += 50) {
    ellipse(x, 100, 50, 50);
  }
```
This code creates a row of circles across the screen. To create a grid, we can write some code that repeats with a changing y coordinate.
```
  let y = 100;
  for (let x = 100;  x <= 500; x += 50) {
    ellipse(x, y, 50, 50); // y is 100
  }
  
  y += 50; // same as y = y + 50;
  for (let x = 100;  x <= 500; x += 50) {
    ellipse(x, y, 50, 50); // y is 150
  }
  
  y += 50;
  for (let x = 100;  x <= 500; x += 50) {
    ellipse(x, y, 50, 50); // y is 200
  }
```
A similar pattern happens here, where our loop is repeated multiple times with different values of `y`. We can make this more compact with yet another loop!

```
 for (let x = 100; x <= 500; x += 50) {
    for (let y = 100;  y <= 500; y += 50) {
      ellipse(x, y, 50, 50);
    }
  }
```
These two loops are now nested. The first loops over the variable `x` and the other loops over the variable `y`. Because they are nested, the *entire* loop for `y` runs for every value of `x`.

[Run example: create a grid of circles with two nested loops](https://editor.p5js.org/kjhollen/sketches/jE0hOsL57)

**Practice exercise**: Create an interactive distortion grid, where shapes respond to their proximity to the mouse. The [`dist()`](https://p5js.org/reference/#/p5/dist) function will be useful for this.

## resources / what's next?

looking for more tutorials? try these!

* [p5.js reference](https://p5js.org/reference/) - list of all p5.js functions, with examples
* [p5.js forums](https://discourse.processing.org/c/p5js) - a good place to ask questions and get help
* [book: getting started with p5.js](https://www.amazon.com/Make-Interactive-Graphics-JavaScript-Processing/dp/1457186772) - by Lauren McCarthy, Casey Reas, and Ben Fry
* [intro to programming in p5.js](https://www.youtube.com/playlist?list=PLT233rQkMw761t_nQ_6GkejNT1g3Ew4PU) - by xin xin
* [the coding train: foundations of programming in javascript](https://www.youtube.com/watch?v=yPWkPOfnGsw&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA) by Dan Shiffman
