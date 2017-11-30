[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# jQuery DOM Manipulation

## Objectives

By the end of this, developers should be able to:

-   Diagram the DOM
-   Reference jQuery documentation when learning a new technique
-   After selecting a DOM node, reach another node using traversal
-   Get data from the DOM using jQuery
-   Put data into the DOM using jQuery

## Preparation

1.  Fork and clone this repository.
 [FAQ](https://github.com/ga-wdi-boston/meta/wiki/ForkAndClone)
1.  Create a new branch, `training`, for your work.
1.  Checkout to the `training` branch.
1.  Install dependencies with `npm install`.

## The Document Object Model (DOM)

-   The DOM is a recursive tree.

The DOM is a (potentially) large object that describes the structure of our
content. Since it's an object, we can use normal techniques to get and set data!
In the browser, the DOM is represented by the `document` object. JS specifies
some built-in methods that make using the DOM easier. Remember! The DOM
**is not** the source code.

## jQuery

-   The "query" in jQuery comes from SQL.
-   We can retrieve and put data into the DOM using jQuery.
-   jQuery uses selectors (css selectors, remember?)

## Demo: Diagram the DOM

Demo translating a wireframe into a tree diagram.

## Lab: Diagram the DOM

1.  Consultant: Give wireframe
1.  Developer: Draw a tree diagram
1.  Consultant: Draw the solution
1.  Discussion and questions

## Code-Along: DOM Traversal

-   Deface the [Jimmy Buffett](https://en.wikipedia.org/wiki/Jimmy_Buffettt)

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

We can use `.val()` on the Jimmy Buffett page to get and set text in the search box.

## Demo: DOM Events and Event Handlers

The DOM emits 'events' when users interact with the browser. Event handlers
'listen' for DOM events emitted from the DOM node they are 'attached' to, and run
code when that event happens. Some common events that we might want to use event handlers on are `'click'`, `'hover'`, `'focus'`, or user keystrokes.
[Full list of DOM events](https://developer.mozilla.org/en-US/docs/Web/Events)

<!-- Demonstrate using an event handler on the Jimmy Buffett page -->

## Lab: Register an Event Handler

Continue defacing the Jimmy Buffett.  This time with an event handler.

## Lab: Research Common jQuery Functions

Here is a list of most commonly used jQuery API functions:

1.  [`find()`](http://api.jquery.com/find)
1.  [`hide()`](http://api.jquery.com/hide)
1.  [`show()`](http://api.jquery.com/show)
1.  [`html()`](http://api.jquery.com/html)
1.  [`append()`](http://api.jquery.com/append)
1.  [`prepend()`](http://api.jquery.com/prepend)
1.  [`on()`](http://api.jquery.com/on)
1.  [`off()`](http://api.jquery.com/off)
1.  [`css()`](http://api.jquery.com/css)
1.  [`attr()`](http://api.jquery.com/attr)
1.  [`val()`](http://api.jquery.com/val)
1.  [`text()`](http://api.jquery.com/text)
1.  [`each()`](http://api.jquery.com/each)

## Demo: event.target

Open the console in chrome and paste the following code in.

```js
$(".toctitle").on('click', function(event){
  console.log("event is ", event)
})
```

How would we access specific attributes of that event? Try adding this code
now as well:

```js
$(".toctitle").on('click', function(event){
  console.log("event.target is ", event.target)
})
$(".toctitle").on('click', function(event){
  console.log("event.type is ", event.type)
})
```
<!-- Use .on() on the Jimmy Buffett page to demonstrate -->

## Bubbling

When dealing with the DOM and click handlers, we're faced with a small
problem that is simple to work-around if you know it exists. **Bubbling**
occurs when an event takes place on a child element of the
DOM that **does not** have an event handler of its own. In the scenario
that this happens, the browser will search up the DOM chain until it finds
an appropriate event handler.

In the example below we have a click handler registered on the `<ul>` with
 `id="thisOne"`. However, if we were to click the 3rd `<li>` with
 `<!--the innermost-->`, it will still run our click handler.

```html
<html>
  <div>
    <ul id="thisOne" class="d1">Title</ul><!-- the topmost -->
      <li class="d2">1</li>
      <li class="d2">2</li>
      <li class="d3">3</li><!-- the innermost -->
    </ul>
  </div>
</html>
```

```js
$("#thisOne").on('click', function(){
  // do some stuff here
})
```

As a quick review, what would the DOM tree look like for the above html? Let's
take 2 minutes and diagram it together. What would we do if the `<li>`s or the
 `<ul>` as a whole weren't present on time of page load, but we needed to add
some event handlers for them?

## Best Practices

-   When attaching a `click` handler (or any handler), opt for the
`.on('click', function(){})` version over the `.click(function(){})` verion. The
 reason is `.on('click', )` accepts more arguments so we can be more specific
 with our handlers. See [.click()](https://api.jquery.com/click/) vs. [.on()](http://api.jquery.com/on/)

## Gotchas

-   Beware the difference between jQuery setters and getters.
-   Beware the difference between `.html()`, `.text()`, and `.val()`
-   Beware treating jQuery objects as arrays. They aren't!
-   Beware attaching click handlers in a loop. It won't work, and it isn't
    necessary, because when you use `.on('click')` jQuery will attach the eventHandler on every single node in the jQuery object.

## Additional Resources

-   [JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
-   [jQuery API Documentation](https://api.jquery.com/)
-   [Quick jQuery Reference Cheatsheet](https://oscarotero.com/jquery/)
-   [JS Fiddle Event Bubbling Example](http://jsfiddle.net/cwtuan/je1g3f29/16/)
-   [Live DOM tree viewer](https://software.hixie.ch/utilities/js/live-dom-viewer/)
-   [jQuery Cheatsheet](http://htmlcheatsheet.com/jquery/)

## License
1.  All content is licensed under a CC­BY­NC­SA 4.0 license.
1.  All software code is licensed under GNU GPLv3. For commercial use or
    alternative licensing, please contact legal@ga.co.
