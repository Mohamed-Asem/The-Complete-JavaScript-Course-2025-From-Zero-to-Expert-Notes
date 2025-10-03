<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# A Closer Look at Functions in JavaScript

---

## Table of Contents

1. [Default Parameters](#default-parameters)
2. [Passing Arguments: Values vs References](#passing-arguments-values-vs-references)
3. [First-Class and Higher-Order Functions](#first-class-and-higher-order-functions)
4. [Function Accepting Callback Functions](#function-accepting-callback-functions)
5. [Function Returning Functions](#function-returning-functions)
6. [call, apply, and bind Methods](#call-apply-and-bind-methods)
7. [Immediately Invoked Function Expressions (IIFE)](#immediately-invoked-function-expressions-iife)
8. [Closures](#closures)

---

## Default Parameters

Set default values for function parameters to avoid manual assignment and make functions more flexible.

**ES5 (using Nullish assignment):**

```js
const createBooking = function (flightNumber, numberOfPassengers, price) {
  numberOfPassengers ??= 1;
  price ??= '125$';
  const booking = { flightNumber, numberOfPassengers, price };
  bookings.push(booking);
  console.log(booking);
};
createBooking('123FE');
```

**ES6 (default parameters):**

```js
const createBooking = function (
  flightNumber,
  numberOfPassengers = 1,
  price = '125$'
) {
  const booking = { flightNumber, numberOfPassengers, price };
  bookings.push(booking);
  console.log(booking);
};
createBooking('123FE');
```

**Dynamic default values:**

```js
const createBooking = function (
  flightNumber,
  numberOfPassengers = 2,
  price = 120 * numberOfPassengers
) {
  const booking = { flightNumber, numberOfPassengers, price };
  bookings.push(booking);
  console.log(booking);
};
createBooking('123FE', 10);
```

---

## Passing Arguments: Values vs References

- Passing primitives: function receives a copy of the value.
- Passing objects: function receives a reference to the same object in memory.

**Example:**

```js
const flight = 'LH123';
const mohamed = { Name: 'mohamed asem', passport: 123456789 };

const checkIn = function (flightNumber, passenger) {
  flightNumber = 'LH9999';
  passenger.Name = 'Mr. ' + passenger.Name;
  if (passenger.passport === 123456789) {
    console.log('Check IN');
  } else {
    console.log('Wrong passport');
  }
};

const newPassportNum = function (passenger) {
  passenger.passport = Math.trunc(Math.random() * 1000) + 1;
};

newPassportNum(mohamed);
checkIn(flight, mohamed);
console.log(flight);
console.log(mohamed);
```

---

## First-Class and Higher-Order Functions

- **First-class functions:** Functions are treated as values (can be stored, passed, returned).
- **Higher-order functions:** Functions that receive other functions as arguments or return them.

**Examples:**

```js
const add = (a, b) => a + b;
const counter = {
  value: 23,
  increment: function () {
    this.value++;
  },
};
const greet = () => console.log('Hi, Mohamed!');
btnOpen.addEventListener('click', greet);
```

---

## Function Accepting Callback Functions

**Example:**

```js
const oneWord = (str) => str.replace(/ /g, '').toLowerCase();
const upperFirstWord = (str) => {
  const splittedStr = str.split(' ');
  splittedStr[0] = splittedStr[0].toUpperCase();
  return splittedStr.join(' ');
};

const transformer = function (str, func) {
  console.log(`The original string is: ${str}`);
  console.log(`Transformed string is: ${func(str)}`);
  console.log(`Transformed By: ${func.name}`);
};

transformer('JavaScript is the best', upperFirstWord);
transformer('JavaScript is the best', oneWord);

const high5 = () => console.log('👋');
document.addEventListener('click', high5);
['mohamed', 'asem', 'ali'].forEach(high5);
```

---

## Function Returning Functions

**Example:**

```js
const greet = function (greeting) {
  return function (Name) {
    console.log(`${greeting} ${Name}`);
  };
};
const callbackFunc = greet('Hello');
callbackFunc('Mohamed');
greet('Hello')('Mohamed');

// Arrow function version
const greetArr = (greeting) => (Name) => console.log(`${greeting} ${Name}`);
greetArr('Hello')('Mohamed');
```

---

## call, apply, and bind Methods

**call:**

```js
const lufthansa = {
  airline: 'Lufthansa',
  iataCode: 'LH',
  bookings: [],
  book(flightNum, Name) {
    console.log(
      `${Name} booked a seat on ${this.airline} flight ${this.iataCode}${flightNum}`
    );
    this.bookings.push({ flight: `${this.iataCode}${flightNum}`, Name });
  },
};
const nasa = { airline: 'Nasa', iataCode: 'NS', bookings: [] };
const Book = lufthansa.book;
Book.call(nasa, 123, 'Mohamed Asem');
Book.call(lufthansa, 234, 'Nada Asem');
```

**apply:**

```js
const journeyInfo = [123, 'Mohamed Asem'];
Book.apply(nasa, journeyInfo);
```

**bind:**

```js
const bookNasa = lufthansa.book.bind(nasa);
bookNasa(231, 'Mohamed Asem');
const nasaBook231 = lufthansa.book.bind(nasa, 231);
nasaBook231('Mohamed Asem');
nasaBook231('Jonas Schmedtmann');
```

**Partial application:**

```js
const addTax = (rate, value) => value + value * rate;
const addTaxVAT = addTax.bind(null, 0.1);
console.log(addTaxVAT(200));
```

**Event listener with bind:**

```js
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  this.planes++;
  console.log(this.planes);
};
buyBtnEl.addEventListener('click', lufthansa.buyPlane.bind(lufthansa));
```

---

## Immediately Invoked Function Expressions (IIFE)

**Syntax:**

```js
(function () {
  console.log('This function will never run again');
})();
(() => console.log('This will never run again too'))();
```

**Modern scope creation:**

```js
{
  const isPrivate = 20;
}
// console.log(isPrivate); // Error
```

---

## Closures

**Example:**

```js
const secureBooking = function () {
  let passengerCount = 0;
  return function () {
    passengerCount++;
    console.log(`passengerCount: ${passengerCount}`);
  };
};
const booker = secureBooking();
booker();
booker();
booker();
console.dir(booker);
```

- Closure: The closed-over variable environment of the execution context in which a function was created, even after that context is gone.
- Closures happen automatically; you can't manually create or access them.

---

_This README was created by Mohamed Asem and summarizes advanced function concepts in JavaScript from personal notes._
