# CSS

## Contents

* [Properties Reference](#properties-reference)
* [Selectors](#selectors)
* [Responsive Design](#responsive-design)
  * Media Query
  * Flexbox
  * Grid
---

CSS (Cascading Style Sheets) is a language used to interact with and style HTML, changing the way it looks according to a series of rules. CSS is what makes websites look nice.

CSS can be applied to HTML in a variety of ways:

* The _style_ attribute `<h5 style="color:blue;text-align:center;"></h5>`. The semicolon-separated CSS properties passed to _style_ will be applied to whatever the tag contains.
* The `<style></style>` tags. This is a useful paradigm to use when reusing the same styling many times throughout a page. The properties listed will apply to all of the tags that are listed.
* A separate .css file: add `<link rel="stylesheet" href="path/to/styles.css">` to the header, and move the CSS code (same format as used inside the `<style></style>` tags). This is often an even better paradigm because it separates two distinctly different things: structure (HTML) and style (CSS), while also being easier to manage and read.

## Properties Reference

There are lots of CSS properties that can be used in a lot of different ways. Check out the [extensive documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) for more information.

Those properties that take arguments in pixels often can take a percentage or simply auto.

* `color: blue`, `color: #0c8e05` can be 1 of ~140 named colors, or a hexadecimal value that represents an RGB value
* `text-align: left` aligns text to left; other possible arguments are center, right, or justify
* `background-color: teal` sets the background to a color, which is the same format as the color property
* `height: 150px` sets the height of an area, in this case to 150px
* `width: 150px` sets the width of an area, in this case to 150px
* `margin: 30px` sets the margin around all four sides of an area, in this case to 30px. Can also be broken up into margin-left, margin-right, margin-top, and margin-bottom
* `padding: 20px` sets the padding around text inside an area. Can be broken up the same way as margin
* `font-family: Arial, sans-serif` sets the font family to be used. A comma-separated list provides alternatives in case a browser doesn’t support a specific font. Generic families such as sans-serif will use browser defaults
* `font-size: 28px` sets the font size
* `font-weight: bold` sets the font weight to quality, a relative measure (lighter), or a number (200)
* `border: 3px solid blue` sets a border around an area.

## Selectors

CSS selectors are used to select different parts of a website to style in particular ways.

Select `h1` and `h2`
```css
h1, h2 {
    color: red;
}
```

Select all `li` that are descendants of `ol` (not necessarily immediate descendants)
```css
ol li {
    color: red;
}
```

Select all `li` that are immediate children of `ol`
```css
ol > li {
    color: red;
}
```

Select all `input` fields with the attribute `type=text`
```css
input[type=text] {
    background-color: red;
}
```

Select all `button`s with the pseudoclass `hover`. A ‘pseudoclass’ is a special state of an HTML element. In this example, the state is whether or not the cursor is hovering over a button.
```css
button:hover {
    background-color: orange;
}
```

Select all `before` pseudoelements of the element `a`. A ‘pseudoelement’ is a way to affect certain parts of an HTML element. In this example, the `before` selector applies `content` with its included styling before the contents of all `a` elements. \21d2 is a hexadecimal value for a Unicode icon, which can represent symbols like emoji.
```css
a::before {
    content: "\21d2 Click here: ";
    font-weight: bold;
}
```

Select all `selection` pseudoelements of the element `p`
```css
p::selection {
    color: red;
    background-color: yellow;
}
```

## Responsive Design

Responsive design is the idea that a website should look good regardless of the platform its viewed from.

In order to interact with the screen size, the following must be included in head: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.
_viewport_ is the visible area on which the screen is being displayed. _content_ refers to the entire webpage the width of which is being set to device-width.

There are multiple ways to achieve this:

* Media Query

`@media` is a media query, which means the following CSS will be applied only in certain situations, namely, when the webpage is being printed. `.screen-only` is a class selector which identifies what content we want to be print only.

```css
<style>
    @media print {
        .screen-only {
            display: none;
        }
    }
</style>
<body>
    <p class="screen-only">This will not appear when printed</p>
</body>
```

When the width of the screen is at least 500px, the background color of `<body>` will be red, while if it is less than 499px, the background color of `<body>` will be yellow.

```css
@media (min-width: 500px) {
    body {
        background-color: red;
    }
}
@media (max-width: 499px) {
    body {
        background-color: yellow;
    }
}
```

* Flexbox

Allows for the reorganization of content based on the size of the viewport.

By setting `display: flex` and `flex-wrap: wrap`, content will wrap vertically if necessary, so no content is lost when the width of the screen is shrunk.

```css
.container {
    display: flex;
    flex-wrap: wrap;
}
```

* Grid

By setting `display: grid`, all the different characteristics of a grid layout can be used to format content. In particular, when defining `grid-template-colummns`, the final column can be set to `auto`, filling up however much screen space may be left. If multiple columns are set to `auto`, they will equally share the remaining space.

```css
.grid {
    display: grid;
    grid-column-gap: 20px;
    grid-row-gap: 10px;
    grid-template-columns: 200px 200px auto;
}
```
