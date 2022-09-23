---
layout: post
title:  "Brief Introduction to the Canvas API"
date:   2022-09-23 15:12:06 -0400
categories: canvas
---
The **Canvas API** mainly focuses on drawing *2D graphics* using the HTML `<canvas>` element.

Let's work with this element in our HTML file to see how easy it is!

> Note: This HTML element has an opening and closing tag --> `<canvas></canvas>`

### Example:

- Add the opening and closing `<canvas>` tags inside `<body>`.

##### index.html

<pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
    &lt;head&gt;
        &lt;meta charset="UTF-8" /&gt;
        &lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
        &lt;title&gt;Brief Introduction to Canvas API&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;canvas&gt;&lt;/canvas&gt;

        &lt;script src="index.js"&gt;&lt;/script&gt;
    &lt;/body&gt;
&lt;/html&gt;
</code></pre>

##### index.js

- Now it's time to manipulate the `<canvas>` element with JavaScript.
To get a reference to the HTML `<canvas>` element in the document, we have to use the
*Document.querySelector()* method. As argument we pass the string "canvas" and use a variable to contain that reference. Now the variable contains the *HTMLCanvasElement* object.

<pre><code>const canvas = document.querySelector("canvas")
</code></pre>

- The *HTMLCanvasElement* interface provides the *getContext()* method which returns:

    a) a drawing context which let us to draw onto the canvas  
    or  
    b) null if the context ID isn't supported.  
    
    As argument we pass the string "2d" when calling the *getContext()* method. *"2d"* is the context ID. The value returned is the *CanvasRenderingContext2D* object.  

    It also provides two properties, namely: width and height. They're self explanatory.

> Note: By default the size of the canvas is 300x150

<pre><code>const context = canvas.getContext("2d")
</code></pre>

> Note: the context ID is case sensitive.

- The *CanvasRenderingContext2D* interface provides the *fillRect()* method to draw a rectangle. It requires four arguments:  
    a) x: the x-axis coordinate  
    b) y: the y-axis coordinate  
    c) width: the rectangle's width  
    d) height: the rectangle's height  

> Note: The point P(x, y), if it equals to P(0, 0), is located at the top left corner inside the canvas. Width's positive values are to the right, negative to the left. Height's positive values are down, and negative are up.


<pre><code>context.fillRect(0, 0, canvas.width, canvas.height)
</code></pre>

- What we get is a canvas with a default color set to #000, with a width set to 300, and height set to 150. But we can change the colour. To do that, before calling the *fillRect()* function, we have to change the *fillStyle* property. Let's do it!

<pre><code>
/* 
Add this before invoking fillRect(). 
Otherwise, it wouldn't work.
You can use any CSS colors.
*/
context.fillStyle = "tomato"
</code></pre>

Here's the final result:

![tomato rectangle](/../../../assets/images/rectangle.png)

### Challenge

1. Experiment changing the width, height, and fillStyle attributes and see what happens.
2. Experiment changing the arguments of fillRect() and see what happens.
