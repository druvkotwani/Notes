JavaScript objects are key-value pairs where keys are strings (or Symbols) and values can be any JavaScript data type, including functions. Objects are used to store complex data structures and are one of the core features of JavaScript, enabling the language's object-oriented programming capabilities.

### Creating Objects

- **Object Literals**: The simplest way to create an object is by using object literal syntax, which involves defining an object within curly braces `{}` with key-value pairs separated by commas. For example:

  ```javascript
  const car = { type: "Fiat", model: "500", color: "white" };
  ```

- **Constructor Function**: You can also create objects using a constructor function. This involves defining a function that initializes the object's properties and then using the `new` keyword to create instances of the object. For example:

  ```javascript
  function Car(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
  }

  const car1 = new Car("Toyota", "Corolla", 2005);
  ```

- **Object.create()**: This method creates a new object, using an existing object as the prototype of the newly created object. For example:

  ```javascript
  const animal = {
    type: "Invertebrates",
    displayType() {
      console.log(this.type);
    },
  };

  const fish = Object.create(animal);
  fish.type = "Fishes";
  fish.displayType(); // Logs: Fishes
  ```

### Accessing and Modifying Object Properties

- **Dot Notation**: To access or modify the properties of an object, you can use dot notation. For example:

  ```javascript
  car.color = "red"; // Modify
  console.log(car.type); // Access
  ```

- **Bracket Notation**: Alternatively, you can use bracket notation, which is useful when the property name is stored in a variable or when the property name is not a valid identifier. For example:

  ```javascript
  const propertyName = "model";
  console.log(car[propertyName]); // Access
  ```

### Methods

- **Defining Methods**: Methods are functions that are properties of an object. They can be defined within the object literal or added to an object after its creation. For example:

  ```javascript
  const person = {
    name: "John Doe",
    greet: function () {
      console.log(`Hello, my name is ${this.name}`);
    },
  };

  person.greet(); // Call the method
  ```

### Prototypes and Inheritance

- JavaScript objects inherit properties and methods from a prototype object. By default, every object has a prototype, and you can access it using `Object.getPrototypeOf(obj)`. You can also set a new prototype for an object using `Object.setPrototypeOf(obj, newPrototype)`.

- **Inheritance**: JavaScript uses prototypal inheritance, where objects can inherit properties and methods from other objects. This is achieved by setting the prototype of an object to another object.

### Summary

JavaScript objects are versatile and powerful, allowing developers to encapsulate related data and functionality into a single entity. They can be created using various methods, including object literals, constructor functions, and `Object.create()`. Objects can contain properties of any data type, including other objects, and methods can be defined to perform operations on the object's data. JavaScript's prototype-based inheritance system allows objects to inherit properties and methods from other objects, enabling code reuse and polymorphism.

---

```javascript
const user = {
  name: "John",
  age: 30,
};
user.name = "Pete";
delete user.name;

// We can also use multiword property names, but then they must be quoted:

let user = {
  name: "John",
  age: 30,
  "likes birds": true, // multiword property name must be quoted
};

// Square brackets also provide a way to obtain the property name as the result of any expression – as opposed to a literal string – like from a variable:
console.log(user["likes birds"]); // true
console.log(user.name); // John
```

```javascript
const func = (function (a) {
  return a;
})(5);

console.log(func); // 5
```

```javascript
const property = "firstName";
const name = "John";

const user = {
  [property]: name,
};

console.log(user.firstName); // John
```

```javascript
const user = {
  name: "John",
  age: 30,
  isAdmin: true,
};

for (key in user) {
  console.log(key, user[key]);
}
```

```javascript
    const user = {
        a: "three" ,
        b: "four"
        a: "one",
    }

    console.log(user) // {a: "one", b: "four"}
```

```javascript
//create a function mulitplyByTwo(obj) that multipies all numeric properties of nums by 2

let nums = {
  a: 100,
  b: 200,
  title: "Multiply by 2",
};

multiplyByTwo(obj);

function multiplyByTwo(obj) {
  for (let key in obj) {
    if (typeof obj[key] === "number") {
      obj[key] *= 2;
    }
  }
}

console.log(nums); // { a: 200, b: 400, title: 'Multiply by 2' }
```

```javascript
//What's the result of this code?

const a = {};
const b = { key: "b" };
const c = { key: "c" };

a[b] = 123;
a[c] = 456;

a["[object Object]"] = 123;
a["[object Object]"] = 456;

console.log(a[b]); // 456
```

```javascript
//What is json.stringify and json.parse

const user = {
  name: "John",
  age: 30,
};

const strObj = JSON.stringify(user);
console.log(strObj); // {"name":"John","age":30}

const obj = JSON.parse(strObj);
console.log(obj); // { name: 'John', age: 30 }

//json.stringify converts an object to a string
//usually used to store data in local storage

//json.parse converts a string to an object
```

```javascript
//What is the result of this code?

console.log([..."hello"]); // [ 'h', 'e', 'l', 'l', 'o' ]
```

```javascript
//What is the result of this code?
const user = {
  name: "John",
  age: 30,
};

const admin = {
  admin: true,
  ...user,
};

console.log(admin); // { admin: true, name: 'John', age: 30 }
```

```javascript
//What is the result of this code?
const setting = {
  username: "John",
  level: 3,
  health: 100,
};

const data = JSON.stringify(setting, ["level", "health"]);
console.log(data); // {"level":3,"health":100}
```

```javascript
//What is the result of this code?

const shape = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius,
};

console.log(shape.diameter()); // 20
console.log(shape.perimeter()); // NaN
```

```javascript
//What is destructuring in JavaScript?

let user = {
  name: "John",
  age: 30,
};
const name = "Dhruv";
const { name: myName, age } = user;
console.log(myName); // John
console.log(name); // Dhruv
```

```javascript
//Nested Destructuring
let user = {
  fullName: {
    firstName: "John",
    lastName: "Doe",
  },
};

const {
  fullName: { firstName, LastName },
} = user;
console.log(firstName); // John
```

```javascript
//What is the result of this code?

function getItems(fruitList, favouriteFruit, ...args) {
  return [...fruitList, favouriteFruit, ...args];
}

// a rest parameter must be the last parameter in a function

console.log(getItems(["apple", "banana", "orange"], "mango", "grapes", "kiwi"));

// [ 'apple', 'banana', 'orange', 'mango', 'grapes', 'kiwi' ]
```

```javascript
//What is the result of this code?

let c = {
  greeting: "Hey!",
};
let d;
d = c;
c.greeting = "Hello";
console.log(d.greeting); // Hello

// d is a reference to c
```

```javascript
//What is the result of this code?

console.log({ a: 1, b: 2 } == { a: 1, b: 2 }); // false
console.log({ a: 1, b: 2 } === { a: 1, b: 2 }); // false

//objects are compared by reference
```

```javascript
//What is the result of this code?
let person = { name: "John" };
const memebers = [person];
person = null;

console.log(memebers); // [ { name: 'John' } ]
```

```javascript
//What is the result of this code?

const value = { number: 10 };

const multiply = (x = { ...value }) => {
  console.log((x.number *= 2));
};

multiply(); //20
multiply(); //20
multiply(value); //20
multiply(value); //40
```

```javascript
//What is the result of this code?

function changeAgeAndReference(person) {
  person.age = 25;
  person = {
    name: "Dhruv",
    age: 30,
  };
  return person;
}

const personObj1 = {
  name: "John",
  age: 50,
};
const personObj2 = changeAgeAndReference(personObj1);

console.log(personObj1); // { name: 'John', age: 25 }
console.log(personObj2); // { name: 'Dhruv', age: 30 }
```

```javascript
//What is shallow copy and deep copy in JavaScript?

//Shallow copy
const user = {
  name: "John",
  age: 30,
  address: {
    city: "New York",
  },
};

const copy = { ...user };
console.log(copy); // { name: 'John', age: 30, address: { city: 'New York' } }

//Deep copy

const deepCopy = JSON.parse(JSON.stringify(user));
console.log(deepCopy); // { name: 'John', age: 30, address: { city: 'New York' } }

//Shallow copy only copies the reference of the object
//Deep copy creates a new object with new reference

//Shallow copy is not suitable for nested objects
```

```javascript
//3 most common ways to copy an object in JavaScript

const user = {
  name: "John",
  age: 30,
};

//1. Object.assign
const copy1 = Object.assign({}, user);

//2. Spread operator
const copy2 = { ...user };

//3. JSON.parse and JSON.stringify
const copy3 = JSON.parse(JSON.stringify(user));
```
