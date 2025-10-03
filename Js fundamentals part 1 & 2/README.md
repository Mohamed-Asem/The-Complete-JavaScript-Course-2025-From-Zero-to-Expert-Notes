<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# JavaScript Fundamentals Part 1 & 2

_Based on my personal notes from Jonas Schmedtmann's "The Complete JavaScript Course 2025: From Zero to Expert!" on Udemy._

---

## Table of Contents

1. [Introduction to JavaScript](#introduction-to-javascript)
2. [Main Technologies in Web Development](#main-technologies-in-web-development)
3. [What JavaScript Can Do](#what-javascript-can-do)
4. [Linking JavaScript Files](#linking-javascript-files)
5. [Values and Variables](#values-and-variables)
6. [Naming Variables](#naming-variables)
7. [Data Types](#data-types)
8. [let, const, and var](#let-const-and-var)
9. [Basic Operators](#basic-operators)
10. [Strings and Template Literals](#strings-and-template-literals)
11. [If/Else Statements](#ifelse-statements)
12. [Type Conversion and Coercion](#type-conversion-and-coercion)
13. [Truthy and Falsy Values](#truthy-and-falsy-values)
14. [Equality Operators](#equality-operators)
15. [Boolean Logic](#boolean-logic)
16. [Switch Statement](#switch-statement)
17. [Ternary Operator](#ternary-operator)
18. [Statements vs Expressions](#statements-vs-expressions)
19. [Strict Mode](#strict-mode)
20. [Functions](#functions)
21. [Function Declaration vs Expression](#function-declaration-vs-expression)
22. [Arrow Functions](#arrow-functions)
23. [Calling Functions from Functions](#calling-functions-from-functions)
24. [Arrays](#arrays)
25. [Array Methods](#array-methods)
26. [Objects](#objects)
27. [Dot vs Bracket Notation](#dot-vs-bracket-notation)
28. [Object Methods & this Keyword](#object-methods--this-keyword)
29. [Loops](#loops)

---

## Introduction to JavaScript

JavaScript is a **high-level**, **object-oriented**, **multi-paradigm** programming language.

- **Programming language**: A tool to instruct computers to perform tasks.
- **High-level**: No need to worry about complex details like memory management.
- **Object-oriented**: Uses objects to store most kinds of data.
- **Multi-paradigm**: Supports different programming styles.

## Main Technologies in Web Development

- **HTML**: Responsible for the content and structure of web pages.
- **CSS**: Handles the presentation, visual styling, and layout of elements written in HTML.
- **JavaScript**: Adds dynamic and interactive effects to web pages, manipulates content and elements, loads data from remote servers, and builds entire web applications in the browser.

## What JavaScript Can Do

1. Build dynamic effects and web applications in the browser (**front-end web applications**).
2. Run on the server using Node.js (**back-end applications**), which interact with databases.
3. Build native mobile applications using React Native.
4. Create desktop applications.

---

## Linking JavaScript Files

To use JavaScript in web applications, you need to attach JS to an HTML document. You can write JS code in two places:

1. **Inline Script**:
   - Use the `<script>` element directly in the HTML document.
   - Advantage: No need to load an external file.
2. **External JavaScript Files** (Best Practice):
   - Separate presentation and logic by linking an external JS file, usually at the end of the `<body>`.
   - Example:
     ```html
     <script src="path.js"></script>
     ```

**Note:** The console is an environment for executing small pieces of code and showing results immediately. To display output in the console from a script, use:

```js
console.log();
```

---

## Values and Variables

- **Value**: A piece of data; the fundamental unit of information in programming.
- **Variable**: Used to store values so they can be reused.

**Variable Declaration:**

```js
let variableName = value;
let firstName = 'Mohamed';
```

Variables are like boxes with labels, used to store and retrieve values.

---

## Naming Variables

- Cannot start with a number.
- Cannot use reserved keywords (e.g., `name`).
- Only underscore `_` and dollar sign `$` are allowed as special characters.

**Conventions:**

1. Use camelCase notation (e.g., `firstName`, `lastName`).
2. Do not start variable names with uppercase letters (reserved for classes and constants like `PI`).
3. Use descriptive names for clarity and maintainability.

**Tip:** Use `let` for initial declaration, and omit `let` when reassigning.

---

## Data Types

JavaScript values can be **primitive** or **object** (reference type).

**Primitive Data Types:**

1. **Number**: Floating point numbers (integers and decimals)
   ```js
   let num = 23;
   ```
2. **String**: Sequence of characters for text
   ```js
   let firstName = 'Mohamed';
   ```
3. **Boolean**: Logical type, `true` or `false`
4. **Undefined**: Variable declared but not assigned a value
   ```js
   let children; // undefined
   ```
5. **Null**: "Empty value" (used in objects)
6. **Symbol** (ES2015): Unique and immutable value
7. **BigInt** (ES2020): Large integers

**Note:** JavaScript has **dynamic typing**—data types are determined automatically.

**typeof Operator:**

```js
let firstName = 'Mohamed';
console.log(typeof firstName); // returns "string"
```

**Comments:**

- Single line: `//`
- Multi-line: `/* ... */`

---

## let, const, and var

Three ways to declare variables:

- `let` and `const` (ES6, modern JavaScript)
- `var` (old way)

### let

- Used for variables that can change (mutable)
  ```js
  let age = 20;
  age = 21;
  ```
- Can declare empty (undefined) variables
  ```js
  let name;
  ```
- Block scope

### const

- Used for variables that should not change (immutable)
  ```js
  const PI = 3.14;
  ```
- Must be assigned a value at declaration
- Block scope

**Best Practice:** Use `const` by default, and `let` only if mutation is needed.

### var

- Old way, should be avoided
- Function scope

**Never write a variable without declaring it!**

---

## Basic Operators

Operators transform or combine values.

**Types:**

1. **Mathematical/Arithmetic Operators**
   - Addition `+`
   - Subtraction `-`
   - Multiplication `*`
   - Exponential `**`
   - Division `/`
   - Modulus `%`
   - Concatenation (with `+` for strings)
2. **typeof Operator**
3. **Assignment Operator** `=` (and composite: `+=`, `-=`, etc.)
4. **Increment/Decrement**: `x++`, `++x`, `x--`, `--x`
5. **Comparison Operators**: `>`, `<`, `>=`, `<=`, `==`, `===`, `!=`

**Operator Precedence:** See MDN for details.

---

## Strings and Template Literals

**Ways to build strings:**

1. **Concatenation** (old way):
   ```js
   const message =
     "Hi, I'm " +
     firstName +
     ", I'm " +
     (2023 - birthYear) +
     ' years old ' +
     job;
   ```
2. **Template Literals** (ES6):
   ```js
   const message = `Hi, I'm ${firstName}, I'm ${
     2023 - birthYear
   } years old ${job}`;
   ```
   - Use backticks `` for multi-line strings and variable interpolation.

---

## If/Else Statements

Control code execution based on conditions.

```js
if (condition) {
  // code if true
} else {
  // code if false
}
```

---

## Type Conversion and Coercion

- **Type Conversion**: Manually convert data types (explicit)
  ```js
  Number('20') + 10; // 30
  String(20); // '20'
  Boolean(10); // true
  ```
- **Type Coercion**: JavaScript automatically converts types (implicit)
  - `+` converts numbers to strings
  - `-`, `*`, `/`, `%` convert strings to numbers

**NaN**: "Not a Number"—result of invalid number operations

---

## Truthy and Falsy Values

**Falsy values:**

1. `0`
2. `''` (empty string)
3. `undefined`
4. `null`
5. `NaN`

**Truthy values:** Anything except the above falsy values.

Conversion to Boolean is usually implicit (e.g., in conditions).

---

## Equality Operators

- `===` (strict equality): No type coercion
- `==` (loose equality): Performs type coercion

**Best Practice:** Use strict equality (`===`) to avoid bugs.

**Opposites:**

- `!==` (strict inequality)
- `!=` (loose inequality)

---

## Boolean Logic

- **AND** `&&`: True if all operands are true
- **OR** `||`: True if at least one operand is true
- **NOT** `!`: Inverts true/false

---

## Switch Statement

Alternative to complicated if/else for comparing one value to multiple options.

```js
switch (value) {
  case val:
    // code
    break;
  default:
    // code
    break;
}
```

Uses strict equality (`===`).

---

## Ternary Operator

Write conditionals in one line.

```js
const canDrive = age >= 18 ? true : false;
console.log(`Is adult: ${age >= 18 ? true : false}`);
```

---

## Statements vs Expressions

- **Expression**: Produces a value (e.g., `3 + 4`, `1991`)
- **Statement**: Performs an action (e.g., `if` statement, `switch` statement)

---

## Strict Mode

Activate with `'use strict'` at the top of your script. Helps catch errors and forbids unsafe actions.

---

## Functions

Reusable blocks of code.

```js
function juiceProcessor(apples, oranges) {
  const juice = `This juice with ${apples} apples and ${oranges} oranges.`;
  return juice;
}

const juice = juiceProcessor(3, 4);
```

**Notes:**

- Use `function` keyword
- Parameters are inputs
- Arguments are actual values passed
- Return value is the result

---

## Function Declaration vs Expression

**Declaration:**

```js
function calcAge1(birthYear, currentYear) {
  return currentYear - birthYear;
}
```

**Expression (anonymous function):**

```js
const calcAge2 = function (birthYear, currentYear) {
  return currentYear - birthYear;
};
```

**Difference:** Declarations can be called before they are defined; expressions cannot.

---

## Arrow Functions

Shorter syntax for function expressions (ES6).

```js
const calcAge3 = (birthYear) => 2023 - birthYear;
const calcAge4 = (birthYear, currentYear) => currentYear - birthYear;
```

**Note:** Arrow functions do not get their own `this` keyword—do not use as object methods.

---

## Calling Functions from Functions

```js
const cutFruits = (fruit) => fruit * 4;
const juiceProcessor = function (apples, oranges) {
  const applePieces = cutFruits(apples);
  const orangePieces = cutFruits(oranges);
  return `This juice with ${applePieces} pieces of apples and ${orangePieces} pieces of oranges.`;
};
console.log(juiceProcessor(3, 4));
```

---

## Arrays

Arrays store multiple related values in one variable.

**Declaration:**

```js
const friends = ['Mohamed', 'Ahmed', 'Yasser'];
const friends2 = new Array('Mohamed', 'Ahmed', 'Yasser');
```

Arrays are zero-based. Access elements by index: `array[index]`.

Get length: `array.length`. Last element: `array[array.length - 1]`.

**Note:** You can mutate array elements even if declared with `const`, but cannot reassign the whole array.

---

## Array Methods

- `push()` — Add to end
- `unshift()` — Add to start
- `pop()` — Remove last
- `shift()` — Remove first
- `indexOf(value)` — Find index
- `includes(value)` — Check existence (strict equality)
- `sort()` — Sort elements
- `reverse()` — Reverse order
- `slice(start, end)` — Copy section
- `splice(start, deleteCount, ...items)` — Remove/insert elements

---

## Objects

Objects store multiple related values as key-value pairs.

**Declaration:**

```js
const mohamed = {
  firstName: 'Mohamed',
  lastName: 'Asem',
  age: 21,
  friends: ['Ahmed', 'Omar', 'AbdElrahman'],
};
```

Order does not matter; access by key name.

---

## Dot vs Bracket Notation

**Dot notation:**

```js
console.log(mohamed.birthday);
```

**Bracket notation:**

```js
console.log(mohamed['name']);
```

Bracket notation allows computed property access and user input.

Add properties:

```js
mohamed.job = 'student';
mohamed['hobby'] = 'coding';
```

---

## Object Methods & this Keyword

Attach functions to objects as methods.

```js
const Jonas = {
  firstName: 'Jonas',
  job: 'teacher',
  friends: ['Micheal', 'Peter', 'Steven'],
  birthYear: 1992,
  calcAge: function (currentYear) {
    return currentYear - this.birthYear;
  },
};
```

**Note:** Arrow functions do not get their own `this` keyword.

Add properties using `this`:

```js
calcAge: function () {
   this.age = 2023 - 1992;
   return this.age;
},
```

---

## Loops

**For loop:**

```js
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

**While loop:**

```js
let counter = 1;
while (counter <= 10) {
  console.log(`Iteration number ${counter}`);
  counter++;
}
```

**Break and Continue:**

- `continue` skips current iteration
- `break` exits the loop

**Looping backwards and nested loops:**

```js
for (let i = arr.length - 1; i >= 0; i--) {
  console.log(arr[i]);
}
```
