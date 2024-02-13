```java

class Parent {
    Parent(){
        System.out.println("Parent Constructor");
    }
}
class Child extends Parent{
    Child(){
        System.out.println("Child Constructor");
    }
}

public class InheritConst{
    public static void main(String[] args) {
        Child ch = new Child();

    }
}

```

- In the above example, the constructor of the parent class is called first and then the constructor of the child class is called.
- The output of the above code will be:

```java
Parent Constructor
Child Constructor
```
