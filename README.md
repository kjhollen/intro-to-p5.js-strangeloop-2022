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

[Demo code](https://editor.p5js.org/kjhollen/sketches/eZsNSfDq2)

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

**Practice exercise**: Make the canvas 300x300 pixels. Using only two colors, make a composition using at least 8 circles. Consider how you can make more complex shapes by overlapping circles in various ways.

**Practice exercise**: Make the canvas 100x100 pixels. Using only black and white (no grayscale yet!), create a sketch that draws a leaf. Note: make the background black or white, too.

## resources / what's next?

looking for more tutorials? try these!

* [p5.js reference](https://p5js.org/reference/) - list of all p5.js functions, with examples
* [p5.js forums](https://discourse.processing.org/c/p5js) - a good place to ask questions and get help
* [book: getting started with p5.js](https://www.amazon.com/Make-Interactive-Graphics-JavaScript-Processing/dp/1457186772) - by Lauren McCarthy, Casey Reas, and Ben Fry
* [intro to programming in p5.js](https://www.youtube.com/playlist?list=PLT233rQkMw761t_nQ_6GkejNT1g3Ew4PU) - by xin xin
* [the coding train: foundations of programming in javascript](https://www.youtube.com/watch?v=yPWkPOfnGsw&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA) by Dan Shiffman
