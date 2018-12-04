[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# jQuery DOM Manipulation

## Objectives

By the end of this, developers should be able to:

- Diagram the DOM.
- Reference jQuery documentation when learning a new technique.
- After selecting a DOM node, reach another node using traversal.
- Get data from the DOM using jQuery.
- Put data into the DOM using jQuery.

## Preparation

1. Fork and clone this repository.
 [FAQ](https://git.generalassemb.ly/ga-wdi-boston/meta/wiki/ForkAndClone)
1. Create a new branch, `training`, for your work.
1. Checkout to the `training` branch.
1. Install dependencies with `npm install`.
2. Run with `grunt serve`.

## The Document Object Model (DOM)

**The DOM is a recursive tree.**

The DOM is a (potentially) large object that describes the structure of our
content. Since it's an object, we can use normal techniques to get and set data!
In the browser, the DOM is represented by the `document` object. This
object represents all elements on the webpage and is the entry point for
accessing those elements. A list of all methods/properties of the document
object can be found [here](https://developer.mozilla.org/en-US/docs/Web/API/Document).
JS specifies some built-in methods that make using the DOM easier. Remember! The
DOM **is not** the source code.

## Demo: Diagram the DOM

Demo translating a wireframe into a tree diagram.

## Lab: Diagram the DOM

1. Consultant: Give wireframe
1. Developer: Draw a tree diagram
1. Consultant: Draw the solution
1. Discussion and questions

## Demo: The Document Object

```js
// returns a representation of the current html document
document

// returns a representation of the body element
document.querySelector('body')

// use document object to change style
document.querySelector('body').style.backgroundColor = 'red'
```

## jQuery

jQuery is a popular JavaScript library that simplifies many developer tasks such
as:

- DOM manipulation
  - select
  - traverse
  - effects and animation
- Event handling
- AJAX calls

The "query" in jQuery means "a request for information". We can make
queries (retrieve and put data into the DOM) using jQuery by way of selectors:

```js
// longhand syntax
jQuery('p')

// shorthand syntax
$('p')

// use modern CSS selectors
$('main .title > .sub-title')
```

## Code-Along: DOM Traversal

- Deface the [Jimmy Buffett](https://en.wikipedia.org/wiki/Jimmy_Buffett) page.

  <!-- Use jQuery to change the Jimmy Buffett page -->

## Demo: jQuery Setters & Getters

When reading the jQuery documentation, be sure to scroll through the whole
document to ensure you're looking at the correct method signature. Most jQuery
methods change their behavior depending on the number of arguments they have
when called.

For example, have a look at [.val()](https://api.jquery.com/val/). Note in the
table of contents that there are two method signatures, `.val()` and
`.val(value)`. This is our hint that `.val()` can do two things.

Reading the documentation, we discover that `.val()` is getter on an element,
but that `.val(value)` is a setter on an element. Be sure you're using the
correct method. Reading examples is very helpful, and the jQuery examples in the
docs are fully functional!

We can use `.val()` on the Jimmy Buffett page to get and set text in the search
box.

## Demo: DOM Events and Event Handlers

The DOM emits 'events' when users interact with the browser. Event handlers
'listen' for DOM events emitted from the DOM node they are 'attached' to, and run
code when that event happens. Some common events that we might want to use event
handlers on are `'click'`, `'mouseover'`, `'focus'`, or user keystrokes.
[Full list of DOM events](https://developer.mozilla.org/en-US/docs/Web/Events).

## Lab: Research Common jQuery Functions

Here is a list of most commonly used jQuery API functions:

1. [`find()`](https://api.jquery.com/find)
1. [`hide()`](https://api.jquery.com/hide)
1. [`show()`](https://api.jquery.com/show)
1. [`html()`](https://api.jquery.com/html)
1. [`append()`](https://api.jquery.com/append)
1. [`prepend()`](https://api.jquery.com/prepend)
1. [`on()`](https://api.jquery.com/on)
1. [`off()`](https://api.jquery.com/off)
1. [`css()`](https://api.jquery.com/css)
1. [`attr()`](https://api.jquery.com/attr)
1. [`val()`](https://api.jquery.com/val)
1. [`text()`](https://api.jquery.com/text)
1. [`each()`](https://api.jquery.com/each)

## Demo: event.target

Open the console in chrome and paste the following code in.

```js
$('.toctitle').on('click', function(event){
  console.log('event is', event)
})
```

How would we access specific attributes of that event? Try adding this code
now as well:

```js
$('.toctitle').on('click', function(event){
  console.log('event.target is ', event.target)
})
$('.toctitle').on('click', function(event){
  console.log('event.type is ', event.type)
})
```

<!-- Use .on() on the Jimmy Buffett page to demonstrate -->

# Lab: Using jQuery in _your_ front-end application

Take a look at the `assets/scripts/app.js` file. Alter this file to log event
information for each event. What kind of information do we see in the `event`
argument that `.on` passes to its callback?

Afterwards, edit the event handlers to perform the following actions:

1. Our HTML element with the ID 'red-and-green' should be red on hover, and
green with no hover.
2. Our HTML element with the ID 'change-my-text' should have it's text changed
on a click event.
3. Our HTML element with the ID 'disappear-me' should disappear on hover.
4. Our button with ID 'input-get' should grab the text within the input element
with ID 'special-input' and `console.log` it or append it to the DOM
5. Our button with ID 'input-set' should set the text within the input element
with ID 'special-input'

## Best Practice

When attaching a `click` handler (or any handler), opt for the
`.on('click', function(){})` version over the `.click(function(){})` version.
The reason is `.on('click', )` accepts more arguments so we can be more specific
with our handlers. See [.click()](https://api.jquery.com/click/) vs.
[.on()](https://api.jquery.com/on/).

## Gotchas

- Beware the difference between jQuery setters and getters.
- Beware the difference between `.html()`, `.text()`, and `.val()`.
- Beware treating jQuery objects as arrays. They aren't!
- Beware attaching click handlers in a loop. It won't work, and it isn't
    necessary, because when you use `.on('click')` jQuery will attach the
    eventHandler on every single node in the jQuery object.

## Additional Resources

- [jQuery API Documentation](https://api.jquery.com/)
- [JS Fiddle Event Bubbling Example](http://jsfiddle.net/cwtuan/je1g3f29/16/)
- [Live DOM tree viewer](https://software.hixie.ch/utilities/js/live-dom-viewer/)
- jQuery Cheatsheets
  - [Quick jQuery Reference Cheatsheet](https://oscarotero.com/jquery/)
  - [jQuery Cheatsheet](http://htmlcheatsheet.com/jquery/)

1. All content is licensed under a CC­BY­NC­SA 4.0 license.
1. All software code is licensed under GNU GPLv3. For commercial use or
    alternative licensing, please contact legal@ga.co.
