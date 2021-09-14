# TypeScript Guide

A guide to typescript.

Go to the [docs](./docs/00-index.md).

## Introduction

> **TypeScript = JavaScript + A Type System**

TypeScript is an open-source language which builds on JavaScript, one of the world’s most used tools, by adding static type definitions.


|![](./docs/screenshots/01-typescript.png)
|--


#### Types

Types provide a way to describe the shape of an object, providing better documentation, and allowing TypeScript to validate that your code is working correctly.

#### The TS Type System:

 - Helps us catch errors during *development*
 - Uses 'type annotations' to analyze our code
 - Only active during development
 - Doesn't provide any performance optimization

#### TypeScript vs JavaScript

JavaScript uses 'dynamic types' (resolved at runtime), whereas TypeScript uses 'static types' (set during development).

Put another way:

JavaScript is a dynamic language and TypeScript is a static(ally typed) language (like C# or Java).

#### How to use TypeScript

TypeScript code is transformed into JavaScript code via the TypeScript compiler or Babel.

|![](./docs/screenshots/02-ts-compiler.png)
|--


#### Summary

|![](./docs/screenshots/03-summary.png)
|--

<br />

## Table of Contents

### Part 1: Type System and Type Annotations

 - [What is a Type System](/docs/01-type-system.md)
 - [Type Annotations and Type Inference](/docs/02-type-annotations-and-inference.md)
 - [Type Annotations with Functions and Objects](/docs/03-type-annotations-with-functions.md)
 - [Type Annotations with Objects](/docs/04-type-annotations-with-objects.md)
 - [Type Annotations with Arrays](/docs/05-type-annotations-with-arrays.md)
 - [Type Annotations with Tuples (And Type Aliases)](/docs/06-type-annotations-with-tuples.md)

### Part 2a: Classes and Interfaces

 - [Interfaces and Type Aliases](/docs/07-interfaces.md)
 - [Classes](/docs/08-classes.md)

### Part 2b: Object Oriented Programming Principles

 - [Object Oriented Programming Principles](/docs/09-object-oriented-programming.md)

### Part 3: Design Patterns

 - [Design Patterns with TypeScript](/docs/10-design-patterns.md)

### Part 4: Intermediate | Misc

 - [Narrowing (Type Guards)](/docs/11-type-guards.md)
 - [Enums](/docs/12-enums.md)
 - [Type Assertions](/docs/13-type-assertions.md)

### Part 5: Advanced

 - [Generics](/docs/14-generics.md)
 - [Decorators](/docs/15-decorators.md)
 - [Metadata](/docs/16-metadata.md)

### Part 6A: React + TypeScript (Main Concepts)

>**Note:** The react guide follows the format of the official react docs and summarizes key points. Where applicable, a guide to using typescript is included.

 - [React: JSX and Rendering](/docs/19-react-jsx-and-rendering.md)
 - [React + TypeScript](/docs/20-ts-and-react.md)
 - [React + TypeScript: Components](/docs/21-tsx-components.md)
 - [React + TypeScript: Props](/docs/22-tsx-props.md)
 - [React + TypeScript: State and Lifecycle](/docs/23-tsx-state-and-lifecycle.md)
 - [React + TypeScript: Hooks](/docs/24-tsx-hooks.md)
 - [React + TypeScript: Events](/docs/25-tsx-events.md)
 - [React + TypeScript: Conditional Rendering and Lists](/docs/26-tsx-conditional-rendering-and-lists.md)

 - [React: Composition vs Inheritance in React](/docs/27-tsx-composition-vs-inheritance.md)
 - [React: Thinking in React - Design Guide](/docs/28-tsx-thinking-in-react.md)

### Part 6B: React + TypeScript (Misc)

 - [React + TypeScript: Styling](/docs/29-tsx-styling.md)
 - [React + TypeScript: Fragments, Portals and Refs](/docs/30-tsx-fragments-portals-and-refs.md)
 - [React + TypeScript: API Calls and Handling Side Effects](/docs/31-tsx-api-calls-and-handling-side-effects.md)
 - [React + TypeScript: Routing](/docs/32-tsx-routing.md)

#### State Management

 - [React + TypeScript: The Context API](/docs/33-tsx-context-api.md)
 - [React + TypeScript: Redux](/docs/34-ts-redux.md)

### Part 6C: React + TypeScript (Advanced Guide)

 - [React: Accessibility]()
 - [React: Code-Splitting]()
 - [React: Error Boundaries]()
 - [React: Forwarding Refs]()
 - [React: Higher-Order Components]()
 - [React: Profiler]()
 - [React: Render Props]()
 - [React + TypeScript: Optimizing Techniques](/docs/36-tsx-optimizing.md)


### Part 7: Integrating TypeScript with JS Libraries

 - [TypeScript + JS Libraries](/docs/17-ts-and-js-libraries.md)
 - [Express + TypeScript](/docs/18-ts-and-express.md)

### Appendix A: TypeScript Setup

 - [TypeScript Setup and Configuration](/docs/98-ts-setup.md)

### Appendix B: TypeScript and Webpack

 - [TypeScript and Webpack](/docs/99-ts-webpack.md)

### Appendix X: TypeScript and Testing

 - [React + TypeScript: Testing](/docs/40-tsx-testing.md)

### Appendix X: TypeScript and Next

 - [TypeScript and Next.js](/docs/35-tsx-next.md)

### Appendix X: Other topics

 - Material UI (for Porterbuddy)

 - Vanilla JS
 - React Native

 - Agile
 - Design Thinking
 - UX Design
 - FORM

## Main Resources

 - [TypeScript: The Complete Developer's Guide](https://www.udemy.com/course/typescript-the-complete-developers-guide)
 - [Understanding TypeScript](https://www.udemy.com/course/understanding-typescript)

 - [https://www.typescriptlang.org/](https://www.typescriptlang.org/)

 - [react-redux-typescript-guide](https://github.com/piotrwitek/react-redux-typescript-guide)

## Disclaimer

This guide has been compiled by taking material (in many cases verbatum) from courses, blogs, tutorials and offical docs.

It is meant to be a personal reference guide but I have made it public in case someone else finds it useful.

If you find something you have written in this guide and would like credit, feel free to make a pull request. Contributors has not been setup for this repo because that was not my intention.

## TODO

 - React Hooks with TypeScript.
 - Everything after that.