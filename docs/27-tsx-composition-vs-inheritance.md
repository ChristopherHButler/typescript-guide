# TypeScript Guide - TypeScript + React: Composition vs Inheritance
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: Composition vs Inheritance

React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components.

#### Containment

Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”.

We recommend that such components use the special children prop to pass children elements directly into their output:

```ts
interface FancyBorderProps {
  color: string;
  children?: React.ReactNode;
};

function FancyBorder({ color, children }: FancyBorderProps): JSX.Element {
  return (
    <div className={'FancyBorder FancyBorder-' + props.color}>
      {props.children}
    </div>
  );
}
```

This lets other components pass arbitrary children to them by nesting the JSX.

While this is less common, sometimes you might need multiple “holes” in a component. In such cases you may come up with your own convention instead of using children. A good example here is a SplitPane component (like a code editor).

```ts
interface SplitContainerProps {
  leftPanel: React.ReactNode;
  rightPanel: React.ReactNode;
};

function SplitContainer({ leftPanel, rightPanel }: SplitContainerProps): JSX.Element {
  return (
    <div className="SplitPane">
      <div className="SplitPane-left">
        {leftPanel}
      </div>
      <div className="SplitPane-right">
        {rightPanel}
      </div>
    </div>
  );
}

// useage
function App() {
  return (
    <SplitContainer
      leftPanel={<Editor />}
      rightPanel={<Viewer />}
    />
  );
}
```

React elements like <Editor /> and <Viewer /> are just objects, so you can pass them as props like any other data. This approach may remind you of “slots” in other libraries but there are no limitations on what you can pass as props in React.

<br />

#### Specialization

Sometimes we think about components as being “special cases” of other components. For example, we might say that a WelcomeDialog is a special case of Dialog.

In React, this is also achieved by composition, where a more “specific” component renders a more “generic” one and configures it with props:

```ts
interface DialogProps {
  title: string;
  message: string;
}

function Dialog({ title, message }: DialogProps): JSX.Element {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        {title}
      </h1>
      <p className="Dialog-message">
        {message}
      </p>
    </FancyBorder>
  );
}

function WelcomeDialog(): JSX.Element {
  return (
    <Dialog
      title="Welcome"
      message="Thank you for visiting our spacecraft!" />
  );
}
```

### So What About Inheritance?

At Facebook, we use React in thousands of components, and we haven’t found any use cases where we would recommend creating component inheritance hierarchies.

Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that components may accept arbitrary props, including primitive values, React elements, or functions.

If you want to reuse non-UI functionality between components, we suggest extracting it into a separate JavaScript module. The components may import it and use that function, object, or a class, without extending it.

### References

 - [Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)

 - [Stephen Grider - Inheritance vs. Composition in TypeScript (without react)](https://www.udemy.com/course/typescript-the-complete-developers-guide/learn/lecture/15066834#overview)