---
layout: post
title:  "Lines in Canvas: I Part"
date:   2022-10-21 15:12:06 -0400
categories: canvas
---
In the Canvas 2D API there are several methods and properties to control how lines are drawn. In this post we're going to look at some of them. Here we're gonna focus on continuous lines and in the next post the focus will be on dashed lines.

##### index.html

&lt;canvas id="canvas"&gt;&lt;/canvas&gt;

> Note: I have omitted the basic structure of an HTML file for brevity.

##### index.js

### The width of a line

To control the thickness of a line we have to change the *lineWidth* property of the *CanvasRenderingContext2D* object. Its value is a number which, by default, is 1.0

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.beginPath()
context.moveTo(150, 0)
/*
The width of the line is changed 
before calling the lineTo() method
*/
context.lineWidth = 10
context.lineTo(150, 150)
context.stroke()
</code></pre>

![width of a line](/../../../assets/images/line_width.png)

### The extremes of a line segment

The *lineCap* property shapes the end points of lines.

It allows one of the following values:

- **butt**: the endpoints are squared off. This is the default value.

- **square**: the endpoints are also squared off but a box is added with an equal width and half the height of the line's thickness. 

- **round**: the endpoints are rounded.

<pre><code>context.lineWidth = 1.0

/* boundary lines */

context.beginPath()
context.moveTo(10, 40)
context.lineTo(90, 40)
context.stroke()

context.beginPath()
context.moveTo(10, 100)
context.lineTo(90, 100)
context.stroke()


context.lineWidth = 10

/* 'butt' value 
The 'lineCap' property hasn't been modified 
since 'butt' is the default value
*/
context.beginPath()
context.moveTo(20, 40)
context.lineTo(20, 100)
context.stroke()

/* 'square' value */
context.beginPath()
context.lineCap = "square"
context.moveTo(50, 40)
context.lineTo(50, 100)
context.stroke()

/* 'round' value */
context.beginPath()
context.lineCap = "round"
context.moveTo(80, 40)
context.lineTo(80, 100)
context.stroke()
</code></pre>

![line endings](/../../../assets/images/line_endings.png)

### Concatenating lines

The *lineJoin* property shapes how two line segments are joined.

It allows one of the following values:

- **miter**: A square corner is drawn at the join. This is the default value.

- **bevel**: An oblique corner is drawn at the join.

- **round**: A round corner is drawn at the join.

<pre><code>/* 'miter' value */
context.beginPath()
context.lineCap = "butt"
context.lineJoin = "miter"
context.moveTo(200, 40)
context.lineTo(200, 80)
context.lineTo(240, 80)
context.stroke()

/* 'bevel' value */
context.beginPath()
context.lineJoin = "bevel"
context.moveTo(260, 40)
context.lineTo(260, 80)
context.lineTo(300, 80)
context.stroke()

/* 'round' value */
context.beginPath()
context.lineJoin = "round"
context.moveTo(230, 100)
context.lineTo(230, 140)
context.lineTo(280, 140)
context.stroke()
</code></pre>

![line joins](/../../../assets/images/line_joins.png)

### Miter limit ratio

When two lines are joined with the *lineProperty* set to *miter* and the angles between each is small, the miter length can be quite long. 

The default value of the *miterLimit* property is 10.

<pre><code>/* 'miterLimit' property */
context.beginPath()
context.lineJoin = "miter"
context.miterLimit = 5
context.moveTo(10, 150)
context.lineTo(10, 190)
context.lineTo(100, 120)
context.stroke()
</code></pre>

![miter limit](/../../../assets/images/miter_limit.png)