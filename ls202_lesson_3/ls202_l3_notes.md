##### LS202 HTML and CSS > Lesson 3: Images

---

## 1. Introduction

## 2. Image Types

* JPG
* PNG
* GIF

---

## 3. Adding Images to Web Pages

`<img>` is a self-closing tag that tells the browser to load and display a foreground image from a separate resource. It has four attributes of particular interest:

* The `src` attribute is required. It tells the browser where to find the image. It uses the same URL format as links in the `<a>` tag and can be relative, root-relative, or absolute.

* The `alt` attribute is optional, but one should almost always use it. It describes the content of the image as an aid for users who cannot see it or that have images disabled. If you have a picture of Da Vinci's smarter sister, Lucrezia, you should say so in the `alt` attribute value. Most browsers display the `alt` text when an image is unavailable or when images have been disabled.

  Screen readers, specialized browsers that read web pages aloud for people with vision problems, use the `alt` attribute to tell the user about image content. Without `alt`, the user has no idea what the image shows. They may not even know it is present: some reader software treats images with no `alt` text as non-essential, so they skip over them while reading the screen.  

  Search engines use `alt` to index images, which makes it relevant for search engine optimization (SEO).  

  If you omit the `alt` attribute, your browser can still render the image. Existing standards require the `alt` attribute *in most cases* to provide text that the browser can display when the image is unavailable. Your HTML won't validate on the W3C validator unless you use the `alt` attribute. If your image isn't significant enough to require an `alt` attribute, you can specify an empty value with `alt=""`. (There are some specific exceptions to this rule, but you should ignore them for this course.)  

* The `width` and `height` attributes are also optional. They provide the width and height of the image in pixels. The CSS `width` and `height` properties override the HTML attributes in the rendered version of the page.

  If you plan to almost always display images with a specific width and height, then you should use the attributes to specify those values. That lets your browser optimize the rendering speed by allocating room for your image before it finishes downloading.  

  In many cases, however, you won't know the specific width and height in advance, especially if the image's size is dependent on the output device. For instance, mobile devices often render images at a smaller size than in a desktop browser. In such cases, providing the `height` and `width` attributes may lead to worse overall performance. Instead, use the `height` and `width` CSS properties exclusively.   

---

## 4. Practice Problems: Images and Figures

These practice problems use [this image](https://d3jtzah944tvom.cloudfront.net/202/images/lesson_3/cats.jpg) which you can download to your system or use directly from its current location, `https://d3jtzah944tvom.cloudfront.net/202/images/lesson_3/cats.jpg`.

1. Write HTML to display the image. Don't use a `<figure>` or `<figcaption>` right now.

   ###### My Solution

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>Image Practice</title>
       <meta charset="utf-8" />
     </head>
     <body>
       <img src="https://d3jtzah944tvom.cloudfront.net/202/images/lesson_3/cats.jpg" alt="A couple of cats" />
     </body>
   </html>
   ```

2. Use CSS to set the width of the image to 250 pixels.

   ```css
   img {
     width: 250px;
   }
   ```

3. Update the CSS width from the previous problem with a height of 350 pixels.

   ```css
   img {
     height: 350px;
   }
   ```

4. Set the width of the image to 400 pixels, but keep the height at 350px.

   ```css
   img {
     height: 350px;
     width: 400px;
   }
   ```

5. Remove the CSS for the `img` element, and wrap the `<img>` in a `<figure>` tag with a yellow background.

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <title>Image Practice</title>
       <meta charset="utf-8" />
       <style>
         figure {
           background-color: yellow;
         }
       </style>
     </head>
     <body>
       <figure>
         <img src="https://d3jtzah944tvom.cloudfront.net/202/images/lesson_3/cats.jpg"
              alt="A couple of cats" />
       </figure>
     </body>
   </html>
   ```

6. Add a caption below the image.

   ```html
   <figure>
     <img src="https://d3jtzah944tvom.cloudfront.net/202/images/lesson_3/cats.jpg"
          alt="A couple of cats" />
   	<figcaption>A couple of cats being a couple of cats.</figcaption>
   </figure>
   ```

7. Move the caption above the image.

   ```html
   <figure>
     <figcaption>A couple of cats being a couple of cats.</figcaption>
     <img src="https://d3jtzah944tvom.cloudfront.net/202/images/lesson_3/cats.jpg"
          alt="A couple of cats" />
   </figure>
   ```

---

## 5. Guided Project: A Simple Photo Gallery

