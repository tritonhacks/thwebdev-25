---
layout: default
title: HTML
nav_order: 2
permalink: Tutorials/HTML
parent: Tutorials
has_toc: true
---

# Hyper Text Markup Language Introduction
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

### HTML
If we imagine the web as a house, HTML lays the foundation and blueprint of the house. Essentially its just text It consists of "tags" enclosed in angle brackets, like ``<tag> content here! </tag>``. Tags define structure and content. There are so many different types of tags, from defining lines and headings, links, forms, images and videos down to a simple text as the ones you are reading right now. These tags create a layout of the webpage.

- **Basic Structure**: An HTML document consists of elements enclosed in tags. Key elements include `<html>`, `<head>`, and `<body>`.
- **Content Elements**: HTML offers various elements for content like headings (`<h1>` to `<h6>`), paragraphs (`<p>`), lists (`<ul>`, `<ol>`, `<li>`), links (`<a>`), images (`<img>`), and more.
- **Semantic HTML**: Semantic HTML elements add meaning to your content, improving accessibility and SEO. These elements help browsers and assistive technologies understand and navigate different parts of your website. Don\'t worry too much about these for now!

If you inspect your browser (right click + click `Inspect`), you can see what elements were used to create this website!

### Basic Structure

#### **The `<html>` tag**

The `<html>` tag **wraps everything inside your HTML document.** It serves as the root element of the page.

It also includes a `lang` attribute, which specifies the language of the document. For our purposes, we’ll set it to English (`en`). It looks like this:

```html
<html lang="en">
  <!-- everything else here! -->
</html>
```

#### **The `<head>` tag**

The `<head>` tag represents the set up for our HTML page.

The two main components included in most `<head>` tags are the `<title>` and `<link>` tags.

We use the `<title>` tag when we include a title for our webpage. The content of the `<title>` tag can be seen in your tab at the top! See image below:

![Title Location](../source/assets/images/HTML_title_location.png)

We use the `<link>` tag for when we want to link a CSS stylesheet to our page, making our HTML look pretty!

We will outline the multiple components that every HTML website has:

#### **The `<body>` tag**
The <body> tag contains **everything that will be visible on the webpage**—all the content users will see and interact with, such as headings, paragraphs, images, buttons, etc.

#### HTML Boilerplate
Here’s a simple HTML boilerplate—the starting template for any webpage:
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My First Webpage</title>
  </head>

  <body>
  </body>
</html>
```


### Content Elements

#### **The header tags**

Header tags represent the titles of our HTML.

There are 6 different types of header tags, each varying by size: `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, and `<h6>`. `<h1>` is the largest, while `<h6>` is the smallest.

To use a header tag, you would do:

```<h + "number">(content here)</h + "number">``` (where number is from 1 to 6)

See relative sizes of the headers below: 
![Headers](../source/assets/images/HTML_heading_example.jpeg)

#### **The `<p>` tag**

The `<p>` tag is used for big blocks of text, or paragraphs. We use it when we want to include big blocks of text on our website, like for a blog or article.

```<p>(insert some text here)</p>```

![p tag](https://blog.hubspot.com/hs-fs/hubfs/Google%20Drive%20Integration/Using%20the%20%3Cp%3E%20Tag%20in%20HTML-1.png?width=657&name=Using%20the%20%3Cp%3E%20Tag%20in%20HTML-1.png)

#### **The `<a>` tag**

The `<a>` tag is a tag is used to link other webpages or websites. 

To use an `<a>` tag, you have to specify the href attribute, which is the url that the tag links to.

```<a href="some url">(content here)</a>```

In between the opening and closing `<a>` tags, you insert some text that serves as the link (don\'t keep the parentheses though!). The default blue color text with the underline shows that the text is a link.

#### **The list tags**

There are two types of lists in HTML:

1. ordered lists (aka numbered)
2. unordered lists (aka bullet points)

#### **Ordered Lists**

With ordered lists, your list items would be in a certain order, going from 1, 2, 3, 4, and so forth.

Ordered lists would look like this:

![ordered list](https://th.bing.com/th/id/OIP.Cpx_G8zpj83y636HSsMcrgHaFj?rs=1&pid=ImgDetMain)

To specify an ordered list, you use the `<ol>` tag. Then, for each list element, you use the `<li>` tag. The format should look something like: 

```
<ol>
    <li>element 1!</li>
    <li>element 2!</li>
</ol>
```

#### **Unordered Lists**

Unlike ordered lists, there would be a bullet point or some form of separator at the front of each list item.

Unordered lists would look like this:

![unordered list](https://th.bing.com/th/id/OIP.HfkBXgQPgATQswMMF43-bwHaEJ?rs=1&pid=ImgDetMain)

To specify an unordered list, you use the `<ul>` tag. Same as ordered lists, to add items to your unordered list you use the `<li>` tag. The format should look something like: 

```
<ul>
    <li>element 1!</li>
    <li>element 2!</li>
</ul>
```

#### **The `<img>` tag**

The `<img>` tag is used to add images to our website.

Unlike the other tags, the image tag does not have a self-closing tag, so instead of ending with ```</img>``` we just end with ```/>```

```<img src="image link" alt="describe image here" />```

![](https://www.codewithfaraz.com/img/image%20tag%20in%20html%20how%20to%20add%20images%20in%20html%20-%20a%20beginners%20guide.jpg)

For more HTML tags, visit the link below:

[More HTML Tags](https://www.w3schools.com/tags/)


_______________________________________________________________

[Previous: Getting Started](Getting Started){: .float-left .v-align-text-top}
[Next: CSS](CSS){: .float-right .v-align-text-top}

