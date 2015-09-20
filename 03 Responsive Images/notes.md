## Responsive Images

* You can select an element by clicking on the element and writing `$0` to get that element in the console.
* You can also record the request in the network settings in the dev console, disable cache and select the images so that you can see the time they take to load.

### Total Bits

* You get the `total bits` by multiplying `pixels` x `bits per pixel`
* The rule for performing images is to deliver them with the lowest possible quality and the smallest size as possible.
* Less pixels x better compression = less bytes.

### Requests & Revenue

* The average page size makes 56 requests for images.
* An increase in page load from 0.4 to 0.9 seconds translates to a loss of 20% in ad revenue.
* Every 100ms increase in Amazon page loads decrease sales by 1%.

### Relative Sizing

* Use `max-width: 100%` so that the image doesn't expand beyond it's natural width.
* To add a margin:
  * You can use `calc` which allows us to do calculation for CSS values. E.G. `width: calc((100% - 10px)/2)`
  * Then you can add `img:last-of-type` to give a margin only to the element in the right.
  * You can also use `img:nth-last-of-type(-n+2)` to select the last two elements that match that type.

### Less Well Known CSS units

* You can use the `vh (view height)` unit to get an image that covers the entire viewport.
* You can do the same with `vw (view width)`.
* If you want the image to resize to the smaller of the viewport, you can use `100vmin`.
* To make the image resize without squashing, you can use `100vmax`.

### Raster vs Vector

* Raster are images form as a grid of pixels
* Vectors are images form as a collection of vector, shapes and so on.
* Vectors can be re-render to any size by the browser.
* Vector files are also smaller.
* Use JPEGs (Raster) or WebP (Which delivers better compression and features) for photo images. WebP supports alpha transparency with lossy and lossless compression.
* Use SVG for vector images or PNG (if you are unable to use SVG). Use PNG always before using GIF.
* Images only need to be as large as they need to be.

### Compression, Optimization and Automation

* One of the best tools to process images in batches is ImageMagick, an open source library that you can use in your terminal.
* You can run a simple server that exposes files with python. Just run `python -m SimpleHTTPServer`

### Performance

* In mobile devices, the number of requests is as significant as the size of the requests.
* Optical fiber's best is the half of the speed of light. For example, data between London and California takes 100 ms to travel.
* To improve performance, is to compress images and reduce the number of images.

### Text Problems

* Display text as text on top of images, don't put it in the image.
* The best way to avoid image problems is to not use images at all and use typography instead.
* With webfonts and css you can pretty much use any text for graphical effects.
* There is a processing cost if you use CSS text effects.

### Background Images

* You can set the `bakcground-size` property in a div to have a background image in a picture.
* With background-size set to `cover`, the image covers all it's width and hides part of its height. It's smallest dimension matches the container's smallest dimension.
* With `contain`, the largest image dimension matches its container's largest dimensions.

### Symbol Characters

* Instead of using pictures, try to see whether you can find a character that matches in a font.
* Check http://unicode-table.com.
* Set character set to UTF-8 to make these available.
* It is recommended that you use the actual unicode character in your code instead of the HTML code, it is easier to mantain.
* Check `Zocial` for a font that uses icons as characters.
* For more fonts, check http://weloveiconfonts.com.

```css
  @import url(http://weloveiconfonts.com/api/?family=zocial);

  [class*="zocial-"]:before {
    display: inline-block;
    font-family: 'zocial', sans-serif;
    text-shadow: 3px 3px 3px #aaa;
    width: 20vw;
  }
```

### Inlining Images with SVG

* To reduce the number of file requests, you can embed the images in your html using `svg` or `data-uri`.
* You can animate SVGs without taking much data.

### sourceset

* This is an image attribute that lets the browser make the best decision based on the dpi of the screen.
* The `1x` and `2x` are the pixel density descriptor.

```html
  <img src="wallaby_1x.jpg" scrset="wallaby_1x.jpg 1x, wallaby_2x.jpg 2x" alt="Wallaby">
```

* You can get the information about your screen pixel density by using `window.devicePixelRatio`.
* If the browser doesn't support `sourceset` it would load the default picture.
* It is recommended that you use the `w` unit so that the browser can pick the best image for your site.

```html
  <img src="wallaby_small.jpg" scrset="wallaby_small.jpg 500w, wallaby_medium.jpg 1000w" alt="Wallaby">
```

### size

* The size attribute tells the browser the size at which the image will be displayed.
* The size attribute does not resize your image.
* The sizes attribute should match the CSS so that the browser can easily find the image to render.

```html
  <img src="wallaby_small.jpg" scrset="wallaby_small.jpg 500w, wallaby_medium.jpg 1000w" sizes="(max-width: 250px) 100vw, 50vw" alt="Wallaby">
```

```css
  @media screen and (max-width: 250px) {
    img {
      width: 100vw;
    }
  }
```

* `sizes` consists of comma separated `mediaQuery width` pairs. `sizes` tells the browser early in the load process that the image will be displayed at some width when the mediaQuery is hit.

### Picture Element

* The picture element allows you to declare sources and an img element within it. If the browser supports the first type of file, it will render, otherwise it will hit the next one.
* If a browser doesn't support picture elements, then you can include an `img` element as a "fallback" option within the picture element.

```html
  <picture>
    <source srcset="kittens.webp" type="image/webp">
    <source srcset="kittens.jpeg" type="image/jpeg">
    <img src="kittens.jpg" alt="Two gray kittens">    
  </picture>
```
### Art Direction

* This is when you use an image based on the layout of the page.
* You can use the picture element to achieve this.
* For browsers that don't support the picture element, you can use picturefuill.js. Download it [here](http://scottjehl.github.io/picturefill/).

```html
  <picture>
    <source
      media="(min-width: 1000px)"
      srcset="kitten_large_1x.png 1x, kitten_large_2x.jpg 2x">
      <source
        media="(min-width: 500px)"
        srcset="kitten_small_1x.png 1x, kitten_small_2x.jpg 2x">
    <img src="kitten_small.png" alt="Cute kitten">
  </picture>
```

### Accesibility

* You have to use the attributes responsively so that visually impaired users can see your site.
* Decorative content should not have the alt attribute, but important content should.
* You can install [ChromeVox](http://www.chromevox.com/) to experience a site as a visually impaired user.
