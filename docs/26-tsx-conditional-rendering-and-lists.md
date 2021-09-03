# TypeScript Guide - TypeScript + React: Conditional Rendering and Lists
Quick Links: [ReadMe](../README.md) | [Table of Contents](00-index.md)

---

## TypeScript + React: Conditional Rendering and Lists


### Rendering Conditional Content

Conditional rendering in React works the same way conditions work in JavaScript. Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.

#### Inline If with Logical && Operator

You may embed expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical && operator. It can be handy for conditionally including an element.

#### Inline If-Else with Conditional Operator

Another method for conditionally rendering elements inline is to use the JavaScript conditional operator `condition ? true : false`.

#### Preventing Component from Rendering

In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return null instead of its render output.

<br />

### Rendering Lists

When we have a list of items we want to render in JavaScript we generally use the `map()` function.

#### Using map with arrays

```ts
const USERS = [{ id: 1, name: 'Chris', devGod: true }];

interface RenderListProps {
  items: {
    id: number;
    name: string;
    devGod: boolean;
  }[];
}

const RenderList = ({ items }: RenderListProps) => {
  return items.map((item) => {
    return (
      <li key={item.id}>
        {item.name}
      </li>
    );
  });

};

```


#### Using map with Objects

In short, if you have an object that somehow contains a list, you first need to convert the `Object` to an `Array`.

There are (at least) 3 variations to do this in vanilla js.

Then you can just chain on a `.map()`.

```ts
const zoo = {
  lion: '🦁',
  panda: '🐼'
};

Object.keys(zoo)
// ['lion', 'panda']

Object.values(zoo)
// ['🦁', '🐼']

Object.entries(zoo)
// [ ['lion', '🦁'], ['panda', '🐼'] ]
```

Check out [samanthaming.com](https://dev.to/samanthaming/converting-object-to-an-array-in-javascript-4bao) for good articles on this.

#### keys

A “key” is a special string attribute you need to include when creating lists of elements.

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.

The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys.

>**Note:** Keys Must Only Be Unique Among Siblings

Keys used within arrays should be unique among their siblings. However, they don’t need to be globally unique. We can use the same keys when we produce two different arrays.

### Rendering Large Lists

As a side topic, you might run into a situation where you have a very large (long) list to render (just think: EVERY social media feed).

4 strategies to deal with this issue are:

 - Pagination
 - Infinite scroll
 - react-virtualized
 - react-window


### References

 - [https://reactjs.org/docs/lists-and-keys.html](https://reactjs.org/docs/lists-and-keys.html)

