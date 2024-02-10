### Encapsulation

Encapsulation is Java is a mechanism
of wrapping the data(variables) and code acting on the data(methods) together as a single unit.

Encapsulation is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates.

In encapsulation, the variables of a class will be hidden from other classes, and can be accessed only through the methods of their current class, therefore it is also known as data hiding.

Encapsulation can be achieved by:

- Declare the variables of a class as private.
- Provide public setter and getter methods to modify and view the variables values.

```java
public class EncapsulationDemo {
    private String name;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

---

### Abstraction

Abstraction allows us to hide complex implementation details and expose only the essentials to the user. It provides a simplified view of the system, focusing on what the object does rather than how it does it. This makes the code easier to understand and maintain, and it hides unnecessary complexity from the user.

---

### Inheritance

Inheritance is a mechanism in which one object acquires all the properties and behaviors of a parent object. It is used for code reusability and to establish a relationship between two classes.

---

### Polymorphism

It means one name many forms. It is further of two types — static and dynamic. Static polymorphism is achieved using method overloading and dynamic polymorphism using method overriding. It is closely related to inheritance. We can write a code that works on the superclass, and it will work with any subclass type as well.

---
