# HTML and CSS Coding Standards

### Standards for developing clean, durable, sustainable and modular HTML and CSS.

This is not a guide, but a set of standard operating procedures for ensuring clean, readable, efficient and maintainable code.

The need for such standards is key for consistent development, especially as codebases grow in length and complexity. Stylistically speaking, the code in any codebase in which multiple others are also contributing, should look the same regardless of who wrote it. This consistency on its own promotes a healthy workflow and has the potential to reduce the number of coding issues. It is, therefore, important to enforcing standards as such at all times.


----------


## Table of contents

* [HTML](#html)
    * [Syntax](#html-syntax)
    * [Semantic Markup](#semantic-markup)
    * [Attribute order](#attribute-order)
* [CSS](#css)
    * [CSS syntax](#css-syntax)
    * [Selectors and hierarchy](#selectors-and-hierarchy)
    * [Classes](#classes)
    * [Shorthand](#shorthand)
    * [Typography](#typography)
    * [Declaration order](#declaration-ordering)
    * [Prefixed properties](#prefixed-properties)
    * [Single declarations](#single-declarations)
    * [Intelligibility](#intelligibility )
    * [Structure pattern](#structure-pattern)
* [Acknowledgments](#acknowledgments)

----------
## HTML

### HTML syntax

* Use soft-tabs with 4 spaces
* Nested elements should be indented once for each nesting level (4 spaces)
* Always use double quotes for attributes

If **HTML5** is used, additionally (and there is no reason not to) these should apply:

* Do not include a trailing slash in self-closing elements
* Enforce standards mode by including <code><!DOCTYPE html></code> at the beginning of every HTML page


**Example:**

```html
<body>
    <img src="images/hi-there.png" alt="Hi there">
    <h1 class="hi-there">Hi there, world!</h1>
</body>
</html>
```

----------

### Semantic markup

Write semantic code. Use tags appropriate for each instance depending on its intended use. Ensure that the parts of the content have a semantic function. In the similar manner as one would not include additional extraneous markup, no semantically appropriate markup should be left out. It is important to keep in mind that the screen is only one output device. By writing semantic code we also promote for client-friendliness, accessibility and SEO.

Exceptions to enforcement of writing semantic markup code should be considered typically only when markup is going to be overly complex with overwhelming number of intricacies, which is not typically a scenario that one should face on a regular basis. In these rare cases, it may be more appropriate to avoid such semantic complexity in favor of non-semantic simplicity. But it's important to tread lightly for these situations as well, and in all cases the holistic vision of what the web page is supposed to accomplish, from a screen to the search engine index, should always be at the forefront of markup decisions.

----------

### Attribute order

HTML attributes should come in this particular order for easier reading of code.

* id
* class
* data-*
* for
* type
* href

**Example:**

```html
<a id="unique-name" class="some-class" data-tracker="track-this" href="some-page.html">Example link</a>
<label for-"hi-world">Hi world</label>
<input id="hi-world" type="text" href="hi-world.html">
```


----------



## CSS

### CSS syntax

* Use soft-tabs with 4 spaces
* When grouping selectors, each individual needs to be on its own line
* One space is required before the opening brace of declaration blocks
* Closing braces of declaration blocks need to be on their own line
* After the ":" of each property a single space needs to be added for visual separattion between property and value 
* Each declaration needs to be on its own line
* All declarations need to be closed with a semi-colon (;)
* Comma-separated values need to include a space after each comma
* Omit the leading zeros and avoid spaces after commas in RGB or RGBa colors
* All hex values need to be in lowercase (e.g., <code>#efefef</code> instead of <code>#EFEFEF</code>)
* Whenever possible use shorthand hex values (e.g., <code>#fc0</code> instead of <code>#ffcc00</code>)
* Attribute values in selectors need to be wrapped in double-quotes (e.g., <code>input[type="text"]</code>)
* Do not specify units for zero values (e.g., <code>padding: 0;</code> instead of <code>padding: 0px;</code>

**Example:**

```css
.selector,
.selector-secondary,
.selector[type="text"] {
    padding: 15px;
    margin: 0 0 15px;
    background-color: rgba(0,0,0,.5);
    box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

----------

### Selectors and hierarchy 

* Use IDs sparingly to identify sections of a page on a high level
* IDs need to be completely unique; no two elements on a single page should have identical IDs
* Do NOT scope IDs; they should be unique enough to not need it
* Do NOT add classes to every single element, but only when the element needs styling or in some cases, when the semantic identification of the element tag itself is not enough to clarify its purpose.
* Keep classes with generic default styling unscoped to allow for custom overrides for various instances of its use that require different treatment 
* Keep selectors short and limit the number of elements in each selector
* Scope classes to the closest parent when many elements inside a parent require styling (this is the opposite strategy of using prefixed classes; see context for which one to use)
* Avoid unnecessary multi-level inheritance: <code>.page-container #stream .stream-item .tweet .tweet-header .username { ... }</code>

**Example:**

```css
#header { ... }
.comments { ... }
.facebook-icon { ... /* default icon */ } 
.comments .facebook-icon { ... /* override icon */ }
.comment-header .gravatar { ... }
```

----------

### Classes

* Class names should all be in lowercase and use dashes for text separation (no underscores or camelCase)
* Avoid arbitrary abbreviations unless it's easy understandable/common nomenclature 
* Class names should be as succinct as possible without losing meaningful references
* Use meaningful, structural or purposeful names over references to intrinsic specific styling reference
* When limited number of elements require styling with a parent, prefix classes based on the closest parent ID or class

**Example:**

```css
.btn { ... }
.question { ... }
.answer   { ... }
.answer-rating { ... }
```

----------

### Shorthand

Certain styles can be written in shorthand. Whenever possible use this shorthand format for simplification and brevity. For example, instead of specifying <code>margin-top: 5px; margin-right: 10px; ...</code> do this: <code>margin: 5px 10px 15px 20px; /\*top right bottom left\*/</code> following the clockwise pattern.

**Example:**

```css
.selector {
    /* Padding and Margins */
    /* [top] [right] [bottom] [left] */
    padding: 0 5px 10px 15px;
    margin: 0 5px 10px 15px;
    
    /* Borders */
    /* [width] [style] [color] [left] */
    border: 1px solid #333;
    
    /* Fonts */
    /* [style] [variant] [weight] [size]/[line height] [font family]  */
    font: italic small-caps bold .75em/1.25em "Helvetica Neue", sans-serif;
    
    /* Backgrounds */
    /* [image] [repeating?] [vertical position] [horizontal position] [color] [attachment] */
    background: url(test.png) no-repeat 10px 50px #eee fixed;
    
    /* Rounded Corners */
    /* [all corners] */
    /* [top-left, bottom-right] [top-right, bottom-left]  */
    /* [top-left] [top-right, bottom-left] [bottom-right]  */
    /* [top-left] [top-right] [bottom-right] [bottom-left]  */
    border-radius: 3px 6px 9px 12px;
    
    /* Lists */
    /* [list-style-image] [list-style-position] [list-style-type] */
    list-style: url(bullet.gif) outside;
    list-style: inside disc;
    
    /* Transitions */
    /* [transition-property] [transition-duration]  [transition-timing-function] [transition-delay] */
    -webkit-transition: height 0.3s ease-out,
                        opacity 0.3s ease 0.5s;
       -moz-transition: height 0.3s ease-out,
                        opacity 0.3s ease 0.5s;
        -ms-transition: height 0.3s ease-out,
                        opacity 0.3s ease 0.5s;
         -o-transition: height 0.3s ease-out,
                        opacity 0.3s ease 0.5s;
            transition: height 0.3s ease-out,
                        opacity 0.3s ease 0.5s;
}
```

----------

### Declaration ordering

Declarations that are closely related should be grouped together, with box model and positioning closest to the top, followed by typography and low level visual properties.


**Example:**

```css
.element-class {
    /* Box-model */
    display: block;
    float: left;
    width: 50px;
    height: 50px;

    /* Positioning */
    position: absolute;
    top: 0;
    left: 0;
    z-index: 50;

    /* Typography */
    font: normal .75em/1.25em "Helvetica Neue", sans-serif;
    color: #333;
    text-align: center;

    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;

    /* Misc */
    opacity: 1;
}
```

----------

### Typography

There are various units used to size fonts: points, pixels, ems, and percentages. Points are best used for the print medium. Pixels have been the long-running standard for font sizing. However, with the incredible growth of devices with various different screen sizes, a reassessment of the standard has seen pixels as a less optimal alternative. Responsive design strategies that employ relative sizing to allow for easy font scaling have made em and percentage-based sizing far more appealing.

In a comparison between these two unit types, ems tend to scale more accurately as they are intended, therefore font sizing is to be done in ems. Also, except for cases where extreme redundancy would occur, shorthand CSS should be used. See 

**Example:**

```css
.element-class {
    font: normal .75em/1.25em "Helvetica Neue", sans-serif;
}
```

----------

### Prefixed properties

Contrary to the general standards, when using vendor prefixed properties, indentation needs to be such that the style value line up vertically for visual clarity and easy editing.

**Example:**

```css
.class {
    -webkit-border-radius: 5px;
       -moz-border-radius: 5px;
            border-radius: 5px;
}
```

----------

### Single declarations

Another exception to the general standards involves single declarations,  several rules are needed with only one declaration for each. In these instances line breaks should be removed between each rule, only to be added back when longer rules follow.

**Example:**

```css
.class1 { width: 5px; }
.class2 { width: 6px; }
.class3 { width: 7px; }

.class55 {
    display: block;
    width: 10px;
    height: 5px;
}
.class60 { height: 10px; }
.class61 { height: 15px; }
.class62 { height: 20px; }
```

----------

### Intelligibility

Make sure that code is intelligible, easy to read, is descriptive and accessible. To this end, it is important to use good descriptive comments throughout the code. Avoid reiterating names in comments, but instead concentrate on relaying context, scope and purpose.

**Example:**

```css
/* Element wraps masthead .header-title and .header-nav */
.masthead-wrapper {
    ...
}
```

----------

### Structure pattern

* Organize sections of code by section, component or feature
* Adopt a custom consistent commenting style
* For multiple CSS files, organize them by section, or feature if appropriate

----------

## Acknowledgments

These coding standards were written by Arthur Khachatryan. Please see the license for reprint and duplication needs. In short, this document may be duplicated in internal environments and for non-commercial use so long as proper credit is given. For other commercial purposes please contact me with more information.

**Arthur Khachatryan**  
[www.aspiremedia.net](http://aspiremedia.net)    
[on Twitter](https://twitter.com/aspiremedianet)  
[on LinkedIn](http://www.linkedin.com/pub/arthur-khachatryan/1/885/ab5/)

----------


### Enjoy!
