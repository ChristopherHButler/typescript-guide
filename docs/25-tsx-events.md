# TypeScript Guide - TypeScript + React: Events
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: Events

### Events

Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:

 - React has eventing system when makes use of synthetic events.
 - React events are named using camelCase, rather than lowercase.
 - With JSX you pass a function as the event handler, rather than a string.

Your event handlers will be passed instances of `SyntheticEvent`, a cross-browser wrapper around the browser’s native event.

You can find the full list of [supported events here](https://reactjs.org/docs/events.html).

#### Basic Event Handling

```ts
import React, { Component, MouseEvent } from 'react';

export class Button extends Component {
  handleClick(event: MouseEvent) {
    event.preventDefault();
    alert(event.currentTarget.tagName); // alerts BUTTON
  }
  
  render() {
    return <button onClick={this.handleClick}>
      {this.props.children}
    </button>
  }
}
```


### Controlled vs uncontrolled components

In a controlled component, form data is handled by a React component. The alternative is uncontrolled components, where form data is handled by the DOM itself.

#### uncontrolled component - listening to user input

When we only listen to user input and do not explicitely set the value of an element, it is uncontrolled.

```ts
const Input = () => {
  // here userInput is not used.
  const [userInput, setUserInput] = useState<string>('');

  return (
    <div>
      <label>Enter some text:</label>
      <input onChange={(e: HTMLInputElement) => setUserInput(e.target.value)} />
    </div>
  );

};
```

#### uncontrolled component - refs

>**Note:** To write an uncontrolled component, instead of writing an event handler for every state update, you can also use a ref to get form values from the DOM.

```ts
const Input = () => {
  const inputRef = useRef<string>('');

  // here we can access the input's value with inputRef.current.value

  return (
    <div>
      <label>Enter some text:</label>
      <input ref={inputRef} />
    </div>
  );
};
```

#### Controlled component - two-way binding

When we listen for user input and set the element's value using `state` it is a controlled component.

```ts
const Input = () => {
  const [userInput, setUserInput] = useState<string>('');

  // notice here we are setting the input's value
  return (
    <div>
      <label>Enter some text:</label>
      <input value={userInput} onChange={(e) => setUserInput(e.target.value)} />
    </div>
  );
};
```


#### Lifting state up

There should be a single “source of truth” for any data that changes in a React application.

Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor.


### References

 - [Handling Events](https://reactjs.org/docs/handling-events.html)
 - [SyntheticEvent](https://reactjs.org/docs/events.html)
 - [TypeScript and React: Events](https://fettblog.eu/typescript-react/events/)
 - [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html)
 - [Uncontrolled Components](https://reactjs.org/docs/uncontrolled-components.html)