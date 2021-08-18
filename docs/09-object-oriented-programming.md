# TypeScript Guide - Object Oriented Programming Principles
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Summary of Object Oriented Programming Principles

Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects.

### 4 Pillars of OOP

#### Encapsulation

The implementation and state of each object are privately held inside a defined boundary: a class. Other objects do not have direct access to this state or the authority to make changes but are only able to call a list of public functions, or methods.

Encapsulation is implemented by using access specifiers.


1. information hiding /  restrict the amount of surface area exposed in index.ts

> Benefits of Encapsulation


#### Abstraction

Class objects can only share public properties and hide private properties. This creates a great way of controlling its behaviour.

Abstraction can be thought of as a natural extension of encapsulation.

Applying abstraction means that each object should only expose a high-level mechanism for using it. This mechanism should hide internal implementation details. It should only reveal operations relevant for the other objects.

> Benefits of Abstraction


#### Inheritance

Inheritance means that you can create a (child) class by deriving from another (parent) class. This way, we form a hierarchy.

The child class reuses all fields and methods of the parent class (common part) and can implement its own (unique part).

The idea of inheritance implements the IS-A relationship.


> Benefits of Inheritance



#### Polymorphism

Simply put, polymorphism gives a way to use a class exactly like its parent so there’s no confusion with mixing types. But each child class keeps its own methods as they are.

This typically happens by defining a (parent) interface to be reused. It outlines a bunch of common methods. Then, each child class implements its own version of these methods.

Objects can take on more than one form depending on the context. The program will determine which meaning or usage is necessary for each execution of that object, cutting down the need to duplicate code.


### Object Oriented Programming Concepts

> **NOTE** check notes from Specialization

#### Composition

>**TODO**

#### Composition vs Inheritance


### SOLID Principles

#### Single Responsibility Principle 

...

#### DRY



### References

 - [How to explain object-oriented programming concepts to a 6-year-old](https://www.freecodecamp.org/news/object-oriented-programming-concepts-21bb035f7260/)