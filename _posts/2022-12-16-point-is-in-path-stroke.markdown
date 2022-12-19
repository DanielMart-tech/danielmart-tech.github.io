---
layout: post
title:  "Determining if Point is in Path/Stroke"
date:   2022-12-16 15:12:06 -0400
categories: canvas
---
It is possible to determine if the points in a plane (the canvas) are situated in a path or stroke.

The ***isPointinPath()*** method allows to know if a specified point (denoted by its x- and y-coordinates) is located in the current path. Optionally we can include a *Path2D* object as an argument. A Boolean value is returned indicating *true* if the point is contained in the path, otherwise *false*.

- **isPointinPath(x, y)**
- **isPointinPath(path, x, y)**

1. x: the x-axis coordinate of the point.
2. y: the y-axis coordinate of the point.
3. path: a *Path2D* object

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.rect(0, 0, 70, 70)
context.fill()

let isPointContained = context.isPointInPath(50, 50)
console.log(isPointContained) // <em>true</em> since the point is in the area covered by the rectangle 

let rect2 = new Path2D()
rect2.rect(80, 0, 70, 70)
context.fill(rect2)

let isPoint2Contained = context.isPointInPath(rect2, 50, 0)
console.log(isPoint2Contained); // <em>false</em> since the point is outside of rect2
</code></pre>

The ***isPointinStroke()*** method is similar since it returns a Boolean value indicating if a particular point is inside the area covered by the stroking of a path.

- **isPointinStroke(x, y)**
- **isPointinStroke(path, x, y)**

### Challenge

1. Read about the *non-zero* and *even–odd winding rules*
2. Try to verify if a point is inside the area of a stroke using the *isPointinStroke()*