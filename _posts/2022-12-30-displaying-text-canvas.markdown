---
layout: post
title:  "Displaying Text in Canvas"
date:   2022-12-30 15:12:06 -0400
categories: canvas
---
To display text in the Canvas API we need the ***fillText()*** or ***strokeText()*** methods.

*fillText()* fills a string of characters (according to the *fillStyle* property) at the specified coordinates.

These are the arguments needed for the *fillText()* method:

- **fillText(text, x , y, maxWidth)**

1. text: the text to be displayed.
2. x: the x-axis coordinate of the point at which to begin drawing the text.
3. y: the y-axis coordinate of the baseline on which to begin drawing the text.
4. maxWidth: this is an optional argument used to specify the maximum number of pixels wide the text may be displayed.

<pre><code>const canvas = document.getElementById("canvas")
const context = canvas.getContext("2d")

context.font = "italic 30px serif"
context.textBaseline = "top"
context.fillText("Hello!", 0, 41)

context.textBaseline = "alphabetic"
context.textAlign = "right"
context.direction = "rtl"
context.fillText("Hello!", 90, 40, 35)

const text = context.measureText("Hello")
console.log(text.width) // 74.01667022705078
</code></pre>

![text](/../../../assets/images/text.png)

We can control how the text is displayed with several properties, such as:

- font: a string like the CSS font shorthand property. Default value is 10px sans-serif.
- textAlign: the alignment of the text. Its values are:
    - left
    - right
    - center
    - start (default value)
    - end
- textBaseline: the position of the baseline. Passible values are:
    - top
    - middle
    - alphabetic (default value)
    - bottom
- direction: possible values:
    - ltr: left-to-right
    - rtl: right-to-left
    - inherit (default value)
- fontKerning: possible values:
    - auto (default value)
    - normal
    - none

We can get information about the measurements of the text thanks to the **TextMetrics** object. To get it we must call the **measureText()** method from the context. These are its read-only properties:

- width: the width of the text.
- actualBoundingBoxLeft: distance to the baseline from the alignment point given by the *textAlign* property to the left side of the bounding rectangle.
- actualBoundingBoxRight: distance to the baseline from the alignment point given by the *textAlign* property to the right side of the bounding rectangle.
- fontBoundingBoxAscent: distance from the horizontal line indicated by the *textBaseline* to the top of the highest bounding rectangle.
- fontBoundingBoxDescent: distance from the horizontal line indicated by the *textBaseline* attribute to the bottom of the bounding rectangle.
- actualBoundingBoxAscent: distance from the horizontal line indicated by the *textBaseline* to the top of the bounding rectangle.
- actualBoundingBoxDescent: distance from the horizontal line indicated by the *textBaseline* to the bottom of the bounding rectangle.

### Challenge

1. *strokeText()* method implements the same arguments. Try to display (outline) some text using this method.