---
layout: default
title: CSS
nav_order: 3
permalink: Tutorials/CSS
parent: Tutorials
has_toc: true
---

# Cascading Style Sheets Introduction
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

### CSS
Every house has an architecture style, or a color scheme. All the rooms would follow that scheme according to the what the house should look like. Wouldn't it be nice to define that in once place? If we have the scheme defined in some place, all the pages we create with HTML would have that style without  specifying them repeteadly. This is where CSS comes in. It adds colors, fonts, spacing and styles of the elements used in HTML.

- **Selectors**: CSS selectors target HTML elements for styling. They can be simple (like element selectors), class-based (using `.class`), or ID-based (using `#id`).
- **Box Model**: CSS box model comprises content, padding, border, and margin, influencing element layout.
- **Styling Properties**: CSS properties like `color`, `font-size`, `background`, `margin`, and `padding` offer control over appearance.
- **Selectors Specificity**: Specificity determines which styles apply when multiple rules target the same element.

When we want to add CSS styling to any of our HTML elements, to select the specific HTML elements we want to style, there are a few different type of CSS selectors we can use

#### **Element Selectors**

Element selectors are the most basic type of CSS selector. To use an element selector, we just get the tag that we want to apply our CSS to

Say we want to style the tag below

`<h1>Hello World!</h1>`

To use an element selector, we just get the tag `h1` and apply our CSS styles!

```
h1 {
    (insert styles here)
}
```

#### **ID Selectors**

You would use id selectors if you only want to apply CSS styling to one HTML element

To use an id selector, in your HTML, you use the id attribute

`<h1 id="any_id">Hello World!</h1>`

And in your CSS, you would use the `#` tag to select the element with a certain id

```
#any_id {
    (insert styles here)
}
```

Only one element can have a certain id, you cannot have two elements with the same id

#### **Class Selectors**

Class selectors allow you to apply the same style attributes to multiple elements

In your HTML, you would assign the class attribute to the tags you want to have the same style

From the below example, we see that there are multiple `<p>` tags

Say we want to style the first two `<p>` tags and not the third one. We can assign them the same class, in this case, "paragraph"

```
<h1>Hello, my name is Deadpool!</h1>
<p class="paragraph">I am an antihero, I have done good but have also done bad</p>
<p class="paragraph">I am played by Ryan Reynolds!</p>
<p>The end!</p>
```

To add style attributes to a class, we use the `.` tag instead

```
.paragraph {
    (insert styles here)
}
```

#### **Basic Style Attributes**

There are many different types of style attributes, but we'll lay out some basic ones.

When writing any CSS code, you have to write it like this:

![CSS basic style example](https://res.cloudinary.com/practicaldev/image/fetch/s--Uvc4p-Vs--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/edojfcbz6sr7j0b2l6v1.jpg)

The ones below are style attributes you would use for **text**

**font-size**: changes the size of the text (font size is based on pixels, or px)

`font-size: 16px;`

**color**: changes the color of the text

`color: blue;`

**font-family**: give a specific font to selected text, there are many different font styles out there (the default is sans-serif)

`font-family: sans-serif;`

**text-align**: controls how text is aligned on a page, can be aligned left, right, or center

`text-align: center;`

For a full list of CSS properties, visit the link below:

[All CSS properties](https://www.dofactory.com/css/properties)

_______________________________________________________________

[Previous: HTML](HTML){: .float-left .v-align-text-top}
[Next: JavaScript](JS){: .float-right .v-align-text-top}