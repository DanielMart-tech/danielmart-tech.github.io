---
layout: post
title:  "Paths for Rectangles in Canvas"
date:   2022-12-02 15:12:06 -0400
categories: canvas
---
In a previous [post](https://danielmart-tech.github.io/canvas/2022/10/07/rectangles-canvas.html) we learned how to draw and instantly render rectangles onto the canvas. However, there is a pair of methods that allows us to add a rectangle to the current path. Because these methods do not render anything, we need to call the *fill()* or *stroke()* methods to visualise the final result.

- **rect(x, y, width, height)**

This method adds a rectangle onto the canvas. It requires the following arguments:

1. x: the x-axis coordinate of the starting point.
2. y: The y-axis coordinate of the rectangle's starting point.
3. width: the rectangle’s width (positive values are to the right, negative to the left.)
4. height: the rectangle’s height (positive values are down, and negative are up.)

- **roundRect(x, y, width, height, radii)**

As its name suggests this method adds a rounded rectangle to the current path. The arguments are the same as the previous one plus the radii of the corners. Radius values work similiar as the border-radius CSS property.

1. x: the x-axis coordinate of the starting point.
2. y: the y-axis coordinate of the rectangle's starting point.
3. width: the rectangle’s width (positive values are to the right, negative to the left.)
4. height: the rectangle’s height (positive values are down, and negative are up.)
5. radii: a number or list specifying the radii for the corners.

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.rect(0, 0, 70, 70)
context.fill()

context.roundRect(90, 0, 70, 70, 20)
context.fill()
</code></pre>

![rects](/../../../assets/images/rects.png)

> The *roundRect()* method is still not supported in Firefox.