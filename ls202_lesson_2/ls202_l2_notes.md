##### LS202 HTML and CSS > Lesson 2: The Box Model

---

## 1. Introduction

#### Vocabulary

As usual with most development topics, there are some new words and concepts you need to know and understand. You should be able to use the following terms properly when discussing the box model and how it works.

* the box model
  * box properties
    * width and height
    * padding and margins
    * borders
  * visual display models
    * `block`
    * `inline`
    * `inline-block`
  * box sizing model
    * `content-box`
    * `border-box`
* dimensions
  * absolute units
  * relative units

You should be familiar with the following terms, but you're not expected to discuss them in detaill.

* container
* physical pixels
* CSS reference pixels

#### Box Properties

* Every box has a width, height, padding, border, and margins; know the differences.
* Padding, borders, and margins have separate properties to set the left, right, top, and bottom of each element. You can use shortcut properties to specify all four sides at once.
* How does the visual display model interact with margins, borders, and padding?

#### Visual Display Models

* Understand the differences between `inline`, `block`, and `inline-block`.
* Containers are almost always `block` elements, while non-containers are `inline`. When in doubt, check MDN.
* Don't try to memorize which HTML elements are `block` or `inline`.
* How and when can you change an element's visual display model?

#### Box Sizing Models

* Understand the `content-box` and `border-box` sizing models.
* How and when can you change the box-sizing model for an element?

#### Dimensions

* Know the differences between `px`, `em`, `rem`, `%`, and `auto`.
* Understand why we need to talk about CSS reference pixels and physical pixels. Don't try to memorize the details, but understand the topic well enough that you won't be too surprised the first time you encounter the differences in the wild.
* Use `auto` margins to center block elements horizontally.

#### HTML

Don't try to memorize any new HTML elements you meet in this lesson.

#### CSS

Become comfortable with the CSS `display`, `box-sizing`, `width`, `height`, `padding`, `border`, and `margin` properties. Memorize this list of properties so you can look up the details when needed.

---

## 2. Everything is a Box

#### Box Properties

Every element box has the following properties (the browser may ignore some of them):

* The **width** and **height** define how much horizontal and vertical space it needs for the _content area_ of the box, which may or may not include the padding and borders. In most cases, the browser can determine the width and height automatically.
* The **padding** is an area that surrounds the content area of the box and separates the content from its border. It is typically opaque and hides anything that it overlays.
* The **border** is a boundary that surrounds the padding.
* The **margin** is a transparent area that lies outside the border and supplies separation between elements.
* The **display** property determines how the browser lays out an element relative to its neighbours.

---

## 3. The Visual Formatting Model

### Block Elements

[Block elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements) appear on almost all web pages: headings, paragraphs, sections, tables, forms, lists, and more are `block` elements.  

Most `block` elements group one or more elements - some of which may themselves be `block`s - into areas of the page. For instance, `header` elements group together elements into a page header. We often call such `block` elements **containers**. The master container (the outermost) is the `body`; every other element belongs to a container.  

By default, a `block` element occupies all horizontal space available within its container, with nothing to the left or right of the `block`. If your page contains 3 `block` elements directly inside the `body` element and nothing else, then all three elements will display one above the other like a stack of blocks. This behavior makes `block` elements predictable and easy to use.  

`block` elements use the box properties (`width`, `height`, `padding`, `border`, `margin`) to determine the size of the element. The browser reserves a box of the right size on the page, and this is where it draws the content.  

Most elements are `block` elements by default. Here are some of the most common:

- `section`, `article`, `aside`, `header`, `footer`
- `p`
- `h1` through `h6`
- `blockquote`
- `ul`, `ol`, `dl`
- `figure` and `figcaption`
- `form` and `fieldset`

You can convert any element to a `block` element with the `display: block` CSS property. It's common to render links (`a`) and images (`img`) as `block` elements.

### Inline Elements

[Inline elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements) provide a small bit of semantic meaning to content; browsers use this to alter the way they display small sections of text, which, in turn, helps the reader spot specific items with ease. For instance, if you want to use bolded text for definitions, you can use the `b` element to render definitions in boldface. The reader can see at a glance where the definitions are in the document. By default, `b` is an `inline` element.  

The following elements are `inline` by default.  

- `span`
- `b`, `i`, `u`, `strong`, `em`
- `a`
- `sub` and `sup`
- `img`

`inline` elements handle the dimension properties (`width`, `height`, `padding`, `border`, and `margin`) differently from the way `block` elements treat them. This difference is where the box model starts to get messy. Browsers handle *left* and *right* margins and padding for `inline` elements in the same way as for `block` elements, but they process other box model properties differently. For `inline` elements, browsers:  

- *ignore* the `width` and `height` properties (except with the `img` element), but instead use values computed from the element content.
- *ignore* top and bottom margins.
- *don't ignore* borders, but the results may look odd (see the next section).
- *don't ignore* top and bottom padding, but you won't notice this unless you have a border or background.

You can convert any element to an `inline` element with the `display: inline` CSS property. The most common reason to do so is to override a prior declaration.  

### Inline-Block Elements

`inline-block` elements are a mixture of both previous types. They act like `block` elements, except for one significant detail: `inline-block` elements do not take up an entire row when the `width` property is less than the available width. Instead, they flow in the same way that text and `inline` elements flow from one line to the next (see Figures 1 and 2 on the previous page), which lets you place `inline-block` elements side-by-side with other `inline` or `inline-block` elements.  

`inline-block` elements also differ from `inline` in that `inline-block` elements observe the `width` and `height` properties. The padding, borders, and margin all work like they do with `block` elements.  

Browsers perform vertical alignment for adjacent `inline-block` elements as well as ordinary `inline` elements.

You can convert any element to an `inline-block` element with the `display: inline-block` CSS property. A useful application for this is to arrange the contents of a list horizontally instead of vertically; horizontal navigation bars often use list elements defined as `inline-block`.

### Other Visual Display Models

As mentioned earlier, there are around two dozen visual display models. Some show up in routine development. For instance, list items default to a `list-item` display model, while table cells have a `table-cell` display model. You won't use these models a lot in practice, so don't bother trying to memorize them. However, some of the variants are sometimes useful. Let an expert tell you when.  

As of 2018, two new `display` properties seem poised for widespread growth: `flex` and `grid`. These properties solve a lot of design problems that plague front-end developers today. It will take some time for best practices to emerge on how and when to use them, but widespread use is coming soon. We'll introduce both in a later lesson.  

---

## Box Sizing

The important takeaways here are:

* The usable `box-sizing` property values are `content-box` and `border-box`. The CSS standard deprecates the `padding-box` setting; **don't use it**.

* The `content-box` setting is the default setting for the `box-sizing` property for all elements in all modern browsers. In this model, the `width` and `height` properties specify the size of the actual content area. You need to add padding and borders to get the size of the visible box.

* The `border-box` setting causes the browser to interpret the `width` and `height` properties as the total width and height of the box excluding the margins. That is, the width and height include the content area as well as the padding and borders.

* The `border-box` setting is the "best" since it simplifies the math a front-end developer must do. For example, if we have a box with a width of 50% and padding of 12px; `border-box` ensures that it's precisely 50% of the container width, not 50% plus 24-pixels.

* If you want to use border-box pretty much everywhere, you can add the following to your CSS:

  ```css
  html {
    box-sizing: border-box;
  }
  
  *, *::before, *::after {
    box-sizing: inherit;
  }
  ```

---

## 5. Practice Problems: The Box Model

1. Given the code below, what is the minimum width and height (in pixels) that the `div` needs to entirely contain the `img` element (including its margins)?

   ```html
   <div>
     <img src="#" alt="test" />
   </div>
   ```

   ```css
   div {
     background-color: lightgray;
     border: 1px solid black;
     box-sizing: border-box;
     display: inline-block;
     margin: 0;
     padding: 0;
   }
   
   img {
     border: 4px solid red;
     box-sizing: content-box;
     display: inline-block;
     height: 300px;
     margin: 20px 19px 10px 11px;
     padding: 10px 20px;
     width: 500px;
   }
   ```

   ###### My Solution:

   height = 300 + 20 + 10 + 10 + 10 + 2(4) = 358

   width = 500 + 19 + 11 + 20 + 20 + 2(4) = 578

   Based on the above code the minimum width and height that the `div` needs to entirely contain the `img` element (including its margins) is: minimum width = 578px; and minimum height = 358px.

   ###### LS Solution:

   Since the `img` has `display: inline-block`, we can compute the dimensions directly from the CSS properties. The element needs 580 pixels horizontally:

   - 500 pixels for the width
   - 8 pixels for the left and right borders
   - 40 pixels for the left and right padding
   - 11 pixels for the left margin
   - 19 pixels for the right margin
   - 2 pixels for the left and right borders of the `div`

   It needs 360 pixels vertically:

   - 300 pixels for the height
   - 8 pixels for the top and bottom borders
   - 20 pixels for the top and bottom padding
   - 20 pixels for the top margin
   - 10 pixels for the bottom margin
   - 2 pixels for the top and bottom borders of the `div`

   Since the `div` uses `border-box` box-sizing, it must have a width and height of at least 580px and 360px, respectively.

   While we don't typically count margins in determining an element's height and width, we need to include them here when calculating how much space we need in the `div`.

2. Given the code below, what is the minimum width and height (in pixels) that the `div` needs to entirely contain the `section` element (including its margins)? How does this differ from the result of the previous practice problem?

   ```html
   <div>
     <section>content</section>
   </div>
   ```

   ```css
   div {
     background-color: lightgray;
     border: 1px solid black;
     box-sizing: border-box;
     display: inline-block;
     margin: 0;
     padding: 0;
   }
   
   section {
     border: 4px solid red;
     box-sizing: content-box;
     display: block;
     height: 300px;
     margin: 20px 19px 10px 11px;
     padding: 10px 20px;
     width: 500px;
   }
   ```

   ###### My Solution:

   We need the same minimum width (580px) and minimum height (360px).

   ###### LS Solution:

   Since the `section` element is a `block` element, we can compute the dimensions directly from the CSS properties. The element needs 580 pixels horizontally:

   - 500 pixels for the width
   - 8 pixels for the left and right borders
   - 40 pixels for the left and right padding
   - 11 pixels for the left margin
   - 19 pixels for the right margin
   - 2 pixels for the left and right borders of the `div`

   It needs 360 pixels vertically:

   - 300 pixels for the height
   - 8 pixels for the top and bottom borders
   - 20 pixels for the top and bottom padding
   - 20 pixels for the top margin
   - 10 pixels for the bottom margin
   - 2 pixels for the top and bottom borders of the `div`

   Since the `div` uses `border-box` box-sizing, it must have a width and height of at least 580px and 360px, respectively. These values are identical to the answer from the previous practice problem. The chief difference is that other elements may appear adjacent to the `img` in problem 1, while the `section` in this problem will always be on a line by itself within the `div` no matter its width.

3. Given the code below, what is the minimum width and height (in pixels) that the `div` needs to entirely contain the `em` element (including its margins)?

   ```html
   <div>
     <em>content</em>
   </div>
   ```

   ```css
   div {
     background-color: lightgray;
     border: 1px solid black;
     box-sizing: border-box;
     display: inline-block;
     margin: 0;
     padding: 0;
   }
   
   em {
     border: 4px solid red;
     box-sizing: content-box;
     display: inline;
     height: 300px;
     margin: 20px 19px 10px 11px;
     padding: 10px 20px;
     width: 500px;
   }
   ```

   ###### LS Solution:

   This code is a bit tricky. Since the `em` element is `inline`, the browser will ignore the width, height, and top and bottom margins specified in the CSS. For this reason, we cannot calculate the amount of space that any given `em` will take unless we know the actual width and height of the content.

   If we assume the `em` requires a 50px width, then the element needs 130 pixels horizontally:

   - 50 pixels for the assumed width
   - 8 pixels for the left and right borders
   - 40 pixels for the left and right padding
   - 11 pixels for the left margin
   - 19 pixels for the right margin
   - 2 pixels for the left and right borders of the `div`

   If we assume the `em` requires a 20px height, then it needs 50 pixels vertically:

   - 20 pixels for the assumed height
   - 8 pixels for the top and bottom borders
   - 20 pixels for the top and bottom padding
   - 0 pixels for the top and bottom margins
   - 2 pixels for the top and bottom borders of the `div`

   Since the `div` uses `box-sizing`, it must have a `width` of at least 130px and a height of at least 50px.

   Keep in mind that the top and bottom padding and borders may intersect with content above and below the `em` element.

4. Given the code below, what is the minimum width and height (in pixels) that the `div` needs to be to entirely contain the `article` element (including its margins)?



