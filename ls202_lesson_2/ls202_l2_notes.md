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

   ```html
   <div>
     <article>content</article>
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
   
   article {
     border: 4px solid red;
     box-sizing: border-box;
     display: inline-block;
     height: 300px;
     margin: 20px 19px 10px 11px;
     padding: 10px 20px;
     width: 500px;
   }
   ```

   ###### My Solution

   Minimum width: 500 + 19 + 11 = 530  

   Minimum height: 300 + 20 + 10 = 330

   ###### LS Solution

   Since the `article` is `inline-block`, we can compute the dimensions directly from the CSS properties. Since we also set the `box-sizing` property to `border-box`, we must ignore the padding and border to calculate the actual dimensions. The element needs 532 pixels horizontally:

   - 500 pixels for the width
   - 0 pixels for the left and right borders
   - 0 pixels for the left and right padding
   - 11 pixels for the left margin
   - 19 pixels for the right margin
   - 2 pixels for the left and right borders of the `div`

   It needs 332 pixels vertically:

   - 300 pixels for the height
   - 0 pixels for the top and bottom borders
   - 0 pixels for the top and bottom padding
   - 20 pixels for the top margin
   - 10 pixels for the bottom margin
   - 2 pixels for the top and bottom borders of the `div`

   Since the `div` uses `box-sizing`, it must have a `width` of at least 532px and a height of at least 332px.

5. Given the code below:

   ```html
   <div>
     <tag1>content</tag1><tag2>content</tag2>
   </div>
   ```

   ```css
   div {
     background-color: lightgray;
     border: 1px solid black;
     box-sizing: content-box;
     display: inline-block;
     margin: 0;
     padding: 0;
     width: 720px;
   }
   
   tag1, tag2 {
     box-sizing: border-box;
     height: 240px;
     margin: 0;
     padding: 0;
     width: 360px;
   }
   
   tag1 {
     background-color: yellow;
   }
   
   tag2 {
     background-color: lime;
   }
   ```

   Which of the following element pairs will display side-by-side in the `<div>`? Select all that apply:

   1. Both elements are `block` elements.
   2. Both elements are `inline` elements.
   3. Both elements are `inline-block` elements.
   4. One element is a `block` element, and one is an `inline` element.
   5. One element is a `block` element, and one is an `inline-block` element.
   6. One element is an `inline` element, and one is an `inline-block` element.

   ###### My Solution

   1. No (correct)
   2. Yes (correct)
   3. Yes (uncertain)
   4. Yes (incorrect)
   5. No (uncertain)
   6. Yes (uncertain)

   ###### LS Solution

   Combinations (2), (3), and (6) will all appear side-by-side. The other three combinations have `block` elements which never appear side-by-side with anything.

6. Will the following code display the two article boxes side-by-side? If not, why not? How would you fix it so that it places the boxes side-by-side?

   ```html
   <section>
   	<article>content</article><article>more content</article>
   </section>
   ```

   ```css
   section {
     background-color: yellow;
     border: 1px solid red;
     box-sizing: content-box;
     display: inline-block;
     height: 400px;
     margin: 0px;
     padding: 20px;
     width: 900px;
   }
   
   article {
     background-color: lime;
     border: 1px solid blue;
     height: 100%;
     margin: 0;
     padding: 10px;
     width: 50%;
   }
   ```

   ###### My Solution

   No, the two article boxes will not fit side-by-side, because they are both block elements. If we change the `display` property in the `article` element selector to `inline-block` and adjust the `width` property to a maximum `428px` then the two article boxes will appear side-by-side.

   ###### LS Solution

   The browser won't display the article boxes side-by-side since they are `block` elements. Even if we could place the `block` elements side-by-side, they won't fit inside the section because the total width of each article is 50% of the width plus 22 pixels for its padding and border.

   The first change we must make is to add `display: inline-block;` to the CSS `article` selector, which lets us position two or more articles side-by-side, provided there is room. To make them fit, we must set the actual width (including padding and the border) to 50% of the available space, so we also add `box-sizing: border-box;` to the `article` selector.  

   ```css
   article {
     background-color: lime;
     border: 1px solid blue;
     box-sizing: border-box;
     display: inline-block;
     height: 100%;
     margin: 0;
     padding: 10px;
     width: 50%;
   }
   ```

7. **Challenge.** Given our solution to the previous question, what will happen if we put the `article` tags on separate lines?

   ```html
   <section>
     <article>content</article>
     <article>more content</article>
   </section>
   ```

   Try to figure out the answer without peeking. Why do you think this is?

   ###### My Solution

   It should not have any affect on the outcome. Putting elements on newlines within html code does not affect the structure of the html and its display by the browser.

   ###### LS Solution

   When you put the `article` elements on separate lines in the HTML, the browser sees the whitespace (a newline and several spaces in this case) between the two articles. It then collapses that whitespace into a single space character and uses the result as content between the elements. Thus, the two articles require 900 pixels total plus a few more pixels to account for the space character. Since that exceeds the 900-pixel width of the `section`, the two `article`s no longer fit on the same line.

   This kind of problem often occurs when one of the elements is an inline-block; the rest of the time, the extra space typically doesn't matter. Aside from placing the two tags up against each other to eliminate the whitespace, there are several other techniques you will see later that let you remove the space or make it invisible.

---

## 6. Padding and Margins

### What is the Difference Between Padding and Margins?

* Both padding and margins surround elements with whitespace. Padding lies inside the border, while margins lie outside it. What if you don't have one? You do - it has zero-width, so it's an invisible border, but the browser knows it's there and uses it in the box model.
* Margins are typically transparent, while the padding is opaque.
* Put another way, padding is part of the visible and clickable bounds of an element, while a margin is spacing between adjacent elements. It's easy to see this with clickable elements. If you click on the content area or anywhere in the padding or border, the browser will process the click. If you click on the margin, nothing happens.

#### Margins, Padding, and Backgrounds

* The background of an element appears in the padding area, while that of a container shows through the contained element's margins.

#### Top and Bottom Margins and Padding on Inline Elements

* As we learned earlier, the browser doesn't use the top and bottom margins and padding for `inline` elements for spacing. New developers often forget this, which leads to headaches as they try to figure out why the margins or padding aren't working the way they expect. No matter how big the top and bottom margins are on an `inline` element, they do not affect the placement of the element's content nor the content surrounding it. See the example under *Borders, Padding, and Inline Elements* in *The Visual Formatting Model* assignment.

#### Margin Collapse

* An even bigger difference between margins and padding is that top and bottom margins "collapse" between `block` elements. If you position two adjacent `block's one above the other, the margin between them isn't the sum of the bottom margin of the first and the top margin of the second. Instead, the margin collapses to the larger of the two margins in question. For instance, assume that we have the following HTML:

  ```html
  <p>This is the first sentence</p>
  <p>This is the second sentence</p>
  ```

  We also have the following CSS:

  ```css
  p {
    margin-bottom: 15px;
    margin-top: 32px;
  }
  ```

  The spacing between the two paragraphs won't be 47 pixels--it'll be 32 pixels.

* Margin collapse occurs with top and bottom margins, not with left and right margins. Padding does not collapse.

### Should I Use Padding or Margins?

There's no firm answer to this question, but one useful strategy is to use margins for spacing between elements, and padding to affect the visible or clickable area of one. Within a container, use padding for horizontal separation between its edges and content, and margins for the vertical distance.  

This approach works well but sometimes leaves you wondering about the correct choice. Another technique is to use margins everywhere except when you need padding. You probably need to use padding when:

- You want to change the height or width of a border.
- You want to adjust how much background is visible around an element.
- You want to alter the amount of clickable area.
- You want to avoid margin collapse.
- You want some horizontal spacing to the left or right of an `inline` element.
- As before, use padding to separate the left and right sides of a container from its content. Use margins for the vertical gap.

This approach is a simple mechanical process: ask yourself whether any of the above options apply to the element. If any do, use padding to provide those features. Otherwise, use margins. This strategy doesn't guarantee that you will make the correct choice between padding and margins in every situation. However, it should help you choose the right property most of the time.

---

## 7. Dimensions

Some CSS properties require lengths as property values to provide the size of some detail on the page. For instance, we've used the `width`, `height`, `margin`, `padding`, and `border` properties to specify the characteristics of element boxes and their attributes. We've also seen a few instances of using `font-size` to specify the text size. Each of these properties includes a length specification, such as `12px`, `3rem`, or `50%`; we call these values **measurements** or **dimensions**. We also call `px`, `rem`, `%`, etc. **measurement units** or **units**.

### When to Use the Different Units

Trying to decide which dimensional units you should use is sometimes difficult. Here are some general guidelines - none of these are absolute, and you will almost certainly find developers that disagree:

- Use absolute units sparingly, and stick with pixels. Pixels work well for:
  - the root font size
  - image widths and heights
  - top and bottom margins and padding, sometimes useful with left and right margins and padding
  - width or height of fixed-width/fixed-height containers such as navigation sidebars
  - border widths
- Use relative units liberally:
  - Use rems for fonts, possibly with a fallback to ems or pixels. The root font should use pixels.
  - If you must use ems instead of rems, try to avoid compounding font sizes.
  - Use rems, ems, or pixels for left and right margins and padding.
  - Use `%` for measurements that are proportional to the container element's width or height. Percentages work best for container dimensions and come in handy when you want certain areas of the page to grow and shrink as the width of the browser window changes.
  - Use `auto` with `width` and `height` to let the browser calculate an appropriate value.
  - Use `auto` with left and right margins to left, center, or right justify a block element within its container.

You can ignore or break any of these rules when appropriate. We violate them often in this course.

---

## 8. Practice Problems: Spacing and Dimensions

