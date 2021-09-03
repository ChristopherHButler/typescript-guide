# TypeScript Guide - TypeScript + React: State and Lifecycle
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: State and Lifecycle

Most of the information here is related to react only (and not typescript).
### TL;DR

>Whereas the state in a class is always an object, with Hooks, the state can be any type. Each piece of state holds a single value, which can be an object, an array, a boolean, or any other type you can imagine.

### State

**State** refers to the current value(s) of any (and all) data (variables) in our application that a) may change and that b) we manage.

State changes over time and so you can think of the current state as a snapshot of all the variables at the current point in time.

Practically, in React, a components state can be different things depending on the type of component.

Traditionally, _state_ was only usable with class based components. Function components were used for presentation only and were also referred to as _stateless components_. With the addition of the Hooks system introduces the ability to use React state and other React features in Function Components without writing a class.

#### Class-based Components

Class components are ES6 classes that extend from React.Component and can have state and lifecycle methods:

```ts
// props interface
interface MessageProps {
  ...
}

class Message extends React.Component<MessageProps> {
  constructor(props) {
    super(props);
    this.state = {
      message: '',
    };
  }

  render() {
    return <div>{this.state.message}</div>;
  }
}
```

#### Functional Components

Functional components are functions that just accept arguments as the properties of the component and return valid JSX:

```ts
function Message(props) {
  return <div>{props.message}</div>
}
```

There are no state or lifecycle methods. However, as of React 16.8, we can use Hooks.
Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.

The `useState` hook enables you to add state to function components.

Calling React.useState inside a function component generates a single piece of state associated with that component.

>Whereas the state in a class is always an object, with Hooks, the state can be any type. Each piece of state holds a single value, which can be an object, an array, a boolean, or any other type you can imagine.



#### State updates

`setState` enqueues changes to the component state and tells React that this component and its children need to be re-rendered with the updated state.

**signature**
```js
setState(updater[, callback])
```

The first argument is an updater function with the signature:

```js
(prevState, props) => stateChange
```

prevState is a reference to the previous state. It should not be directly mutated. Instead, changes should be represented by building a new object based on the input from prevState and props.


```js
this.setState((prevState, props) => ({
  counter: prevState.counter + props.increment
}));
```

Due to the async nature of setState, it is not advisable to use this.state to get the previous state within setState. Instead, always rely on the above way. Both prevState and props received by the updater function are guaranteed to be up-to-date. The output of the updater is shallowly merged with prevState.

#### Using State Correctly

 - Do Not Modify State Directly
 - State Updates May Be Asynchronous
 - State Updates are Merged

#### Data Flows Down

Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.

This is why state is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.

<br />

### Lifecycle Methods

Each component has several “lifecycle methods” that you can override to run code at particular times in the process.

The official react docs give a good overview of these methods: [https://reactjs.org/docs/react-component.html](https://reactjs.org/docs/react-component.html)

#### Mounting

These methods are called in the following order when an instance of a component is being created and inserted into the DOM:

 - `constructor()`
 - `static getDerivedStateFromProps()`
 - `render()`
 - `componentDidMount()`
#### Updating

An update can be caused by changes to props or state. These methods are called in the following order when a component is being re-rendered:

 - `static getDerivedStateFromProps()`
 - `shouldComponentUpdate()`
 - `render()`
 - `getSnapshotBeforeUpdate()`
 - `componentDidUpdate()`

#### Unmounting

This method is called when a component is being removed from the DOM:

 - `componentWillUnmount()`

#### Error Handling

These methods are called when there is an error during rendering, in a lifecycle method, or in the constructor of any child component.

 - `static getDerivedStateFromError()`
 - `componentDidCatch()`

<br />

### Resources

 - [https://reactjs.org/docs/state-and-lifecycle.html](https://reactjs.org/docs/state-and-lifecycle.html)
 - [useState in React: A complete guide](https://blog.logrocket.com/a-guide-to-usestate-in-react-ecb9952e406c/)
 - [https://itnext.io/react-setstate-usage-and-gotchas-ac10b4e03d60](https://itnext.io/react-setstate-usage-and-gotchas-ac10b4e03d60)
