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

