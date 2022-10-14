---
layout: post
title:  "Drawing Rectangles in Canvas"
date:   2022-10-07 15:12:06 -0400
categories: canvas
---
The rectangle is the primitive or geometric form from which others derived in the Canvas 2D API.

In today's post, we'll learn how to draw rectangles onto the canvas. So, let's get ready!

##### index.html

<pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
    &lt;head&gt;
        &lt;meta charset="UTF-8" /&gt;
        &lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
        &lt;title&gt;Drawing Rectangles in Canvas&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;canvas id="canvas"&gt;
            draw of three rectangles
        &lt;/canvas&gt;

        &lt;script src="index.js"&gt;&lt;/script&gt;
    &lt;/body&gt;
&lt;/html&gt;
</code></pre>

The text inside the tags is just alternative content in case one of the two following events happens:

1. An older browser which doesn't support canvas.
2. Or in browsers with JavaScript disabled.

##### index.js

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")
</code></pre>

The value returned by the *getContext("2d")* method is the *CanvasRenderingContext2D* object which provides three different methods for drawing rectangles.

- **fillRect(x, y, width, height)**

This method requires four arguments:

1. x: the x-axis coordinate.
2. y: the y-axis coordinate  
3. width: the rectangle's width
4. height: the rectangle's height

### The Coordinate System

The origin of the coordinate system on canvas, i.e. the point P(0,0), is placed at the upper-left corner. Positive X coordinates are to the right; positive Y coordinates are down.

![coordinate system](/../../../assets/images/coordinate_system.png)

Let's call the *fillRect()* method.

<pre><code>context.fillRect(0, 0, canvas.width/2, canvas.height/2)
</code></pre>

This is the result:

![black rectangle at origin](/../../../assets/images/black_rectangle_at_origin.png)

The rectangle's top-left corner is at (0,0) and its width and height are half the canvas.
By default, the colour is '#000' (black). However, this property can be changed. Let's do it!
Before calling *fillRect()*, let's add the following line of code.

<pre><code>context.fillStyle = "#ffdde2"
context.fillRect(0, 0, canvas.width/2, canvas.height/2)
</code></pre>

![pink rectangle](/../../../assets/images/pink_rectangle.png)

Now we have a rectangle filled with pink.

- **strokeRect(x, y, width, height)**

This method allows us to delineate a rectangle. The same four arguments are required as the previous method. By default, the colour is black. To change it, we previously modify the *strokeStyle* property.

Time to outline a rectangle:

<pre><code>context.strokeStyle = "#2334ad"
context.strokeRect(canvas.width/2, 0, canvas.width/2, canvas.height/2)
</code></pre>

![filled & stroked rectangles](/../../../assets/images/filled_&_stroked_rectangles.png)

We get a bluish stroked rectangle as seen in the image.

- **clearRect(x, y, width, height)**

The last method is *clearRect()*. It requires the four arguments mentioned above as well.
This method clears the specified area to transparent.

<pre><code>context.clearRect(5, 5, 80, 40)
</code></pre>

This rectangle is placed on top of the pink rectangle and we can see how a transparent region has been drawn.

![cleared rectangle](/../../../assets/images/cleared_rectangle.png)