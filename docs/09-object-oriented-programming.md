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

This typically happens by defining a (parent) interface to be reused (abstract classes). It outlines a bunch of common methods. Then, each child class implements its own version of these methods.

Objects can take on more than one form depending on the context. The program will determine which meaning or usage is necessary for each execution of that object, cutting down the need to duplicate code.


### Object Oriented Programming Concepts

#### Composition

Composition is a type of relationship between classes where one class contains another instead of inheriting from another.

Composition should be favored above inheritance because it’s more flexible and allows us to design loosely coupled applications.

Where inheritance can be thought of as an is-a relationship, composition can be thought of as a has-a relationship.



#### Composition vs Inheritance


### SOLID Principles

#### Single Responsibility Principle

 - Every object should have a single responsibility and that responsibility should be entirely encapsulated by the class. 
 - There should never be more than one reason for a class to change. 

> Key Concepts:
**Cohesion** – how strongly-related and focused are the various responsibilities of a module
**Coupling** – The degree to which each program module relies on each one of the other modules
 - We want to strive for low coupling and high cohesion. 
 - When a class has more responsibilities, there is a higher likelihood for a reason to change. 
 - Multiple small interfaces (that follow the Interface segregation principle (ISP)) can help to achieve SRP.

#### The Open / Closed Principle

Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.
> Key concepts: 
**Open to Extension** – New behavior can be added in the future
**Closed to Modification** – Changes to source or binary code are not required
 - The key is to rely on abstractions (interfaces and abstract base classes)
 - From your experience in the problem domain, if you know that a particular class is likely to change, you can apply OCP up front in your design.
 - Otherwise, don’t apply OCP at first. If the module changes once, accept it. If it changes again, refactor to achieve OCP. 
 - The way you do that is by finding an abstraction, creating an interface, and then extracting out the if then logic, or switch statement logic, into separate classes where each one represents a particular node in that decision tree.


#### The Liskov Substitution Principle

 - Subtypes must be substitutable for their base types.
 - Child classes must not remove base class behavior or violate base class invariants
 - In general, calling code must not know there are differences from a derived type and their base type.
 - LSP suggest that IS-A should be replaced with IS-SUBSTITUTABLE-FOR
 - Related Fundamentals: Polymorphism, Inheritance, ISP, OCP

#### The Interface Segregation Principle

 - Clients should not be forced to depend on methods that they do not use.
 - Prefer small, cohesive interfaces to “fat” interfaces

> Code smells include:
 - Unimplemented interface methods
 - When a client references a class but only uses a small portion of it

> Refactoring to a better design:
 - If you find yourself depending on a fat interface that you own and this is causing problems because of the dependencies involved, the best thing to do is create a smaller interface that has just what the client needs, have the fat interface implement this new interface. Then reference the new interface within your client code, ignoring the fat interface.
 - Related: polymorphism, Inheritance, LSP, façade pattern.

#### The Dependency Inversion Principle 

 - High level modules should not depend on low level modules. Both should depend on abstractions.
 - Abstractions should not depend on details. Details should depend on abstractions.


#### The Don’t Repeat Yourself Principle (DRY)

 - The DRY principle is stated as "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system".


### References

 - [How to explain object-oriented programming concepts to a 6-year-old](https://www.freecodecamp.org/news/object-oriented-programming-concepts-21bb035f7260/)