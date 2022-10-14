---
layout: post
title:  "Paths in Canvas"
date:   2022-10-14 15:12:06 -0400
categories: canvas
---
The Canvas 2D API offers us the possibility to draw paths and sub-paths to create different shapes and figures.

To initiate a new path we have to call the *beginPath()* method from the *CanvasRenderingContext2D* object.

##### index.html

<pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
    &lt;head&gt;
        &lt;meta charset="UTF-8" /&gt;
        &lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
        &lt;title&gt;Paths in Canvas API&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;canvas id="canvas"&gt;
            drawing of a line, triangle & cube
        &lt;/canvas&gt;

        &lt;script src="index.js"&gt;&lt;/script&gt;
    &lt;/body&gt;
&lt;/html&gt;
</code></pre>

##### index.js

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.beginPath()
</code></pre>

Now that we have created a new path, we can start drawing some lines.
To do that, first let's move our graphics paintbrush to the (x, y) coordinates we want.

<pre><code>context.moveTo(140, 72)
</code></pre>

From that starting point let's draw a straight line to another (x, y) coordinates we want.
To achieve this we need to call the *lineTo()* method. This connects the last point, in our example P(140, 72), to the specified (x, y) coordinates.

<pre><code>context.lineTo(45, 23)
</code></pre>

We still cannot see anything. The reason why is that this method doesn't render anything, we must then call the *stroke()* method.

<pre><code>context.stroke()
</code></pre>

Here's the result:

![line](/../../../assets/images/line.png)

### Drawing a triangle

<pre><code>context.beginPath()
context.moveTo(200, 120)
context.lineTo(233, 99)
context.lineTo(199, 145)
context.closePath()
context.stroke()
</code></pre>

![line & triangle](/../../../assets/images/line_and_triangle.png)

Notice the *closePath()* method. This adds a line from the current point, in our case O(199, 145), to the starting point of the current sub-path, in our example is the point M(200, 120), to close the triangle.

### Drawing a cube

<pre><code>context.beginPath()
context.moveTo(170, 80)
context.lineTo(170, 40)
context.lineTo(210, 40)
context.lineTo(210, 80)
context.closePath()
context.moveTo(170, 40)
context.lineTo(185, 15)
context.lineTo(225, 15)
context.lineTo(210, 40)
context.moveTo(225, 15)
context.lineTo(225, 55)
context.lineTo(210, 80)
context.stroke()
</code></pre>

![line, triangle & cube](/../../../assets/images/line_triangle_cube.png)

### Challenge

1. Try to draw a basic figure of your own choice.