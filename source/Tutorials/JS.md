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

Here is some basic information about what JS can do: 
- **DOM Manipulation**: JavaScript interacts with the DOM (Document Object Model), enabling dynamic content updates and element manipulation.
- **Event Handling**: JavaScript responds to user interactions like clicks and keystrokes, triggering actions or behavior changes.
- **Asynchronous Operations**: JavaScript handles asynchronous tasks like fetching data from servers or APIs using promises or async/await.

#### Where does the code go?

The browser reads HTML top‑to‑bottom. If JavaScript runs before the page is loaded you’ll get errors. Placing code in the right spot keeps everything in sync.

| Style        | Snippet                           | When to use                         |
| ------------ | --------------------------------- | ----------------------------------- |
| **Inline**   | `<button onclick="alert('hi')">`  | Tiny demos, email templates         |
| **Internal** | `<script>/* code */</script>`     | Single‑file school projects         |
| **External** | `<script src="main.js"></script>` | Real websites (easiest to maintain) |

> **What’s happening**: The `<script>` tag tells the browser to fetch and run JavaScript. Putting it *just before* `</body>` (or using `defer` in the `<head>`) waits until the HTML is ready.

**Learn more** → [MDN: Script tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)

---

#### Variables – your labeled “storage boxes”

Programs need to *remember* things—scores, names, settings. Variables are boxes with labels you create to store that info.

```javascript
let score = 0;          // Number – math ready ✔️
const name = "Alex";     // String – text
let loggedIn = false;     // Boolean – true / false switch
```

* `let` creates a box you can re‑label (re‑assign) later.
* `const` is a permanent label—great for settings that shouldn’t change.

**Learn more** → [MDN: Variables](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables)

---

#### Operators (math & logic)

Operators let you **calculate** and **compare** so your program can make decisions.

```javascript
score = score + 1;   // Arithmetic: + - * / %

// Comparison returns true / false
a > b     // greater than

// Combine with logical operators
if (score >= 10 && loggedIn) {
  console.log("High‑score user logged in!");
}
```

> **What’s happening**: `>=` checks a condition. `&&` means *both* parts must be true for the block to run.

**Learn more** → [MDN: Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

---

#### Control Flow – decision forks & loops

Code usually isn’t top‑to‑bottom; it zig‑zags based on conditions and repeats when needed.

```javascript
// IF…ELSE – choose a path
if (score < 5) {
  alert("Keep going!");
} else {
  alert("Great job!");
}

// FOR loop – repeat exactly 3 times
for (let i = 0; i < 3; i++) {
  console.log("Loop number", i);
}
```

> **What’s happening**: The `for` loop creates a counter (`i`) that starts at 0, checks a condition (`i < 3`), runs the block, then increments (`i++`).

**Learn more** → [MDN: Control flow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)

---

#### Arrays & Objects – grouping data

Real apps juggle *lists* (arrays) and *complex things* (objects) instead of single numbers.

```javascript
// Array: ordered list
let colors = ["red", "green", "blue"];
console.log(colors[0]);   // red – arrays start at index 0

// Object: key–value pairs
let player = {
  name: "Alex",
  score: 12,
  powerUps: ["shield", "speed"]
};
console.log(player.name); // Alex
```

> **What’s happening**: `colors[0]` grabs the first item. `player.name` drills into an object using the dot.

**Learn more** → [MDN: Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array), [MDN: Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

---

#### Functions – mini machines you can reuse

Functions bundle steps into one command, so “mix‑once‑use‑many‑times.”

```javascript
// Traditional function
function add(a, b) {
  return a + b;        // spits back a value
}

// Arrow function (short form)
const double = (n) => n * 2;

console.log(add(2, 3));   // 5
```

> **What’s happening**: `return` sends data back to wherever the function was called.

**Learn more** → [MDN: Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

---

#### Talking to the page (DOM Manipulation)

The **DOM (Document Object Model)** can help your website gain functionality. It can do things like trigger a pop up when a button is clicked, or other things like that. **You can change any HTML attribute or CSS property of any HTML element on the page using this.**

```html
<p id="welcome">Hello!</p>

<script>
  const msg = document.getElementById("welcome"); // grab element 🌳
  msg.textContent = "Welcome, " + name + "!";     // change its text
</script>
```

> **What’s happening**: `getElementById` returns a DOM node. Editing `textContent` swaps the words without reloading.

**Learn more** → [MDN: DOM Intro](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

---

#### Listening for events

JavaScript comes alive when it *reacts* to clicks, keys, or scrolling.

```html
<button id="clickMe">Click me</button>

<script>
  document.getElementById("clickMe")
    .addEventListener("click", () => {
      alert("Thanks for clicking!");
    });
</script>
```

> **What’s happening**: `addEventListener` waits for the user’s click, then runs the arrow function.

**Learn more** → [MDN: Events](https://developer.mozilla.org/en-US/docs/Web/Events)

---

#### Async magic – fetching data without reloading

Modern sites pull data from servers in the background so pages feel instant.

```javascript
async function getJoke() {
  // 1️⃣ fetch – ask the server
  const response = await fetch("https://api.example.com/joke");
  // 2️⃣ response.json() – turn bytes into JS object
  const data = await response.json();
  console.log(data.setup + " " + data.punchline);
}
getJoke();
```

> **What’s happening**: `await` pauses the function until each promise resolves, so code reads top‑to‑bottom even though work happens in the background.

**Learn more** → [MDN: Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), [MDN: Async/await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await), also check out the backend section in the An Example section!

---

### Debugging

Use `console.log()` to print out variables to see what went wrong. 

_______________________________________________________________

[Previous: CSS](CSS){: .float-left .v-align-text-top}
[Next: Python](Python){: .float-right .v-align-text-top}