A Promise in JavaScript represents the eventual completion (or failure) of an asynchronous operation and its resulting value. It is a way to handle asynchronous operations in a more manageable way than traditional callback functions. A Promise has three states:

- **Pending**: The initial state; neither fulfilled nor rejected.
- **Fulfilled**: The operation completed successfully.
- **Rejected**: The operation failed.

A Promise is said to be **settled** if it is either fulfilled or rejected.

Here's a basic example of creating a Promise:

```javascript
let promise = new Promise((resolve, reject) => {
  // Simulate an asynchronous operation using setTimeout
  setTimeout(() => {
    resolve("Promise is fulfilled");
  }, 1000);
});

promise.then((value) => console.log(value)); // Logs "Promise is fulfilled" after  1 second
```

In this example, `new Promise((resolve, reject) => {...})` creates a new Promise object. The executor function passed to the Promise constructor takes two functions as parameters: `resolve` and `reject`. When the asynchronous operation is completed successfully, `resolve` is called with the result. If the operation fails, `reject` is called with the reason for failure.

The `then` method is used to specify what should happen when the Promise is fulfilled. It takes two arguments: a callback function for the success case and another for the failure case. Both are optional, so you can use `then` for success or failure only.

Chaining Promises allows you to perform multiple asynchronous operations in sequence. Each `then` returns a new Promise, allowing for further chaining.

```javascript
new Promise((resolve, reject) => {
  setTimeout(() => resolve("First promise"), 1000);
})
  .then((result) => {
    console.log(result); // "First promise"
    return new Promise((resolve, reject) => {
      setTimeout(() => resolve("Second promise"), 1000);
    });
  })
  .then((result) => console.log(result)); // "Second promise"
```

In this chained example, the first `then` logs the result of the first Promise and returns a new Promise. The second `then` logs the result of the second Promise.

Promises are a powerful feature in JavaScript for handling asynchronous operations, providing a more readable and manageable way to work with asynchronous code compared to callbacks.

## Synchronous code vs Asynchronous code

Synchronous and asynchronous code in JavaScript are fundamental concepts that define how JavaScript executes code. Understanding the difference between them is crucial for writing efficient and responsive applications.

### Synchronous Code

Synchronous code in JavaScript executes one statement at a time in the order they appear in the code. The program waits for each statement to finish executing before moving on to the next one. This means that if a function call takes a long time to complete, it will block the entire program until it’s done. This can cause performance problems if there are many long-running synchronous operations, as the program will appear unresponsive to the user.

Example of synchronous code:

```javascript
function add(a, b) {
  return a + b;
}

const x = add(1, 2);
console.log(x); // Outputs:  3
```

In this example, the `add` function is a synchronous function. The program waits for the `add` function to return its result before executing the `console.log` statement [1].

### Asynchronous Code

Asynchronous code allows multiple operations to be executed concurrently without blocking the program. This is achieved by using callbacks, promises, or async/await syntax to signal when an operation has completed, allowing the program to continue executing other statements while the operation is being performed. Asynchronous code is often used for operations that may take a long time to complete, such as network requests or file I/O.

Example of asynchronous code:

```javascript
console.log("Before setTimeout");

setTimeout(() => {
  console.log("Inside setTimeout");
}, 2000);

console.log("After setTimeout");
```

In this example, the `console.log` statements are executed synchronously, but the `setTimeout` function is asynchronous. The program continues to execute the next line of code without waiting for the `setTimeout` callback to execute. The output of the program will be:

```
Before setTimeout
After setTimeout
Inside setTimeout
```

This demonstrates how asynchronous code can improve the performance and responsiveness of a program by allowing multiple tasks to run in parallel [1].

### Conclusion

In summary, synchronous code executes one statement at a time in a single thread, blocking the program until each operation completes. Asynchronous code, on the other hand, allows multiple operations to be executed concurrently without blocking the program, making it suitable for long-running operations and improving the user experience by keeping the application responsive [1][2].

## Promise

```javascript
console.log("start");

const sub = new Promise((res, rej) => {
  setTimeout(() => {
    const result = true;
    if (result) res("Dhruv kotwani");
    else rej(new Error("Error"));
  }, 2000);
});

sub
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });

console.log("stop");
```
