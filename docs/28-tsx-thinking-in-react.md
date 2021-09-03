# TypeScript Guide - TypeScript + React: Thinking in React
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: Thinking in React

One of the many great parts of React is how it makes you think about apps as you build them.

The following guide is taken pretty much verbatum from the react docs but it's so good I wanted to ensure I had a copy.

### Design Process

#### Step 0: Start with a Mock 

- Imagine that we already have a JSON API and a mock from our designer.

#### Step 1: Break The UI Into A Component Hierarchy

 - The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names.
<br />

 - But how do you know what should be its own component? Use the same techniques for deciding if you should create a new function or object. One such technique is the **single responsibility principle**, that is, a component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.
<br />

 - Since you’re often displaying a JSON data model to a user, you’ll find that if your model was built correctly, your UI (and therefore your component structure) will map nicely. That’s because UI and data models tend to adhere to the same information architecture. Separate your UI into components, where each component matches one piece of your data model.
<br />

#### Step 2: Build A Static Version in React

 - Now that you have your component hierarchy, it’s time to implement your app. The easiest way is to build a version that takes your data model and renders the UI but has no interactivity. It’s best to decouple these processes because building a static version requires a lot of typing and no thinking, and adding interactivity requires a lot of thinking and not a lot of typing.
<br />

 - To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props. props are a way of passing data from parent to child. If you’re familiar with the concept of state, don’t use state at all to build this static version. State is reserved only for interactivity, that is, data that changes over time. Since this is a static version of the app, you don’t need it.
<br />

 - You can build top-down or bottom-up. That is, you can either start with building the components higher up in the hierarchy or with the ones lower in it. In simpler examples, it’s usually easier to go top-down, and on larger projects, it’s easier to go bottom-up and write tests as you build.
<br />

#### Step 3: Identify The Minimal (but complete) Representation Of UI State

 - To make your UI interactive, you need to be able to trigger changes to your underlying data model. React achieves this with state.
<br />

 - To build your app correctly, you first need to think of the minimal set of mutable state that your app needs. The key here is DRY: Don’t Repeat Yourself. Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand. For example, if you’re building a TODO list, keep an array of the TODO items around; don’t keep a separate state variable for the count. Instead, when you want to render the TODO count, take the length of the TODO items array.
<br />

 - Think of all the pieces of data in your application. Go through each one and figure out which one is state. Ask three questions about each piece of data:

  1. Is it passed in from a parent via props? If so, it probably isn’t state.
  
  2. Does it remain unchanged over time? If so, it probably isn’t state.
  
  3. Can you compute it based on any other state or props in your component? If so, it isn’t state.

<br />

#### Step 4: Identify Where Your State Should Live

 - OK, so we’ve identified what the minimal set of app state is. Next, we need to identify which component mutates, or owns, this state.
<br />

 - Remember: React is all about one-way data flow down the component hierarchy. It may not be immediately clear which component should own what state. This is often the most challenging part for newcomers to understand, so follow these steps to figure it out:

For each piece of state in your application:

 - Identify every component that renders something based on that state.

 - Find a common owner component (a single component above all the components that need the state in the hierarchy).

 - Either the common owner or another component higher up in the hierarchy should own the state.

 - If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

<br/>

#### Step 5: Add Inverse Data Flow

So far, we’ve built an app that renders correctly as a function of props and state flowing down the hierarchy. Now it’s time to support data flowing the other way: the form components deep in the hierarchy need to update the state higher up.

IMO, most apps of any size will use a state management library like redux so this step then translates to wiring up redux to your components (firing actions creators).


### References

 - [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)