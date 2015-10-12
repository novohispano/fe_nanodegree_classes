## Intro to jQuery

### The Basics

#### Intro

* jQuery is a JavaScript library.
* Manipulating the DOM with vanilla JavaScript is harder and more verbose. It also unifies the different browser implementation of the DOM.
* jQuery is a JavaScript function and therefore, an object.

#### The `$`

* The jQuery object and the `$` sign are the same thing. It is a pointer to the jQuery object.
* It was implemented so that you can write jQuery functions faster.
* The return value of `$` is an array with additional methods.
* You can pass a string as an argument that includes the selector of the element you want to retrieve.
* You can also pass functions as an argument.
* You can also pass a DOM element as well.
* You can call methods directly on the jQuery object, like `.ajax()`.

#### The DOM

* The Document Object Model (DOM) is a data structure that is similar to a family tree.
* Elements can have parents, children and siblings.
* Children elements are nested within an element.
* Sibling elements are at the same level within an element.
* Parent elements are the outer container of an element.

#### How to Include jQuery

* You can include jQuery as a file in your HTML Head.
* This file can be hosted locally or in a CDN. It is recommended that you use the CDN since they are much faster and you won't have to spend resources serving it yourself.
* Remember to use the minified version of jQuery in production since the file size is smaller.

#### Selectors

* The string that we pass onto the jQuery object is called a jQuery selector.
* This specifies the element, class or id that matches an element in the DOM that we want to select.
* To select an element, you do: `$('h1')`.
* To select an element with a class, you do: `$('.class')`.
* To select an element with an id, you do: `$('#id')`.
* Any valid CSS selector is a valid jQuery selector.

#### DOM Traversal methods

* `.parent()` returns the element that contains the current element.
* `.parents()` returns the elements that contains the current element.
* `.children()` returns the elements that are contained within the current element.
* `.find()` finds a particular element contained within an element by its selector. This functions requires a selector. If you want to select all of the descendants, you can use `.find('*')`.
* `.siblings()` finds elements at the same level than the current element.
* This methods accept a selector in case you want to find an specific element.

### DOM Manipulation

* `.toggleClass()` adds and removes a class to an element in the DOM.
* `.next()` selects the next element that matches a selector.
* `.attr()` allows you to get or modify an attribute.
* `.css()` using this element adds inline css to an element.
* `.html()` allows you to get all (or modify) the HTML inside that element.
* `.text()` allows you to get (or modify) only the text contained within the element.
* `val()` gets or sets the value of an input box.
* `.remove()` removes a DOM element.
* `.append()` adds a DOM element as the last child of the selected item.
* `.prepend()` adds a DOM element as the first child of the selected item.
* `.insertBefore()` adds a DOM element as a sibling before the selected item.
* `.insertAfter()` adds a DOM element as a sibling after the selected item. `.after()` does the same, but its syntax is similar to `.append()`.
* `.each()` allows you to iterate over a jQuery collection.
* It is important to wait until the document is ready to execute your jQuery scripts. Otherwise, the elements might not be there. You can do so by doing:

```js
$(function(){
  // code goes here
});
```

### jQuery Events

* A browser event is an action performed by the user in the browser, such as dragging the mouse, submitting a form and submitting a button.
* Chrome uses the `monitorEvents()` function that allows you to observe the events as they happen under the hood. You pass the element that you are watching as an argument for that function. This function only works in the console in Developer Tools, don't try to use it in your JS file. Use it like this `monitorEvents(document.body, 'mouse')`
* You can check the available events here: https://developer.mozilla.org/en-US/docs/Web/Events#Categories.

#### Anatomy of Events

* First you need to select the target element.
* Then you need to call the `.on()` method that will indicate the event that you want to listen to.
* The second argument is a function that will be executed when the event occurs. This function is called `callback`.

#### Event Object

* The event object is the object that gets passed to an event listener’s callback.
* This object holds useful information that can be used by the function.
* This object, which is usually referenced in JavaScript as e, evt, or event, has several properties that you can use to determine the flow of your code.
* You can try logging the object to see what's available:

```js
$( 'article' ).on( 'click', function( evt ) {
    console.log( evt );
});
```

* The target property holds the page element that is the target of the event. This can be extremely useful if an event listener has been set up for a number of elements:


```js
$( 'article' ).on( 'click', function( evt ) {
    $( evt.target ).css( 'background', 'red' );
});
```

* The event object also comes in handy when you want to prevent the default action that the browser would perform. For example, setting up a click event listener on an anchor link:

```js
$( '#myAnchor' ).on( 'click', function( evt ) {
    evt.preventDefault();
    console.log( 'You clicked a link!' );
});
```

In the code above, the evt.preventDefault(); line instructs the browser not to perform the default action.

* Other uses include:
  * `event.keyCode` to learn what key was pressed - invaluable if you need to listen for a specific key
  * `event.pageX` and `event.pageY` to know where on the page the click occurred - helpful for analytics tracking
  * `event.type` to find what event happened - useful if listening to a target for multiple events

#### jQuery Convenience Methods

* These methods are shortcuts for the event handlers.
* Example: `$(selector).click(callback)` is a shortcut for `$(selector).on('click', callback`.
* Not all events handlers have their convenience method.

#### Event Delegation

* Event delegation is useful when you want to attach an event to an element in the DOM that does not yet exist.
* You can do so by attaching the event to the parent, and make the parent delegate the occurrence of an event to its children.
* Example:

```js
$('parent').on('event', 'children', callback)
```

* Also, you can use it when you want to add an event listener for several children elements instead of setting up one event listener per child.
