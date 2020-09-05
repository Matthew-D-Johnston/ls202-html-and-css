##### LS202 HMTL and CSS > Lesson 4: Lists and Tables

---

## 1. Introduction

## 2. Lists Overview

Three list types:

* unordered
* ordered 
* description

### Unordered Lists

Unordered lists contain a series of unordered items. By unordered, we mean that there is no visual numbering or naming system for the items in the list. The content itself may have an implicit ordering, perhaps alphabetical, but the browser displays a **bullet** -- a glyph that looks like a small dot, disc, circle, or square -- instead of a number or letter before each item. By default, browsers render unordered lists vertically, each proceeded by a bullet. However, you can choose a horizontal display and hide the bullets. You can even use custom bullets.

### Ordered Lists

Ordered lists have ordered content; that is, they have a sequence that is a visual component of the list. By default, most browsers render a vertical list of numbered items, but you can change this to roman numbers as well as alphabetic letters, including foreign alphabets. Examples of ordered lists include a numbered list of the top 10 programming languages or a numbered list of the steps required to make a pot of coffee.

### Description Lists

Description lists (called definition lists before HTML5) contain a list of terms and definitions. Each item in the list includes one or more terms and one or more definitions. Examples of description lists include dictionaries, bibliographies, and, that relic of the past, the phone book.  

HTML uses the `<dl>`, `<dt>` and `<dd>` tags to construct description lists. Here's a simple example:

```html
<dl>
  <dt>Unordered</dt>
  <dd>A simple list with bullets.</dd>
  <dd>A plain list with no bullets or sequence numbers.</dd>

  <dt>Ordered</dt>
  <dd>A simple list with sequence numbers or letters.</dd>

  <dt>Description</dt>
  <dt>Definition</dt>
  <dd>A list with terms and definitions.</dd>
</dl>
```

### Navigation Menus

For a horizontal list:

* Set the width of the menu (`ul`).
* Set the font for the list (`ul`) to 0, then restore it for the list items (`li`).
* Set the list items to `inline-block`.
* Set the width of the list items to a value that will distribute the values the way you want them distributed (typically, you want a percentage width).
* Center the list items horizontally.

```html
<nav>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">Projects</a></li>
    <li><a href="#">Team</a></li>
    <li><a href="#">Help</a></li>
  </ul>
</nav>
```

```css
nav ul {
  font-size: 0;
  width: 100%;
}

nav li {
  display: inline-block;
  font-size: 1.25rem;
  text-align: center;
  width: 25%;
}
```

---

## 3. Practice Problems: Lists

1. Using the "Raw Text" shown below, create a Web page that looks like the image pictured below it.

   **Raw Text**

   ```plaintext
   The Next Reckoning: Capitalism and Climate Change
   By NATHANIEL RICH
   The world’s most difficult problem has a solution so simple that it can be
   expressed in four words: Stop burning greenhouse gases. How exactly to pull
   this off is somewhat more complicated — just not as complicated as most
   Americans have been led to believe.
   
   Related articles
   What Survival Looks Like After the Oceans Rise
   How Big Business is Hedging Against the Apocalypse
   Climate Chaos is Coming–and the Pinkertons Are Ready
   ```

   **How it should look in your browser:**

   ![Climate Change Article](https://d3jtzah944tvom.cloudfront.net/202/images/lesson_4/climatechange.png)

   ###### My Solution

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>List Practice</title>
       <meta charset="utf-8" />
       <style>
         body {
           width: 46%;
           font-size: 16px;
         }
   
         h1 {
           font-size: 2rem;
         }
       </style>
     </head>
     <body>
       <article>
         <h1>The Next Reckoning: Capitalism and Climate Change</h1>
         <p>By NATHANIEL RICH</p>
         <p>
           The world’s most difficult problem has a solution so simple that it can be
           expressed in four words: Stop burning greenhouse gases. How exactly to pull
           this off is somewhat more complicated — just not as complicated as most
           Americans have been led to believe.
         </p>
         <h2>Related article</h2>
         <ul>
           <li>What Survival Looks Like After the Oceans Rise</li>
           <li>How Big Business is Hedging Against the Apocalypse</li>
           <li>Climate Chaos is Coming–and the Pinkertons Are Ready</li>
         </ul>
       </article>
     </body>
   </html>
   ```

   ###### LS Solution

   ```html
   <header>
     <h1>The Next Reckoning: Capitalism and Climate Change</h1>
     <p>By NATHANIEL RICH</p>
   </header>
   
   <p>
     The world’s most difficult problem has a solution so simple that it can be
     expressed in four words: Stop burning greenhouse gases. How exactly to
     pull this off is somewhat more complicated — just not as complicated as
     most Americans have been led to believe.
   </p>
   
   <h2>Related articles</h2>
   <ul>
     <li>What Survival Looks Like After the Oceans Rise</li>
     <li>How Big Business is Hedging Against the Apocalypse</li>
     <li>Climate Chaos is Coming–and the Pinkertons Are Ready</li>
   </ul>
   ```

   The `header` provides [semantic meaning](https://developer.mozilla.org/en-US/docs/Glossary/Semantics) to the elements that it contains. Here, it shows that the `h1` and `p` tags are part of the page header. You should use `header` consistently with any part of your page that you think of either a page header or a section header.

2. Add CSS to your solution for the previous problem to remove the bullet character before each list item.

   ###### My Solution

   ```css
   ul {
     list-style: none;
   }
   ```

   ###### LS Solution

   ```css
   ul {
     list-style-type: none;
   }
   ```

3. Using the "Raw Text" shown below, create a Web page that looks like the image pictured below it.

   ###### My Solution

   ```html
   <header>
     <h1>5 Reasons to Use jQuery</h1>
   </header>
   <ol>
     <li>Open Source</li>
     <li>Endless Tutorials</li>
     <li>Huge Library</li>
     <li>Cross-browser Compatibility</li>
     <li>Large Variety of Plugins</li>
   </ol>
   ```

   ###### LS Solution

   ```html
   <h1>5 Reasons to Use jQuery</h1>
   <ol>
     <li>Open Source</li>
     <li>Endless Tutorials</li>
     <li>Huge Library</li>
     <li>Cross-browser Compatibility</li>
     <li>Large Variety of Plugins</li>
   </ol>
   ```

4. Add CSS to your solution for the previous problem to change the numbers from decimal to uppercase Roman digits (I, II, III, IV, V).

   ###### My Solution

   ```css
   ol {
     list-style-type: upper-roman;
   }
   ```

   ###### LS Solution

   ```css
   <style>
     ol {
       list-style-type: upper-roman;
     }
   </style>
   ```

5. Update your solution from the previous problem to number the items in descending order (V, IV, III, II, I).

   ###### My Solution

   ```html
   <ol reversed>
     <li>Open Source</li>
     <li>Endless Tutorials</li>
     <li>Huge Library</li>
     <li>Cross-browser Compatibility</li>
     <li>Large Variety of Plugins</li>
   </ol>
   ```

   ###### LS Solution

   ```html
   <h2>5 Reasons to Use jQuery</h2>
   <ol reversed>
     <li>Open Source</li>
     <li>Endless Tutorials</li>
     <li>Huge Library</li>
     <li>Cross-browser Compatibility</li>
     <li>Large Variety of Plugins</li>
   </ol>
   ```

6. Using the "Raw Text" shown below, create a Web page that looks like the image pictured below it.

   **Raw Text**

   ```plaintext
   HTML
   Hypertext Markup Language, a standardized system for tagging text files to
   achieve font, color, graphic, and hyperlink effects on World Wide Web pages.
   
   Semantic
   Relating to meaning in language or logic.
   
   CSS
   A style sheet language used for describing the presentation of a document
   written in a markup language.
   ```

   **How it should look in your browser:**

   ![Definitions](https://d3jtzah944tvom.cloudfront.net/lesson_2/exercises_basic_html/b3.jpg)

   ###### My Solution

   ```html
   <dl>
     <dt>HTML</dt>
       <dd>
         Hypertext Markup Language, a standardized system for tagging text files to
         achieve font, color, graphic, and hyperlink effects on World Wide Web pages.
       </dd>
     <dt>Semantic</dt>
       <dd>
         Relating to meaning in language or logic.
       </dd>
     <dt>CSS</dt>
       <dd>
         A style sheet language used for describing the presentation of a document
         written in a markup language.
       </dd>
   </dl>
   ```

   ###### LS Solution

   ```html
   <dl>
     <dt>HTML</dt>
     <dd>
       Hypertext Markup Language, a standardized system for tagging text files
       to achieve font, color, graphic, and hyperlink effects on World Wide Web
       pages.
     </dd>
     <dt>Semantic</dt>
     <dd>
       Relating to meaning in language or logic.
     </dd>
     <dt>CSS</dt>
     <dd>
       A style sheet language used for describing the presentation of a
       document written in a markup language.
     </dd>
   </dl>
   ```

7. The following code is an attempt to create a vertical navigation list on a web page:

   ```html
   <nav>
     <ul>
       <li>Home</li>
       <li>Projects</li>
       <li>Team</li>
       <li>Help</li>
     </ul>
   </nav>
   ```

   ```css
   html {
     font-size: 20px;
   }
   
   nav ul {
     background-color: yellow;
     width: 200px;
   }
   
   nav li {
     color: blue;
   }
   
   nav a {
     box-sizing: border-box;
     line-height: 2.5;
     padding: 0 10px;
     text-decoration: none;
     width: 100%;
   }
   ```

   Modify the code to remove the bullets. Each item should be 10px from the left edge of the yellow box. When you point to any line in the menu, the browser should highlight the entire line inside the yellow box. The final result should look like this:

   ![Vertical navbar](https://d3jtzah944tvom.cloudfront.net/202/images/lesson_4/vertical-nav.png)

   ###### My Solution

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>List Practice</title>
       <meta charset="utf-8" />
       <style>
         html {
           font-size: 20px;
         }
   
         nav ul {
           background-color: yellow;
           width: 200px;
           padding-left: 0;
         }
   
         nav li {
           color: blue;
           list-style-type: none;
         }
   
         nav a {
           box-sizing: border-box;
           display: block;
           line-height: 2.5;
           padding: 0 10px;
           text-decoration: none;
           width: 100%;
           color: blue;
         }
   
         nav a:hover {
           background-color: green;
           color: yellow;
         }
       </style>
     </head>
     <body>
       <nav>
         <ul>
           <li><a href="#">Home</a></li>
           <li><a href="#">Projects</a></li>
           <li><a href="#">Team</a></li>
           <li><a href="#">Help</a></li>
         </ul>
       </nav>
     </body>
   </html>
   ```

   ###### LS Solution

   ```html
   <nav>
     <ul>
       <li><a href="#">Home</a></li>
       <li><a href="#">Projects</a></li>
       <li><a href="#">Team</a></li>
       <li><a href="#">Help</a></li>
     </ul>
   </nav>
   ```

   ```css
   
   html {
     font-size: 20px;
   }
   
   nav ul {
     background-color: yellow;
     list-style-type: none;
     padding-left: 0;
     width: 200px;
   }
   
   nav li {
     color: blue;
   }
   
   nav a {
     box-sizing: border-box;
     display: inline-block;
     line-height: 2.5;
     padding: 0 10px;
     text-decoration: none;
     width: 100%;
   }
   
   nav a:hover,
   nav a:focus {
     background-color: green;
     color: yellow;
   }
   ```

8. Convert the solution from the last problem to a horizontal navigation bar that takes up the full width of the page. Again, try not to peek at the previous assignment. The final result should look like this:

   ![Horizontal navbar](https://d3jtzah944tvom.cloudfront.net/202/images/lesson_4/horizontal-nav.png)

   ###### My Solution

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>List Practice</title>
       <meta charset="utf-8" />
       <style>
         html {
           font-size: 20px;
         }
   
         nav ul {
           box-sizing: border-box;
           background-color: yellow;
           list-style-type: none;
           padding-left: 0;
           width: 500px;
         }
   
         nav li {
           display: inline-block;
           background-color: yellow;
           padding: 0;
           text-align: center;
           color: blue;
           width: 25%;
         }
   
         nav a {
           box-sizing: border-box;
           display: inline-block;
           line-height: 2.5;
           padding: 0;
           text-decoration: none;
           width: 100%;
         }
   
         nav a:hover,
         nav a:focus {
           background-color: green;
           color: yellow;
         }
       </style>
     </head>
     <body>
       <nav>
         <ul>
           <li><a href="#">Home</a></li><!-- 
            --><li><a href="#">Projects</a></li><!-- 
            --><li><a href="#">Team</a></li><!-- 
            --><li><a href="#">Help</a></li>
         </ul>
       </nav>
     </body>
   </html>
   ```

   ###### LS Solution

   ```css
   nav ul {
     font-size: 0;
     width: 100%;
   }
   
   nav li {
     display: inline-block;
     font-size: 1rem;
     text-align: center;
     width: 25%;
   }
   ```

   

---

