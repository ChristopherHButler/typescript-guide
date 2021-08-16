# TypeScript Guide - Classes
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Classes

A class is a blueprint to create an object with some fields / properties (values) and methods (functions) to represent a 'thing'.


#### Defining a Class

```ts
// blueprint to 'make' a Vehicle
class Vehicle {
  drive(): void {
    console.log('chugga chugga');
  }
}

// creates a new Vehicle object
const vehicle = new Vehicle();
```

Notice how the constructor is optional.

<br />

#### Defining fields using the Constructor

Having a member in a class and initializing it like below:

```ts
class Foo {
    x: number;
    constructor(x:number) {
        this.x = x;
    }
}
```

is such a common pattern that TypeScript provides a shorthand where you can prefix the member with an access modifier and it is automatically declared on the class and copied from the constructor. So the previous example can be re-written as (notice public x:number):

```ts
class Foo {
    constructor(public x:number) {
    }
}
```

<br />

#### Basic Inheritance

Classes in TypeScript (like other languages) support single inheritance using the extends keyword.
Here class Car extends (or inherits) the parent Vehicle class.

```ts
class Vehicle {

  drive(): void {
    console.log('chugga chugga');
  }

  honk(): void {
    console.log('beep');
  }

}

class Car extends Vehicle {

  // drive overrides the drive method on the parent class
  drive(): void {
    console.log('vroom');
  }
}

const car = new Car();

car.drive();
car.honk();

```

> **Note:**
If you have a constructor in your class then you must call the parent constructor from your constructor (TypeScript will point this out to you). This ensures that the stuff that it needs to set on this gets set.
Followed by the call to super you can add any additional stuff you want to do in your constructor.

```ts
class Vehicle {
  color: string;

  constructor(color: string) {
    this.color = color;
  }
}

class Car extends Vehicle {

  constructor(public wheels: number, color: string) {
    super(color);
  }
}

const car = new Car(4, 'red');
```

<br />

#### Instance Method Modifiers

If we do not specify a modifier, it is public by default.

|![](./screenshots/09-instance-method-modifiers.png)
|--

**Note:**

We do not mark methods as being private over any security concern and we do not add any layer of application security. 

The only reason to mark something as private is to restrict the different methods that other developers can call.

<br />

#### Abstract

abstract can be thought of as an access modifier. We present it separately because opposed to the previously mentioned modifiers it can be on a class as well as any member of the class. Having an abstract modifier primarily means that such functionality cannot be directly invoked and a child class must provide the functionality.

`abstract classes` cannot be directly instantiated. Instead the user must create some class that inherits from the abstract class.

`abstract members` cannot be directly accessed and a child class must provide the functionality.


<br />

#### Fields in Classes

```ts
class Vehicle {
  color: string;

  constructor(color: string) {
    this.color = color;
  }
}
```

**Property Initializer**

This is a feature supported by TypeScript (from ES7 actually). You can initialize any member of the class outside the class constructor, useful to provide default.

```ts
class Vehicle {
  color: string = 'red';
}
```

#### Static Properties

TypeScript classes support static properties that are shared by all instances of the class. A natural place to put (and access) them is on the class itself and that is what TypeScript does:

```ts
class Something {
    static instances = 0;
    constructor() {
        Something.instances++;
    }
}

var s1 = new Something();
var s2 = new Something();
console.log(Something.instances); // 2
```


#### References

[https://www.typescriptlang.org/docs/handbook/2/classes.html](https://www.typescriptlang.org/docs/handbook/2/classes.html)

[https://basarat.gitbook.io/typescript/future-javascript/classes](https://basarat.gitbook.io/typescript/future-javascript/classes)