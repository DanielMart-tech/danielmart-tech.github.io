---
layout: post
title:  "Clipping Regions in Canvas"
date:   2022-12-23 15:12:06 -0400
categories: canvas
---
In Canvas we can define a clipping region through the ***clip()*** method. This allows us to define a portion onto the canvas where only parts of shapes are visible.

Let's examine the following code to see this method in action:

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.beginPath()
context.moveTo(0, 0)
context.lineTo(233, 99)
context.lineTo(199, 145)
context.closePath()
context.stroke()

context.clip()

context.fillStyle = "orange"
context.fillRect(0, 10, 200, 50)
</code></pre>

First, we create a path in which we draw a triangle.

Next, we invoke the *clip()* method to define this triangular region. 

Finally, we call the *fillRect()* method. The only visible part of our rectangle is that intersected in the triangle shape.

![clip](/../../../assets/images/clip.png)