The `useRef` hook in React is used to create a mutable reference object whose `.current` property is initialized with the passed argument. The returned object will persist for the full lifetime of the component [1][2].

Here's a simple example:

```jsx
import React, { useRef } from "react";

function TextInputWithFocusButton() {
  const inputEl = useRef(null);

  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };

  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

In this example, `useRef` is used to store a reference to an input element. The `onButtonClick` function uses this reference to focus the input when the button is clicked. This is a common use case for `useRef`: when you need to interact with a DOM element directly, like focusing an input field or measuring its dimensions.

Another common use case for `useRef` is to keep track of mutable values across renders without causing re-renders. Unlike `useState`, updating a ref does not trigger a re-render. This makes it useful for storing values that change over time but do not need to trigger a re-render when they change.

Here's an example:

```jsx
import React, { useRef, useEffect } from "react";

function Timer() {
  const intervalRef = useRef();

  useEffect(() => {
    const id = setInterval(() => {
      console.log("Interval triggered");
    }, 1000);
    intervalRef.current = id;

    return () => {
      clearInterval(intervalRef.current);
    };
  }, []); // Empty dependency array ensures effect runs once on mount and cleanup on unmount

  return <h1>Check the console log!</h1>;
}
```

In this example, `useRef` is used to store the ID of a setInterval timer. The ID is needed to clear the interval when the component unmounts. By storing the ID in a ref, we ensure that the interval ID is preserved across renders and can be accessed in the cleanup function [0][1].
