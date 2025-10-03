<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# Data Structures, Modern Operators, and Strings in JavaScript

---

## Table of Contents

1. [Array Destructuring](#array-destructuring)
2. [Object Destructuring](#object-destructuring)
3. [Spread Operator](#spread-operator)
4. [Rest Pattern and Parameters](#rest-pattern-and-parameters)
5. [Short Circuiting with && and ||](#short-circuiting-with--and-)
6. [Nullish Coalescing Operator](#nullish-coalescing-operator)
7. [Logical Assignment Operators](#logical-assignment-operators)
8. [For-of Loop](#for-of-loop)
9. [Enhanced Object Literals](#enhanced-object-literals)
10. [Optional Chaining](#optional-chaining)
11. [Looping Objects](#looping-objects)
12. [Set](#set)
13. [Map](#map)
14. [Map Iteration](#map-iteration)
15. [Choosing Data Structures](#choosing-data-structures)
16. [Working with Strings - Part 1](#working-with-strings---part-1)
17. [Working with Strings - Part 2](#working-with-strings---part-2)
18. [Working with Strings - Part 3](#working-with-strings---part-3)

---

## Array Destructuring

Destructuring (ES6) is a way to unpack values from arrays or objects into separate variables. It makes retrieving elements from arrays easy and concise.

```js
const arr = [1, 2, 3];
const [a, b, c] = arr; // a=1, b=2, c=3
const [first, , third] = arr; // first=1, third=3
[first, third] = [third, first]; // swap values
```

You can use destructuring with nested arrays, set default values, and unpack only the needed elements.

---

## Object Destructuring

Object destructuring is useful for handling API results and third-party data. Use curly braces and match property names.

```js
const student = {
  firstName: 'Mohamed',
  lastName: 'Asem',
  level: 4,
  jobTitle: 'JS full-stack developer',
};
const { firstName, level, jobTitle } = student;
```

You can rename variables, set default values, mutate variables, and destructure nested objects or function parameters.

---

## Spread Operator

Expands an array into its elements. Useful for creating new arrays, copying, merging, and passing values to functions.

```js
const arr = [1, 2, 3];
console.log(...arr); // 1 2 3
const newArr = [...arr, 4, 5];
```

Works with iterables (arrays, strings, maps, sets), but not objects (except for shallow copy).

---

## Rest Pattern and Parameters

Rest pattern collects multiple elements into an array. Used in array/object destructuring and function parameters.

```js
const [n1, n2, ...others] = [1, 2, 3, 4, 5];
const add = (...numbers) => numbers.reduce((a, b) => a + b, 0);
```

---

## Short Circuiting with && and ||

Logical operators can use any data type, return any data type, and perform short circuiting.

- `||` returns the first truthy value or the last value if all are falsy.
- `&&` returns the first falsy value or the last value if all are truthy.

Use for setting default values and conditional execution.

---

## Nullish Coalescing Operator

`??` deals with nullish values (`null` or `undefined`). Useful for setting default values when `0` or `''` are valid.

```js
const guest = restaurant.guestNum ?? 20;
```

---

## Logical Assignment Operators

- `||=` assigns value if variable is falsy.
- `??=` assigns value if variable is nullish.
- `&&=` assigns value if variable is truthy.

---

## For-of Loop

Loops over arrays, giving access to each element. Use `.entries()` for index and value.

```js
for (const [index, element] of arr.entries()) {
  console.log(`${index}: ${element}`);
}
```

---

## Enhanced Object Literals

ES6 introduced easier ways to write object literals:

- Shorthand for property names
- Shorthand for methods
- Computed property names

---

## Optional Chaining

Safely access nested properties, methods, or array elements. Returns `undefined` if not found, preventing errors.

```js
restaurant.openingHours?.mon?.open ?? 'Closed';
```

---

## Looping Objects

Objects are not iterable, but you can loop over keys, values, or entries using:

- `Object.keys(obj)`
- `Object.values(obj)`
- `Object.entries(obj)`

---

## Set

A collection of unique values. No duplicates, no order, no indexes. Useful for removing duplicates from arrays.

**Create and Use Set:**

```js
const s1 = new Set(['sat', 'sun', 'mon', 'sat']);
for (const day of s1) {
  console.log(day);
}
```

**Remove Duplicates from Array:**

```js
const daysUnique = [...new Set(['sat', 'sun', 'mon', 'sat'])];
```

**Set Methods:**

```js
s1.has('sat');
s1.add('fri');
s1.delete('sun');
s1.clear();
console.log(s1.size);
```

---

## Map

A data structure for mapping keys to values. Keys can be any type.

**Create and Use Map:**

```js
const rest = new Map();
rest.set('Name', 'Classico Italiano');
rest.set(true, 'We are open');
rest.set(false, 'We are closed');
rest.set(1, 'Italy');
rest.set('open', 11);
rest.set('close', 23);
console.log(rest.get('Name'));
```

**Map Methods:**

```js
rest.has('Name');
rest.delete('open');
rest.size;
rest.clear();
```

---

## Map Iteration

Create maps from arrays, convert objects to maps, and loop over maps using `for-of` and destructuring.

**Create Map from Array:**

```js
const question = new Map([
  ['question', 'What is the best PL?'],
  [1, 'C'],
  [2, 'Java'],
  [3, 'JS'],
  ['correct', 3],
  [true, 'Correct'],
  [false, 'Try again'],
]);
```

**Convert Object to Map:**

```js
const openingHoursMap = new Map(Object.entries(restaurant.openingHours));
```

**Loop Over Map:**

```js
for (const [key, value] of question) {
  if (typeof key === 'number') {
    console.log(`Answer ${key}: ${value}`);
  }
}
```

**Convert Map to Array:**

```js
const arrayAgain = [...question];
console.log(arrayAgain);
console.log([...question.values()]);
```

---

## Choosing Data Structures

- Use arrays for ordered lists (duplicates allowed).
- Use sets for unique values and high performance.
- Use objects for key-value pairs and including functions.
- Use maps for key-value pairs with any key type and easy iteration.

---

## Working with Strings - Part 1

- Access characters by index
- Get length
- Find index with `indexOf` and `lastIndexOf`
- Extract substrings with `slice`
- String methods work by temporarily boxing primitives as objects

**Examples:**

```js
console.log('Mohamed'[0]); // 'M'
console.log('Mohamed'.length); // 7
console.log('Mohamed'.indexOf('h')); // 2
console.log('Mohamed'.lastIndexOf('m')); // 6
console.log('Mohamed'.slice(1, 4)); // 'oha'
```

**Check Middle Seat Example:**

```js
function checkMiddleSeat(seat) {
  if (seat.slice(-1) === 'B' || seat.slice(-1) === 'E') {
    console.log('This is the middle seat');
  } else {
    console.log('This is not a middle seat');
  }
}
checkMiddleSeat('11B');
```

---

## Working with Strings - Part 2

- Change case: `toUpperCase`, `toLowerCase`, `trim`
- Replace parts: `replace`, `replaceAll`, regex
- Check content: `includes`, `startsWith`, `endsWith`

**Examples:**

```js
const passengerName = 'jOnAs';
const correctedPassengerName =
  passengerName[0].toUpperCase() + passengerName.slice(1).toLowerCase();
console.log(correctedPassengerName); // 'Jonas'

const email = 'hello.io.email.com';
const loginEmail = '     HEllo.io.email.com   \n';
if (loginEmail.toLowerCase().trim() === email) {
  console.log('Welcome to our website');
}

const priceGB = '288,97E';
const priceUS = priceGB.replace('E', 'US').replace(',', '.');
console.log(priceUS); // '288.97US'

const announcement =
  'all passengers come to boarding door 23. boarding door 23';
console.log(announcement.replace(/door/g, 'gate'));

console.log('Mohamed'.startsWith('Moh')); // true
console.log('Mohamed'.endsWith('d')); // true
console.log('Mohamed'.includes('ham')); // true

function checkBaggage(item) {
  const baggage = item.toLowerCase();
  if (baggage.includes('knife') || baggage.includes('gun')) {
    console.log('You are not allowed on board');
  } else {
    console.log('Welcome aboard!');
  }
}
checkBaggage('i have a laptop , some foods and a pocket Knife');
```

---

## Working with Strings - Part 3

- Split strings into arrays: `split`
- Join arrays into strings: `join`
- Capitalize names
- Pad strings: `padStart`, `padEnd`
- Mask credit card numbers
- Repeat strings: `repeat`

**Examples:**

```js
console.log('a+very+nice+string'.split('+'));
const [firstName, lastName] = 'Mohamed Asem'.split(' ');
const newName = ['Eng.', firstName, lastName].join(' ');
console.log(newName); // 'Eng. Mohamed Asem'

function capitalizeName(name) {
  const splittedName = name.split(' ');
  const capitalizedNames = [];
  for (const n of splittedName) {
    capitalizedNames.push(n[0].toUpperCase() + n.slice(1));
  }
  console.log(capitalizedNames.join(' '));
}
capitalizeName('jessica ann smith davis');

const Name = 'Mohamed';
console.log(Name.padStart(25, '$'));
console.log(Name.padEnd(25, '$'));

function maskCreditCard(creditNumber) {
  const stringNumber = String(creditNumber);
  const maskedCard = stringNumber.slice(-4).padStart(stringNumber.length, '#');
  console.log(maskedCard);
}
maskCreditCard('12345678910121');
```

---

_This README was created by Mohamed Asem and summarizes data structures, modern operators, and string methods in JavaScript from jonas schemedtman course just personal notes._
