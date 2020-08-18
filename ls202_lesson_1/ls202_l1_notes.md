##### LS202 HTML and CSS > Lesson 1: Your First Web Pages

---

## 1. Welcome

### Where to Find More Information

* Google (or whatever search engine you prefer) is your leading resource when you have a problem or question. Often, all you have to do is ask a question, and one of the top results will provide an answer. For example, try "How do I create superscripts in HTML?" It's also helpful to provide `mdn` or `w3c` in your search to access two of the most useful resources:

  * The [Mozilla Developer Network](https://developer.mozilla.org/), or **MDN**, is perhaps the best resource for extensive and accessible information about the Web, specifically HTML, CSS, and JavaScript. In fact, it's so good that we suggest that you get in the habit of adding **mdn** to your searches. For instance, `mdn form tag` will find the MDN documentation on the `<form>` tag. If MDN fails to help, a more global search will often turn up a video, tutorial, or Stack Overflow question that provides all the information you need.

    MDN is free and continually updated. Mozilla, the makers of the Firefox Web browser, maintains the site. MDN isn't official, but it's up-to-date, generally accurate, and easier to use than the official specification documents at W3C.

  * The [W3C](http://www.w3.org/), the World Wide Web Consortium, is the standards body for Web technologies, so it serves as the official source of information for HTML and CSS. The content is often dry and academic, but it's an essential resource that you shouldn't ignore. You can add the word **w3c** to your searches to find W3C information about specific topics, e.g., `w3c textarea tag`.

  * In mid-2019, W3C announced that it would collaborate with the Web Hypertext Application Technology Working Group, [WHATWG](https://whatwg.org/), on future HTML and DOM standards, effectively giving up control over those standards. The effects of this collaboration are still unclear at this time. However, it may lead to more rapid development of HTML and DOM standards. The most recent standards documents for the HTML and browser DOM standards can be located at the WHATWG site:

    * [HTML Standard](https://html.spec.whatwg.org/multipage/)
    * [DOM Standard](https://dom.spec.whatwg.org/)

* If you omit "mdn" or "w3c" from the search query, the first result is often from a website called W3 Schools. Material from this site is frequently outdated and incorrect. We suggest that you steer clear of those results.

  Don't confuse W3 Schools with W3C; W3C has no affiliation with W3 Schools.

---

## 2. Introduction

### What to Focus On

#### Vocabulary

As with everything else in the developer's world, there's a wealth of specialized terminology you must learn to converse with other developers and designers. The vocabulary you need here, though, is small compared to most languages, and most terms are easy to learn. In particular, you should become comfortable with:

* element and tag
* self-closing tag
* document type definition (DOCTYPE, DTD)
* attribute
* selector
* property
* id, class, and name

#### The Difference Between HTML and CSS

These two technologies are so intertwined in contemporary Web pages that it seems like they do the same thing, and that they are dependent on each other. However, they are distinct and independent with different purposes. **HTML provides the structure and content of a web page; CSS describes the appearance, or presentation, of the page.** There is a bit of overlap that can lead to some confusion: CSS can dictate the apparent structure, while HTML can inform the browser of some presentation elements.

#### HTML and CSS Syntax

HTML and CSS both have simple syntax; you can learn nearly all you need for each language in a few minutes. Take the time you need to learn it well, and both HTML and CSS will become routine in no time.

For the most part, you shouldn't worry about the specific tags, attributes, selectors, and properties yet. Instead, focus on how to put these items together to create well-formed HTML and CSS. The rest will come with time and practice.

#### Structure of a Web Page

All web pages start with some routine code that defines the basic layout of the document. It includes a DOCTYPE (we'll explain this later), an `<html>`, `<head>`, and `<body>` element, and a few other tags in the `<head>` section. Learn what this boilerplate code does, and how to use it in your web pages.

#### Basic HTML Elements

The best way to learn HTML is to use it. The more you use it, the less often you'll need to refer to the documentation; however, you'll probably never learn it all, so don't try.

Start by learning to use the `<p>` (paragraph), `<a>` (anchor), and `<h1>`-`<h6>` elements. Paragraphs are the primary organizational construct for text on web pages, and anchors represent links to other pages, while headings occur on most pages. These elements are so common that you want to learn them as soon as possible, so go ahead and memorize them.

You should also become familiar with these elements:

- `<em>`, `<strong>`
- `<header>`, `<main>`
- `<article>`, `<section>`, `<aside>`
- `<div>` and `<span>`

You don't have to know them by heart; you will remember them through repeated use.

#### Using CSS With HTML

Become familiar with the three ways to use CSS in an HTML document: inline, internal, and external. For now, you should learn to use the `<style>` tag to provide internal CSS.

#### Basic CSS Selectors

CSS has three primary types of selectors (tag, id, and class) that select elements based on the tag name, `id` attribute, or `class` attribute. Learn the syntax for these three selectors, but don't get bogged down trying to memorize how you can combine them. For now, rely on the documentation.

#### CSS Properties

Stick to the documentation as you start out; don't try to memorize CSS properties until you've used them a few times and seen how they work and interact with your HTML. This way, you'll learn the features you need most often without spending a lot of time absorbing material that you may never use.

The most important properties introduced in this lesson are `color`, `background-color`, `font-family`, and `font-size`; we recommend memorizing these. The other properties you see in this lesson will become familiar with time and practice.

---

## 3. Install Software

## 4. Getting Started

### Read the Tutorial

#### 1. [Building Your First Web Page](https://learn.shayhowe.com/html-css/building-your-first-web-page/)

This tutorial introduces the vocabulary of HTML and CSS and demonstrates a few of the most common tags and rules.

##### Understanding Common HTML Terms:

* While getting started with HTML, you will likely encounter new—and often strange—[terms](http://www.scriptingmaster.com/html/HTML-terms-glossary.asp). Over time you will become more and more familiar with all of them, but the three common HTML terms you should begin with are *elements*, *tags*, and *attributes*.
* **Elements:** Elements are designators that define the structure and content of objects within a page. Some of the more frequently used elements include multiple levels of headings (identified as `<h1>` through `<h6>` elements) and paragraphs (identified as the `<p>` element); the list goes on to include the `<a>`, `<div>`, `<span>`, `<strong>`, and `<em>` elements, and many more.
* **Tags:** The use of less-than and greater-than angle brackets surrounding an element creates what is known as a *tag*. Tags most commonly occur in pairs of opening and closing tags.
* **Attributes:** *Attributes* are properties used to provide additional information about an element. The most common attributes include the `id` attribute, which identifies an element; the `class` attribute, which classifies an element; the `src` attribute, which specifies a source for embeddable content; and the `href` attribute, which provides a hyperlink reference to a linked resource.

##### Setting Up the HTML Document Structure:

* All HTML documents have a required structure that includes the following declaration and elements: `<!DOCTYPE html>`, `<html>`, `<head>`, and `<body>`.

  ```html
  <!DOCTYPE html>
  <html>
    <head>
      
    </head>
    <body>
      
    </body>
  </html>
  ```

##### Understanding Common CSS Terms

* In addition to HTML terms, there are a few common [CSS terms](http://www.impressivewebs.com/css-terms-definitions/) you will want to familiarize yourself with. These terms include *selectors*, *properties*, and *values*. 

* **Selectors:** 

  * As elements are added to a web page, they may be styled using CSS. A *selector* designates exactly which element or elements within our HTML to target and apply styles (such as color, size, and position) to. Selectors may include a combination of different qualifiers to select unique elements, all depending on how specific we wish to be. For example, we may want to select every paragraph on a page, or we may want to select only one specific paragraph on a page.

  * Selectors generally target an attribute value, such as an `id` or `class` value, or target the type of element, such as `<h1>` or `<p>`.

  * Within CSS, selectors are followed with curly brackets, `{}`, which encompass the styles to be applied to the selected element. The selector here is targeting all `<p>` elements.

    ```css
    p { ... }
    ```

* **Properties:**

  * Once an element is selected, a property determines the styles that will be applied to that element. Property names fall after a selector, within the curly brackets, `{}`, and immediately preceding a colon, `:`. There are numerous properties we can use, such as `background`, `color`, `font-size`, `height`, and `width`, and new properties are often added. In the following code, we are defining the `color` and `font-size` properties to be applied to all `<p>` elements.

    ```css
    p {
      color: ...;
      font-size: ...;
    }
    ```

* **Values:**

  * So far we’ve selected an element with a selector and determined what style we’d like to apply with a property. Now we can determine the behavior of that property with a value. Values can be identified as the text between the colon, `:`, and semicolon, `;`. Here we are selecting all `<p>` elements and setting the value of the `color` property to be `orange` and the value of the `font-size` property to be `16` pixels.

    ```css
    p {
      color: orange;
      font-size: 16px;
    }
    ```

