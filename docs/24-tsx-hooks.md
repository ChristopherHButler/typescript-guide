# TypeScript Guide - TypeScript + React: Hooks
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: Hooks

The Hooks system is all about giving functional components, more functionality.

Hooks are functions that let you “hook into” React state and lifecycle features from function components. Hooks don't work inside classes — they let you use React without classes.

Hooks are a way to write reusable code, instead of more classic techniques like Inheritance.

### React Hooks
#### useState

`useState` is a function that lets you use state in a functional component.

**Primitives**

```ts
// string
const [name, setName] = useState<string>('');

// number
const [activeIndex, setActiveIndex] = useState<number>(0);

// boolean
const [open, setOpen] = useState<boolean>(false);
```

**Complex Types**

```ts
// using an interface - initialized with null-ish default values
interface User {
  name: string;
  email: string;
}

const [user, setUser] = React.useState<User | null>(null);


// using a type
type Option = {
  label: string;
  value: string;
};

const [language, setLanguage] = useState<Option>(options[0]);
```

#### useEffect (and useLayoutEffect)

`useEffect` is a function that lets you use something _like_ lifecycle methods in a functional component.

both `useEffect` and `useLayoutEffect` are used for performing side effects and returns an optional cleanup function which means they do not deal with returning values and **no types are necessary**.

#### useRef

`useRef` is a function that lets you create a **ref** in a function component.

**Use with DOM Elements**

```ts
// on a div: <div ref={ref}>
const ref = useRef<HTMLDivElement | null>(null);

// on an input element: <input ref={inputRef} />
const inputRef = useRef<HTMLInputElement | null>(null);
```

**Use to store data**

```ts
const intervalRef = useRef<number | null>(null);
```

#### useReducer

#### useContext

#### useMemo

#### useCallback

#### useImperativeHandle

#### useDebugValue

### Custom Hooks


### References

 - [Mastering TypeScript for React Hooks](https://javascript.plainenglish.io/mastering-typescript-for-react-hooks-3e9e9e3797d7)
 - [https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/hooks/](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/hooks/)
 - []()
 - [https://fettblog.eu/typescript-react/hooks/](https://fettblog.eu/typescript-react/hooks/)