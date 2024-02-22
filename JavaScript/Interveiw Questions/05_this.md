## Explain "this" in JavaScript

`this` is a keyword in JavaScript that refers to the object it belongs to. It has different values depending on where it is used

Yes, you can conceptualize the relationship between `this` in arrow functions and normal functions in JavaScript using the notation you provided, but with a slight adjustment for clarity:

- **Arrow Function**: `this -> parent -> parent`
- **Normal Function**: `this -> parent`

This notation captures the essence of how `this` behaves differently in arrow functions compared to normal functions:

- **Arrow Function**: Arrow functions do not bind their own `this`. Instead, they inherit `this` from the enclosing lexical scope (the nearest non-arrow parent function or global scope if there's no enclosing function). This means that `this` in an arrow function is determined by the `this` value of the parent scope, not by how the arrow function is called. This behavior is due to the lexical scoping of `this` in arrow functions, which is why they are often referred to as lexically bound [Source 0][Source 2].

- **Normal Function**: In normal functions, `this` is determined by how the function is called. If a normal function is called as a method of an object, `this` refers to the object. If it's called as a standalone function, `this` refers to the global object (or `undefined` in strict mode) [Source 0][Source 2].

This distinction is crucial for understanding how to correctly use arrow functions and normal functions in different contexts, especially when dealing with object methods and callbacks where `this` binding is expected to refer to the object or the context in which the function is defined [Source 4].

```javascript
this.a = 5;

function getParam = () =>{
    console.log(this.a);
}

getParam(); // 5
```

```javascript
let user = {
  name: "John",
  age: 30,
  childObj: {
    newName: "Dhruv",
    getDetails() {
      console.log(this.newName, this.name);
    },
  },
};
user.childObj.getDetails(); // Dhruv undefined
```

```javascript
let user = {
  name: "John",
  age: 30,
  getDetails: () => {
    console.log(this.age, this.name);
  },
};
user.getDetails();

//the value of 'this'in arrow function comes from its parent function in this case- window object
```

```javascript
let user = {
  name: "John",
  age: 30,
  getDetails() {
    const nested = () => console.log(this.age, this.name);
    nested();
  },
};
user.getDetails(); // 30 John
```

```javascript
class user {
  contructor(name, age) {
    this.name = name;
    this.age = age;
  }

  getDetails() {
    console.log(this.name, this.age);
  }
}

const user = new User("Dhruv", 30);
user.getDetails(); // Dhruv 30
```

```javascript
//What is the result of this code?

const user = {
  firstName: "John",
  getName() {
    const firstName = "Doe";
    return this.firstName;
  },
};

console.log(user.getName()); // John
```

```javascript
// What is the result of accessing its ref? Why?

function makeUser() {
  return {
    name: "John",
    ref() {
      return this;
    },
  };
}

let user = makeUser();
console.log(user.ref().name); // John
```

```javascript
// What is the result of this code?

const user = {
  name: "John",
  logMessage() {
    console.log(this.name);
  },
};

setTimeout(user.logMessage, 1000); // undefined

//The value of 'this' in the logMessage function is window object
//Fix:
setTimeout(() => user.logMessage(), 1000); // John
```

```javascript
// What is the result of this code?

const user = {
  name: "Dhruv",
  greet: function () {
    console.log(`Hello, ${this.name}`);
  },
  farewell: () => {
    console.log(`Goodbye, ${this.name}`);
  },
};

user.greet(); // Hello, Dhruv
user.farewell(); // Goodbye, undefined

//The value of 'this' in the farewell function comes from its parent function in this case- window object
```

```javascript
// Create an object calculator

let calculator = {
  read() {
    this.a = +prompt("a = ", 0);
    this.b = +prompt("b = ", 0);
  },
  sum() {
    return this.a + this.b;
  },
  mul() {
    return this.a * this.b;
  },
};

calculator.read();
console.log(calculator.sum());
console.log(calculator.mul());
```

```javascript
// What will be the output

var length = 4;

function callback() {
  console.log(this.length);
}

const object = {
  length: 5,
  method(callback) {
    callback();
  },
};

object.method(callback); // 4
```

```javascript
//Implement Calc

const calc = {
    total: 0,
    add(a){
        this.total += a;
        return this
    }
    sub(a){
        this.total -= a;
        return this
    },
    mul(a){
        this.total *= a;
        return this
    },
    div(a){
        this.total /= a;
        return this
    },
}

const result = calc.add(2).mul(3).div(4).sub(2).result();
console.log(result.total); // 1.5
```

```javascript

```
