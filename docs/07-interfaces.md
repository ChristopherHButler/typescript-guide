# TypeScript Guide - Interfaces
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Interfaces

An interface creates a new type, describing the property names and value types of an object. An interface is kind of like a variable that refers to a type.

You can also think of an interface as a contract that states what needs to be done but doesn’t specify how it will be done.

An interface contains the name of all the properties along with their types. It also includes the signature for functions along with the type of arguments and return type.

Interfaces contain only the declaration of the members. It is the responsibility of the deriving `class` to define the members.

A class or function can implement an interface to define the implementation of the properties as defined in that interface.

<br />

#### General Code Reuse Strategy

Interfaces + Classes = How we get really strong code reuse in TS.

|![](./screenshots/08-code-reuse-strategy.png)
|--

<br />


#### Defining an Interface

```ts
interface Vehicle {
  name: string;
  miles: number;
  year: Date;
};
```

#### Functions in Interfaces

An interface can also be used for defining the structure of a function.

```ts
interface Vehicle {
  name: string;
  miles: number;
  year: Date;
  summary(): string; // here string is the return value for the function
};
```

#### Optional Properties in Interfaces

You can use the ? to indicate a property or function is optional.

```ts
interface Vehicle {
  name: string;
  miles: number;
  year: Date;
  broken?: boolean; // here, the broken property is optional
};
```

#### Read-only properties

Read-only properties cannot be changed once they are initialized.

```ts
interface Vehicle {
  name: string;
  readonly miles: number;
  year: Date;
};
```

#### Using Generics in Interfaces

> **[HOLD]**




#### Interface vs Type Alias

Type aliases are sometimes similar to interfaces, but can name primitives, unions, tuples, and any other types that you’d otherwise have to write by hand.

Almost all features of an interface are available in type, the key distinction is that a type cannot be re-opened to add new properties vs an interface which is always extendable.

Because an interface more closely maps how JavaScript objects work by being open to extension, we recommend using an interface over a type alias when possible.

On the other hand, if you can’t express some shape with an interface and you need to use a union or tuple type, type aliases are usually the way to go.

Ref: [https://www.typescriptlang.org/docs/handbook/advanced-types.html](https://www.typescriptlang.org/docs/handbook/advanced-types.html)

