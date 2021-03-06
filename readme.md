---
title: CSS-Layout
type: Lesson
duration: "2:00"
Created:
    Campus: GA DC/GA Boston
    Creator: Jesse Shawl
    Contributors: Lauren Fazah, Rachel S., Brian Berzellini, Matt Brendzel, Json Wharff
Edited:
    name: Eric Stermer
    city: PVD
competencies: Front-end frameworks
---

# CSS Layout

### Learning Objectives
- Link to files using their paths
- Position elements using relative, fixed, & absolute positioning
- Describe floats, & clearfix
- Understand the difference between block, inline, & inline-block elements
- Use flexbox to create a layout
- Practice using a custom grid system
- Describe the difference between normalize and reset and know what they do

### Framing 

Layout with CSS is hard.

There are over 500 CSS properties. It's impossible to memorize them. The key is to just get an idea of what you can accomplish with CSS, and then know what to Google.

There are also many frameworks and libraries that can aid your layout development, each with their own pros and cons. The goal as a developer is to become familiar with each to use them as you need.

# Box Model (10)

(open a website and the chrome dev tools)

In addition to setting an element's `height` and `width`, elements have three
other properties that explicitly control spacing:

1.  'Border' sets a perimeter around an element. In addition to specifying a color
and a particular type of border, you can also specify a thickness.
2.  'Margin' specifies spacing between the outside of an element's border and any
adjacent elements.
3.  'Padding' specifies spacing between the inside of an element's border and the
contents of that element (which includes `height` and `width`!)

Together, these attributes form _the box model_, a way of describing the space
taken up by an element.

_Note: an element's size is determined by its content's height and width.Border, margin, and padding add to that size._
_To calculate those into the element's size, the element's CSS [`box-sizing`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) property should be changed from the default `content-box` to `border-box.`_
![Box Model](https://mdn.mozillademos.org/files/8685/boxmodel-3.png)

Every one of these attributes, including `height` and `width`, can be specified
in the following terms:

-   `px` : fixed number of pixels
-   `%`  : size is relative to element that contains it ("parent"). As a value of
`height`, `%` is relative to the parent's `height`, but for every other
dimension, `%` is relative to the parent's `width` value.
-   `em` : ties dimensions to *font size* - one `em` is the width of the letter 'm'.
For all dimensions except `font-size`, `em` will refer to the font size of the
element; as a value for `font-size`, `em` refers to the font size of the
*parent*

# You do: Layout Reading (30)

Take your time reading [learn layout](http://learnlayout.com/)

### Things to focus on:
 - elements with diferent preset display styles
 - margin: 0 auto
 - max/min-width/height
 - position
 - float + clear + hack
 - media queries
 - CSS Framworks llinks at the end
 
Notice there was information about flex-boxes, we will cover that later

### Questions (10)

# Layout Comparison (10)

Adapted from [Karen Menezes excellent blog post](http://blog.karenmenezes.com/2014/apr/13/floats-inline-block-or-display-table-or-flexbox/)

#### Floats
**Advantages**
- Most popular way to lay things out; most grid frameworks follow this.
- Everyone's aware of float bugs due to the popularity of floating, and there are well documented ways to overcome them.

**Disadvantages**
- Need to be cleared. Can be quite painful if you're changing widths at 2-3 media query breakpoints, because the floats will need to be cleared that many times.
- No vertical centering
- No equal heights
- No source order independence

**Use for:**
- Large layout blocks that don't need equal heights and vertical centering

---

#### Inline Block
**Advantages**
- Vertical centering is most useful for some layouts
- Don't need to be cleared. Useful for complex layouts when breakpoints need to be changed at more than a couple of screen widths. You can see this demo to understand how advantageous inline-block can be, for this use case.

**Disadvantages**
- Suffers from inherent whitespace, which will disturb your grid calculations. You can't make a two column grid with the left being 30% and the right being 70%, with display: inline-block, because the whitespace will break the grid and push the second column to the next line. There are ways around this. The easiest is if you're using lists with the HTML5 doctype, because you don't need to add closing list tags and this removes the whitespace bug. See this article for more.
- No equal heights
- No source order independence

**Use for**
- When you require vertical centering, but not equal heights with CSS.
- When you want to avoid clearing your floats at different breakpoints.
- When you can get around the whitespace issue, without driving the rest of your dev team crazy.
- When you can get around the whitespace issue, whilst ensuring that your templating language does not try to add closing li items. That's not cool, bro.
- When you're using list items for layout and don't need a closing li tag, inline-block truly shines.

---

#### Flexbox
**Advantages**
- Source order independence. Could be of tremendous value for responsive layouts and eliminates the need for JS for this.
- Vertical centering
- Equal heights
- Flex boxes move along interchangebly the X and Y axis, with such ease, that you can really change things around with a couple of properties.
- Boxes grow and shrink, can be columns or rows, fit to the available space however you wish to declare this.
- There are multiple ways to do the same thing with flexbox.

**Disadvantages**
- Syntax is initially unintuitive. You spend the first few hours looking at demos saying WOW, followed by WTF.
- Lots of vendor prefixes, with a different syntax for older IE and Webkit. Use something like Autoprefixr to work around this. Or write some mixins. Or do something..
- Doesn't work on IE9. If you don't have to support IE9, you're fine.
- Reports of the older syntax impacting performance. I wouldn't care too much about this honestly, especially if you were using JS to do the things Flexbox now can...

**Use for**
- You can already start using it for vertical centering, if you don't need things to look the same on IE9.
- If you don't need IE9 support, it's perfect for source order independent layouts, equal heights.
- I would highly recommend using it for personal projects.
- App layouts where things need to stretch and squish. Flexbox really shines here.

#### Example / Play with code (20)

##### Setup
 - go into your wdi folder
 - `mkdir css-layout` and `cd` into it
 - create 2 files `touch index.html style.css`
 - open folder in atom with `atom .`
 - open index.html and create the html boiler plate
 - include the link the css in the html head

 - Lets create some `<div>`'s 
    ```
     <div></div>
     <div></div>
     <div></div>
     <div></div>
    ```
  
  - Go into the css file and access the `<div>` element and giv them each a height, widths, and a background-color
  ```
  div {
    height: 200px;
    width: 200px;
    background-color: green;
  }
  ```
  
  - Now lets see what happens when we add float to our div.
  - Now try playing with the display.
  - Now lets use display flex  


## Break (5)

# You Do: Flex Froggy (20)

Lets practice layout with flex-boxes. This is a just another way to make layout a little easier.

It is built into CSS3.

A great resource to learning flex-boxes is this [flexbox frog game](http://flexboxfroggy.com/).

It is a simple 20 something challenge game that touches on each flex method with great visuals.

# You Do: Hyrule Potion Shop (20 / 70)

Please count off again, and complete this exercise:

Google is your friend, please look up things you don't know!
These might also help:

- [css-tricks: complete guide to flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [scotch.io: visual guide to flexbox](https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties)
- [fluid layouts with flexbox](http://webagility.com/posts/fluid-layouts-done-right-with-flexbox)

Please clone and complete the [hyrule potion shop](https://github.com/ga-wdi-exercises/hyrule_potion_shop) exercise

### Other layout methods to touch on

# Grids

For complicated layouts it is often advantageous to create a set of classes that control layout properties that can be applied to elements to position them. This enables positioning properties to be reused instead of having to create css rules ad-hoc for every element that needs to be moved. 

Many `css frameworks` come with a grid system. Almost all of these systems use some combination of columns with percentage widths that are floating or inline-block.

[here's an article on building one with flexbox](https://philipwalton.github.io/solved-by-flexbox/demos/grids/)

[here's a link to many examples using grids](http://gridbyexample.com/examples/)

## Why use a CSS grid? (5 / 100)

### Structure
* Grids are a simple way to apply layout to a webpage. A better layout improves the user experience.
* Grids help avoid stressful CSS debugging by starting out on the right foot.

### Reusability
* Grids make the layout process easier because of resusable, semantically-named "utility classes" (i.e., a library of CSS class selectors).
* Grids aren't limited to a particular project. We can apply them to pretty much everything we do.
* Grids are highly customizable. You can really make them your own.

_Even if you don't use a grid system, these concepts will translate across other layout problems._

### Basic components of a grid (5 / 105)

#### Rows
* The highest-level component of a grid.
* Comprised of columns.

#### Columns
* Contain and separate site content.

#### Gutters
* Provides spacing between our columns. Optional, but useful.

## Break (5-10)

### Clearfix (10 / 125)

Our grid relies on being able to float columns. These columns will most likely contain content of various sizes.
* We need to make sure each piece of content is constrained to its respective row and column containers

Let's [illustrate this problem](http://codepen.io/adambray/pen/GoWobo?editors=110).
* As this code stands, we have a row that contains two squares. But these squares are overflowing out of the row, which appears as a straight black line.

This is where the clearfix technique comes in. Fortunately, it's easy to implement (as long as you don't care about how your site looks in Internet Explorer).

```css
.row {
  overflow: auto;
}
```

Here is a more robust version of clearfix and the one you should use most of the time:
```css
.row:after {
  content: "";
  display: table;
  clear: both;
}
```

[css-tricks all about floats](https://css-tricks.com/all-about-floats/)


### Q. What is Bootstrap, and how do you feel about it? (5 / 130)

> Bootstrap is a CSS *library*: it's a stylesheet you can link to in your HTML, and it provides you with a bunch of classes that you can apply that make things look really nice.

> Many designers sniff at Bootstrap because, they argue, sites that use it all look the same. However, unless you plan on specializing in front-end design, a Bootstrapped site may be better than a site with no CSS, or a site with handmade CSS: it shows that you recognize what your strengths are and are focused on delivering a product, rather than doing things the "right" way.

There are [many other](http://designsparkle.com/bootstrap-alternatives/) 'design frameworks' that are similar to bootstrap

## Browser Styles (10 / 140)

Browsers have default styles for different elements. For example `<body>` tags often have a default margin of ~8px. A `div` element in Chrome will has a height of 18px, in Firefox it's 19.2px. While this difference may be small it does vary. We often start our CSS by overriding, or reseting, some of these default properties:

```css
body {
  margin: 0;
}
```
We can override or work with these default styles on an ad-hoc bassis, simple changing things when they seem appropriate.

#### Reset

An alternative is to use a [CSS Reset](http://meyerweb.com/eric/tools/css/reset/).
To use the reset we can save this into it's own CSS file and link it in our head, or we can copy it into the top of our current CSS file.

- _**Reset removes all built-in styling, essentially provides a blank canvas**_

#### Normalize

Another approach instead of unstyling all of the default properties is to try to work with them. [Normalize CSS](https://necolas.github.io/normalize.css/) seeks to make syles consistent across browsers. Normalize is often linked as file in the project directory, or from a CDN link.

```html
<link rel="stylesheet" href="normalize.css">
/* VS. */
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/4.0.0/normalize.css">
```

- _**Normalize provides a cross-browser starting point with some properties**_

# Outtro (5 / 145)

Remember that Google is your friend. As junior devs, it is impossible to remember everything, especially in a fast changing environment liek coding. There will always be many ways to do the same thing. Find what works for you and your style. All you need to know is what techniques are out there to know what to look for.

### Tools that can help

**[The CSS Validator](http://jigsaw.w3.org/css-validator/#validate_by_input)** is a tool into which you can copy and paste your CSS, and it'll tell you precisely what's wrong with it. We'll be expecting you to validate your CSS during this course.

**The Chrome element inspector** lets you look at a specific element on a page, see exactly which CSS rules are being applied to it, and turn those rules on and off and modify them. It doesn't change your file; refresh the page, and the changes are gone.

## Quiz Questions

- What is the purpose of `flex-box`?
- What does `*` select?
- What does `box-sizing:border-box` do?
- What's the difference between `position:relative`, `position:absolute`, and `position:fixed`?
- What's the difference between borders, margins, and padding?
- What's the difference between an outline and a border?
- How would you apply styles only for screens narrower than 480 pixels?

## Further Reading

- [Shay Howe's HTML/CSS Guide](http://learn.shayhowe.com)
- [LearnLayout.com](http://learnlayout.com/)
  - An great interactive tutorial that details CSS' many properties and quirks.
- [W3Schools CSS Reference](http://www.w3schools.com/cssref/default.asp)
  - Almost every CSS property ever.
- [Mozilla Developer Network CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)
  - Like W3Schools, but in *much* more detail.
- [CanIUse.com](http://caniuse.com/)
  - Search for a CSS property (or HTML, or JS), and it'll tell you on which web browsers it functions.
- [CSS Validator](https://jigsaw.w3.org/css-validator/#validate_by_input)
  - Copy and paste your CSS in here and it tells you what's wrong with it.
- [CSS Tricks Almanac](https://css-tricks.com/almanac/)
  - A list of css selectors and properties
- [CSS Units - em vs px etc](http://kyleschaeffer.com/development/css-font-size-em-vs-px-vs-pt-vs/)

## Additional Resources

- [Codrops](http://tympanus.net/codrops/)
- [Codyhouse](https://codyhouse.co/library/)

