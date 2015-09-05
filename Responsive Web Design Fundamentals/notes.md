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
