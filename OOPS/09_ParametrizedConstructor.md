# Parametrized Constructor in Inheritance

- A constructor with parameters is called a parametrized constructor.
- The main purpose of the parametrized constructor is to initialize the instance variables of the class with the provided values.

```java
class Parent {
    int a;
    Parent(int a){
        this.a = a;
        System.out.println("Parent Constructor");
    }
}
class Child extends Parent{
    int b;
    Child(int a, int b){
        super(a);
        this.b = b;
        System.out.println("Child Constructor");
    }
}
```

- In the above example, the `Parent` class is having a parametrized constructor that takes an integer value as a parameter.
- The `Child` class is having a parametrized constructor that takes two integer values as parameters.
- The `super` keyword is used to call the constructor of the parent class.
- The `this` keyword is used to refer to the current class instance variable.

```java
public class InheritConst{
    public static void main(String[] args) {
        Child ch = new Child(10, 20);
    }
}
```

- The output of the above code will be:

```java
Parent Constructor
Child Constructor
```

- In the above example, the constructor of the parent class is called first and then the constructor of the child class is called.
