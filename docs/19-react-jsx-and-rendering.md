# TypeScript Guide - React: JSX and Rendering
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## React

>**Note:** The react guide follows the format of the official react docs and summarizes key points. Where applicable, a guide to using typescript is included.


### JSX

>JSX is a JavaScript Extension Syntax used in React to easily write HTML, CSS and JavaScript together.

After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.

**Note:** React DOM uses camelCase property naming convention instead of HTML attribute names.


### How React (Babel and JSX) works behind the scenes

#### JSX Represents Objects

Babel compiles JSX down to `React.createElement()` calls.

These two examples are identical:

```js
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

`React.createElement()` performs a few checks to help you write bug-free code has the following signature:

```js
React.createElement(type, [props], [...children])
```
 - **type** can be an HTML tag like h1, div or it can be a React component
 - **props** are the attributes you want the element to have
 - **children** contain other HTML tags or can be a component

and essentially it creates an object like this:

```js
// Note: this structure is simplified
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

These objects are called “React elements”. You can think of them as descriptions of what you want to see on the screen. React reads these objects and uses them to construct the DOM and keep it up to date.

### Rendering Elements

React DOM takes care of updating the DOM to match the React elements.

#### Updating the Rendered Element

React elements are immutable. 

#### React Only Updates What’s Necessary

React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

#### Virtual DOM

**Definition**
The virtual DOM (VDOM) is a programming concept where an ideal, or “virtual”, representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM. This process is called reconciliation.

**Explained**
DOM manipulation is the heart of the modern, interactive web. Unfortunately, it is also a lot slower than most JavaScript operations.

This slowness is made worse by the fact that most JavaScript frameworks update the DOM much more than they have to.

In React, for every DOM object, there is a corresponding “virtual DOM object.” A virtual DOM object is a representation of a DOM object, like a lightweight copy.

A virtual DOM object has the same properties as a real DOM object, but it lacks the real thing’s power to directly change what’s on the screen.

Manipulating the DOM is slow. Manipulating the virtual DOM is much faster, because nothing gets drawn onscreen. Think of manipulating the virtual DOM as editing a blueprint, as opposed to moving rooms in an actual house.

When you render a JSX element, every single virtual DOM object gets updated.

This sounds incredibly inefficient, but the cost is insignificant because the virtual DOM can update so quickly.

Once the virtual DOM has updated, then React compares the virtual DOM with a virtual DOM snapshot that was taken right before the update.

By comparing the new virtual DOM with a pre-update version, React figures out exactly which virtual DOM objects have changed. This process is called “diffing.”

Once React knows which virtual DOM objects have changed, then React updates those objects, and only those objects, on the real DOM.


### Referneces

 - [https://reactjs.org/](https://reactjs.org/)
 - [React: The Virtual DOM](https://www.codecademy.com/articles/react-virtual-dom)
 - [Virtual DOM and Internals](https://reactjs.org/docs/faq-internals.html)