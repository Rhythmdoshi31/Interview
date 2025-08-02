#### 1. What is OOPS ?
	- It is a paradigm built on the concepts of objects.
	- It is an approach to problem solving carried out using Objects.

#### 2. What are Classes & Objects ? 
	Class --> user defined data type that acts as a blueprint for creating objects.
	Object --> Instace of a Class
``` java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();  // Object created
        myCar.color = "Red";
        myCar.speed = 120;
        myCar.drive();  // Output: Car is driving
    }
```

#### 3. Explain Constructors . 
	- Contructors are Special methods to Initialize Objects.
	- They have have the same name as the class.
	- They have no return type
	- Auto called when an Object is created.
	- Can be Overloaded.
###### There are 3 Types of Constructors -->
	1. Default Constructors (has no parameters).
	2. Parameterized Constructors.
	3. Copy Constructors (NOT IN JAVA).

#### 4. Explain Inheritance .
	Inheritance lets a class to inherit properties and characteristics from another class.
	
	Types of Inheritance -->
		1. Single Inheritance.
		2. MultiLevel Inheritance.
		3. Hierarchial Inheritance.
		4. Hybrid Inheritance.
![[Pasted image 20250801140620.png]]
	###### NO MULTIPLE INHERITANCE IN JAVA USING CLASSES  TO AVOID AMBIGUITY.
``` java
class Animal {
    void eat() { System.out.println("eating..."); }
}

class Dog extends Animal {
    void bark() { System.out.println("barking..."); }
}

class Cat extends Animal {
    void meow() { System.out.println("meowing..."); }
}
```

#### 5. Explain Encapsulation .
	- Wrapping up the DATA and their methods that operate the data together in a classa and only exposing a controlled Interface to access it.
	- IT increases SECURITY, gives CONTROL and EASIER MAINTAINANCE.
###### Encapsulation can be done by PRIVATE variables and public GETTERS & SETTERS.
``` java
public class Person {
    private String name;     // private = hidden from outside

    // public getter
    public String getName() {
        return name;
    }

    // public setter
    public void setName(String name) {
        this.name = name;
    }
}

```

#### 6. Explain Abstraction .
	- Abstractiion means hiding INTERNAL DETAILS and SHOWING only essential details.
	- The Focus is on What Data is Exposed.
	- Done to reduce Complexity and Code Duplication and Increase Security.
###### Abstraction can be done by using ABSTRACT classes or INTERFACES.
``` java
// Interface - only defines *what* to do
interface Animal {
    void makeSound();  // abstract method
}

// Concrete classes - define *how* to do it
class Dog implements Animal {
    public void makeSound() {
        System.out.println("Dog barks");
    }
}
```

#### 9. Explain Polymorphism .
	- The word polymorphism means Many Forms.
	- It allows an object to have Multiple Behaviors.
	- It allows Javaq to call the Correct Method based on Object's actual type OR method signature.
	Types of Polymorphism -->
		1. Compile Time Polymorphism. [Static Binding]
		2. Run Time Polymorphism. [Dynamic Binding]
###### 1. Compile-Time Polymorphism --> 
	- Happens at compile time.
	- Done using Method OverLoading
	- Happens within the SAME CLASS.
	- SAME METHOD NAME BUT DIFFERENT PARAMETERS.
``` java
class Calculator {
	int add (int a, int b) {
		return a + b;
	}
	int add (int a, int b, int c) {
	return a + b + c;
	}
}
```

###### 2. Run-Time Polymorphism --> 
	- Happens at runtime.
	- Done using Method Overriding.
	- Requires INHERITANCE.
	- SAME METHOD NAME< SAME PARAMETERS BUT DIFFERENT IMPLEMENTATION IN CHILD CLASS.
``` java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Dog barks");
    }
}
```

#### 10. Explain Abstract classes & Interfaces.
	- Abstract classes are blueprints for other classes inherited from it.
	- They cannot be instantized [Their objects cannot be created directly].
	- USED TO MAINTAIN A COMMON STRUCTURE ACROSS ALL RELATED CLASSES.
	- USED WHEN YOU HAVE SHARED LOGIC + UNIMPLEMENTED BEHAVIOR.
	- Can have constructors.
``` java
abstract class Animal {
    abstract void makeSound();  // abstract method

    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Dog barks");
    }
}

```

	- Interfaces let us use Multiple Inheritane in Java.
	- Interfaces have no constructors.
``` java
interface A {
    void methodA();
}

interface B {
    void methodB();
}

class C implements A, B {
    public void methodA() {
        System.out.println("Method A");
    }
    public void methodB() {
        System.out.println("Method B");
    }
}
```

