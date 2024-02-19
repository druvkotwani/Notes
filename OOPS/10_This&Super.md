# This keyword

- The `this` keyword is used to refer to the current class instance variable.
- The `this` keyword is used to call the constructor of the current class.
- The `this` keyword is used to call the method of the current class.
- The `this` keyword is used to pass the current class instance as an argument to another method.
- The `this` keyword is used to return the current class instance from the method.

```java
class Student {
    int rollno;
    String name;
    float fee;

    Student(int rollno, String name, float fee) {
        this.rollno = rollno;
        this.name = name;
        this.fee = fee;
    }

    void display() {
        System.out.println(rollno + " " + name + " " + fee);
    }
}

public class ThisKeyword {
    public static void main(String[] args) {
        Student s1 = new Student(111, "ankit", 5000f);
        Student s2 = new Student(112, "sumit", 6000f);
        s1.display();
        s2.display();
    }
}
```

- In the above example, the `this` keyword is used to refer to the current class instance variable.
- The `this` keyword is used to initialize the instance variables of the class with the provided values.
- The `this` keyword is used to call the method of the current class.

  ```java
  void display() {
      System.out.println(rollno + " " + name + " " + fee);
  }
  ```

- The `this` keyword is used to pass the current class instance as an argument to another method.
- The `this` keyword is used to return the current class instance from the method.

# Super keyword

- The `super` keyword is used to refer to the immediate parent class instance variable.
- The `super` keyword is used to call the immediate parent class constructor.
- The `super` keyword is used to call the immediate parent class method.

```java
class Animal {
    String color = "white";
}

class Dog extends
Animal {
    String color = "black";

    void printColor() {
        System.out.println(color); // prints color of Dog class
        System.out.println(super.color); // prints color of Animal class
    }
}

public class SuperKeyword {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.printColor();
    }
}
```

- In the above example, the `super` keyword is used to refer to the immediate parent class instance variable.
- The `super` keyword is used to call the immediate parent class method.

  ```java
  void printColor() {
      System.out.println(color); // prints color of Dog class
      System.out.println(super.color); // prints color of Animal class
  }
  ```

- The `super` keyword is used to call the immediate parent class constructor.

# Final keyword

- The `final` keyword is used to restrict the user.
- The `final` keyword is used to restrict the class.
- The `final` keyword is used to restrict the method.
- The `final` keyword is used to restrict the variable.

```java
final class A {
    // final method
    final void display() {
        System.out.println("Final method");
    }
}

class B extends A {
    void display() {
        System.out.println("Non-final method");
    }
}

public class FinalKeyword {
    public static void main(String[] args) {
        B obj = new B();
        obj.display();
    }
}
```

- In the above example, the `final` keyword is used to restrict the class.
- The `final` keyword is used to restrict the method.
- The `final` keyword is used to restrict the variable.

- the output of the above code will be:

```java
Final method
```
