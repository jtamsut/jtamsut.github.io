# Mastering the Fundamentals of Cascading Style Sheets

Cascading Style Sheets (CSS) is a <b>*language*</b> that allows you to programmatically specify how elements on a web page appear and how they are arranged. CSS allows a web developer to build <b>responsive</b> web applications and separate out a document's content from its presentation. A responsive web application is one that provides the "optimal" viewing experience across a wide range of devices with different screen sizes and software systems. By "optimal" I mean a viewing experience that is intuitive and aesthetically pleasing to the user.

https://www.smashingmagazine.com/mastering-css-principles-comprehensive-reference-guide/

TODO: Provide a more comprehensive descriptin of all that CSS can do. CSS allows a front end web developer to specify the color of some element on a web page as well as create animations and change the 2-dimensional and 3-dimensional orientation of elements on a web page.

## CSS Basics

Fundamentally, what CSS does is identify a piece of HTML it wants to apply a <b>style</b> to.
In CSS you specify what HTML element you want a style applied to using a selector. The element specified by the selector has its style specified by a key-value pair. The key is called a <b>property</b> and the value is called a <b>value</b>. Together, the property and value form a valid CSS <b>declaration</b>.

![](https://developer.mozilla.org/@api/deki/files/6164/=css_syntax_-_declaration.png)


It should be noted that each property has a finite number of values specified by the formal grammar of the CSS language. Properties and values are case sensitive. A declaration plus a selector is called a <b>ruleset</b>:

```css
.cat {
  display: block;
}
```

Invalid (syntactically incorrect) CSS rulesets are simply ignored by the browser. Stylesheets are read from top to bottom. If two rulesets with equal specificities apply a style to the same element, the style closer to the bottom of the stylesheet will override the first style.

TODO: Provide an example of this.

> <b>How to link a style sheet to an HTML file</b><br>
In order to manipulate how elements appear on a page you must have elements to manipulate in the first place! Place this in the head of an HTML file to link a CSS stylesheet your HTML file: `<link rel="stylesheet" href="./path/to/stylesheet.css">`

## CSS Selectors

Selectors provide you with the ability to specify which HTML elements you want to apply certain styles to. There are different types of selectors that allow you to select HTML elements to style in different ways:

* Basic Selectors:
  * Type selectors (e.g., `h1 { color: red; }`)
  * Class selectors (e.g., `.dog { color: red; }`)
  * ID Selectors (e.g., `#dog { color: red; }`)
  * Universal selectors (e.g., `* { color: red; }`)
  * Attribute selectors
* Combinators:
  * Adjacent sibling selectors (`+`)
  * General sibling selectors (`~`)
  * Child selectors (`>`)
  * Descendant selectors (e.g., `A B`)
  * Pseudo-elements
  * Peudo-classes

#### Basic Selectors

Basic selectors allow you to specify an HTML element to style based on its id, class or type. For example, the declaration below selects the HTML element with an `id="dog"` and makes its font color blue.

`#dog { color: blue; }`

The universal selector (`*`) matches any element type.

#### CSS Combinators

A CSS selector can contain more than one basic selector. These selectors can be combined with combinators. A combinator is an *operator* that combines two or more *selectors*.

<table>
<tr>
<td>
<b>Combinator Name</b>
</td>
<td>
<b>Combinator Syntax</b>
</td>
<td>
<b>Description of Combinator Does</b>
</td>
</tr>
<tr>
<td>
Adjacent Sibling
</td>
<td>
A + B
</td>
<td>
Will select the first sibling of type B that follows A.
</td>
</tr>
<tr>
<td>
General Sibling
</td>
<td>
A ~ B
</td>
<td>
This selects all B elements that follow A. A and B must share a common parent.
</td>
</tr>
<tr>
<td>
Child
</td>
<td>
A > B
</td>
<td>
Selects all elements of type B that are direct children of A.
</td>
</tr>
<tr>
<td>
Descendant
</td>
<td>
A B
</td>
<td>
Selects any ancestors of A that have a type B
</td>
</tr>
</table>

For practice with CSS selectors I just [this](http://flukeout.github.io/) awesome multi-level game.

#### CSS "and" Notation

If a single HTML element has multiple classes defined on it or a class and an id defined on it you can use the following notation to select the element:

* `.A.B`
* `.B.A`
* `#A.B`
* `.B#A`

This notation selects `class="A"` and `class="B"` or `id="A"` and `class="B"`.

### When to Use a .class and When to Use an #id

https://css-tricks.com/the-difference-between-id-and-class/

### 3D CSS
https://desandro.github.io/3dtransforms/docs/perspective.html

### Flexbox

### CSS Box Model

Read this: https://www.w3.org/People/Bos/DesignGuide/toc.html

http://www.standardista.com/category/css3/

### CSS Performance

### At-Rules

An <b>at-rule</b> is a CSS statement beginning with an `@`. The regular syntax for at-rules is as follows:

```
@[KEYWORD] (RULE);
```

#### CSS Layout

Every element has a default display value depending on what type of element it is. The default for most elements is usually `block` or `inline`.

A `<div>` is the standard block-level element. A block-level element starts on a new line and stretches out to the left and right as far as it can.

```css
#A {
  box-sizing: border-box;
}
```

When you set `box-sizing: border-box;` on an element, the padding and border of that element no longer increase its width.


Floats are removed from the document flow.

#### Block Formatting Context

http://yuiblog.com/blog/2010/05/19/css-101-block-formatting-contexts/


#### Understanding the clearfix hack

http://fuseinteractive.ca/blog/understanding-humble-clearfix#.V1dBQ5MrJTa
### CSS Animations


https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions


<b>CSS transitions</b> give you  a way to control animation speed when changing CSS properties. You can specify transitions to occur at time intervals that follow an acceleration curve.

Animations that involve transitioning between two states are often called implicit transitions as the states in between the start and final states are implicitly defined by the browser.

CSS transitions let you decide which properties to animate (by listing them explicitly)

<!--
# CSS Reset

A CSS Reset is a short, often compressed set of CSS rules that resets the styling of all HTML elements to a consistent baseline.

## CSS Selectors
### Tag, id and class selectors
### Pseudo classes

CSS is applied to elements through <b>selectors</b>. A selector is a specification of an element you want to style. This section will cover the most common selectors.

Let's create some table based on some illustrations here

##### Element

##### id
##### class

```
Table of Contents
I. Introduction
II. CSS Basics
III. Selectors
IV. Specificity
Have an example that clearly illustrates specificity of class, ids, universal selector (*), class, inline styles, !
important
V. Preprocessors
VI. Responsiveness
Read this: http://www.standardista.com/css3/css-specificity/

INCLUDE SPECIFISHITY DIAGRAM

How to make a triangle in CSS

V. Positioning
VI. Colors
```



You can combine a class selector with "dot" notation.

`ul.dog` will select of all the `ul` elements that have the class `dog`.



UI Pseudo Class
:target
:root
##### Attribute Selectors
https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors

## A Melange of CSS Properties and their Values



allows web developers to control the way parts of a web document are arranged as well as their appearance. Knowing CSS well is a fundamental skill that all good full stack web developers should know well

# CSS Specificity
# Using id's once and classes multiple times
# Floats
# Positioning
# Selectors
There are five position properties:
1. fixed
2. relative
3. absolute
4. static
5. initial
6. inherent

What does display do?
id's have specificity over classes

Contenteditable: https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_Editable

Talk about pseudo-classes

nth pseudo-class
can specify odd, even or an equation
# Cross browser compatibility

CSS Reset: http://cssreset.com/what-is-a-css-reset/

What is the difference between classes and IDs in CSS?
What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
Describe Floats and how they work.
Describe z-index and how stacking context is formed.
Describe BFC(Block Formatting Context) and how it works.
What are the various clearing techniques and which is appropriate for what context?
Explain CSS sprites, and how you would implement them on a page or site.
What are your favourite image replacement techniques and which do you use when?
How would you approach fixing browser-specific styling issues?
How do you serve your pages for feature-constrained browsers?
What techniques/processes do you use?
What are the different ways to visually hide content (and make it available only for screen readers)?
Have you ever used a grid system, and if so, what do you prefer?
Have you used or implemented media queries or mobile specific layouts/CSS?
Are you familiar with styling SVG?
How do you optimize your webpages for print?
What are some of the "gotchas" for writing efficient CSS?
What are the advantages/disadvantages of using CSS preprocessors?
Describe what you like and dislike about the CSS preprocessors you have used.
How would you implement a web design comp that uses non-standard fonts?
Explain how a browser determines what elements match a CSS selector.
Describe pseudo-elements and discuss what they are used for.
Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
What does * { box-sizing: border-box; } do? What are its advantages?
List as many values for the display property that you can remember.
What's the difference between inline and inline-block?
What's the difference between a relative, fixed, absolute and statically positioned element?
The 'C' in CSS stands for Cascading. How is priority determined in assigning styles (a few examples)? How can you use this system to your advantage?
What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
Have you played around with the new CSS Flexbox or Grid specs?
How is responsive design different from adaptive design?
Have you ever worked with retina graphics? If so, when and what techniques did you use?
Is there any reason you'd want to use translate() instead of absolute positioning, or vice-versa? And why?
-->

CSS Methodologies: http://getbem.com/introduction/

SMACCS
BEM

## Flexbox

http://philipwalton.github.io/solved-by-flexbox/

http://www.skilledup.com/articles/25-css-interview-questions-answers

http://fuseinteractive.ca/blog/understanding-humble-clearfix#.V1c-ApMrJZp

Respsonsive Design: http://www.creativebloq.com/rwd/responsive-web-design-tutorials-71410085

SMASHING MAGAZINE RESOURCES

# Generated Content

Computer graphics: https://courses.edx.org/courses/course-v1:UCSDx+CSE167x+2T2016/courseware/Unit_1/L4/
