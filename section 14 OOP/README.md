<div align="center">
  <img src="https://img.shields.io/badge/Created%20by-Mohamed%20Asem-blueviolet?style=for-the-badge" alt="Created by Mohamed Asem" />
</div>

# Object-Oriented Programming (OOP) in JavaScript

---

## Table of Contents

1. Introduction to OOP
2. OOP Principles
3. OOP in JavaScript
4. Constructor Functions
5. Prototype
6. ES6 Classes
7. Setters and Getters
8. Static Methods
9. Object.create()
10. Inheritance in Constructor Functions
11. Inheritance in ES6 Classes
12. Inheritance in Object.create()

---

## 1. Introduction to OOP

Object-Oriented Programming (OOP) is a paradigm based on the concept of objects, which contain data (properties/state) and code (methods/behavior). Objects are used to model real-world or abstract features and interact through public interfaces (APIs).

## 2. OOP Principles

- **Abstraction:** Hide details that don't matter, exposing only what's necessary.
- **Encapsulation:** Keep properties and methods private, exposing only essential methods as public API.
- **Inheritance:** Child classes inherit properties and methods from parent classes, forming a hierarchy.
- **Polymorphism:** Child classes can override inherited methods.

## 3. OOP in JavaScript

JavaScript uses prototypal inheritance, where objects are linked to prototype objects. Methods and properties are accessible to all objects linked to a prototype. There are three main ways to implement OOP in JS:

- Constructor functions
- ES6 classes
- Object.create()

---

## 4. Constructor Functions

```js
const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
};
const mohamed = new Person('Mohamed', 2001);
console.log(mohamed instanceof Person); // true
```

---

## 5. Prototype

Methods and properties can be added to the constructor's prototype so all instances share them.

```js
Person.prototype.calcAge = function () {
  console.log(2023 - this.birthYear);
};
const ahmed = new Person('Ahmed', 2000);
mohamed.calcAge();
ahmed.calcAge();
console.log(mohamed.__proto__ === Person.prototype); // true
```

---

## 6. ES6 Classes

```js
class PersonCl {
  constructor(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  }
  calcAge() {
    console.log(2023 - this.birthYear);
  }
  sayHi() {
    console.log(`Hi, ${this.firstName}`);
  }
}
const mohamed = new PersonCl('Mohamed', 2002);
mohamed.calcAge();
mohamed.sayHi();
```

---

## 7. Setters and Getters

Setters and getters are special properties for getting and setting values, often used for validation.

```js
class Person {
  constructor(name, birthYear) {
    this.name = name;
    this.birthYear = birthYear;
  }
  get age() {
    return 2023 - this.birthYear;
  }
}
const mohamed = new Person('Mohamed', 2002);
console.log(mohamed.age);
```

---

## 8. Static Methods

Static methods are attached to the class itself, not to instances.

```js
class Person {
  static hey() {
    console.log('👋👋');
  }
}
Person.hey();
```

---

## 9. Object.create()

Object.create() allows manual linking of objects to prototypes.

```js
const PersonProto = {
  calcAge() {
    console.log(2023 - this.birthYear);
  },
  init(name, birthYear) {
    this.name = name;
    this.birthYear = birthYear;
  },
};
const mohamed = Object.create(PersonProto);
mohamed.init('Mohamed', 2002);
mohamed.calcAge();
```

---

## 10. Inheritance in Constructor Functions

```js
const Person = function (name, birthYear) {
  this.name = name;
  this.birthYear = birthYear;
};
Person.prototype.calcAge = function () {
  console.log(2023 - this.birthYear);
};
const Student = function (name, birthYear, course) {
  Person.call(this, name, birthYear);
  this.course = course;
};
Student.prototype = Object.create(Person.prototype);
Student.prototype.introduce = function () {
  console.log(`My name is ${this.name}, and I am a student at ${this.course}`);
};
const mohamed = new Student('Mohamed', 2002, 'Computer Science');
mohamed.introduce();
mohamed.calcAge();
```

---

## 11. Inheritance in ES6 Classes

```js
class Person {
  constructor(name, birthYear) {
    this.name = name;
    this.birthYear = birthYear;
  }
  calcAge() {
    return 2023 - this.birthYear;
  }
}
class Student extends Person {
  constructor(name, birthYear, course) {
    super(name, birthYear);
    this.course = course;
  }
  introduce() {
    console.log(
      `Hello, my name is ${
        this.name
      }, I'm ${this.calcAge()}, and I'm a student at ${this.course}`
    );
  }
}
const mohamed = new Student('Mohamed', 2002, 'Computer Science');
mohamed.introduce();
```

---

## 12. Inheritance in Object.create()

```js
const Person = {
  calcAge() {
    return 2023 - this.birthYear;
  },
  init(fullName, birthYear) {
    this.fullName = fullName;
    this.birthYear = birthYear;
  },
};
const Student = Object.create(Person);
Student.init = function (fullName, birthYear, course) {
  Person.init.call(this, fullName, birthYear);
  this.course = course;
};
Student.introduce = function () {
  console.log(
    `Hello, my name is ${
      this.fullName
    }, I am ${this.calcAge()} years old, now I am a student at ${this.course}`
  );
};
const mohamed = Object.create(Student);
mohamed.init('Mohamed', 2002, 'Computer Science');
mohamed.introduce();
```

---

_This README was created by Mohamed Asem and summarizes OOP concepts and examples in JavaScript from personal notes._
