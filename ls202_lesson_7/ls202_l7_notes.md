##### WLS202 HTML and CSS > Lesson 7: Design Files

---

## 1. Introduction

## 2. CSS Resets

A reset is a bit of CSS that "resets" your CSS to a known state in a variety of different browsers. Thus, your favorite browser renders your web page in the same way that other browsers do. Resets do this by removing or overriding most browser styling defaults; for instance, they set a default font, zero out margins and padding, and eliminate browser-specific styling on input controls. These actions give you a fresh start from which to work and leave you free to add the styles you need without worrying about unexpected results in other browsers.

While there are plenty of resets available, most developers choose one of these popular files:

- [Eric Meyer's reset](http://meyerweb.com/eric/tools/css/reset/)
- [Normalize.css](http://necolas.github.io/normalize.css/)
- [Tantek Celik's whitespace reset](http://cssreset.com/scripts/undohtml-css-tantek-celik/).

The resets vary in aggressiveness, and it's probable that you'll end up with a reset that you like, except for one or two problems. People often customize the reset they use, as we do at Launch School: we use a custom version of Tantek Celik's reset. It's a simple one:

```css
/*
----------------------------------------
Tantek Celik's Whitespace Reset
     Author:    Tantek Celik, Shane Riley
    Version:    (CC) 2010 Some Rights Reserved - http://creativecommons.org/licenses/by/2.0
Description:  Resets default styling of browsers to a common base
----------------------------------------
*/

ul, ol { list-style: none; }
h1, h2, h3, h4, h5, h6, pre, code { font-size: 1em; }
ul, ol, li, h1, h2, h3, h4, h5, h6, pre, form, body, html, p, blockquote,
fieldset, input, dl, dt, dd, figure, figcaption {
  margin: 0;
  padding: 0;
}
a img, :link img, :visited img, fieldset { border: none; }
address { font-style: normal; }
header, section, article, nav, footer, hgroup, details, summary, figure, main {
  display: block;
}
mark {
  color: inherit;
  background-color: transparent;
}
abbr { border: none; }
summary::-webkit-details-marker { display: none; }
```

As you can see, there's not much to it. This reset:

- removes the bullets on ordered and unordered lists.
- sets all headings and a few other items to use the same font size.
- sets the padding and margins on most `block` elements to 0.
- removes the border that surrounds images inside links on older browsers.
- removes the border on `fieldset`.
- converts `address` elements to look like regular text.
- sets newer HTML elements to `display: block`, in case the user has an old browser that defaults to `inline`.
- removes garish colors from the `mark` element.
- removes the bottom border from `abbr` elements.
- removes the toggle marker from the `summary` element.

---

## 3. Working With Design Files

### Photoshop and Design Files

When you first start writing HTML and CSS for a real-world project, a designer will probably give you a **design file** (it's possible that you may be the designer): a mockup of the finished project pages. The design file is almost always a Photoshop document, a PSD file, which is a multi-layered image that contains layers for each part of the design: images, shapes, text, etc. You're expected to use the design file to create your image and background assets as well as obtain information regarding padding, margins, font-size, and color. Knowing your way around Photoshop well enough to extract this information will help you get work as a front-end developer.  

There are alternatives to Photoshop that can read and process PSD files, but we haven't yet determined whether any of these programs do everything needed to examine design files usefully. Most are not free. Some programs provide the ability to read layered PSD files, but they may lack the functionality you need to extract information from those layers.  

Here are a few alternatives that may do the job.

- [Photopea](https://www.photopea.com/) is a free online alternative to Photoshop that some of our students recommend. The support for Launch School project files appears to be excellent; we've had no reports of problems working on the projects in this course.
- [Affinity Photo](https://affinity.serif.com/en-us/photo/) Serif claims that Affinity can access PSD file layers, but with some limitations. The chief lack appears to be support for "smart objects," which you may need with some design files. A 10 day trial period may be available.
- [Photoshop Elements](https://www.adobe.com/) Adobe claims that Photoshop Elements can access PSD files, but with some limitations. It doesn't go into detail, though. A 30 trial period may be available.
- [GIMP](https://www.gimp.org/) As with Affinity Photo, GIMP can read PSD files with some limits, but it is also free. Note that we know that GIMP doesn't work with the Company Site project later in this lesson, but it seems to work well with the other projects provided that you use "Open as Layers" to open the files.
- [Adobe Creative Assets](https://assets.adobe.com/) This free online tool supplied by Adobe lets you look at PSD file layers, measure distances and colors, and extract resources such as images. It works somewhat differently from Photoshop and other tools, but it can be a useful alternative to purchasing Photoshop or using one of the above tools.

If you find one of these programs or another application useful, or find that one doesn't work, let us know!

### PNG Design Files

In the absence of Photoshop, we will provide you with a design file that we've collapsed down to a PNG format. PNG files aren't the best tool for the job, but they work well enough for your Launch School projects.  

There are several problems with using PNG files for design:

- There is no way to examine and measure fonts.
- It is hard to measure colors when the color patch is less than 5-10 pixels thick, such as line drawings and text.
- Extracting images is tedious. If it has curved, jagged, or fuzzy edges, obtaining a clean result may be almost impossible. We'll avoid this by providing you with the images that you need.

To use PNG design files, you'll need tools that:

- open and view PNG files at the intended screen size
- measure sizes, padding, and margins
- measure colors

The macOS program, Preview, displays PNG files. Use View, Actual Size to view the image at its actual size. Drag out rectangular marquees to measure a component. However, there is no way to measure colors.  

On a Mac, Digital Color Meter (found under Applications, Utilities) can help measure colors. Select View, Display Values, as Hexadecimal to display color values in hex, and use Display in sRGB on the drop-down list. You can use Shift-Cmd-C to copy the color under the cursor to the cut-and-paste buffer as a hex value suitable for use in your CSS.  

---

## 4. Walkthrough: Using A Photoshop Design File

