# TypeScript Guide - Type Annotations with Functions
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## Type Annotations with Functions

With functions we can specify the types of the arguments as well as the type of the value being returned.

> **Note:** Type Inference only works around the return value from a function. 
So it will try to figure out what type of value you are returning from a function, but not what type of values the arguments are.

This means we will ALWAYS add type annotations for function arguments.


|![](./screenshots/06-annotate-vs-infer-funcs.png)
|--


#### Annotating Function Arguments and Return Values
```ts
const add = (a: number, b: number): number => {
  return a + b;
};
```

> **Note:** Type Inference also does not check your LOGIC to ensure your code does the correct thing. So if we wrote the above function as follows, TypeScript does not care. For Example:

```ts
const add = (a: number, b: number): number => {
  return a - b;
};
```

> **Note:** Even though TypeScript will infer the return value, we will **ALWAYS** add type annotations for the return value as well. The reason is that we could easily make a mistake writing the function. For example: 

```ts
const subtract = (a: number, b: number): number => {
  // no return statement
  a - b;
};
```

#### Annotating Arrow Functions
```ts
const subtract = (a: number, b: number): number => {
  return a - b;
};
```

#### Annotating Named Functions
```ts
function divide(a: number, b: number): number {
  return a / b;
}
```

#### Annotating Anonymous Functions assigned to a variable
```ts
const multiply = function(a: number, b: number): number {
  return a * b;
}
```

#### Annotating Function Return Types: Void and Never
```ts
const logger = (message: string): void => {
  console.log(message);
  // can use void to return null or undefined
};

const throwError = (message: string): never => {
  throw new Error(message);
};
```

#### Destructuring and Annotations

```ts
const todaysWeather = {
  date: new Date(),
  weather: 'sunny'
};

// const logWeather = (forecast: { date: Date, weather: string }): void => {
//   console.log(forecast.date);
//   console.log(forecast.weather);
// };

const logWeather = ({ date, weather }: { date: Date, weather: string }): void => {
  console.log(date);
  console.log(weather);
};

logWeather(todaysWeather);
```