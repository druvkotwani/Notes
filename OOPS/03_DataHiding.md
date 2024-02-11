# Data Hiding

Data hiding is a concept that allows restricting access to certain parts of an object, hiding the data from the outside world.

Data hiding is a way to protect the data from the outside world. It is a way to ensure that the data is not misused. Data hiding is also known as encapsulation.

In Java, we can hide the data by declaring the attributes of a class as private. We can provide public methods to access and modify the attributes. These methods are called getter and setter methods.

```java
public class Rectangle {
    private double length;
    private double breadth;

    public double getLength() {
        return length;
    }

    public void setLength(double length) {
        this.length = length;
    }

    public double getBreadth() {
        return breadth;
    }

    public void setBreadth(double breadth) {
        this.breadth = breadth;
    }

    double area(){
        return length*breadth;
    }
    double perimeter(double length, double breadth){
        return 2*(length + breadth);
    }

}
```
