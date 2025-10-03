<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# How JavaScript Works Behind the Scenes

---

## Table of Contents

1. [High-Level Overview of JavaScript](#high-level-overview-of-javascript)
2. [JavaScript Engine and Runtime](#javascript-engine-and-runtime)
3. [Compilation vs Interpretation](#compilation-vs-interpretation)
4. [Just-In-Time Compilation](#just-in-time-compilation)
5. [JavaScript Runtime Components](#javascript-runtime-components)
6. [Execution Context and Call Stack](#execution-context-and-call-stack)
7. [Scoping and Scope Chain](#scoping-and-scope-chain)
8. [Hoisting](#hoisting)
9. [The this Keyword](#the-this-keyword)

---

## High-Level Overview of JavaScript

JavaScript is a high-level, prototype-based, object-oriented, multi-paradigm, interpreted or just-in-time compiled, dynamic, single-threaded, garbage-collected programming language with first-class functions.

- **High-level**: No need to manage resources (memory/CPU).
- **Garbage-collected**: Memory management is automatic; unused objects are removed.
- **Interpreted or Just-In-Time Compiled**: JS code is converted to machine code inside the engine.
- **Multi-paradigm**: Supports procedural, object-oriented, and functional programming.
- **Prototype-based, Object-oriented**: Most things are objects; arrays inherit methods from their prototype.
- **First-class functions**: Functions are treated as variables and can be passed/returned.
- **Dynamic**: Dynamically typed; variable types are determined at runtime.
- **Single-threaded, Non-blocking Event Loop**: JS runs in one thread; uses event loop for concurrency.

---

## JavaScript Engine and Runtime

- **JavaScript Engine**: Program that executes JS code (e.g., V8 in Chrome and Node.js).
- **Components**:
  - **Call Stack**: Where code is executed using execution contexts.
  - **Heap**: Unstructured memory pool for storing objects.

---

## Compilation vs Interpretation

- **Compilation**: Entire source code is converted to machine code at once, producing a portable file.
- **Interpretation**: Source code is executed line by line; slower than compilation.

---

## Just-In-Time Compilation

Modern JS engines use a mix of compilation and interpretation called Just-In-Time (JIT) compilation:

- Code is parsed into an Abstract Syntax Tree (AST).
- AST is compiled into machine code.
- Machine code is executed immediately (no portable file).
- Code is optimized and recompiled in the background for performance.

---

## JavaScript Runtime Components

- **JavaScript Engine**: Executes JS code.
- **Web APIs**: Provided by the browser (DOM, timers, fetch, console, etc.).
- **Callback Queue**: Holds callback functions ready to be executed (e.g., event handlers).
- **Event Loop**: Moves callbacks from the queue to the call stack when it's empty.

---

## Execution Context and Call Stack

- **Execution Context**: Environment where JS code is executed (stores info for execution).
- **Global Execution Context**: Created for top-level code (outside functions).
- **Function Execution Context**: Created for each function/method call.
- **Call Stack**: Tracks execution contexts; the top context is currently running.

**Execution Context Components:**

1. Variable environment (variables, functions, arguments)
2. Scope chain (references to outer variables)
3. `this` keyword

---

## Scoping and Scope Chain

- **Scoping**: Organization and accessibility of variables.
- **Lexical Scoping**: Controlled by placement of functions/blocks in code.
- **Scope Types**:
  - **Global Scope**: Top-level code, accessible everywhere.
  - **Function Scope**: Variables accessible only inside the function.
  - **Block Scope**: Variables accessible only inside the block (let/const, ES6).
- **Scope Chain**: Each scope has access to variables from outer scopes; variable lookup moves outward.

---

## Hoisting

- **Hoisting**: Some variables/functions are accessible before declaration.
- **How it works:**
  - Function declarations: Hoisted, block scoped in strict mode.
  - `var` variables: Hoisted, initialized as `undefined`, function scoped.
  - `let`/`const`: Not hoisted, in Temporal Dead Zone (TDZ), block scoped.
  - Function expressions/arrow functions: Depends on declaration type.
- **TDZ**: Cannot access variable before declaration; results in reference error.

**Best Practices:**

- Use `const` by default, `let` for mutated variables, avoid `var`.
- Declare variables/functions at the top of their scope.

---

## The this Keyword

- Special variable created for every execution context.
- Value depends on how the function is called:
  1. As a method: `this` = object calling the method.
  2. Simple function call: `this` = `undefined` (strict mode) or `window` (non-strict).
  3. Arrow function: No own `this`; inherits from parent scope.
  4. Event listener: `this` = DOM element the handler is attached to.
- `this` never points to the function itself or the variable environment.
- In global scope: `this` = `window` (browser global object).

---

_This README was created by Mohamed Asem and summarizes how JavaScript works behind the scenes from personal notes._
