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

