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
### [Constructor keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)


### [Super keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super)

> ### Extra reading:

> [MDN Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
>
> [MDN construcor keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)
>
