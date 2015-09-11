## Responsive Design

### Pixels

* There are hardware pixels and CSS pixels called DPIs.
* DPIs are based on the ratio that is equivalent on hardware pixels.

### Viewport

* It is recommended that users set viewport to prevent browsers from guessing the right zoom.
* You can set that this using the `viewport` metatag.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Max-Width

* Use relative units to prevent content from overflowing the containers.
* To prevent this, you can set the `max-width` property to 100%.
* It is recommended that you do a catch all style for images, embed, object and video.
* The `max-width` property overrides the width property.

```css
img,
embed,
object,
video {
  max-width: 100%;
}
```

### Tap Targets

* Tap targets are elements that the user use to interact with. This could be buttons, links, forms, and so on.
* For them to work they need to be big enough to be clicked.
* Fingers are about 10 millimeters wide, which is about 40 CSS pixels.
* However, buttons should be 48 x 48 pixels minimum so that there is enough room between the elements and users don't click two things by accident.
* It is ok to have smaller elements, as long as there are 40 pixels of room between them.
* To make sure that all tappable elements follow this, you must add this, for example:

```css
nav a, button {
  min-width: 48px;
  min-height: 48px;
}
```

### Start Small

* You should always start your design with the smallest possible viewport, and then working your way up to bigger screen sizes.
* This workflow forces you to prioritize what is important to your users, and forces you to think about which content you are going to be streaming to your users.

### Basic Media Queries

* You can add new stylesheet with a media query that will apply when a view port is wider than a certain length.
* In media, just stick to `screen`. Use `print` in case you want to print anything.

```html
<link rel="stylesheet" media="screen and (min-width:500px)" href="over500.css">
```

### Adding Media Queries to CSS

* You can also embed queries to your CSS using `@media`.

```css
@media screen and (min-width: 500px) {
  body { background-color: green; }
}
```

* You can also embed them using `@import` but you want to avoid that for performance reasons.
* With linked css (using `link` in the html) you get many small http requests. With `@media` you get few big http requests.
* The CSS in different viewports adds up unless you specify a different behavior.
* `max-width` is also used to specify a viewport that is less than a particular `width`.
* **Never** use `min-device-width` or `max-device-width` since this is based on the device screen and not in the size of the browser window.

### Picking Breakpoint

* You should never pick device screens to select your breakpoints. This will become a maintenance nightmare.
* Instead, you should let your content guide you.
* It is a good exercise to start always in the smallest viewport and then start resizing your screen slowly with the developer tools open.

### Flexboxes

* You can use flexboxes to make your grid adaptable.
* When you use `display: flex` divs that would be displayed one on top of another, would align in a row.
* If you add `flex-wrap: wrap` then the divs will adapt to the layout and will move to accommodate unless it is no longer possible.
* You can also order the items by adding `order: (value)` to each div. You should adjust the widths as well to render more complicated layouts.

### Responsive Patterns

* There are four main responsive patterns that you can use:
  * Mostly Fluid
  * Column Drop
  * Layout Shifter
  * Off Canvas
* Sometimes, a page could use a combination of patterns.

### Column Drop

* It is the easiest pattern.
* As it narrows, each element stack on each other.
* As it widens, each element expand until the first Breakpoint and then the elements start coming side by side, and then reflow to a three column layout.
* Then margins started added around the columns.

```css
  .container {
    display: flex;
    flex-wrap: wrap;
  }

  box {
    width: 100%
  }

  @media screen and (min-width: 450px) {
    .dark-blue {
      width: 25%;
    }

    .light-blue {
      width: 75%;
    }
  }

  @media screen and (min-width: 550px) {
    .light-blue {
      width: 50%;
    }

    .dark_blue, .green {
      width: 25%;
    }
  }
```

```html
  <div class="container">
    <div class="box dark-blue"></div>
    <div class="box light-blue"></div>
    <div class="box green"></div>
  </div>
```

### Mostly Fluid

* It is similar than column drop.
* It gets stacked when narrower.
* As it gets wider, the grid pattern starts to appear.
* Once the layout gets its wider viewport, margins are added next to the outside columns.

```css
  .container {
    display: flex;
    flex-wrap: wrap;
  }

  .box {
    width: 100%;
  }

  @media screen and (min-width: 450px) {
    .light-blue, .green {
      width: 50%;
    }
  }

  @media screen and (min-width: 550px) {
    .dark-blue, .light-blue {
      width: 50%;
    }

    .green, .red, .orange {
      width: 33.33333%;
    }
  }

  @media screen and (min-width: 700px) {
    .container {
      width: 700px;
      margin-left: auto;
      margin-right: auto;
    }
  }
```

```html
  <div class="container">
    <div class="box dark-blue"></div>
    <div class="box light-blue"></div>
    <div class="box green"></div>
    <div class="box red"></div>
    <div class="box orange"></div>
  </div>
```
