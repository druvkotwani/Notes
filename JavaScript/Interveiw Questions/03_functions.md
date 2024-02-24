# Function

## Q1.What is function declaration/function statement/function prototype/function definition

```javascript
function square(num) {
  return num * num;
}
```

## Q2.What is function expression

- When you store a function inside of a variable it's called a function expression.
- The function which is used to stored inside this variable usually is a anonymous function(func with no name).

```javascript
const square = function (nums) {
  return nums * nums;
};
square();
```

- a function expression can be called normally like a function

## Q3.What are First Class function?

First-class functions are a fundamental concept in programming languages, including JavaScript, where functions are treated like any other variable. This means that functions can be assigned to variables, passed as arguments to other functions, and returned as values from other functions. This characteristic distinguishes JavaScript from many other programming languages and allows for powerful programming patterns, such as callbacks and higher-order functions.

### Key Characteristics of First-Class Functions

- **Functions as Values**: Functions in JavaScript can be treated as values, allowing them to be assigned to variables, stored in data structures, and passed as arguments to other functions .
- **Function Expressions**: Functions can be defined as expressions and assigned to variables. This includes anonymous functions and arrow functions, which are particularly useful for creating functions on-the-fly .
- **Passing Functions as Arguments**: Functions can be passed as arguments to other functions. This is a cornerstone of callback functions and event handling in JavaScript, enabling powerful patterns for asynchronous operations and event-driven programming .
- **Functions as Return Values**: Functions can be the result of another function, enabling the creation of higher-order functions. This is a crucial aspect of functional programming, allowing for the creation of more abstract and reusable code .

### Benefits of First-Class Functions

- **Code Reusability**: First-class functions allow for the encapsulation of logic into reusable units, reducing redundancy and promoting cleaner, more maintainable code. Higher-order functions extend this by abstracting common patterns into reusable functions, further reducing code duplication and enhancing code expressiveness .
- **Modularity**: The ability to break down complex tasks into smaller, manageable functions, each focusing on a specific aspect of a problem, makes code easier to understand, test, and maintain. This is particularly important in large codebases and complex applications .
- **Functional Programming Paradigm**: First-class and higher-order functions are foundational to functional programming, which emphasizes immutability, pure functions, and declarative code. This paradigm leads to code that is more predictable, testable, and parallelizable .

### Real-World Scenarios

- **Functional Libraries**: Libraries like Lodash and Ramda rely heavily on first-class and higher-order functions, providing utilities for common tasks like data manipulation, iteration, and composition. These libraries make JavaScript more concise and expressive, enabling developers to tackle complex programming challenges with elegance and efficiency .

In summary, first-class functions in JavaScript are a powerful feature that enables a wide range of programming patterns and paradigms, including functional programming. This characteristic not only makes JavaScript a versatile language for web development but also opens up new possibilities for writing clean, modular, and expressive code.

## Q4. What is IIFE?

An Immediately Invoked Function Expression (IIFE) in JavaScript is a function that runs as soon as it is defined. It is a design pattern that allows for creating a scope that is isolated from the global scope, preventing the pollution of the global namespace with variables and functions that could potentially conflict with other scripts. This pattern is also known as a Self-Executing Anonymous Function.

The IIFE consists of two parts:

1. An anonymous function with lexical scope enclosed within the Grouping Operator `()`. This prevents accessing variables within the IIFE idiom as well as polluting the global scope.
2. The immediately invoked function expression `()` through which the JavaScript engine will directly interpret the function.

Here's a basic example of an IIFE:

```javascript
(function () {
  // Code to be executed immediately
})();
```

IIFEs are particularly useful for several reasons:

- **Scope Isolation**: They help in avoiding global scope pollution by encapsulating variables and functions within their own scope. This reduces the risk of naming conflicts with other scripts.
- **Creating Private Variables**: Variables declared within an IIFE are not accessible outside of it, providing a way to create truly private variables.
- **Asynchronous Operations**: IIFEs can be used to perform asynchronous operations immediately, such as using `setTimeout()` for delayed execution.

In practical applications, IIFEs can be used to create modules or namespaces, manage private variables, and execute setup code without exposing it to the global scope .

## Q5. What is the ouput

```javascript
(function (x{
  return (function(y){
    console.log(x) //1
  })(2)
})(1))
```

## Q6. Lexical scope

Lexical scope in JavaScript refers to the ability of a function to access variables from its parent scope. This means that a function's scope is determined by its location in the source code, or "lexically," rather than where it is called during execution. In JavaScript, child functions can access variables from their parent scopes all the way up to the global scope, but they cannot access variables from the functions defined inside them. This concept is crucial for understanding how variables are accessed and how closures work in JavaScript [0][2].

For example, if a variable is declared within a function, that variable is only accessible within that function and any nested functions. This is because the variable is lexically bound to the function in which it is declared. If a function is defined within another function, it has access to the variables of its parent function due to lexical scoping [1][2].

Here's a simple example to illustrate lexical scope:

```javascript
function outerFunction() {
  const outerVariable = "I'm outside!";

  function innerFunction() {
    console.log(outerVariable); // This can access outerVariable because of lexical scoping
  }

  innerFunction();
}

outerFunction(); // Outputs: I'm outside!
```

In this example, `innerFunction` has access to `outerVariable` because it is lexically scoped within `outerFunction`. This means that the scope of `innerFunction` includes the scope of `outerFunction`, allowing it to access variables declared in its parent scope [1][2].

## Q7. What is the output

```javascript
for (let i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log(i);
  }, i * 1000); //0 1 2 3 4
}

for (var i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log(i);
  }, i * 1000); // 5 5 5 5 5
}
```

## Q8. Function hoisting

```javascript
functionName();

function functionName() {
  console.log("DhruvKotwani");
}
```

## Q9. O/p based question on Function hoisting

- When we have variable present in the scope we will not check in the global scope

```javascript
var x = 21;

function a() {
  console.log(x);
  var x = 20;
}

a();
```

## Q10.Params vs arguments

```javascript
function square(num) {
  //param
  console.log(num * num);
}

square(5); //arguments
```

## Q11. Spread vs rest

The spread and rest operators in JavaScript, while they share the same syntax (`...`), serve different purposes and are used in different contexts.

### Spread Operator

The spread operator is used to expand iterables into individual elements. This is particularly useful in array literals, function calls, and object literals. When used in function calls, it allows you to pass elements of an array as separate arguments to the function. Similarly, in array literals, it can be used to concatenate arrays or insert elements into an array.

**Example of Spread Operator in Function Calls:**

```javascript
function myBio(firstName, lastName, company) {
  return `${firstName} ${lastName} runs ${company}`;
}

myBio(...["Oluwatobi", "Sofela", "CodeSweetly"]); // Outputs: "Oluwatobi Sofela runs CodeSweetly"
```

In this example, the spread operator is used to expand the array into individual arguments for the `myBio` function call [0][1][3].

### Rest Operator

The rest operator, on the other hand, is used to collect multiple elements into an array. It's commonly used in function parameters to collect all remaining arguments passed to a function into an array. This is particularly useful when you don't know how many arguments will be passed to a function or when you want to handle a variable number of arguments.

**Example of Rest Operator in Function Parameters:**

```javascript
function myBio(firstName, lastName, ...otherInfo) {
  return otherInfo;
}

myBio("Oluwatobi", "Sofela", "CodeSweetly", "Web Developer", "Male"); // Outputs: ["CodeSweetly", "Web Developer", "Male"]
```

Here, the rest operator collects all arguments after the first two into an array named `otherInfo` [0][1][3].

### Key Differences

- **Spread Operator**: Expands iterables into individual elements.
- **Rest Operator**: Collects multiple elements into an array.
- **Usage**: Spread is used to expand elements, while rest is used to collect elements into an array.

Both operators are powerful tools in JavaScript, allowing for more flexible and concise code when dealing with arrays, function parameters, and object properties [0][1][2][3][4].

## Q12. Callback function

A callback function in JavaScript is a function that is passed as an argument to another function and is executed after the first function has completed its task. This mechanism is particularly useful for handling asynchronous operations, such as network requests or file I/O, ensuring that certain code doesn't run until a specific task is completed. Callbacks allow developers to separate the code that initiates asynchronous operations from the code that handles the results of those operations, enhancing the readability and maintainability of the code [0][2][3].

### Example

Consider the `setTimeout` function, which is a common use case for callbacks. It waits for a specified amount of time (in milliseconds) before executing the callback function.

```javascript
setTimeout(function () {
  console.log("This message is displayed after  2 seconds");
}, 2000);
```

In this example, the anonymous function is the callback. It's passed as the first argument to `setTimeout`, and it will be executed after 2000 milliseconds (2 seconds) [2][3].

### Common Issues and Solutions

- **Not Being Called**: Ensure the callback function is defined correctly and is passed to the appropriate function. Check the function signature and the function call to confirm the callback is supplied as an argument [2].
- **Called Too Late or Too Early**: For asynchronous operations, ensure the callback is invoked after the asynchronous action has completed. Avoid calling the callback function until the asynchronous operation is finished [2].
- **Forgetting to Pass the Callback Function**: Double-check that the callback function is indeed supplied when invoking a function that expects a callback. Verify the callback parameter is present in the function signature and that the callback is supplied as an argument [2].
- **Error Handling**: If the callback function handles errors, ensure it properly screens for and responds to any issues that might arise. This includes looking for error objects and treating them appropriately [2].

Callback functions are a fundamental part of asynchronous programming in JavaScript, providing a way to manage asynchronous operations and sequence of execution in a clean and organized manner.

## Q13. Higher Order functions

Higher-order functions in JavaScript are functions that can take one or more functions as arguments or return a function as their result. This concept is a powerful feature in JavaScript, allowing for more abstract and flexible programming patterns.

### What is a Higher-Order Function?

A higher-order function is defined by its ability to work with other functions, either by taking them as parameters or by returning them. This distinction is not unique to JavaScript but is highlighted by its ability to treat functions as first-class citizens, meaning functions can be assigned to variables, passed as arguments to other functions, and returned as values from other functions.

### Example of a Higher-Order Function

```javascript
// Callback function, passed as a parameter in the higher order function
function callbackFunction() {
  console.log("I am a callback function");
}

// higher order function
function higherOrderFunction(func) {
  console.log("I am higher order function");
  func();
}

higherOrderFunction(callbackFunction);
```

In this example, `higherOrderFunction` is a higher-order function because it accepts another function (`callbackFunction`) as its argument. This demonstrates the core principle of higher-order functions: they can manipulate or use other functions as part of their execution [1].

### Benefits of Higher-Order Functions

- **Improved Code Legibility**: Higher-order functions can make code more concise and easier to understand, which can speed up development and debugging.
- **Code Organization**: They help in organizing code into smaller, manageable chunks, making it easier to maintain and extend.

### Practical Use Cases

Higher-order functions are used extensively in JavaScript, especially with built-in array methods like `map()`, `filter()`, and `reduce()`. These methods are higher-order functions that iterate over arrays and perform operations on each element, providing a powerful way to manipulate and transform data.

- **map()**: Transforms an array by applying a function to each of its elements and returning a new array with the results.
- **filter()**: Creates a new array with all elements that pass a test implemented by the provided function.
- **reduce()**: Applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single output value.

### Conclusion

Higher-order functions are a fundamental concept in JavaScript, enabling developers to write more abstract, modular, and efficient code. By understanding and utilizing higher-order functions, developers can create more concise, legible, and maintainable codebases [1][2].

## Q14. Arrow functions

```javascript
const add = (firstNum, secondNum) => firstNum + secondNum;
```

## Q15. Diff between Arrow and Normal function

Arrow functions and regular functions in JavaScript, while similar in purpose, have distinct differences in syntax, behavior, and use cases. Here's a concise comparison:

### Syntax

- **Arrow Functions**: Introduced in ES6, arrow functions use a concise syntax and do not require the `function` keyword. They are defined using the `=>` symbol. For example:

  ```javascript
  const add = (a, b) => a + b;
  ```

- **Regular Functions**: Traditional function definitions require the `function` keyword and a function name. For example:
  ```javascript
  function add(a, b) {
    return a + b;
  }
  ```

### `this` Keyword

- **Arrow Functions**: Arrow functions do not have their own `this` context. Instead, they inherit `this` from the enclosing scope. This behavior is particularly useful when working with callbacks or methods where you want `this` to refer to the object that the method is defined on.

- **Regular Functions**: Regular functions have their own `this` context. The value of `this` inside a regular function depends on how the function is called (e.g., as a method, as a constructor, or as a callback).

### Method Definitions

- **Arrow Functions**: Not suitable for object method definitions because they do not have their own `this` context.

- **Regular Functions**: Preferred for object method definitions as they have their own `this` context, which is crucial for accessing other properties and methods of the object.

### Constructor Functions

- **Arrow Functions**: Cannot be used as constructor functions. Arrow functions are not suitable for creating objects with the `new` keyword because they do not have their own `this` context.

- **Regular Functions**: Can be used as constructor functions. When called with the `new` keyword, regular functions create a new object and bind `this` to that object.

### Use Cases

- **Arrow Functions**: Ideal for short, non-method functions, especially in callbacks and functional programming patterns. They are concise and do not introduce their own `this` context, which is beneficial in certain scenarios.

- **Regular Functions**: Suitable for a wide range of applications, including object methods, constructor functions, and when you need a function with its own `this` context.

In summary, while both arrow functions and regular functions serve similar purposes in JavaScript, the choice between them depends on the specific requirements of your code, such as the need for a specific `this` context or the desire for concise syntax [1][2][3][4].
