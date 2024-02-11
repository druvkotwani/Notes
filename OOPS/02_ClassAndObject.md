# How to write a class

A class is a blueprint for creating objects. It defines a set of attributes and methods that will characterize any object that is instantiated from this class.

```java
public class Rectangle {
    double length;
    double breadth;

    double area(){
        return length*breadth;
    }
    double perimeter(double length, double breadth){
        return 2*(length + breadth);
    }

}

class Druv{
    public static void main(String[] args) {
        Rectangle r1 = new Rectangle();
        r1.length = 5;
        r1.breadth = 5;

        System.out.println(r1.area());
        System.out.println(r1.perimeter(4, 5));
    }
}

```

In the above example, we have created a class named `Rectangle`. It has two attributes `length` and `breadth` and two methods `area` and `perimeter`. We have created an object of the `Rectangle` class and accessed its attributes and methods.

# Object

An object is an instance of a class. When a class is defined, no memory is allocated for its attributes. When an object is created, memory is allocated for the attributes. An object is also called an instance of a class.

```java
Rectangle r1 = new Rectangle();
r1.length = 5;
r1.breadth = 5;
```

In the above example, `r1` is an object of the `Rectangle` class. We have accessed its attributes `length` and `breadth` and assigned values to them.
