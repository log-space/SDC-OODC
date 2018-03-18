<p align="right">
	<b>Top Principle</b>
</p>

<hr/>

###### Don't Repeat Yourself

```java

// A principle of development aimed at reducing repetition of software patterns.
// Replacing them with abstraction technique
// Then several copies of the same data using data normalization to avoid redundancy.
```

###### Law of Demeter

```java

// Refer to "Talk to friend not to stranger" is principle that one object knows another object.
// It seems like they have a dependency.
// According to Law of Demeter, a method M of object O should only call following types of methods :
//
// - Methods of Object O itself
// - Methods of Object passed as an argument
// - Method of object which is held in instance variable
// - Any Object which is created locally in method M

class Computer {

	void saveData(Hardisk seagate) {
	
		// as per first rule this method invocation is fine because 'seagate' is an argument.
		/* Hardisk samsung = seagate.create(); */
		
		// this call is a violation as we are using 'samsung' which we got from 'Hardisk'.
		/* samsung.newFolder(); */
		
		// this is also a violation instead using temporary variable it uses method chain.
		/* seagate.create().newFolder(); */
		
		// this is ok a constructor call not a method call.
		/* Trash cleaner = new Trash(); */
		
		// as rule four this method call is ok because instance of 'Trash' is created locally.
		/* cleaner.clean(); */
	};
}
```

###### Cohesion and Coupling

![low-cohesion](https://user-images.githubusercontent.com/36118701/36674867-faba5dc2-1b39-11e8-9530-394250e11ee2.jpg)

```java
// Cohesion

/*
 * Low Cohesion
 */

// Some methods not related to a class and not all of fields used by method
```

![high_cohesion](https://user-images.githubusercontent.com/36118701/36674864-fa144fea-1b39-11e8-80e2-fc50e5f05228.jpg)

```java
/*
 * High Cohesion
 */

// Method should be strong part of class' context and 80% of fields must be used by each methods
```

![low_coupling](https://user-images.githubusercontent.com/36118701/36674866-fa853b06-1b39-11e8-9508-5fe94e0d9ce9.jpg)

```java
// Coupling

/*
 * Low Coupling
 */

interface IPersistenceable {

	public abstract void create(String data);
	public abstract void retrieve(String data);
	public abstract void modify(String data);
	public abstract void destroy(String data);
}

class Hardisk implements IPersistenceable {

	public void create(String data) { System.out.print("Creating..." + data); };
	public void retrieve(String data) { System.out.print("Retrieving..." + data); };
	public void modify(String data) { System.out.print("Modifying..." + data); };
	public void destroy(String data) { System.out.print("Destroying..." + data); };
}

class Computer {

	private IPersistenceable storage;
	
	public Computer(IPersistenceable storage) {
	
		this.storage = storage;
	};
	
	void saveData(String data) {
	
		storage.create(data);
	};
	
	void showData(String data) {
	
		storage.retrieve(data);
	};
	
	void editData(String data) {
	
		storage.modify(data);
	};
	
	void deleteData(String data) {
	
		storage.destroy(data);
	};	
}

public class Main {

	public static void main(String[] args) {
	
		IPersistenceable seagate = new Hardisk();
		Computer asus = new Computer(seagate);
		
		asus.saveData("index");
		asus.showData("index");
		asus.editData("index");
		asus.deleteData("index");
	};
}
```

![high_coupling](https://user-images.githubusercontent.com/36118701/36674865-fa4d8800-1b39-11e8-92d8-f2c57a71fbb3.jpg)

```java
/*
 * High Coupling
 */

class Hardisk {

	public static final int size = 10000;
}

class Computer {

	void saveData(Hardisk seagate) {
	
		System.out.print(seagate.size);
	};
}

public class Main {

	public static void main(String[] args) {

		Computer asus = new Computer();
		Hardisk seagate = new Hardisk();

		asus.saveData(seagate);
	};
};
```
