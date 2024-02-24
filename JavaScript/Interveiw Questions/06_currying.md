Currying is a function that takes one argument at a time and returns a new function expecting the next argument. It is a conversion of functions from callable as f(a,b,c)into callable as f(a)(b)(c).

Basically Currying doesn’t call a function. It just transforms a function. They are constructed by chaining closures by immediately returning their inner functions simultaneously.

Currying in JavaScript is a technique derived from functional programming that transforms a function with multiple arguments into a sequence of functions, each taking a single argument. This allows for the creation of partially applied functions that can be reused and composed in various ways to achieve more complex functionality.

### Basic Concept of Currying

At its core, currying involves taking a function with multiple arguments and turning it into a series of functions where each function takes a single argument. Here's a simple example to illustrate this concept:

```javascript
function add(x) {
  return function (y) {
    return x + y;
  };
}

const add2 = add(2);
console.log(add2(3)); //  5
console.log(add2(4)); //  6
```

In this example, `add` is a function that takes one argument `x` and returns another function that takes one argument `y` and returns the sum of `x` and `y`. By calling `add(2)`, we create a new function `add2` that adds `2` to any number passed to it [1][3].

### Practical Applications of Currying

Currying can be used in various practical scenarios, such as:

- **Creating Reusable Utility Functions**: By currying, you can create utility functions that are easily customizable for specific use cases. For example, you can create a function that returns another function with a partially applied argument, allowing for more specific use cases [1].

- **Event Handling**: In event-driven programming, currying can be used to create event handlers with specific configurations while keeping the core event handling function generic. This can lead to cleaner and more maintainable code [1].

- **Customizing API Calls**: Currying can help in creating more specific API calls based on a generic API call function. This allows for a more flexible and reusable way to make API requests with different parameters [1].

### Currying vs. Partial Application

While currying and partial application are related concepts, they are not the same. Partial application involves applying a function to some of its arguments, returning a new function that takes the remaining arguments. Currying, on the other hand, transforms a function into a sequence of functions, each taking a single argument, until the function is fully applied [0][1].

### Implementing Currying

Implementing currying in JavaScript typically involves using closures to capture the arguments passed to the curried functions. This allows the curried functions to retain access to the arguments passed to their parent functions, enabling the creation of a sequence of functions that can be called one at a time to eventually produce a result [0][3].

### Conclusion

Currying is a powerful technique in JavaScript that enables more modular, reusable, and composable code. It allows for the creation of functions that can be partially applied, leading to more flexible and concise code. Whether you're creating utility functions, handling events, or making API calls, currying can be a valuable tool in your JavaScript programming toolkit [0][1][3].

---

## 01. f(a, b) into f(a)(b)

```javascript
function f(a) {
  return function (b) {
    return `${a} ${b}`;
  };
}

console.log(f(5)(6));
```

## 02. Why should we use currying?

- It helps in avoiding the same variable again and again.
- It is a checking method that checks if you have all the things before you proceed.
- It divides one function into multiple functions so that one handles one set of responsibility.

## 03. sum(2)(6)(1)

```javascript
function sum(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}

console.log(sum(2)(6)(1));
```

## 03. evaluate ("sum")(4)(2) => 6 | ("multiply")(4)(2) => 8 | ("divide")(4)(2) => 2 | ("subtract")(4)(2) => 2

```javascript
function evaluate(operation) {
  return function (a) {
    return function (b) {
      if (operation == "sum") return a + b;
      else if (operation == "divide") return a / b;
      else if (operation == "multiply") return a * b;
      else if (operation == "substract") return a - b;
      else return "Invalid operation";
    };
  };
}
console mul = evaluate("multiply")
console sub = evaluate("subtract")
console sum = evaluate("sum")
console.log(sum(4)(2) )//6
console.log(mul(4)(2) )//8
```

## 04. Infinite currying -> sum(1)(2)(3)...(n)

```javascript
function add(a) {
  return function (b) {
    if (b) return add(a + b);
    return a;
  };
}
console.log(add(5)(2)(5)(4)());
```

## 04. Currying vs Partial Application

```javascript
function add(a) {
  return function (b, c) {
    return a + b + c;
  };
}
const x = sum(10);
console.log(x(5, 6));

// or

console.log(sum(20)(1, 4));
```

## 05. Manipulation DOM

## 06. Curry() implementation
