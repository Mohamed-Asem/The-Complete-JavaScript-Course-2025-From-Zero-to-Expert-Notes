<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# DOM and Events Fundamentals

---

## Table of Contents

1. [Selecting Elements](#selecting-elements)
2. [What is DOM and DOM Manipulation](#what-is-dom-and-dom-manipulation)
3. [Selecting and Manipulating Elements](#selecting-and-manipulating-elements)
4. [Handling Click Events](#handling-click-events)
5. [Manipulating CSS Styles](#manipulating-css-styles)
6. [Coding Techniques](#coding-techniques)
7. [Manipulating Classes](#manipulating-classes)
8. [Responding to Keyboard Events](#responding-to-keyboard-events)
9. [Pig Game Project Notes](#pig-game-project-notes)

---

## Selecting Elements

- Use `document.querySelector('selector')` to select elements from the HTML document (similar to CSS selectors).
- Returns the entire element matching the selector.
- To get only the text content: `element.textContent`.
- To get the value of an input field: `element.value`.

```js
document.querySelector('.message').textContent;
document.querySelector('.guess').value;
```

---

## What is DOM and DOM Manipulation

- **DOM manipulation**: Making JS interact with the webpage.
- **DOM**: Document Object Model; a structured representation of the HTML document.
- Allows JS to access and manipulate HTML elements and styles.
- DOM is the connection point between JS and HTML.
- Created automatically by the browser when the HTML loads, stored as a tree structure.
- Each HTML element is a node in the DOM tree (parent, child, sibling relationships).
- The `document` object is the entry point to the DOM.
- DOM includes nodes for elements, text, comments, etc.
- DOM methods and properties are part of Browser APIs (not core JS).

---

## Selecting and Manipulating Elements

- Use `querySelector` to select elements:
  ```js
  document.querySelector('selector');
  document.querySelector('selector').textContent;
  document.querySelector('.guess').value;
  ```
- To set values:
  ```js
  document.querySelector('.score').textContent = '100';
  document.querySelector('.input').value = '100';
  ```

---

## Handling Click Events

- Use event listeners to react to actions (events) on the page (e.g., mouse click, button press).
- Add an event listener:
  ```js
  document.querySelector('.check').addEventListener('click', function () {
    console.log('Event handler executed successfully');
  });
  ```
- Event handler functions should be function expressions (anonymous functions).
- JS engine calls the handler when the event occurs.
- Input field values are usually strings; check for empty values before processing.
- Generate random numbers:
  ```js
  Math.trunc(Math.random() * 20);
  ```

---

## Manipulating CSS Styles

- Changing styles with JS writes inline styles (does not affect CSS files).
- Syntax:
  ```js
  element.style.propertyName = 'value';
  // Use camelCase for multi-word properties (e.g., backgroundColor)
  document.querySelector('body').style.backgroundColor = 'green';
  ```

---

## Coding Techniques

1. Make code work first, then refactor to improve and eliminate duplication.
2. Refactoring: Restructure code without changing its behavior.
3. Use functions to keep code DRY (Don't Repeat Yourself).
4. To stop live-server, kill the terminal or press Ctrl+C.

---

## Manipulating Classes

- Manipulating classes is key to changing webpage appearance.
- Select multiple elements with the same class using `querySelectorAll('selector')` (returns a NodeList).
- Loop through NodeList to access elements:
  ```js
  const btnOpenModal = document.querySelectorAll('.show-modal');
  for (let i = 0; i < btnOpenModal.length; i++) {
    console.log(btnOpenModal[i].textContent);
  }
  ```
- Use `classList` property to add/remove classes:
  ```js
  modal.classList.remove('hidden');
  modal.classList.add('hidden');
  ```
- Adding/removing classes is the main way to change styles, as classes aggregate multiple CSS rules.
- For event listeners, you can pass a named function without parentheses:
  ```js
  const closeModal = function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
  };
  closeModalButtons.addEventListener('click', closeModal);
  overlay.addEventListener('click', closeModal);
  ```

---

## Responding to Keyboard Events

- Keyboard events are global; listen on the whole document.
- Types: `keydown`, `keypress`, `keyup`.
- Add event listener:
  ```js
  document.addEventListener('keydown', function (event) {
    console.log(event.key);
  });
  ```
- JS creates an event object with info about the event (e.g., which key was pressed).
- Example: Close modal on Escape key:
  ```js
  document.addEventListener('keydown', function (event) {
    if (event.key === 'Escape') {
      if (!modal.classList.contains('hidden')) {
        closeModal();
      }
    }
  });
  ```

---

## Pig Game Project Notes

- Use `getElementById('idName')` to select elements by ID (faster than `querySelector`).
- Use comments to structure and plan code/features.
- Initial conditions: Reset values of all elements at app start.
- Manipulate image `src` attribute:
  ```js
  imgEl.src = 'newValue';
  ```
- Use state variables; do not depend on the DOM for state.
- Use `classList.toggle('className')` to add/remove a class based on its current state.
- Use flags to check if the game is finished and stop event handlers accordingly.

---

_This README was created by Mohamed Asem and summarizes DOM fundamentals and best practices from personal notes._
