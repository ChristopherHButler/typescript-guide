# TypeScript Guide - TypeScript + React
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## TypeScript + React

For detailed notes, checkout the official [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/docs/basic/setup).
It has a good overview on how to use React with TypeScript.

### Pros and Cons

|![](./screenshots/24-ts-react-pros-cons.png)
|--


### Setup

#### Using create-react-app

```ts
> npx create-react-app my-app --template typescript
```

#### non-cra apps

>**[HOLD]**
Setup for non-cra apps covered in another template project.

<br />

## React

>**TOODO** Add notes from sg portfolio course

### Components

There are two basic types of components: Functional and Class-based.

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
interface AppProps {
  color: string;
}

// component with interface reference
class App extends Component<AppProps> {
  render() {
    return <div>{this.props.color}</div>
  }
}

// passing props in
ReactDOM.render(<App color="red" />, document.querySelector('#root'));
```

>**Note:** defining state in a class based component using an object on the class is NOT the same as defining it via the constructor and will have very different implications.

#### 

## Redux

### Action Creators

```ts
const url = 'https://jsonplaceholder.typicode.com/todos';

interface Todo {
  id: number;
  title: string;
  completed: boolean;
}

interface FetchTodosAction {
  type: ActionTypes.fetchTodos;
  payload: Todo[];
}

export const fetchTodos = () => {
  return async (dispatch: Dispatch) => {
    const response = await axios.get<Todo[]>(url);

    // 
    dispatch<FetchTodosAction>({
      type: ActionTypes.fetchTodos,
      payload: response.data,
    });
  };
};
```

### Action Types

```ts
export enum ActionTypes {
  fetchTodos = 'FETCH_TODOS'
}
```

>**Note:** You do not need to assign enums a value. By default it will be assigned 0, 1, 2 but that is ok because redux only requres the values to be unique.


### Reducers

```ts
import { Todo, FetchTodosAction } from '../actions';
import { ActionTypes } from '../actions/types';

export const todosReducer = (state: Todo[] = [], action: FetchTodosAction) => {
  switch (action.type) {
    case ActionTypes.fetchTodos:
      return action.payload;
    default:
      return state;
  }
};
```


## References

 - [https://create-react-app.dev/docs/adding-typescript/](https://create-react-app.dev/docs/adding-typescript/)

 - [React + TypeScript Cheatsheets](https://github.com/typescript-cheatsheets/react#reacttypescript-cheatsheets)