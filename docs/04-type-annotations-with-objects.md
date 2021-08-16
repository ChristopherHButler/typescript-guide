# TypeScript Guide - Type Annotations with Objects
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Type Annotations with Objects

```ts
// object
const profile = {
  name: 'chris',
  age: 37,
  coords: {
    lat: 0,
    lng: 15
  },
  // function definition inside object
  setAge(age: number): void {
    this.age = age;
  }
};

// ES2015 destructuring example
const { age }: { age: number } = profile;
const { coords: { lat, lng } }: { coords: { lat: number; lng: number } } = profile;
```