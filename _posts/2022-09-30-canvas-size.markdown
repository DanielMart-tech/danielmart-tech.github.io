---
layout: post
title:  "The Canvas Size"
date:   2022-09-30 15:12:06 -0400
categories: canvas
---
The HTML `<canvas>` element has, by default, a width of 300px and a height of 150px.

##### index.html

<pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
    &lt;head&gt;
        &lt;meta charset="UTF-8" /&gt;
        &lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
        &lt;link rel="stylesheet" href="style.css"&gt;
        &lt;title&gt;The Canvas Size&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;canvas&gt;&lt;/canvas&gt;
        &lt;canvas id="canvas2"&gt;&lt;/canvas&gt;

        &lt;script src="index.js"&gt;&lt;/script&gt;
    &lt;/body&gt;
&lt;/html&gt;
</code></pre>

##### index.js

Let's check out the width and height values of the `<canvas>` element by getting a reference to it.

To get a reference to the HTML `<canvas>` element in the document, we have to use the
*Document.querySelector()* method. As argument we pass the string "canvas" and use a variable to contain that reference. Now the variable contains the *HTMLCanvasElement* object.

<pre><code>const canvas = document.querySelector("canvas")
</code></pre>

Now, we can access its properties, i.e, width and height.

<pre><code>console.log(canvas.width) // 300
console.log(canvas.height) // 150
</code></pre>

If we wish, we can modify its width and height attributes by assigning new values. These values must be *positive integers*.

### Changing the size of a canvas element with CSS

It's possible to change the size of the canvas using CSS. However, doing this might give unexpected results. But why?

If we change the width and height properties using CSS, the web browser will scale the surface.

Let's see this in action.

First, let's draw a 150x75 rectangle and place it at the center of the canvas.

<pre><code>const rectXCoordinate = canvas.width / 2
const rectYCoordinate = canvas.height / 2

const context = canvas.getContext("2d")
context.fillRect(rectXCoordinate-75, rectYCoordinate-37.5, 150, 75)
</code></pre>

Now let's get a reference to our second `<canvas>` element with the 'canvas2' id, get the context and draw a rectangle. Let's pass the same arguments to the *fillRect()* method.

<pre><code>const canvas2 = document.getElementById("canvas2")

const rect2XCoordinate = canvas2.width / 2
const rect2YCoordinate = canvas2.height / 2

const context2 = canvas2.getContext("2d")
context2.fillRect(rect2XCoordinate-75, rect2YCoordinate-37.5, 150, 75)
</code></pre>

##### style.css

In our CSS file, let's add the following:

<pre><code>#canvas2 {
    width: 600px;
    height: 300px;
}
</code></pre>

![black rectangle](/../../../assets/images/black_rectangle.png)

![scaled black rectangle](/../../../assets/images/scaled_black_rectangle.png)

As we can observe in the second image the drawing has been scaled (even though it's got the same arguments or values as the first one). Since we have changed the width and height using CSS, the browser will scale the surface trying to fit the drawing onto the canvas.

>Note: It's better to use the canvas' width and height attributes to size the element instead of using CSS.

### Challenge

1. Modify the width and height directly in the 'canvas' tag. Has the drawing surface been scaled?