# TypeScript Guide - Type Assertions
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Type Assertions

TypeScript allows you to override its inferred and analyzed view of types in any way you want to. This is done by a mechanism called "type assertion". TypeScript's type assertion is purely you telling the compiler that you know about the types better than it does, and that it should not second guess you.

A type assertion is like a type cast in other languages, but it performs no special checking or restructuring of data. It has no runtime impact and is used purely by the compiler. TypeScript assumes that you, the programmer, have performed any special checks that you need.

Type assertions have two forms.

#### `as` syntax

```ts
let someValue: unknown = "this is a string";
 
let strLength: number = (someValue as string).length;
```

#### `angle-bracket` syntax

```ts
let someValue: unknown = "this is a string";
 
let strLength: number = (<string>someValue).length;
```

> **Note**
The two samples are equivalent. Using one over the other is mostly a choice of preference; however, when using TypeScript with JSX, only as-style assertions are allowed.

#### Type Assertions vs Casting

The reason why it's not called "type casting" is that casting generally implies some sort of runtime support. However, type assertions are purely a compile time construct and a way for you to provide hints to the compiler on how you want your code to be analyzed.


#### References

 - [https://www.typescriptlang.org/docs/handbook/basic-types.html](https://www.typescriptlang.org/docs/handbook/basic-types.html)

 - [https://basarat.gitbook.io/typescript/type-system/type-assertion](https://basarat.gitbook.io/typescript/type-system/type-assertion)
