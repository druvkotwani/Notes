React Hooks are a feature introduced in React 16.8 that allow you to use state and other React features without writing a class component. They make it easier to reuse stateful logic between components, which can lead to cleaner and more readable code
Let's take a look at a couple of common Hooks: `useState` and `useEffect`.

1. **useState**: This Hook allows you to add state to a functional component. Consider this simple example where we display a counter and a button to increment it:

```javascript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default Counter;
```

In this example, `useState(0)` initializes the `count` state variable to 0. `setCount` is the function we use to update the count state [1].

2. **useEffect**: This Hook allows you to perform side effects in functional components. Side effects could be data fetching, subscriptions, or manually changing the DOM. Here's an example:

```javascript
import React, { useState, useEffect } from "react";

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

In this example, the `useEffect` Hook updates the document title after React updates the DOM. The empty array `[]` passed as a second argument to `useEffect` means that the effect will only run once, similar to `componentDidMount` in class components

Remember, Hooks are completely optional. You don’t have to learn or use Hooks right now if you don’t want to. They are designed to work side-by-side with existing code, so you can adopt them gradually
