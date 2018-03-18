<p align="right">
	<b>Class Design Principle</b>
</p>

<hr/>

###### Single Responsibility Principle
```java
// A class should have only one responsibility and it should be entirely encapsulated by the class.
// High Cohesion.
```

![single responsibility principle](https://user-images.githubusercontent.com/36118701/36731238-b960e3aa-1bfc-11e8-9c7a-e31241daea31.png)

###### Open Close Principle
```java
// Software entities should be opened for extension but closed for modification.
// Low Coupling.
```

```java
/*
 * Wrong Example
 */

class AreaCalculator {

	public double calculateRectangleArea(Rectangle rectangle) {
	
		return rectangle.length * rectangle.width;
	};
	
	public double calculateCircleArea(Circle circle) {
	
		return (22/7) * circle.radius * circle.radius;
	};
}

class Rectangle {

	double length;
	double width;
}

class Circle {

	double radius;
}
```

```java
/*
 * Correct Example
 */

interface Shape {

	public abstract double calculateArea();
}

class Rectangle implements Shape {

	double length;
	double width;
	double calculateArea() {
	
		return length * width;
	};
}
 
class Circle implements Shape {

	double radius;
	double calculateArea() {
	
		return (22/7) * circle.radius * circle.radius;
	};
}

class AreaCalculator {

	public double calculateShapeArea(Shape shape) {
	
		return shape.calculateArea();
	};
}
```

###### Liskov's Substitution Principle
```java
// If S is a subtype of T then object of type T may be replaced with objects of type S.
// Combination of Inheritance and Polymorphism.
```

![single responsibility principle](https://user-images.githubusercontent.com/36118701/36732901-9dc4f23a-1c01-11e8-9ca6-4667343d2e69.png)

###### Interface Segregation Principle
```java
// Clients should not be forced to depend upon interfaces that they don't use.
// Splitting the interfaces.
```

```java
/*
 * Wrong Example
 */
```
![wrong](https://user-images.githubusercontent.com/36118701/36735178-20b2273e-1c08-11e8-99e3-5bc6032875cd.png)

```java
/*
 * Correct Example
 */
```
![correct](https://user-images.githubusercontent.com/36118701/36735177-206dbe6e-1c08-11e8-9d6c-4df0b1f97464.png)

###### Dependency Inversion Principle
```java
// High-level modules should not depend on low-level modules. Both should depend on abstractions.
// Big Low Coupling.
```

```java
/*
 * Wrong Example
 */
```
![wrong](https://user-images.githubusercontent.com/36118701/36735984-07b7f068-1c0a-11e8-90c0-e7db73e224b7.png)

```java
/*
 * Correct Example
 */
```
![correct](https://user-images.githubusercontent.com/36118701/36735983-07742b08-1c0a-11e8-8f8d-d5f73330828e.png)
