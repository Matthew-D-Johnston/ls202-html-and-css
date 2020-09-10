##### LS202 HTML and CSS > Lesson 5: Forms

---

## 1. Introduction

### What to Focus On

* Use the `form` tag.
* Know the differences between checkboxes, radio buttons, and selection lists.
* Use `input` and `textarea` text tags.
* Understand the `type` attribute on `input` tags:
  - `checkbox`, `radio`
  - `text`, `email`, `tel`, `password`
  - `submit`, `reset`
  - `hidden`
* Construct `select` lists
* Use labels in a form with both container and `for` formats.
* Use description lists to help format forms.

---

## 2. Forms Overview

### The `form` Tag

* The `form` tag is the parent for all form-related tags. It tells the browser where and how to send the data. The most important attributes are `action` and `method`.
* A form should contain at least one `input`, `textarea`, or `select` tag; without one, the form is useless. We use the terms **control**, **widget**, and **input** informally to refer to any of these elements as a group. If we need to be more specific, we'll talk about an input tag or input element or use `input` with inline-code styling. In the real world, there is no single term like **control** or **input** that has the same connotation -- **widget** probably comes closest.

###### The `method` Attribute

* The `method` attribute tells the browser whether it should use the HTTP GET or HTTP POST method when sending the data to the server. You should use `method="get"` when requesting information from the server, and use `method="post"` when updating data on the server.
* HTTP supports several other methods, but HTML limits you to `GET` and `POST`. You must use JavaScript or a backend application to use the other methods.

###### The `action` and `formaction` Attributes

* `action` provides the URL to which the browser sends requests. Individual action items (`button` and `input type="submit"` elements) in a form can override the form's `action` value by using the `formaction` attribute.

### The `fieldset` Tag

* `fieldset` is an optional tag that groups together form content as a set of related data; most browsers draw a border around the content. While it's common to remove that border with CSS, `fieldset` still provides useful semantic data to the browser, and developers can reference it in their CSS for layout and styling purposes.

* Forms can have multiple `fieldset` tags.

  ```html
  <form action="/login" method="post">
    <fieldset>
      <input type="text" name="username" />
      <input type="password" name="password" />
    </fieldset>
    <fieldset>
      <input type="submit" value="Save" />
      <input type="submit" value="Forgot Password" formaction="/forgot" />
    </fieldset>
  </form>
  ```

### The `label` Tag

* The `label` tag provides a way to associate some identifying text with an input field. Here we associate the label `Phone` with the field named `phone_number`:

  ```html
  <label for="phone">Phone</label>
  <input type="text" id="phone" name="phone_number" />
  ```

* The browser uses the `for` attribute in the `label` tag and the `id` attribute in the `input` tag to associate the two items. One advantage of this association is that the user can click on the label to make the cursor jump to the desired field.

* You can also use `label` tags as containers:

  ```html
  <label>
    Phone
    <input type="text" name="phone" />
  </label>
  ```

* The "container" syntax eliminates the need for the `for` and `id` attributes, so it's easier to use. However, styling can be more difficult with the container syntax, and there are times when you must use a `for` attribute, so learn both variants.

----

## 3. Input Types

### Type

The most common input types are as follows:

###### Type `text`

* The `text` type creates a simple text entry field. The user can enter any text desired in this control, though the developer should almost always validate the data. Use the `maxlength` attribute to specify the input's maximum length.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
      	First Name
        <input type="text" name="first_name" value="Tom" />
      </label>
    </fieldset>
  </form>
  ```

###### Type `password`

* The `password` type creates a single-line text field with an obscured value, often used for passwords and other sensitive information. Use the `maxlength` attribute to specify the input's maximum length.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label for="password">Password</label>
      <input type="password" name="password" id="password"
             value="Not-good-password" size="35" />
    </fieldset>
  </form>
  ```

###### Type `email`

* The `email` type allows entry of an email address in the form `username@domain`. Browsers that implement this type try to prevent incorrectly formatted email addresses. However, the developer should almost always validate the data too.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        Email
        <input type="email" name="email" placeholder="username@domain" />
      </label>
    </fieldset>
  </form>
  ```

###### Type `tel`

* The `tel` type allows entry of a telephone number. Browsers that implement this type don't validate the input since phone numbers vary so much worldwide.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        Phone
        <input type="tel" name="phone" placeholder="(###) ###-####" />
      </label>
    </fieldset>
  </form>
  ```

###### Type `checkbox`

* The `checkbox` type lets the user choose one or more items from a series of yes/no-type options. Use the `value` attribute to give the value the form sends to the server when the user selects that checkbox. Use the `checked` attribute to pre-select checkboxes. Use the `name` attribute to name a set of related checkboxes. The user can select zero or more items in each set of checkboxes.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        <input type="checkbox" name="choice" value="search" />
        Sort search results
      </label>
      
      <label>
        <input type="checkbox" name="choice" value="google" checked />
        Search on Google
      </label>
      
      <label>
        <input type="checkbox" name="choice" value="recent" checked />
        Recent results (within last year)
      </label>
    </fieldset>
  </form>
  ```

###### Type `radio`

* The `radio` type lets the user choose zero or one item from a list of options. Use the `value` attribute to define the value submitted by this item. Use the `checked` attribute to mark the default radio button. If there is no default button, use the `required` attribute on all of the buttons in a group to enforce selecting a button. Use the `name` attribute to name a set of related radio buttons. The user can select precisely one radio button from each group.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        <input type="radio" name="color" value="red" />
        Red
      </label>
      
      <label>
        <input type="radio" name="color" value="green" checked />
        Green
      </label>
      
      <label>
        <input type="radio" name="color" value="blue" />
        Blue
      </label>
    </fieldset>
  </form>
  ```

###### Type `submit`

* The `submit` type creates a button that the user can click to submit the contents of a form to the server. The `action` attribute on the `form` tag typically provides the URL of the server, but you can override that by using the `formaction` attribute with this tag.

  ```html
  <form action="#" method="post">
    <fieldset>
      <input type="submit" value="Save" />
    </fieldset>
  </form>
  ```

###### Type `reset`

* The `reset` type creates a button that the user can click to reset the contents of a form to its default values. Clicking a `reset` button does not send a request to the server.

  ```html
  <form action="#" method="post">
    <fieldset>
      <input type="reset" value="Clear Form" />
    </fieldset>
  </form>
  ```

---

## 4. Input Attributes

The `input` tag supports a variety of attributes -- some work with most input types, and some with just one. We describe the features worth memorizing in this assignment.

###### The `value` Attribute

Most input controls can use the `value` attribute, but the meaning varies with the `type`.

* For text-based types such as `text`, `email`, and `number`, the `value` assigns a default value for the control. If you don't supply a default value, the browser uses an empty string.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        Phone
        <input type="tel" name="phone" value="503-555-1212" />
      </label>
    </fieldset>
  </form>
  ```

  You should use `value` when you already have a value, either loaded from a database or provided by the user during the session.

* `checkbox` and `radio` types use the `value` attribute to set the value that the form submits for the indicated checkbox or radio group element.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        <input type="radio" name="color" value="red" />
        Red
      </label>
      <br />
  
      <label>
        <input type="radio" name="color" value="blue" checked />
        Blue
      </label>
      <br />
  
      <label>
        <input type="radio" name="color" value="green" />
        Green
      </label>
    </fieldset>
  </form>
  ```

  Technically, `radio` input types don't require the `value` attribute, but that can lead to undesirable behavior; we recommend always using a `name` value and using the same `name` on all radio buttons that belong together.  

  Note that we added a `checked` attribute to the blue button to make that button the initial selection. If we want to leave all of the radio buttons unselected, but still require a selection, we can add a `required` attribute to each button.  

* Button types, such as `submit`, `reset`, and the `button` type use the `value` attribute for the label that appears on the button:

  ```html
  <form action="#" method="post">
    <fieldset>
      <input type="submit" value="Save" />
    </fieldset>
  </form>
  ```

###### The `size` and `maxlength` Attributes

These attributes apply to most text-based input types.  

The `size` attribute lets you control the size of an `input` element in characters. You can also specify the width with the CSS `width` property, but it does not support character measurements. `maxlength` is similar, but it limits the maximum length of input values; this value can be more or less than the `size` value.

```html
<form action="#" method="post">
  <fieldset>
    <label>
      Phone
      <input type="tel" name="phone" size="10" maxlength="16" />
    </label>
    <br />
    <label>
      Cell Phone
      <input type="tel" name="cell-phone" size="20" maxlength="40" />
    </label>
  </fieldset>
</form>
```

###### The `placeholder` Attribute

The `placeholder` attribute lets you display some text when a field is empty to help describe the expected input; it applies to most of the text-based `input` types. Most browsers display `placeholder` text using a grayed-out format, and they erase the placeholder text as soon as you start typing:  

```html
<form action="#" method="post">
  <fieldset>
    <label>
      Phone
      <input type="tel" name="phone" placeholder="###-###-####" />
    </label>
  </fieldset>
</form>
```

###### The `disabled` Attribute

The `disabled` attribute lets you disable `input` elements; the browser renders disabled elements but won't let the user interact with them. The rendering looks different from enabled attributes, often by using a gray or lighter color. `disabled` also turns on the `:disabled` CSS pseudo-class. (Non-disabled elements set the `:enabled` pseudo-class.)  

Most web applications handle the `disabled` attribute programmatically, either at the time the application generates the HTML or dynamically with JavaScript. You still need to know that `disabled` exists, though; you may have to write some HTML for a program that expects disabled inputs on the original form.

```html
<form action="#" method="post">
  <fieldset>
    <label>
      Email
      <input type="email" name="email" value="xyz@example.com" disabled />
    </label>
    <br />
    <input type="submit" value="Save" disabled />
  </fieldset>
</form>
```

###### The `required` Attribute

The `required` attribute marks an `input` as required; the browser won't let you submit the form until the user completes all required fields. `required` also turns on the `:required` CSS pseudo-class.

```html
<form action="#" method="post">
  <fieldset>
    <label>
      Home Phone
      <input type="text" name="home_phone" required />
    </label>
    <br />
    <label>
      Business Phone
      <input type="text" name="business_phone" />
    </label>
    <br />
    <input type="submit" value="Save" />
  </fieldset>
</form>
```

###### The `autocomplete` Attribute

You can use `autocomplete` on most `input` text-box elements. This attribute prevents the browser from storing data for later reuse by the browser's `autocomplete` features. Autocomplete is common on smartphones and tablets but can be a nuisance. You can use the values `on` and `off` to explicitly turn `autocomplete` on or off on any given field.

```html
<input type="tel" value="123-456-7890" name="phone" autocomplete="off" />
```

The `autocomplete` option does not affect the `password` input type.

###### The `autocapitalize` Attribute

Some browsers recognize an `autocapitalize` attribute to turn autocapitalization on and off for the first letter of words or sentences. Browsers that recognize this tag default to `sentences`. Use `autocapitalize="none"` when expecting input that you don't want to capitalize. You can also specify `autocapitalize="words"` or `autocapitalize="characters"`.

```html
<input type="text" name="full-name" autocapitalize="words" />
```

`autocapitalize` is not part of the HTML standard, but an attribute provided by some *mobile* browsers, such as iOS Safari and Google Chrome. It does not affect desktop and laptop systems. The W3C HTML validator presently complains about `autocapitalize` since it is non-standard. If you want to use this attribute, you'll have to suffer that complaint.

###### The `autocorrect` Attribute

Some browsers support an `autocorrect` attribute that turns automatic spelling correction on and off. You can disable this feature with `autocorrect="off"`; you should usually disable it with names, addresses, and other information where autocorrection would be a bother.

```html
<input type="text" name="full-name" autocorrect="off" />
```

`autocorrect` is non-standard HTML, but an attribute presently provided by iOS Mobile Safari. Since it is non-standard, the W3C HTML validator will complain about the `autocorrect` attribute. If you want to use this attribute, you'll need to get used to this complaint.

---

## 5. Select and Textarea

### The `textarea` Element

`textarea` lets the user input multiple lines of text. Unlike `text`-type inputs, which ignore carriage returns, newlines, and other whitespace characters, `textarea` elements retain them and use them to format the text into lines and paragraphs. Unlike other controls, though, the value of the `textarea` doesn't use the `value` attribute to provide a value for the element. Instead, you need to contain the text between the opening and closing tags.

```html
<form action="#" method="post">
  <fieldset>
    <label>
      Comment
      <textarea name="tweet">I got 20% off my first purchase at joesburgers.com! You can too!</textarea>
    </label>
  </fieldset>
</form>
```

###### Rows and Cols

`textarea` uses the `rows` and `cols` attributes to control the height and width of the text box; `rows` is the height in lines, while `cols` is the width in characters. As with the `size` attribute on some `input` tags, neither measurement is precise - the browser may choose to display more or fewer lines or columns than requested. The CSS `height` and `width` properties will also override these attributes. Furthermore, the `rows` value is not a maximum for the number of lines of input allowed; instead, it's the number of visible lines. The text box enables vertical scrolling when the content exceeds the `rows` count.  

Most browsers today let the user resize the `textarea` box by dragging and dropping a small triangle that appears in the lower-right corner of the text box.

```html
<form action="#" method="post">
  <fieldset>
    <lable>
      Comment
      <textarea name="tweet" rows="5" cols="40">I got 20% off my first purchase at joesburgers.com! You can too!</textarea>
    </lable>
  </fieldset>
</form>
```

### The `select` Element

`select` creates a drop-down list of options from which the user can select zero or more options. It has two possible child elements, the `option` and `optgroup` elements (we won't discuss `optgroup` in this course). `select` uses the `name` attribute like other form elements, but it uses the `option` elements within it to describe the values shown to the user and sent to the server (which may be different).  

###### The `option` Element

An `option` defines one of the choices a user can make in a `select` tag. A `select` element is useless without its `option` elements. Each `option` represents a possible value for the select, and they use the `value` attribute as the value sent as the value of the `select` element's name. If an `option` does not have a `value` attribute, the browser uses the text contained by the `option` element instead.  

`select` elements often have a placeholder `option` that says something like `Choose one` and has a `value` of an empty string, as well as a `disabled` and `selected` attribute. This option works something like the placeholder attribute on text boxes: the user can see some helpful text, but she cannot select that text.

```html
<form action ="#" method="post">
  <fieldset>
    <label>
      Colors
      <select name="color">
        <option value="" disabled selected>Choose one</option>
        <option value="#f00">Red</option>
        <option value="#0f0">Green</option>
        <option value="#00f">Blue</option>
      </select>
    </label>
  </fieldset>
</form>
```

By default, `select` lets the user choose precisely one option or leave the option unselected if it contains a `disabled selected` option as shown above. If you add the `multiple` attribute, the user can select more than one option. On most browsers, a `select` with `multiple` appears as a (possibly scrolling) rectangle that displays several options. The user then Ctrl-clicks (Windows) or Cmd-clicks (Mac) to select the options she wants. If you use `multiple`, you can also supply the `size` attribute to control the height of the selection box.

```html
<form action="#" method="post">
  <fieldset>
    <label>
      Choose Your Favorite Movies
      <select name="favorites" multiple size="4">
        <option value="" disabled selected>Select One or More</option>
        <option>2001: A Space Odyssey</option>
        <option>Arrival</option>
        <option>Close Encounters of the Third Kind</option>
        <option>District 9</option>
        <option>Guardians of the Galaxy</option>
        <option>Interstellar</option>
        <option>Serenity</option>
        <option>Silent Running</option>
      </select>
    </label>
  </fieldset>
</form>
```

---

## 6. Form Layouts

