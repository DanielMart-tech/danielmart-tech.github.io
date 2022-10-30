---
layout: post
title:  "Lines in Canvas: II Part"
date:   2022-10-28 15:12:06 -0400
categories: canvas
---
As promised in [the previous post](https://danielmart-tech.github.io/canvas/2022/10/21/lines-in-canvas.html), now it's time to draw dashed lines.

##### index.html

&lt;canvas id="canvas"&gt;&lt;/canvas&gt;

> Note: The basic structure of an HTML file has been omitted for brevity.

### Setting a dashed line

***setLineDash()*** is the method that establishes the line dash pattern. It requieres an array of numbers which determines distances to draw a line and a gap. If the number of elements is odd, the same pattern is repeated and concatenated.

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.lineWidth = 3

context.beginPath()
context.setLineDash([5, 10])
context.moveTo(10, 0)
context.lineTo(10, 150)
context.stroke()

context.beginPath()
context.setLineDash([5, 10, 3]) // the pattern is [5, 10, 3, 5, 10, 3]
context.moveTo(50, 0)
context.lineTo(50, 150)
context.stroke()
</code></pre>

![dashed lines](/../../../assets/images/dashed_lines.png)

### The outset of a dashed line

The ***lineDashOffset*** property sets the start of a line dash. A floating-point number must be specified. 

<pre><code>context.beginPath()
context.setLineDash([5, 10])
context.lineDashOffset = 5.0
context.moveTo(90, 0)
context.lineTo(90, 150)
context.stroke()
</code></pre>

![dashed lines & offset](/../../../assets/images/offset_dashed_lines.png)

### Recovering the current line dash pattern

The method ***getLineDash()*** returns the array of the current line dash pattern.

<pre><code>context.getLineDash() // Array [ 5, 10 ]
</code></pre>

### Challenge

1. Pass an empty array to the *setLineDash()* method and see what happens.