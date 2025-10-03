<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# Array Methods in JavaScript

---

## Table of Contents

1. [Basic Array Methods](#basic-array-methods)
2. [Looping Arrays: forEach](#looping-arrays-foreach)
3. [forEach with Maps and Sets](#foreach-with-maps-and-sets)
4. [Data Transformations: map, filter, reduce](#data-transformations-map-filter-reduce)
5. [Method Chaining](#method-chaining)
6. [find and findIndex Methods](#find-and-findindex-methods)
7. [some and every Methods](#some-and-every-methods)

---

## Explanations

### What are Array Methods?

Array methods are built-in functions attached to all arrays in JavaScript, thanks to prototypal inheritance. They allow you to manipulate, transform, and analyze array data efficiently. Arrays themselves are objects, and methods are simply functions that can be called on these objects.

### slice(begin, end)

Returns a copy of a section of an array. Negative indices count from the end. Does not mutate the original array. Useful for shallow copying and extracting subarrays.

### splice(begin, count, ...items)

Removes elements from the array, mutating the original. Can also insert new elements. Returns the removed elements.

### reverse()

Reverses the order of array elements. Mutates the original array.

### concat(array)

Combines two arrays into a new one. Does not mutate the originals.

### join(separator)

Returns a string with array elements joined by the separator.

### at(index)

Returns the element at the given index. Supports negative indices for easy access to the last element. Does not mutate the array.

### forEach

Loops over each element in the array, executing a callback function. Cannot be broken out of early. Useful for side effects, not for creating new arrays.

### forEach with Maps and Sets

forEach also works with Map and Set objects. In Maps, the callback receives value, key, and the map. In Sets, the callback receives value, key (same as value), and the set.

### Data Transformation Methods

- **map()**: Transforms each element and returns a new array. Does not mutate the original.
- **filter()**: Returns a new array with elements that pass a test. Does not mutate the original.
- **reduce()**: Reduces the array to a single value by accumulating results. Does not mutate the original.

### Method Chaining

You can chain array methods together if each returns an array. This is powerful for data processing, but avoid chaining methods that mutate the original array (like splice or reverse).

### find and findIndex

- **find()**: Returns the first element that matches a condition. Returns a single value, not an array.
- **findIndex()**: Returns the index of the first element that matches a condition.

### some and every

- **some()**: Returns true if at least one element matches a condition.
- **every()**: Returns true only if all elements match a condition.

---

## Basic Array Methods Examples

**slice(begin, end):**

```js
const arr = ['a', 'b', 'c', 'd', 'e', 'f'];
console.log(arr.slice(0, -2)); // ['a', 'b', 'c', 'd']
console.log(arr.slice()); // shallow copy
```

**splice(begin, count, ...items):**

```js
const arr = ['a', 'b', 'c', 'd', 'e', 'f'];
console.log(arr.splice(-2, 2, 'Mohamed', 'Asem'));
// arr is now ['a', 'b', 'c', 'd', 'Mohamed', 'Asem']
```

**reverse():**

```js
const arr = [1, 2, 3];
arr.reverse(); // [3, 2, 1]
```

**concat(array):**

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
console.log(arr1.concat(arr2)); // [1, 2, 3, 4]
```

**join(separator):**

```js
const arr = ['a', 'b', 'c'];
console.log(arr.join('-')); // 'a-b-c'
```

**at(index):**

```js
const arr = [1, 2, 3, 4, 5];
console.log(arr.at(-1)); // 5
```

---

## Looping Arrays: forEach

**forEach:**

```js
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
movements.forEach(function (value) {
  value > 0
    ? console.log(`${value} added to your account`)
    : console.log(`${Math.abs(value)} removed from your account`);
});
```

**for...of (alternative):**

```js
for (const value of movements) {
  value > 0
    ? console.log(`${value} added to your account`)
    : console.log(`${Math.abs(value)} removed from your account`);
}
```

---

## forEach with Maps and Sets

**Map:**

```js
const currencies = new Map([
  ['USD', 'United States dollar'],
  ['EUR', 'Euro'],
  ['GBP', 'Pound sterling'],
]);
currencies.forEach(function (val, key) {
  console.log(`key: ${key}`);
  console.log(`value: ${val}`);
});
```

**Set:**

```js
const set = new Set(['USD', 'EUR', 'GBP', 'USD']);
set.forEach(function (value, _, set) {
  console.log(value);
});
```

---

## Data Transformations: map, filter, reduce

**map():**

```js
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
const eur = movements.map((mov) => Math.trunc(mov * 1.1));
const movementDescription = movements.map((mov, i) =>
  mov > 0
    ? `Movement ${i + 1}: you deposit ${mov}`
    : `Movement ${i + 1}: you withdrawal ${Math.abs(mov)}`
);
console.log(movementDescription);
```

**filter():**

```js
const deposits = movements.filter((mov) => mov > 0);
```

**reduce():**

```js
const sum = movements.reduce((acc, cur) => acc + cur, 0);
const maxVal = movements.reduce(
  (acc, current) => (acc > current ? acc : current),
  movements[0]
);
console.log(maxVal);
```

---

## Method Chaining

```js
const result = movements
  .filter((mov) => mov > 0)
  .map((mov) => Math.trunc(mov * 1.1))
  .reduce((acc, current) => acc + current, 0);
console.log(result);
```

---

## find and findIndex Methods

**find():**

```js
const user = accounts.find((account) => account.userName === 'jd');
console.log(user);
```

**findIndex():**

```js
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
console.log(movements.findIndex((mov) => mov === -400));
```

---

## some and every Methods

**some():**

```js
const hasDeposit = movements.some((mov) => mov > 0);
```

**every():**

```js
const allDeposits = movements.every((mov) => mov > 0);
```

---

_This README was created by Mohamed Asem and summarizes array methods in JavaScript from personal notes._
