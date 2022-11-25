---
layout: post
title:  "Drawing Arcs in Canvas"
date:   2022-11-25 15:12:06 -0400
categories: canvas
---
Another type of shape we can draw using the Canvas API is an arc.
There are three methods which will help us to fulfill this task.

- **arc(x, y, r, startAngle, endAngle, counterclockwise)**

The arguments required are:

1. x: the x-axis coordinate of the center of the arc.
2. y: the y-axis coordinate of the center of the arc.
3. r: the radius of the arc.
4. startAngle: the angle at which the arc starts, from the positive x-axis. (measured in radians)
5. endAngle: the angle at which the arc ends, from the positive x-axis. (measured in radians)
6. counterclockwise: This parameter is optional. If it is passed, a boolean value must be indicated. *true* draws the arc counter-clockwise.

Here's a list of some useful conversions:

360º = 2π

180º = π

90º = π/2

45º = π/4

0º = 0

### π in JavaScript

JavaScript has the *Math* built-in object, amongst its properties there is *Math.PI* which represents the ratio of the circumference of a circle to its diameter, useful when drawing arcs.

### Drawing a full and semi-circle

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

// drawing a full arc
context.arc(75, 75, 35, 0, 2*Math.PI)
context.fill()

// drawing a semi-arc
context.arc(150, 75, 35, 0, Math.PI)
context.fill()
</code></pre>

![full and semi-arcs](/../../../assets/images/full_and_semi_arcs.png)

We can also add an arc by connecting it to the current sub-paths using control points.

- **arcTo(cp1x, cp1y, cp2x, cp2y, r)**

The arguments required are:

1. cp1x: the x-axis coordinate of the first control point.
2. cp1y: the y-axis coordinate of the first control point.
3. cp2x: the x-axis coordinate of the second control point.
4. cp2y: the y-axis coordinate of the second control point.
5. r: the radius of the arc.

<pre><code>context.beginPath()
context.lineWidth = 5
context.moveTo(30, 120)
context.arcTo(59, 250, 75, 160, 20)
context.stroke()
</code></pre>

![arcTo](/../../../assets/images/arcTo.png)

> If the radius of the arc is too large, we may encounter some difficulties.

### Drawing an ellipse

Ellipses are drawn with the *ellipse()* method.

- **ellipse(x, y, rx, ry, rotation, startAngle, endAngle, counterclockwise)**

As seen above, the arguments required are:

1. x: the x-axis coordinate of the center of the ellipse.
2. y: the y-axis coordinate of the center of the ellipse.
3. rx: The ellipse's major-axis radius.
4. ry: The ellipse's minor-axis radius.
5. rotation: the rotation of the ellipse (measured in radians).
6. startAngle: the angle at which the ellipse starts, from the positive x-axis. (measured in radians)
7. endAngle: the angle at which the arc ends, from the positive x-axis. (measured in radians)
8. counterclockwise: This parameter is optional. If it is passed, a boolean value must be indicated. *true* draws the arc counter-clockwise.

<pre><code>context.beginPath()
context.ellipse(140, 160, 20, 35, Math.PI / 4, 0, 2*Math.PI)
context.stroke()
</code></pre>

![ellipse](/../../../assets/images/ellipse.png)