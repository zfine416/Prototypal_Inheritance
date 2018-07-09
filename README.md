# Prototypal Inheritance

## Objectives

By the end of the lesson students will be able to ...

* Demonstrate a use case that explains prototypal inheritance
* Demonstrate what kind of flexibility prototypal inheritance gives
programmers

## Methods vs Functions:

What's the difference between a method and a function?


Methods belong to objects, while functions do not.

```javascript
// bark function
function bark() {
  console.log(`My name is ${this.name}, bark, bark!!`);
}

// Cooper has a method called bark
let cooper = {name: 'Cooper', bark: bark};
```

## Prototypes:

What is this:

`let empty = {};`

How many **properties** does empty have?


How many **methods** does empty have?


Let's open our developer tool!

`console.log(empty.toString);`

WHAT!!!!!!!!!

In addition to their own set of properties, most objects also have a prototype. A prototype is another object that is used as a fallback source of properties. When an object gets a request for a property that it does not have, its prototype will be searched for the property, then the prototype’s prototype, and so on.

Who is the prototype of empty?

```javascript
console.log(Object.getPrototypeOf({}) === Object.prototype);
// true
```

Object.protoype is the ancestral prototype behind most all objects in JavaScript

The prototype relations of JavaScript objects form a tree-shaped structure, and at the root of this structure sits Object.prototype. It provides a few methods that show up in all objects, such as toString, which converts an object to a string representation.

## Prototypal Inheritance in JavaScript

Let's do our own Prototypal Inheritance:

```javascript
let protoDog = {
  speak(line) {
    console.log(`The ${this.color} dog says ${line}`);
  }
};
```

**NOW WATCH THIS!!**

```javascript
let redDog = Object.create(protoDog);
redDog.color = 'red';
```

You can use **Object.create** to create an object with a specific prototype

:scream::scream::scream:
We did prototypal inheritance in JavaScript!!

## Prototypal Inheritance in JavaScript with Classes

```javascript
function Dog(name, color) {
  this.name = name;
  this.color = color;
}

Dog.prototype.sayHi = function() {
  console.log(`Hey! I'm ${ this.name }, the ${ this.color } dog.`);
};

let clifford = new Dog('Clifford', 'red');
```

If you put the keyword **new** in front of a function call, the function is treated as a constructor. This means that an object with the right prototype is automatically created, bound to this in the function, and returned at the end of the function.









### Source
https://eloquentjavascript.net/06_object.html

