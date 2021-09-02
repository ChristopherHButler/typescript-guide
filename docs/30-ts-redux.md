# TypeScript Guide - TypeScript + Redux
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + Redux




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