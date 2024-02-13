# Inheritance

- Inheritance is the process of acquiring features of a existing class into a new class

```java

class Parent {
    void show(){
        System.out.println("Parent Class");
    }
}

class Child extends Parent{
    void display(){
        System.out.println("Child Class");
    }
}

public class Inherit{
    public static void main(String[] args) {
        Child ch = new Child();
        ch.show();
        ch.display();
    }
}

```

- In the above example, the `Child` class is inheriting the `show()` method from the `Parent` class.
- The `Child` class is also having its own method `display()`.
- The `main` method is creating an object of the `Child` class and calling the `show()` and `display()` methods.
- The output of the above code will be:

  ```java
  Parent Class
  Child Class
  ```
