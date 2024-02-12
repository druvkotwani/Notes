# Constructor in Java

## What is a Constructor?

A constructor in Java is a special method that is used to initialize objects. The constructor is called when an object of a class is created. It can be used to set initial values for object attributes.

## Why use a Constructor?

The constructor is used to ensure that the object is properly initialized when it is created. It can be used to set initial values for object attributes. It can also be used to perform any necessary setup for the object.

## How to create a Constructor?

A constructor is created by defining a method with the same name as the class. The constructor does not have a return type. It can take parameters, just like any other method.

Here is an example of a constructor:

```java
public class MyClass {
  int x;

  // Constructor with a parameter
  public MyClass(int y) {
    x = y;
  }
}
```

In this example, the constructor takes a parameter and sets the value of the `x` attribute to the value of the parameter.

## Types of Constructors

There are two types of constructors in Java:

1. Default Constructor

A default constructor is a constructor that does not take any parameters. If a class does not have any constructor, then a default constructor is automatically created by the compiler.

Here is an example of a default constructor:

```java

public class MyClass {
  int x;

  // Default constructor
  public MyClass() {
    x = 5;
  }
}
```

In this example, the default constructor sets the value of the `x` attribute to 5.

2. Parameterized Constructor

A parameterized constructor is a constructor that takes one or more parameters. It is used to set initial values for object attributes.

Here is an example of a parameterized constructor:

```java
public class MyClass {
  int x;

  // Parameterized constructor
  public MyClass(int y) {
    x = y;
  }
}
```

In this example, the parameterized constructor takes a parameter and sets the value of the `x` attribute to the value of the parameter.

## Constructor Overloading

Constructor overloading is a concept in Java where a class can have more than one constructor. Each constructor must have a unique parameter list.

Here is an example of constructor overloading:

```java

public class MyClass {
  int x;

  // Constructor with no parameters
  public MyClass() {
    x = 5;
    }

    // Constructor with a parameter

    public MyClass(int y) {
    x = y;
    }
}
```

In this example, the class `MyClass` has two constructors: one with no parameters and one with a parameter.

## Summary

- A constructor is a special method that is used to initialize objects.
- The constructor is called when an object of a class is created.
- A constructor does not have a return type.
- There are two types of constructors in Java: default constructor and parameterized constructor.
- Constructor overloading is a concept in Java where a class can have more than one constructor.
