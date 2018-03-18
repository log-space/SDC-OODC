<p align="right">
	<b>Concept</b>
</p>

<hr/>

###### Enscapsulation
```java
class Notebook {

	private int width;
	private int height;

	public int getWidth() {
		
		return width;
	};
	
	public void setWidth(int width) {
		
		this.width = width;
	};
	
	public int getHeight() {
		
		return height;
	};
	
	public void setHeight(int height) {
		
		this.height = height;
	};
}
```

###### Inheritance
```java
class Computer {

	void saveData() {};
	void displayImage() {};
	void playSound() {};
}

class Notebook extends Computer {

	void connectWireless() {};
	void readOpticalDisc() {};
}

public class Main {

	public static void main(String[] args) {
	
		Notebook asus = new Notebook();
		
		asus.connectWireless();
		asus.readOpticalDisc();
	};
}
```

###### Abstraction
```java
interface IOperateable {

	public abstract void add();
	public abstract void substract();
	public abstract void multiply();
	public abstract void divide();
}

abstract class Calculator implements IOperateable {

	abstract void calculatePercentage();
	abstract void calculateRoot();
	abstract void calculateTrigonometric();
	abstract void calculateStatistic();
	public void add() {};
	public void substract() {};
	public void multiply() {};
	public void divide() {};
}

abstract class Computer implements IOperateable {

	abstract void saveData();
	abstract void displayImage();
	abstract void playSound();
	public void add() {};
	public void substract() {};
	public void multiply() {};
	public void divide() {};
}

class Notebook extends Computer {

	void readOpticalDisc() {};
	void connectWireless() {};
	void saveData() {};
	void displayImage() {};
	void playSound() {};
}

class Smartphone extends Computer {

	void call() {};
	void sendMessage() {};
	void connectWireless() {};
	void saveData() {};
	void displayImage() {};
	void playSound() {};
}
```

###### Polymorphism
```java
//* Method Overloading */
class Notebook {

	void saveData(int data) {
	
		System.out.print(data);
	};

	void saveData(int data, int size) {
	
		System.out.print(data);
		System.out.print(size);
	};

	void saveData(String data) {
	
		System.out.print(data);
	};

	void saveData(String data, String size) {
	
		System.out.print(data);
		System.out.print(size);
	};
}

/* Method Overriding */
class Computer {

	void saveData() {
	
		System.out.print("Save Data...");
	};
}

class Notebook extends Computer {

	void saveData() {
	
		System.out.print("Save Data to Laptop...");
	};
}
```

```java
/* Upcasting */
class Computer {

	void saveData() {
	
		System.out.print("Save Data...");
	};
}

class Notebook extends Computer {

	void saveData() {
	
		System.out.print("Save Data to Laptop...");
	};
	
	void connectWireless() {
	
		System.out.print("Connecting...");
	};
}

public class Main {
	
	public static void main(String[] args) {
		
		Computer asus = new Notebook();
		
		asus.saveData();					//Output : Save Data to Laptop...
	//	asus.connectWireless();					//Compile Time Error!!!
	};
}

/* Downcasting */
class Computer {

	void saveData() {
	
		System.out.print("Save Data...");
	};
}

class Notebook extends Computer {

	void saveData() {
	
		System.out.print("Save Data to Laptop...");
	};
	
	void connectWireless() {
	
		System.out.print("Connecting...");
	};
}

public class Main {

	public static void main(String[] args) {
		
		Computer asus = new Notebook();
		
		if (asus instanceof Notebook) {
		
			Notebook asusZenBookPro = (Notebook) asus;
			
			asusZenBookPro.saveData();			//Output : Save Data to Laptop...
			asusZenBookPro.connectWireless();		//Output : Connecting...
		};
	};
}
```
