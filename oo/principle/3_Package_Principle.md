<p align="right">
	<b>Package Cohesion</b>
</p>

<hr/>

###### Reuse-release Equivalence Principle
```java
// The granule of reuse is the granule of release.
/*
 * THE GRANULE OF REUSE IS THE GRANULE OF RELEASE.
 * ONLY COMPONENTS THAT ARE RELEASED THROUGH A TRACKING SYSTEM CAN BE EFFECTIVELY REUSED.
 * THIS GRANULE IS THE PACKAGE.
 */
```

###### Common-Reuse Principle
```java
// Classes that change together are packaged together.
/*
 * THE CLASSES IN A PACKAGE ARE REUSED TOGETHER.
 * IF YOU REUSE ONE OF THE CLASSES IN A PACKAGE, YOU REUSE THEM ALL.
 */
```

###### Common-Closure Principle
```java
// Classes that are used together are packaged together.
/*
 * THE CLASSES IN A PACKAGE SHOULD BE CLOSED TOGETHER AGAINST THE SAME KINDS OF CHANGES.
 * A CHANGE THAT AFFECTS A PACKAGE AFFECTS ALL THE CLASSES IN THAT PACKAGE.
 */
```

<p align="right">
	<b>Package Coupling</b>
</p>

###### Acyclic Dependencies Principle
```java
// The dependency graph of packages must have no cycles.
/*
 * THE DEPENDENCY STRUCTURE BETWEEN PACKAGES MUST BE A DIRECTED ACYCLIC GRAPH (DAG).
 * THAT IS, THERE MUST BE NO CYCLES IN THE DEPENDENCY STRUCTURE.
 */
```

![adp without cycle](https://user-images.githubusercontent.com/36118701/36739856-922e37bc-1c13-11e8-8b7c-bc501ed3a923.PNG)

![adp with cycle](https://user-images.githubusercontent.com/36118701/36739855-91e58ef4-1c13-11e8-8b4d-de7936e7220c.PNG)

###### Stable-Dependencies Principle
```java
// Depend in the direction of stability.
/*
 * THE DEPENDENCIES BETWEEN PACKAGES IN A DESIGN SHOULD BE IN THE DIRECTION OF THE STABILITY OF THE PACKAGES.
 * A PACKAGE SHOULD ONLY DEPEND UPON PACKAGES THAT ARE MORE STABLE THAT IT IS.
 */
```

![sdp](https://user-images.githubusercontent.com/36118701/36739859-9262c16c-1c13-11e8-8d99-10759ef9771d.PNG)

###### Stable-Abstractions Principle
```java
// Abstractness increases with stability.
/*
 * PACKAGES THAT ARE MAXIMALLY STABLE SHOULD BE MAXIMALLY ABSTRACT.
 * INSTABLE PACKAGES SHOULD BE CONCRETE.
 * THE ABSTRACTION OF A PACKAGE SHOULD BE IN PROPORTION TO ITS STABILITY.
 */
```

