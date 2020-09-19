##### LS202 HTML and CSS > Lesson 6: Advanced Layout

---

## 1. Introduction

#### What to Focus On

In this lesson, we'll take a whirlwind tour of some layout-related features of CSS: floats, positioning, flex, grid, CSS frameworks, and responsive design. None of these topics are easy; in fact, unlike most of our material here at Launch School, **we don't expect you to master them in this lesson**. Instead, familiarize yourself with the concepts and what you can do with them, then use Google and MDN when you need to use them. Master the material we discussed in the previous lessons, but leave advanced layout until you're ready to use it. Don't struggle. When you've had more experience, you will get a better handle on the subject.  

For now, you should know how to use the following in simple projects and problem sets:  

* floated elements, including how to clear floats
* positioning with `position: absolute`
* basic media queries
* liquid and fluid layouts

---

## 2. Floats

## 3. Containing Floats

## 4. Practice Problems: Floats (1)

For these problems, you'll work with two columns of different sizes. You can grab some content for both over at [lipsum.com](http://www.lipsum.com/); generate several paragraphs of copy for both columns. For the best results, the two columns should have differing amounts of text.  

After most problem descriptions, you'll see a screenshot of how your page should look. The background colors help show where each element begins and ends; choose any colors you want.

1. Create a `section` element with a fixed width of 750px, and horizontally center it on the page using CSS margins. Create two columns inside it, a 500px-wide `article` and a 250px-wide `aside`, positioned side-by-side with CSS floats. The left column should contain the `article`. Each column should have `1rem` of whitespace between the text and edges of the container. Add some background colors to the `body`, `section`, `article`, and `aside` `body` so you can see the boundaries of each element.

   ![Fixed width floated columns](https://d3jtzah944tvom.cloudfront.net/202/images/lesson_6/f1.png)

   ###### My Solution

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>Practice Problems: Floats(1)</title>
       <meta charset="utf-8" />
       <style>
         section {
           background-color: #D8DDE6;
           width: 750px;
           margin: auto;
           padding: 0 1.5rem 1.5rem 1.5rem;
           overflow: hidden;
         }
   
         article, aside {
           display: inline-block;
           box-sizing: border-box;
           padding: 1rem;
         }
   
         article {
           background-color: #FCFBC0;
           width: 500px;
           float: left;
         }
   
         aside {
           background-color: #C1FDBE;
           width: 250px;
           float: right;
         }
       </style>
     </head>
     <body>
       <section>
         <article>
           Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.
         </article>
         <aside>
           The standard chunk of Lorem Ipsum used since the 1500s is reproduced below for those interested. Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et Malorum" by Cicero are also reproduced in their exact original form, accompanied by English versions from the 1914 translation by H. Rackham.
         </aside>
       </section>
     </body>
   </html>
   ```

   ###### LS Solution

   ```html
   <section>
     <article>
       <p><!-- lipsum content #1 --></p>
       <p><!-- lipsum content #2 --></p>
         <!-- more content -->
     </article>
     <aside>
       <p><!-- lipsum content #3 --></p>
       <p><!-- lipsum content #4 --></p>
         <!-- more content -->
     </aside>
   </section>
   ```

   ```css
   body, section, article, aside {
     margin: 0;
     padding: 0;
   }
   
   body {
     background-color: #ccc;
   }
   
   section {
     background-color: white;
     margin: 0 auto;
     width: 750px;
   }
   
   article, aside {
     box-sizing: border-box;
     float: left;
     padding: 1rem;
   }
   
   article {
     background-color: #ffc;
     width: 500px;
   }
   
   aside {
     background-color: #cfc;
     width: 250px;
   }
   ```

   You can also float the `aside` to the `right` since the total of the column widths matches that of the container.  

   Note that we need padding to provide the whitespace between the text and the edges of the container. Since we're mixing `padding` with `width`, we should also use `border-box` box-sizing to simplify our calculations.

2. If necessary, add some more text to the `article` to ensure it is noticeably taller than the `aside`. Can you see the background color you set on the section element? Why not? What can you add to your CSS to fix it?

   ###### My Solution

   ```css
   section {
     background-color: white;
     margin: 0 auto;
     width: 750px;
     overflow: hidden;
   }
   ```

   ###### LS Solution

   Since the browser removes floats from the normal flow, the parent element doesn't contain them properly. Thus, the background color doesn't paint to the bottom of the taller column. You need to tell the container (the `section`) to expand itself enough to cover the area used by the taller column. Use `overflow` or a clearfix as desired.

   ```css
   /* Using overflow */
   section {
     overflow: hidden;  /* beware of clipping */
   }
   ```

   ```css
   /* Using clearfix */
   section::after {
     clear: both;
     content: "";
     display: block;
   }
   ```

3. Remove the fixed width of 750px from the `section` and set a maximum width of 1000px instead. Modify the right column to take up the remainder of the space without floating the column or giving it a specific width.

   ###### My Solution

   ```css
   This one had me puzzled
   ```

   ###### LS Solution

   Adding `overflow: hidden` to the last floated element in a row and removing the `float` and `width` properties cause it to take up the remaining space within the row. This technique is useful when your last element should take up the leftover space in a variable width layout.

   ```css
   section {
     max-width: 1000px;
     /* width: 750px; */
   }
   
   aside {
     float: none;
     overflow: hidden;
     /* width: 250px; DELETE */
   }
   ```

   Modify the CSS as shown and watch what happens as you adjust your browser's width. Be sure to narrow your browser down to the point where there is no more room for the `aside` and observe the behavior as you go past that point.  

4. Change the left column from a fixed width to a variable width of 70% of the parent's width.

   ###### My Solution

   ```css
   article {
     background-color: #FCFBC0;
     /*width: 500px;*/
     width: 70%;
   }
   ```

   ###### LS Solution

   If you haven't already done so, use the `box-sizing` property to ensure that your `article` takes up precisely 70% of the row width, rather than 70% plus the padding.

   ```css
   article {
     box-sizing: border-box;
     width: 70%;
   }
   ```

5. Add a `footer` below the two columns.

   ![Clearing columns](https://d3jtzah944tvom.cloudfront.net/202/images/lesson_6/f3.png)

   ###### My Solution

   ```html
   <body>
     <section>
       <article>
         <p>
           Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.
         </p>
         <p>
           It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
         </p>
       </article>
       <aside>
         <p>
           The standard chunk of Lorem Ipsum used since the 1500s is reproduced below for those interested. Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et Malorum" by Cicero are also reproduced in their exact original form, accompanied by English versions from the 1914 translation by H. Rackham.
         </p>
       </aside>
     </section>
     <footer>
       <p>
         Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
       </p>
     </footer>
   </body>
   ```

   ```css
   body, section, article, aside, footer {
     margin: 0;
     padding: 0;
   }
   
   body {
     background-color: #ccc;
   }
   
   section, footer {
     background-color: white;
     margin: 0 auto;
     /*width: 750px;*/
     max-width: 1000px;
     overflow: hidden;
   }
   
   ...
   
   footer {
     box-sizing: border-box;
     background-color: #D5E6F5;
     padding: 1rem;
   }
   ```

   ###### LS Solution

   If you used a clearfix in problem 2, you can remove it and clear the floats with the `footer` element and `clear: both`.

   ```html
   <section>
     <article>
       content
     </article>
     <aside>
       content
     </aside>
     <footer>
       <p><!-- lipsum content #7 --></p>
     </footer>
   </section>
   ```

   ```css
   section {
     /* overflow: hidden; */
   }
   
   /*
   section::after {
     clear: both;
     content: "";
     display: block;
   }
   */
   
   footer {
     background-color: #ebecff;
     clear: both;
     padding: 1rem;
   }
   ```

---

## 5. Practice Problems: Floats (2)

For this problem set, use the Inspector to add CSS properties to the working page and see immediate results. If you need a review of the Inspector, see [the documentation](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/). You must know how to inspect and edit pages and styles for this assignment; you don't need any other developer tools.

1. [Open this page](https://d3jtzah944tvom.cloudfront.net/lesson_4/exercises_floating_positioning/float1.html) then open the Inspector and find the div with the "floated" ID. Select it, then make the `div` float left by updating the styles tab.

   Solution

   The page should now look something like this.

   

   ![Floating a short column](https://d3jtzah944tvom.cloudfront.net/lesson_4/exercises_floating_positioning/float1.jpg)

   

2. Can you determine why the blue paragraph hangs out beneath the right edge of the orange `div`? Add a CSS property to force the blue box beneath the orange; don't worry about the widths - the blue box will be wider than the orange.

   Solution

   ```css
   /* A selector of `#floated + p` will also work */
   main > p {
     clear: both;
   }
   ```

3. Why is the orange container now narrower than the blue? How can you keep the orange box floated but take on the same width as the blue?

   Solution

   When you float an element, it uses as much space as it needs to display its content, which is less than that required by the `main` element. To use all available width, add `width: 100%`.

   ```css
   #floated {
     width: 100%;
   }
   ```

4. Change the floated element's width to 20%, then remove the `clear` from the `p` below it. Try setting a left margin on the blue paragraph equal to the width of the floated element.

   Solution

   This code works to produce a two-column layout here.

   ```css
   #floated {
     width: 20%;
   }
   
   main > p {
     /* clear: both; */
     margin-left: 20%;
   }
   ```

   This code works, but it isn't robust. For instance, if you add a fixed height to the blue paragraph that isn't enough to fully contain the text, the text will overflow. If you add `overflow: hidden` to the blue box, the overflowing text will get clipped. If you add `overflow: auto` instead, you will be able to scroll the blue box.

   Can you find other ways to demonstrate the lack of robustness?

5. Remove the left margin on the blue paragraph, and have it float right instead. What do you think will happen? Will the orange and blue elements sit side-by-side?

   Solution

   The blue element ends up too large to fit within the remaining space. Remember that floated elements take up as much space as they need for the content, within the bounds of any space constraints.

6. Ideally, you want both boxes side-by-side. In an attempt to do that, you add a width of 80% to the blue paragraph. What happens? How can you fix this problem without changing the width setting?

   Solution

   Since the paragraph has 1em of padding on all sides, we need to account for that when we set the width. In fact, as is, the blue box is 80% of the container width plus an additional 2rem. To fix this issue, set the box-sizing mode to `border-box`.

---

## 6. Positioning

## 7. Practice Problems: Positioning

For these problems, create a simple HTML page with a few paragraphs of text. You should have enough content that you must scroll the browser window to read the bottommost content; you can also shorten the window height if you prefer. If you add any elements to the page, add them after the paragraph elements.

1. Starting with a new document, create an element and position it at the top right of the page. It should scroll with the rest of the window when you scroll.

   ###### My Solution

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>your page title goes here</title>
       <meta charset="utf-8" />
       <style>
         .positioned {
           background-color: lightyellow;
           width: 200px;
           height: 100px;
           margin: 0;
           position: fixed;
           right: 0;
           top: 0;
           text-align: center;
           line-height: 100px;
         }
       </style>
     </head>
     <body>
       <p class="positioned">I'm positioned!</p>
       <p>
         The economic impact of COVID-19 has raised the stakes for policy makers everywhere, and central bankers are all in. But perhaps none more so than Jerome Powell, Chairman of the U.S. Federal Reserve. From rate cuts to liquidity support and from swap lines to asset purchase schemes, the Fed has opened up the floodgates. It’s still not clear when they’ll be closed again. But with all this new money gushing into the economy, shouldn’t Chairman Powell, the rest of the FOMC, and everyone else be worried about inflation?
       </p>
       
       ...
       
     </body>
   </html>
   ```

   ###### LS Solution

   ```html
   <section>
     <!-- text paragraphs go here -->
   </section>
   
   <div id="positioned">I'm positioned!</div>
   ```

   ```css
   #positioned {
     background-color: #ffc;
     padding: 30px 15px;
     position: absolute;
     right: 0;
     top: 0;
   }
   ```

   

2. Change the element to remain in the top right of the viewport when the window scrolls.

   ###### My Solution

   ```css
   #positioned {
     position: fixed;
   }
   ```

   

3. Set the element's width to 400px and center it horizontally. Centering positioned elements is tricky, so feel free to check the hints and use Google.

   ###### My Solution

   ```css
   #positioned {
     width: 400px;
     right: 50%;
     margin-right: -200px;
   }
   ```

   ###### LS Solution

   To horizontally center a positioned element with fixed width, you can move it to the center of the container with a `left` offset of 50%, and a negative left margin that is half the width of the element. In our example, we're moving the element from the left edge to the center of the container, then reversing direction by using a negative margin.

   ```css
   #positioned {
     box-sizing: border-box;
     left: 50%;
     margin-left: -200px;
     /* right: 0; */
     width: 400px;
   }
   ```

4. Place a new element between the page contents and the yellow item; by between, we mean in a 3D sense. Consider the page content to be at the bottom of a stack and the yellow at the top; place the new element between the two.

   The new element should take up the full width and height of the page. Use the CSS below to get started; note that it sets the background to a translucent color. The new element should fill the browser's entire window, and it should appear in front of the paragraphs but behind the yellow box.

   ```css
   background-color: rgba(0, 0, 0, .6);
   ```

   ###### My Solution

   ```html
   ...
   
   			<p>
           Companies saying they are finding it hard to find qualified labor is just another way of saying they don’t want to pay to train people, they want the government to do it. If the labor market was tight and the economy was booming, firms would be throwing out all kinds of incentives to attract anybody with two feet and heart beat. Firms would not only train workers, they’d actually offer paid training. Imagine that was the way the world worked. Alas, we’re still waiting.
         </p>
       </section>
       <div id="positioned">I'm positioned!</div>
       <div id="middle"></div>
     </body>
   </html>
   ```

   ```css
   #positioned {
     background-color: #ffc;
     padding: 30px 15px;
     position: fixed;
     box-sizing: border-box;
     right: 50%;
     margin-right: -200px;
     top: 0;
     width: 400px;
     z-index: 1;
   }
   
   #middle {
     background-color: rgba(0, 0, 0, .6);
     height: 100%;
     width: 100%;
     position: fixed;
     z-index: auto;
     top: 0;
   }
   ```

   ###### LS Solution

   To take up the entirety of the window, we can use a width and height of `100%`. We can use z-index values for both elements to position one on top of the other.

   ```html
   <div id="fixed"></div>
   ```

   ```css
   #positioned {
     /* z-index must be greater than that of the elements you want overlay */
     z-index: 2; /* 2 must be > 1 */
   }
   
   #fixed {
     background-color: rgba(0, 0, 0, .6);
     height: 100%;
     left: 0;
     position: fixed;
     top: 0;
     width: 100%;
     z-index: 1; /* 1 must be < 2 */
   }
   ```

5. Create a new element inside the `#positioned` container. Starting with the CSS below, move the new item partially outside the parent's boundaries by 10px to the left and top. To ensure you can see everything, move the parent element down from the top of the page.

   ```css
   ... {
     /* code omitted */
     background-color: pink;
     height: 20px;
     width: 20px;
   }
   ```

   ###### My Solution

   ```html
   <div id="positioned">
     <div id="inside"></div>
     I'm positioned!
   </div>
   ```

   ```css
   #positioned {
     background-color: #ffc;
     padding: 30px 15px;
     position: fixed;
     box-sizing: border-box;
     right: 50%;
     margin-right: -200px;
     top: 20px;
     width: 400px;
     z-index: 2;
     display: inline-block;
   }
   
   #inside {
     background-color: pink;
     height: 20px;
     width: 20px;
     position: relative;
     top: -40px;
     left: -25px;
     display: inline-block;
     box-sizing: border-box;
   }
   ```

   ###### LS Solution

   ```html
   <div id="positioned">
     <span></span>
     I'm positioned!
   </div>
   ```

   ```css
   #positioned {
     top: 20px;
   }
   
   #positioned span {
     background-color: pink;
     height: 20px;
     left: -10px;
     position: absolute;
     top: -10px;
     width: 20px;
   }
   ```

---

## 8. On Your Own: Floats and Positioning