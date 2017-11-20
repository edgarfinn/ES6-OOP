# ES6 Objects

ES6 classes are primarily syntactic sugar over Javascript's prototype-based inheritance, providing an easier way to create objects and deal with inheritance. Strictly speaking Javascript is a class-less language unlike C++ or Java. Javascript uses **prototypal inheritance** instead of classical inheritance.

Objects and Classes: brief refresher on ES5 basics.
---
Javascript objects have properties associated to them (variables, which are accessed via the object ``` objectName.propertyName ```)


``` js
var myCar = new Object();
myCar.make = 'Ford';
myCar.model = 'Mustang';
myCar.year = 1969;

console.log(myCar);
// {
//   make: 'Ford',
//   model: 'Mustang',
//   year: 1969
// }

console.log(myCar.make);
// ->  Ford
```

Just like variables, these properties have names (ie make,model and year), which are associated with values ('Ford', 'Mustang', 1969).

In ES5, a **class** is probably most commonly defined using a constructor function, which provides a template for an object with pre-defined properties, ready and waiting for the values to be defined for each new instance of that object:

```js
// Define a new class constructor function.
function Car(make,model,year) {
  // Assign pre-defined properties: 'make', 'model' and 'year'.
  this.make = make;
  this.model = model;
  this.year = year;
}
```
Once defined, multiple instances of objects can be created from this class constructor using the ```new``` keyword before an invocation of the constructor function.

```js
// Create a new instance of a car object, and set its properties.
var banger = new Car('ford', 'mustang', 1976);
var racer = new Car('ferrari', 'spider', 2000);

console.log(racer)
// -> Car {make: "ferrari", model: "spider", year: 2000}

console.log(banger.make)
// -> ford

```
Defining classes with ES6
---

Classes are like special functions, and as with all functions, can be defined using both class expressions or class declarations.

### Class Declarations
To declare a class, you use the class keyword with the name of the class

```js
class Car {
  constructor(make,model,year) {
    this.make = make;
    this.model = model;
    this.year = year;    
  }
}
```

#### Hoisting:

UNLIKE function declarations, class declarations are not hoisted. So the class must first be defined, before instances of objects can be created from it.

### Class Expressions
Class expresssions can be named and unnamed. The name given to a class expression is local to the class's body.

```js
// unnamed
var Car = class {
  constructor(make,model,year) {
    this.make = make;
    this.model = model;
    this.year = year;    
  }
}

// named
var Car = class Car {
  constructor(make,model,year) {
    this.make = make;
    this.model = model;
    this.year = year;    
  }
}
```
### [Constructor()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)
- The constructor method is a special method for creating an object from a class, and initialising that object with a pre-defined set of properties.
- A class' pre-defined properties can be set using the ```constructor()``` method, and whenever objects are created from the respective class the constructor method is called, and that instance then automatically inherits the properties determined by the constructor method.
- If no constructor method is specified for a class, a default constructor is automatically used instead.

```js
class Polygon {
  constructor(height, width) {
    this.name = 'Polygon';
    this.height = height;
    this.width = width;
    console.log('A new polygon is being created.')
  }
}

const square = new Polygon(3,3)
//  -> A new polygon is being created.

console.log(square);
//  -> Polygon { name: 'Polygon', height: 3, width: 3 }
```

### The 'extends' keyword and the ['super'](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super) keyword

- The ```extends``` keyword can be used in class declarations or class expressions to create a sub-class of an existing class. When using the extends keyword, it is also possible to alter and override pre-existing properties of the parent class.

- The super keyword is used to access and call functions on an object's parent.

```js
class Polygon {
  constructor(height, width) {
    this.name = 'Polygon';
    this.height = height;
    this.width = width;
  }
}

const mySquare = new Polygon(3,3)
console.log(mySquare.name)
// -> Polygon

class Square extends Polygon {
  constructor(length) {
    // super calls the parent class (Polygon)'s constructor function
    super(length, length);
    // super() must be called before the 'this' keyword can be used.
    this.name = 'Square';
  }
}

const extendSquare = new Square(3);
console.log(extendSquare.name)
// -> Square

console.log(typeof Square)
// -> function

```
A static method is a method that can only be called on the class or children (ie extansions) of the class. Static methods cannot be called on instances of the class (ie objects created from the class using the ```new``` keyword). Static methods are often used to create utility functions.

```js
class Human {
  constructor() {}
  static ping() {
    return 'ping';
  }
}

class Computer extends Human {
  constructor() {}
  static pingpong() {
    return super.ping() + ' pong';
  }
}

const person = new Human();

person.ping()
// -> TypeError: person.ping is not a function

Computer.ping();
// -> 'ping'
Computer.pingpong();
// -> 'ping pong'
```


> ### Extra reading:

> [MDN Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
>
> [MDN construcor keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)
>
