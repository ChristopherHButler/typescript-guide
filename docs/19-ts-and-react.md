# TypeScript Guide - TypeScript + React
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## TypeScript + React

### Pros and Cons

|![](./screenshots/24-ts-react-pros-cons.png)
|--


### Setup

>**[HOLD]**
Setup for non-cra apps covered in another template project.

<br />

## React

>**TOODO** Add notes from sg portfolio course

### Components

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



#### Functional Components

```ts
// props interface
interface AppProps {
  color: string;
}

// component with props annotation and return type annotation
const App = (props: AppProps): JSX.Element => {
  return <div>{props.color}</div>
};

// passing props in
ReactDOM.render(<App color="red" />, document.querySelector('#root'));
```


<br />

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


### 