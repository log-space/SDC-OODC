<p align="right">
	<b>Concept</b>
</p>

<hr/>

###### Generalization & Specialization
![single inheritance](https://user-images.githubusercontent.com/36118701/36641405-89c6bcb0-1a61-11e8-87a2-de3064ff1820.PNG)

```java
// Single Inheritance

class Computer {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	public Computer() {
	
		...
	};
}

class Notebook extends Computer {

	void connectWireless() { ... };
	void readOpticalDisc() { ... };
	public Notebook() {
	
		//Constructor of Computer will be invoked first
		...
	};
}
```

![multilevel inheritance](https://user-images.githubusercontent.com/36118701/36641404-8991da72-1a61-11e8-9ada-2b7d517f8609.PNG)

```java
// Multilevel Inheritance

class Computer {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	public Computer() {
	
		...
	};
}

class Desktop extends Computer {

	void readOpticalDisc() { ... };
	void request() { ... };
	public Desktop() {
	
		//Constructor of Computer will be invoked first
		...
	};
}

class Server extends Desktop {

	void respond() { ... };
	public Server() {
	
		//Constructor of Desktop will be invoked first
		...
	};
}
```

![hierarchical inheritance](https://user-images.githubusercontent.com/36118701/36641403-895a28a2-1a61-11e8-8085-3b40488d2c40.PNG)

```java
// Hierarchical Inheritance

class Computer {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	public Computer() {
	
		...
	};
}

class Notebook extends Computer {

	void connectWireless() { ... };
	void readOpticalDisc() { ... };
	public Notebook() {
	
		//Constructor of Computer will be invoked first
		...
	};
}

class Smartphone extends Computer {

	void call() { ... };
	void sendMessage() { ... };
	void connectWireless() { ... };
	public Smartphone() {
	
		//Constructor of Computer will be invoked first
		...
	};
}
```


###### Generalization & Specialization : Abstraction
![generalization specialization - abstraction](https://user-images.githubusercontent.com/36118701/36641400-87bff076-1a61-11e8-8d82-09c17d50f3df.PNG)

```java
abstract class Computer {

	abstract void saveData() { ... };
	abstract void displayImage() { ... };
	abstract void playSound() { ... };
	public Computer() {
	
		...
	};
}

class Notebook extends Computer {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	void connectWireless() { ... };
	void readOpticalDisc() { ... };
	public Notebook() {
	
		//Constructor of Computer will be invoked first
		...
	};
}

class Smartphone extends Computer {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	void call() { ... };
	void sendMessage() { ... };
	void connectWireless() { ... };
	public Smartphone() {
	
		//Constructor of Computer will be invoked first
		...
	};
}
```

###### Generalization & Specialization : Realization
![generalization specialization - realization - multiple inheritance](https://user-images.githubusercontent.com/36118701/36641402-8876c0d0-1a61-11e8-9673-e396047639f6.PNG)

```java
// Multiple Inheritance

interface IPlugable {

	abstract void plugWiredTechnology();
}

interface IPairable {

	abstract void pairWirelessTechnology();
}

interface IOperateable extends IPlugable, IPairable {

	abstract void add();
	abstract void substract();
	abstract void multiply();
	abstract void divide();
}

class Computer implements IOperateable {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	void plugWiredTechnology() { ... };
	void pairWirelessTechnology() { ... };
	void add() { ... };
	void substract() { ... };
	void multiply() { ... };
	void divide() { ... };
}
```

![generalization specialization - realization - hybrid inheritance](https://user-images.githubusercontent.com/36118701/36641401-8842020a-1a61-11e8-91bc-502e941bbf1a.PNG)

```java
// Hybrid Inheritance

interface ISignal {

	public static final int voltageDown = 0;
	public static final int voltageUp = 1;
}

interface IPlugable extends ISignal {

	abstract void plugWiredTechnology();
}

interface IPairable extends ISignal {

	abstract void pairWirelessTechnology();
}

interface IOperateable extends IPlugable, IPairable {

	abstract void add();
	abstract void substract();
	abstract void multiply();
	abstract void divide();
}

class Computer implements IOperateable {

	void saveData() { ... };
	void displayImage() { ... };
	void playSound() { ... };
	void plugWiredTechnology() { ... };
	void pairWirelessTechnology() { ... };
	void add() { ... };
	void substract() { ... };
	void multiply() { ... };
	void divide() { ... };
}
```

###### Dependency
![capture](https://user-images.githubusercontent.com/36118701/36647119-66440124-1ab3-11e8-8c72-397bf9d43838.PNG)

```java
public class Hardisk {

	public static final int size = 536870912000;
}

public class Computer {

	void saveData(Hardisk seagate) {
	
		System.out.print(seagate.size);
	};
}
```

###### Association : Unary-Association
![association - unary-association](https://user-images.githubusercontent.com/36118701/36641398-874f7724-1a61-11e8-9c1c-d5ed12057d3f.PNG)

```java
class Computer {

	Computer partitionC;
	Computer partitionD;
	public Computer() {
	
		...
	};
}
```

###### Association : Binary-Association
![association - binary-association](https://user-images.githubusercontent.com/36118701/36641395-864a47d2-1a61-11e8-8048-f032c2986192.PNG)

```java
class Smartphone {

	Computer asus;
	public Smartphone() {
	
		...
	};
}

class Computer {

	Smartphone[] samsung;
	public Computer() {
	
		...
	};
}
```

###### Association : Binary-Association : Aggregation
![association - binary-association - aggregation](https://user-images.githubusercontent.com/36118701/36641393-8570226e-1a61-11e8-93bc-911de4ed01f6.PNG)

```java
/* 
 * Computer need a monitor,
 * without monitor computer still booting and monitor will have its own functional life.
 */

class Monitor {

	...
}

class Computer {

	Monitor dell;
	public Computer(Monitor dell) {
	
		this.dell = dell;
	};
}
```

###### Association : Binary-Association : Composition
![association - binary-association - composition](https://user-images.githubusercontent.com/36118701/36641394-85c3b6d6-1a61-11e8-9c7a-7857dadadcf2.PNG)

```java
/* 
 * Computer need a processor,
 * without processor computer cannot booting and processor will don't have any functional life.
 */

class Processor {

	...
}

class Computer {

	Processor amd;
	public Computer() {
	
		this.amd = new Processor();
		...
	};
}
```

###### Association : Ternary-Association
![association - ternary-association](https://user-images.githubusercontent.com/36118701/36641397-86cb0656-1a61-11e8-8379-9c4d07dda4e8.PNG)

```java
class Router {

	Tablet[] apple;
	Smartphone[] samsung;
	Computer[] asus;
	public Router() {
	
		...
	};
}

class Tablet {

	Router zte;
	public Tablet() {
	
		...
	};
}

class Smartphone {

	Router zte;
	public Smartphone() {
	
		...
	};
}

class Computer {

	Router zte;
	public Computer() {
	
		...
	};
}
```
