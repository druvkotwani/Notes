# var, let and const

## Hoisting, Scoping, Shadowing and Temporal Dead Zone

### 1. Scope

In JavaScript, scope determines the accessibility of variables, objects, and functions from different parts of the code. There are three types of scope in JavaScript:

- **Global Scope**: Variables declared globally (outside any function) are accessible from anywhere in a JavaScript program. They are attached to the global `window` object in a browser environment.

- **Function Scope**: Each function creates a new scope. Variables defined inside a function are not accessible from outside the function. This applies to variables declared with `var`, `let`, and `const` within a function.

- **Block Scope**: Introduced with ES6, variables declared with `let` and `const` inside a block (enclosed by `{}`) are not accessible from outside the block. This is known as block scope.

Here are some key points about scope in JavaScript:

- **`var` Keyword**: Variables declared with `var` are function-scoped, meaning they are only accessible within the function they are declared in. They are also hoisted to the top of their scope, which means they can be used before they are declared.

- **`let` and `const` Keywords**: Variables declared with `let` and `const` are block-scoped, meaning they are only accessible within the block they are declared in. They are not hoisted, so they cannot be used before they are declared.

- **Global Variables**: Global variables are accessible from anywhere in the code. They are properties of the global object (`window` in browsers).

- **Lifetime**: The lifetime of a variable starts when it is declared. Function variables are deleted when the function is completed. Global variables are deleted when the browser window (or tab) is closed.

- **Hoisting**: JavaScript hoists variable and function declarations to the top of their scope. This means that a variable can be used before it is declared. However, only the declaration is hoisted, not the initialization.

Here are some examples to illustrate the different scopes:

```javascript
// Global scope example
var globalVar = "I'm global";

function exampleFunction() {
  // Function scope example
  var functionVar = "I'm in a function";

  if (true) {
    // Block scope example
    let blockVar = "I'm in a block";
    const blockConst = "I'm a constant in a block";
  }
}
```

In the example above, `globalVar` is accessible anywhere in the code, `functionVar` is only accessible within `exampleFunction`, and `blockVar` and `blockConst` are only accessible within the `if` block.

---

var is function scoped when declared within a function, otherwise it is globally scoped.

```javascript
var a = 1;
console.log(a); // 1

{
  var a = 2;
}
console.log(a); // 2
```

let and const are block scoped.

```javascript
{
  let a = 3;
}
console.log(a); // undefined
```

---

---

### 2. Shadowing

Variable shadowing in JavaScript occurs when a variable declared within a certain scope (like a function or a block) has the same name as a variable declared in an outer scope. This inner variable "shadows" or hides the outer variable, making references to the variable within the inner scope refer to the inner variable, not the outer one.

Here's an example to illustrate variable shadowing:

```javascript
let x = 10;

function foo() {
  let x = 20;
  console.log(x); // Outputs  20
}

foo();
console.log(x); // Outputs  10
```

In this example, there are two variables named `x`. The outer `x` has a value of `10`, while the inner `x` has a value of `20`. When we call the `foo` function, it logs `20` to the console, which is the value of the inner `x`. However, when we log `x` outside the function, it refers to the outer `x`, and thus logs `10` to the console.

Variable shadowing can lead to ambiguity and unexpected results, making the code harder to understand and maintain. It's important to be aware of shadowing to avoid unintended consequences. To mitigate these issues, you can:

- Use descriptive and meaningful names for variables to minimize the chances of inadvertently shadowing variables.
- Utilize JavaScript linters like ESLint to detect and warn about variable shadowing in your codebase.

It's also worth noting the concept of "illegal shadowing," which occurs when a variable is declared in a global scope with `let` and another variable with `var` in a block scope with the same name. This will throw an error because `let` and `var` have different scoping rules, and `let` does not allow re-declaration within the same scope .

---

---

### 3. Re-Declaration

In JavaScript, redeclaration of variables refers to the act of declaring a variable that has already been declared. The behavior of redeclaration varies depending on the keyword used to declare the variable: `var`, `let`, and `const`.

- **`var` Keyword**: Variables declared with `var` can be redeclared and reassigned within the same scope. This means that you can change the value of a `var` variable without any issues. However, redeclaring a `var` variable with a different type or value will not throw an error, but it will change the value of the variable globally or within the scope where the redeclaration occurs .

  ```javascript
  var x = 10;
  var x = 20; // This is a redeclaration of 'x', and it's allowed.
  console.log(x); // Outputs  20
  ```

- **`let` Keyword**: Variables declared with `let` cannot be redeclared in the same scope. Attempting to do so will result in a `SyntaxError`. However, the value of a `let` variable can be reassigned within its scope .

  ```javascript
  let y = 10;
  let y = 20; // This will throw a SyntaxError
  y = 20; // This is a reassignment, and it's allowed.
  console.log(y); // Outputs  20
  ```

- **`const` Keyword**: Variables declared with `const` cannot be redeclared or reassigned. Once a `const` variable has been declared and assigned a value, you cannot change its value or redeclare it in the same scope. Attempting to do so will result in a `SyntaxError`.

  ```javascript
  const z = 10;
  const z = 20; // This will throw a SyntaxError
  z = 20; // This will also throw a SyntaxError
  console.log(z); // Outputs  10
  ```

It's important to note that `var` has function scope, which means that if you redeclare a `var` variable within a function, it will not affect the value of the variable outside the function. On the other hand, `let` and `const` have block scope, meaning that they are only accessible within the block they are declared in .

---

---

### 4. Javascript Execution Context

The JavaScript Execution Context is a fundamental concept that defines the environment in which JavaScript code is executed. It is a data structure that contains information about the environment, including the variables, functions, and parameters defined in that environment, as well as the scope chain and the `this` keyword .

There are two types of execution contexts:

- **Global Execution Context (GEC)**: This context is created when a JavaScript script first starts to run. It represents the global scope in JavaScript and is the base/default Execution Context where all JavaScript code that is not inside of a function gets executed .

- **Function Execution Context (FEC)**: This context is created whenever a function is called, representing the function's local scope. Each function call creates a new FEC, which is pushed onto the call stack .

The Execution Context goes through two phases:

- **Creation Phase**: The JavaScript engine sets up the environment, determines the values of variables and functions, and sets up the scope chain for the execution context .

- **Execution Phase**: The JavaScript engine executes the code in the execution context, processing any statements or expressions in the script and evaluating any function calls .

The Execution Stack, also known as the Call Stack, keeps track of all the Execution Contexts created during the life cycle of a script. When a function is called, a new FEC is created and pushed onto the top of the stack. When a function returns, its execution context is popped off the stack. This stack is a last-in, first-out (LIFO) data structure .

---

When we try execute a Javascript code there are two phases that happens in the background. They are:

- **Creation Phase**: In this phase, the JavaScript engine sets up the environment, determines the values of variables and functions, and sets up the scope chain for the execution context.

  - it creates the global object (window in a browser environment).
  - set up memory space for variables and functions (hoisting).
  - it initializes the value of variables and functions as `undefined`.
  - and for function declaration it sets up the reference to the function.

- **Execution Phase**: In this phase, the JavaScript engine executes the code in the execution context, processing any statements or expressions in the script and evaluating any function calls.

  - during this phase, the JavaScript engine assigns values to variables and executes the code line by line.
  - and for every new function call, a new execution context is created and pushed onto the call stack.

---

---

### 5. Hositing

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compilation phase. This means that regardless of where variables and functions are declared, they are moved to the top of their scope, making them accessible before they are actually declared .

Here are some key points about hoisting:

- **Variable Hoisting**: Variables declared with `var` are hoisted to the top of their scope and initialized with a value of `undefined`. This means that you can use a variable before it is declared, but its value will be `undefined` until it is assigned a value.

  ```javascript
  console.log(x); // Outputs: undefined
  var x = 10;
  ```

- **Function Hoisting**: Function declarations are also hoisted to the top of their scope, allowing you to call a function before it is declared in the code.

  ```javascript
  foo(); // Outputs: "Hello, world!"
  function foo() {
    console.log("Hello, world!");
  }
  ```

- **Function Expressions**: Function expressions, on the other hand, are not hoisted. Only the variable declaration is hoisted, not the function assignment.

  ```javascript
  bar(); // Throws a TypeError: bar is not a function
  var bar = function () {
    console.log("Hello, world!");
  };
  ```

It's important to note that while hoisting moves the declarations to the top of the scope, the initializations remain in place. This means that variables and functions are accessible before they are declared, but their values are `undefined` until they are assigned a value .

---

---

### 6. Temporal Dead Zone (TDZ)

The Temporal Dead Zone (TDZ) is a behavior in JavaScript that occurs when trying to access a variable before it has been initialized. This happens with variables declared using `let` and `const` due to their block scoping and hoisting behavior.

When a variable is declared with `let` or `const`, it is hoisted to the top of its block scope, but it is not initialized. This means that the variable exists in the scope, but it cannot be accessed or assigned a value until the declaration statement is reached in the code. Attempting to access the variable before its declaration results in a `ReferenceError` due to the TDZ.
