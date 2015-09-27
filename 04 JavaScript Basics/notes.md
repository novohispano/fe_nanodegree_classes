## JavaScript Basics

### Lesson 0 - Setup

#### console.log()

* It is the function to print something in JS.
* The return value of console.log() is `undefined`, meaning that there is no value to be returned.
* In JS, semicolons are optional, but it is recommended to include them.

#### jQuery

* The `$` sign is an indication that you are using jQuery.
* You can fetch elements using $("element").
* The `html()` function replaces the html of the fetched element.

#### Commenting

* You can comment JS with `//` or with `/* */`.

#### .append()

* You can use `.append()` function to add HTML content on the page.

### Lesson 1 - Data Types

#### Variables

* You can store values in variables.
* To declare a variable you start with `var`.
* All numbers in JS are saved as 64 bit floating points.

#### string.replace()

* With string replace allows you to replace a part of a string with new content.
* You can use a regular expression to remove a character. For example: `/<|>/g` will match either `<` or `>` globally.

#### $.append() vs $.prepend()

* `append()` is add contents to the end of the inside of an HTML element.
* `prepend()` is an element that adds the content at the beginning of the inside of an HTML element.

#### slice()

* Returns the string minus the characters specified.

#### toUpperCase()

* Capitalize a letter.

#### Truthy vs Falsy

| Truthy           | Falsy     |
|------------------|-----------|
| true             | false     |
| non-zero numbers | zero      |
| "strings"        | ""        |
| objects          | undefined |
| arrays           | null      |
| functions        | NaN       |

* `NaN` is a value that appears when you ask JS to do impossible arithmetic things.
* If a variable is declared but not defined, you will get `undefined` as its return value.
* If you call a variable that doesn't exist, it will return `ReferenceError`.

#### arrays

* Arrays in JS are similar to lists in Python. They are a collection of elements based on a zero index.
* `length` gives you the size of the array.
* `indexOf()` gives you the index of a particular element.
* `pop()` allows you to remove an element from the array. The return value is the removed value.
* `push()` allows you to insert an element into an array. The return value is the added value.
* We can use `slice(0)` to make a copy of an array.
* `slice()` accepts two arguments, when the second is included, it returns a segment where the first value starts and the second finishes.

#### Objects

* Objects can hold `state` and `behavior`.
* There are no classes in JavaScript. There are ways to mimic classes, but they are just objects.
* The `object literal` notation works as follow:

```javascript
var bio = {
    "name" : "James",
    "age"  : 32
};
```

* To access a property in an object, use the `object.property`.

#### Dot Notation

* Dot notation allows you to call a property of an object using `object.attribute` syntax.
* This also allows you to rewrite a property or to set a new value.
* With `dot notation` you don't need `var` because you are not creating a new variable or object, you are just accessing its properties.

#### Bracket Notation

* You can also use brackets to access and set properties in an object.
* Bracket notation always works. Dot notation requires properties that begin with a letter and do not include special characters.

#### Function syntax

* Functions are objects in JavaScript.

#### JSON

* JavaScript Object Notation. JSON is a popular and simple format for storing and transferring nested or hierarchal data.
* Use a http://jsonlint.com to validate your JSON.

#### DOM

* Browsers convert all of the HTML they receive into a JavaScript object called the Document Object Model (DOM).
* `document` is the JS object that represents the DOM.
* We can fetch an element with raw JS using `.getElementById(id)` or `.getElementByClass(class)`.
* You can use `.style` to modify the CSS style of a particular element.
