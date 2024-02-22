# 1. Map

The `map()` function in JavaScript is a method of the `Array` object that creates a new array by applying a callback function to each element of the original array. It does not modify the original array but instead returns a new array with the results of the callback function.

Here is the basic syntax for the `map()` function:

```javascript
array.map(callbackFn, thisArg);
```

- `callbackFn`: A function that is called for each element in the array. It takes three arguments:
  - `currentValue`: The current element being processed in the array.
  - `index` (optional): The index of the current element being processed in the array.
  - `arr` (optional): The array `map` was called upon.
- `thisArg` (optional): An object to which the `this` keyword can refer inside the `callbackFn` function.

Here's an example of how to use `map()`:

```javascript
let numbers = [1, 2, 3, 4];
let squares = numbers.map(function (number) {
  return number * number;
});
console.log(squares); // [1,  4,  9,  16]
```

You can also use arrow functions for a more concise syntax:

```javascript
let numbers = [1, 2, 3, 4];
let squares = numbers.map((number) => number * number);
console.log(squares); // [1,  4,  9,  16]
```

The `map()` function can be used with objects by first obtaining the values using `Object.values()` and then applying `map()`:

```javascript
const scores = { math: 50, English: 70, Physics: 45, Agric: 60 };
let newScores = Object.values(scores).map((score) => score + 5);
console.log(newScores); // [55,  75,  50,  65]
```

Remember that `map()` does not mutate the original array but instead returns a new array. If you need to modify the original array, you should use other methods like `forEach()`.

---

# 2. Filter

The `filter()` function in JavaScript is a method of the `Array` object that creates a new array with all elements that pass the test implemented by the provided function. It does not mutate the original array but instead returns a new array with the elements that pass the test.

Here is the basic syntax for the `filter()` function:

```javascript
array.filter(callbackFn, thisArg);
```

- `callbackFn`: A function that is called for each element in the array. It takes three arguments:
  - `currentValue`: The current element being processed in the array.
  - `index` (optional): The index of the current element being processed in the array.
  - `arr` (optional): The array `filter` was called upon.
- `thisArg` (optional): An object to which the `this` keyword can refer inside the `callbackFn` function.

Here's an example of how to use `filter()`:

```javascript
function isBigEnough(value) {
  return value >= 10;
}

const filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
console.log(filtered); // [12,  130,  44]
```

You can also use arrow functions for a more concise syntax:

```javascript
const filtered = [12, 5, 8, 130, 44].filter((value) => value >= 10);
console.log(filtered); // [12,  130,  44]
```

The `filter()` function can be used with objects by first obtaining the values using `Object.values()` and then applying `filter()`:

```javascript
const scores = { math: 50, English: 70, Physics: 45, Agric: 60 };
let passingScores = Object.values(scores).filter((score) => score > 60);
console.log(passingScores); // [70,  60]
```

Remember that `filter()` does not mutate the original array but instead returns a new array. If you need to modify the original array, you should use other methods like `forEach()` .

---

# 3. Reduce

The `reduce()` function in JavaScript is a method of the `Array` object that executes a reducer function on each element of the array, resulting in a single output value. It does not mutate the original array but instead returns a single value.

The `reduce()` method in JavaScript is a method of the `Array` object that executes a reducer function on each element of the array, resulting in a single output value. It is used to reduce the array to a single value by accumulating a result, which is returned as the final output.

Here is the basic syntax for the `reduce()` function:

```javascript
array.reduce(callbackFn, initialValue);
```

- `callbackFn`: A function that is called for each element in the array. It takes four arguments:
  - `accumulator`: The accumulated value previously returned in the last invocation of the callback, or `initialValue` if supplied.
  - `currentValue`: The current element being processed in the array.
  - `currentIndex` (optional): The index of the current element being processed in the array.
  - `arr` (optional): The array `reduce` was called upon.
- `initialValue` (optional): A value to use as the first argument to the first call of the `callbackFn`. If no initial value is supplied, the first element in the array will be used and the iteration will start from the second element.

Here's an example of how to use `reduce()`:

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);
console.log(sum); //  15
```

In this example, `reduce()` is used to calculate the sum of all numbers in the array. The accumulator starts at 0 (the `initialValue`) and adds the current value to it with each iteration.

It's important to note that `reduce()` should not be used to modify the original array or external state. The callback function should be pure, meaning it should not have side effects. Instead, it should return a new value based on the inputs .

Remember that `reduce()` is a powerful tool but can be difficult to understand, especially for less-experienced developers. It's always good to consider the readability of your code when deciding whether to use `reduce()` over other array methods .

---

# 4. Polyfill for Map, Filter, and Reduce

The `map()`, `filter()`, and `reduce()` methods are part of the `Array` prototype in JavaScript and are available in modern browsers. However, if you need to support older browsers or environments that don't have these methods, you can create your own polyfills to provide these functionalities.

Here's an example of a polyfill for the `map()` method:

```javascript
// Polyfill for map
// Array.map((num, i, arr)=>{})

Array.prototype.myMap = function (cb) {
  let arr = [];
  for (let i = 0; i < this.length; i++) {
    arr.push(cb(this[i], i, this));
  }
  return arr;
};
```

And here's an example of a polyfill for the `filter()` method:

```javascript
// Polyfill for filter

Array.prototype.myFilter = function (cb) {
  let arr = [];
  for (let i = 0; i < this.length; i++) {
    if (cb(this[i], i, this)) {
      arr.push(this[i]);
    }
  }
  return arr;
};
```

And here's an example of a polyfill for the `reduce()` method:

```javascript
// Polyfill for reduce

Array.prototype.myReduce = function (cb, initialValue) {
  var accumulator = initialValue;

  for (let i = 0; i < this.length; i++) {
    accumulator = acumulator ? cb(accumulator, this[i], i, this) : this[i];
  }

  return accumulator;
};
```

# 5. forEach

The `forEach()` function in JavaScript is a method of the `Array` object that executes a provided function once for each array element. It does not mutate the original array but instead returns `undefined`.

Here is the basic syntax for the `forEach()` function:

```javascript
array.forEach(callbackFn, thisArg);
```

Here's an example of how to use `forEach()`:

```javascript
let numbers = [1, 2, 3, 4];

numbers.forEach(function (number) {
  console.log(number);
});

// 1
// 2
// 3
// 4
```

You can also use arrow functions for a more concise syntax:

```javascript
let numbers = [1, 2, 3, 4];

numbers.forEach((number) => console.log(number));
```

The `forEach()` function can be used with objects by first obtaining the values using `Object.values()` and then applying `forEach()`:

```javascript
const scores = { math: 50, English: 70, Physics: 45, Agric: 60 };

Object.values(scores).forEach((score) => console.log(score));
```

Remember that `forEach()` does not mutate the original array but instead returns `undefined`. If you need to modify the original array, you should use other methods like `map()` or `filter()`.

---

# Questions based on output

1.  Return the name of the student with the Capital letters

```javascript
let students = [
  { name: "John", rollNo: 20, marks: 80 },
  { name: "Doe", rollNo: 21, marks: 90 },
  { name: "Smith", rollNo: 22, marks: 85 },
  { name: "Alex", rollNo: 23, marks: 95 },
];
```

```javascript
let name = students.map((student) => student.name.toUpperCase());
console.log(name);
```

2. Return only the details of the student who has marks greater than 85

```javascript
let greaterThan85 = students.filter((obj) => obj.marks > 85);
```
