# TypeScript Guide - Type Annotations with Tuples
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Type Annotations with Tuples

**Tuple**

Array-like structure where each element represents some property of a record.

**Array vs. Tuple**

In an array, each element will generally represent a single record and different elements will have the same types of data, whereas each element in a tuple represents some property of the same record and a tuple will mix and match many different types of data.


> **Annotating a Tuple**

```ts
const pepsi: [string, boolean, number] = ['brown', true, 40];
```

> **Tuple with Type Aliases**

```ts
// type alias for a drink tuple
type Drink = [string, boolean, number];

// pepsi is now of type 'Drink' represented as a tuple
const pepsi: Drink = ['brown', true, 40];
```

> **Array of Objects (with Type Aliases)**

```ts
// type alias for a drink as an object
type Drink = {
  color: string;
  carbonated: boolean;
  sugar: number;
};

// Drink object
let coke: Drink = {
  color: 'brown',
  carbonated: true,
  sugar: 38,
};

// drinks is a Drink array
const drinks: Drink[] = [coke];
```


#### Type Aliases

Type aliases create a new name for a type. Type aliases are sometimes similar to interfaces, but can name primitives, unions, tuples, and any other types that you’d otherwise have to write by hand.