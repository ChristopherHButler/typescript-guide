# TypeScript Guide - TypeScript + React: Props
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: Props

When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props”.

### Props are Read-Only

#### Pure Functions
Functions that do not attempt to change their inputs, and always return the same result for the same inputs are called _pure_ functions.

>React is pretty flexible but it has a single strict rule:
**All React components must act like pure functions with respect to their props.**

<br />

### Basic props

#### Functional Components

**Preferred Syntax**

 - props are destructured and uses an interface to annotate props
 - return type annotation is explicit (`JSX.Element`)

```ts
interface TodoProps {
  id: number;
  title: string;
  completed: boolean;
}

export const Todo = ({ id, title, completed }: TodoProps): JSX.Element => {
  return (
    <div>{title}</div>
  );
};
```

**Alternatives**

 - You do not need to use an interface and you could equally use a type alias,class or just inline the type declation.
 - The return type annotation of `JSX.Element` could be left off and TypeScript will infer the return type.
 - You can annotate the type of the Function itself using `React.FC` but this is discouraged for several reasons. Check the [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/function_components/) for more details.


<br />

#### Class Based Components

```ts
// props interface
interface TodoProps {
  id: number;
  title: string;
  completed: boolean;
}

// component with interface reference
class App extends Component<AppProps> {
  render() {
    return <div>{this.props.title}</div>
  }
}
```



### `children` props

The React children prop allows components to be composed together and is a key concept for building reusable components. Visually, we can think of it as a hole in the component where the consumer controls what is rendered. This section covers different approaches to strongly-typing this powerful and flexible prop with TypeScript.

#### TL; DR

Prefer ReactNode to type the children prop. It allows multiple elements, strings, numbers, fragments, portals

```ts
interface AppProps {
  title: string;
  children?: React.ReactNode;
};

const App = ({ title, children }: AppProps) => {
  return (
    <div>
      {children}
    </div>
  );
};
```

#### React.FC - Implicitly defining the children prop type

There is a standard React type, FC, that we can use on arrow function components. FC stands for Function Component, and it aliases a type called FunctionComponent. 

>**Note:** it's use is [discouraged](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/function_components).

```ts
interface PageProps {
  title: string,
};

const Page: React.FC<PageProps> = ({ title, children }) => (
  <div>
    <h1>{title}</h1>
    {children}
  </div>
);
```

FC is a generic type that takes in the specific type for all the component props. In the example above, we passed in a PageProps interface containing a title prop. Alternatively, a type alias could be used to define Props.

Notice that children isn’t defined in PageProps. Instead, it is already defined in the FC type. This is nice if you know this fact, but it might be a bit confusing if you don’t.

#### Explicitly defining the children prop type

**Using JSX.Element**

```ts
interface Props {
  title: string,
  children?: JSX.Element, // using ? makes it optional
};
const Page = ({ title, children }: Props) => (
  <div>
    <h1>{title}</h1>
    {children}
  </div>
);
```

JSX.Element is good if the child is required to be a single React element. However, it doesn’t allow multiple children. So, we could make the following adjustment:

```ts
interface Props {
  title: string;
  children?: JSX.Element | JSX.Element[];
};
```

**Using ReactChild**

A downside of JSX.Element is that it doesn’t allow strings. So, we could add strings to the union type:

```ts
interface Props {
  title: string;
  children:
    | JSX.Element
    | JSX.Element[]
    | string
    | string[];
};
```

...but what about numbers? This is getting out of hand.

Fortunately, there is a standard type called ReactChild that includes React elements, strings and numbers. So, we could widen the type for children as follows:

```ts
type Props = {
  title: string;
  children?:
    | React.ReactChild
    | React.ReactChild[];
};
```

React.ReactChild | React.ReactChild[] gives the breadth of values we need, but is a little verbose.


### References:

 - [React Children with TypeScript](https://www.carlrippon.com/react-children-with-typescript/)