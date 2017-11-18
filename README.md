# ES6 Objects

ES6 classes are primarily syntactic sugar over Javascript's prototype-based inheritance, providing an easier way to create objects and deal with inheritance. Strictly speaking Javascript is a class-less language unlike C++ or Java. Javascript uses **prototypal inheritance** instead of classical inheritance.

Objects and Classes: refresher on the basics.
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


A **class** is essentially a template for an object with pre-defined properties, ready and waiting for the values to be defined for each new instance of that object:

```js
// Define a new object class (template).
// With pre-defined properties: 'make', 'model' and 'year'.

function car(make,model,year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
// Create a new instance of a car object, and set its properties.
var banger = new car('ford','mustang',1976);

console.log(banger.make)
// -> ford
```

Here, ```Car``` is the class, and can be used many times
