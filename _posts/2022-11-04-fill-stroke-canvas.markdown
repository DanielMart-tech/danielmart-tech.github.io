---
layout: post
title:  "Filling and Stroking Shapes in Canvas"
date:   2022-11-04 15:12:06 -0400
categories: canvas
---
### Fill
When drawing shapes, it's possible to fill them using the *fillStyle* property.

Here we're going to analyse every single possible value that can be used with this property.

- Color

A string indicating a CSS color.

There are different ways in which the color CSS data type can be defined. Let's see.

a) As a keyword: 

<pre><code>context.fillStyle = "yellowgreen"
</code></pre>

b) As a hexadecimal value:

<pre><code>context.fillStyle = "#9acd32"
</code></pre>

c) As an RGB(A) value:

<pre><code>context.fillStyle = "rgb(154,205,50)" // the alpha channel can be included
</code></pre>

d) As an HSL(A) value:

<pre><code>context.fillStyle = "hsl(80 60.8% 50%)" // the alpha channel can be included
</code></pre>

- Gradient

A **CanvasGradient** object (a linear, radial or conic gradient).

a) **createLinearGradient(x<sub>0</sub>, y<sub>0</sub>, x<sub>1</sub>, y<sub>1</sub>)**: It creates a linear gradient along the line connecting the passed arguments. The first coordinate (x<sub>0</sub>, y<sub>0</sub>) represent the start point and the last one the end point (x<sub>1</sub>, y<sub>1</sub>).

b) **createRadialGradient(x<sub>0</sub>, y<sub>0</sub>, r<sub>0</sub>, x<sub>1</sub>, y<sub>1</sub>, r<sub>1</sub>)**: It creates a radial gradient using the coordinates and radii of two circles. The first three parameters (x<sub>0</sub>, y<sub>0</sub>, r<sub>0</sub>) are the the x- and y-axis coordinates and radius of the first circle; the last three parameters (x<sub>1</sub>, y<sub>1</sub>, r<sub>1</sub>) are the x- and y-axis coordinates and radius of the second circle.

c) **createConicGradient(startAngle, x, y)**: It creates a conic gradient around a point represented by the passed arguments. *startAngle* is the angle in radians at which to begin the gradient; angle measurements start vertically above the center.

The *CanvasGradient*'s ***addColorStop()*** method adds colours 

**addColorStop(offset, color)**

1. offset: a number between 0 and 1 signaling the position of the colour stop. 0 indicates the start, 1 indicates the end.
2. color: a CSS colour


- Pattern

A **CanvasPattern** object which represents an image, canvas, or video-based pattern.
We get this object through the *createPattern()* method from the *CanvasRenderingContext2D* interface. The *createPattern()* method requires two arguments:

**createPattern(image, repetition)**

An image can be:
1. HTMLImageElement (\<img\>)
2. SVGImageElement (\<image\>)
3. HTMLVideoElement (\<video\>)
4. HTMLCanvasElement (\<canvas\>)
5. ImageBitmap
6. OffscreenCanvas
7. VideoFrame

A repetition pattern can be any of the following strings:

1. "repeat" (both directions)
2. "repeat-x" (horizontal only)
3. "repeat-y" (vertical only)
4. "no-repeat" (neither direction)

Let's see the *fillStyle* property in action:

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.fillStyle = "brown"
context.fillRect(0, 0, 50, 50)

const linearGradient = context.createLinearGradient(70, 25, 120, 25)
linearGradient.addColorStop(0, "brown")
linearGradient.addColorStop(1, "khaki")
context.fillStyle = linearGradient
context.fillRect(70, 0, 50, 50)

const radialGradient = context.createRadialGradient(165, 25, 10, 147.5, 25, 30)
radialGradient.addColorStop(0, "brown")
radialGradient.addColorStop(1, "khaki")
context.fillStyle = radialGradient
context.fillRect(140, 0, 50, 50)

const conicGradient = context.createConicGradient(0, 235, 25)
conicGradient.addColorStop(0, "brown")
conicGradient.addColorStop(1, "khaki")
context.fillStyle = conicGradient
context.fillRect(210, 0, 50, 50)

const img = new Image()
img.src = "insect.jpg"
img.onload = () => {
  const pattern = context.createPattern(img, "repeat");
  context.fillStyle = pattern;
  context.fillRect(0, 70, 300, 200);
}
</code></pre>

![fill](/../../../assets/images/fill.png)

### Stroke

The *strokeStyle* property delineates the shapes of figures.
Working with the *strokeStyle* is similar to *fillStyle*.
The values used are solid colours, gradients and patterns.

### Challenge
1. Implement the *strokeStyle* property with values mentioned above.

---
Photo by <a href="https://unsplash.com/@sxtcxtc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Sorin Gheorghita</a> on <a href="https://unsplash.com/s/photos/mariquita?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Unsplash</a>