---
layout: default
title: JavaScript
nav_order: 4
permalink: Tutorials/JS
parent: Tutorials
has_toc: true
---

# JavaScript Introduction
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

### JavaScript
Now that we've created a structure and style, we would want functionality and interaction. If we turn on the switch, what parts of the rooms will light up? Do you want your house to have automatic temperature adjusting to which part of the room you are in? JavaScript is the "code" of the webpage that defines and adds that functionality and behavior. It responds to the inputs and actions user gives, and creates outputs.

- **Basic Syntax**: JavaScript syntax includes variables, data types, operators, functions, and control structures like `if` statements and loops.
- **DOM Manipulation**: JavaScript interacts with the DOM (Document Object Model), enabling dynamic content updates and element manipulation.
- **Event Handling**: JavaScript responds to user interactions like clicks and keystrokes, triggering actions or behavior changes.
- **Asynchronous Operations**: JavaScript handles asynchronous tasks like fetching data from servers or APIs using promises or async/await.

#### **Variables and Data Types**

JavaScript allows you to store and manipulate data in variables. It supports several data types including strings, numbers, booleans, objects, and arrays.

```javascript
var name = "Anthony"; // String
var age = 30; // Number
var isDeveloper = true; // Boolean
```

#### **Operators**

| Type          | Operators        | Description                         |
|---------------|------------------|-------------------------------------|
| Arithmetic    | `+`, `-`, `*`, `/` | Used to perform basic mathematical operations such as addition, subtraction, multiplication, and division. |
| Logical       | `&&`, `||`, `!`   | Used to perform logical operations. `&&` is logical AND, `||` is logical OR, and `!` is logical NOT. |
| Comparison    | `==`, `!=`, `===`, `!==` | Used to compare two values. `==` and `!=` check for equality and inequality without type coercion, whereas `===` and `!==` check for equality and inequality with type coercion. |

#### **Functions**
Functions are reusable blocks of code that perform a specific task. They can be called as needed, accept parameters, and return results.

```javascript
function greet(name) {
    return "Hello, " + name + "!";
}
console.log(greet("Anthony"));  // Outputs: Hello, Anthony!
```

#### **Event Handling**
You can make things happen when buttons are clicked:

```javascript
<button id="clickMe">Click me!</button>
<script>
    document.getElementById('clickMe').addEventListener('click', function() {
        alert('Thanks for clicking!');
    });
</script>
```

#### **DOM Manipulation**
You can modify the content without needing to reload the page. 

```javascript
document.getElementById('welcome').textContent = 'Welcome to our website!';
```

_______________________________________________________________

[Previous: CSS](CSS){: .float-left .v-align-text-top}
[Next: Python](Python){: .float-right .v-align-text-top}