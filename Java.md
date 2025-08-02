#### 1. How is Java Platform Independent ?
	It compiles the program into bytecode which is independent of hardware/software.
	It still needs JVM for further execution of bytecode.

#### 2 What is JVM ?
	JVM runs the Bytecode.
	It is the Java Interpreter, responsible for loading, verifying and executing the bytecode created in java.

![[Pasted image 20250801100740.png]]

#### 3. What is JIT ?
	JIT compiler is a part of JVM which is used to compile the Bytecode.

#### 4. Explain Heap and Stack memory in Java .
	- The Stack memory stores the References to Objects, Method Calls, and local Variable. [Smaller Size & Faster & LIFO]
	- The Heap memory stores the actual Objects and Classes, and is Managed by the GC. [Larger Size & Slower]
``` javascript 
	String name = new String("Rhythm")
```
	Here, the reference "name" is stored in Stack, while the Object is in Heap.

#### 5. Explain  --> public static void main(String args[]) . 
	- Public --> Access Modifier to make Main function Globally Available.
	- Static --> Keyword to Start the function without initiating a Object, as no Objects have been created when Main method is called. (So that a single copy of Object is used among all Methods / Objects)
	- Void   --> Return type
	- Main   --> Identifies the starting point of Interpretation done by JVM.
	- Args[] --> Allows us to pass command-line Args + Starting point Identification for JVM.

#### 6. Explain Function vs Method ?
	- Function is a Stand-Alone Block of Code to perform a task.
	- Method is Function tha belongs to an Object or a Class.
	- Java doesn't support Functions.

#### 7. Explain Java String Pool ?
	Place in Heap where all the Strings defined in the program are stored.

#### 8. Explain Packages in Java ?
	Packages are folders to group the related classes together and avoid naming conflicts.
		- Packages are of 2 types -
			1. Built In --> java.utils, java.io
			2. User Defined
	Also, Different Packages can have the Same Class names.

#### 9. What are the data types in Java ?
###### 1. Primitive Data Types --> 
	1. boolean
	2. byte (8 bit)
	3. char (16 bit)
	4. double (64 bit)
	5. float (32 bit)
	6. short (16 bit)
	7. int (32 bit)
	8. long (64 bit)
###### 2. Non-Primitive Data Types --> 
	1. Strings
	2. Arrays.
	3. Classes.
	4. Objects.
	5. Interfaces.

#### 10. Class Variables (Static Variables) ?
	These Variables are declared static and outside of any methods, they are accessible anywhere in the class.
``` java
class Hello {
    public static int count = 0;	
}
```
	A class Variable without Static is called as Instance Variable.

#### 11. Explain the Scanner Class in java .
	Used to take inputs.
``` java
	Scanner sc = new Scanner(System.in);
	int x = sc.nextInt();
```

#### 12. What are Constructors ?
	- Special Methods to initialize Objects.
	- It has the same name as the Class.
	- It has No Return Type.
###### Constructors can also be private to limit there scope to a class.

#### 13. Explain This Keyword .
	This refers to the current Object in the a class Method or constructor.

#### 14. Final vs Finally vs Finalized ?
	- Final -> Keyword to prevent Inheritance or Overriding.
	- Finally -> Runs after try and catch.
	- Finalized -> Method used by GC before deleting an Object.
``` java
final int x = 10; // Cannot change later

try {
    // risky code
} finally {
    System.out.println("Always executes");
}

protected void finalize() {
    System.out.println("Object destroyed");
}
```

#### 15. Explain Checked vs Unchecked Exceptions .
	Checked exceptions are handled at compile-time [ IOException ].
	Unchecked exceptions aren't handled at compile-time [NullPointerException].

#### 16. Explain the Collections Framework ?
	It is a set of classes and interfaces.
	Like - Lists, Sets, maps etc.

#### 17. MultiThreading in Java .
	A Thread is the smallest unit of execution.
	Java has multiple threads which allow multile tasks to run concurrently.
	This improves the efficiency and performace.
	Java handles Multithreading Using THREAD class or RUNNABLE interface.


#### 18. Synchronization in Java.
	Synchronzation keywork ensure One Thread can access One Resource at a time.
	They are used to Prevent Consistency that is caused due to Multiple Threads accessing the same data at the same time.

#### 19. What are the Different States of a Thread ?
	New, Runnable, Running, Blocked, Waiting, Terminated.

#### 20. Explain difference between Throw and Throws .
	Throw is used to throw an exception inside the body.
	Throws is used to declare that a method might throw an Exception and is declared at the method signature.

#### 21. What is GC and its algos in Java ?
	GC is used to automatically remove unused objects from the Heap that are no longer reachable.
	The Different GC algoithms are -->
		- G1 (Garbage First) [Default in JVM] - Splits heap into regions and collects them in Parellel to reduce pause times.
		- Mark and Sweep - marks live objects and removes unmarked ones.
		- Generational GC - Divides heap into Young, Old and Permanent generations.

#### 22. What are Deadlocks ?
	DeadLock happends when 2 or more Threads are locked in Waiting State for each other and none of them can proceed.

#### 23. Explain Comparable vs Comparator .
	Comparable is used to define the natural Ordering of a Class. (Only 1 type or sorting is possible in a class with Comaparable)
``` java
public class Student implements Comparable<Student> {
    int roll;
    String name;

    public Student(int roll, String name) {
        this.roll = roll;
        this.name = name;
    }

    // Sort by roll number (ascending)
    public int compareTo(Student other) {
        return this.roll - other.roll;
    }
}
```
	Comparators are used to define Custom Sorting of Objects.
``` java
class NameComparator implements Comparator<Student> {
    public int compare(Student a, Student b) {
        return a.name.compareTo(b.name);
    }
}
Collections.sort(studentList, new NameComparator());
```

###### Eg. Comparator for a PriorityQueue - 
``` java
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Comparator.reverseOrder());

 // Or using Lambda Expressions --> 

PriorityQueue<Student> pq = new PriorityQueue<>((a, b) -> b.marks - a.marks);

```

#### 24. Explain Constructor Overloading .
	 Creating multiple Contructors with same name but different parameters.

#### 25. Explain Access Specifiers .
``` java
public int a;        // accessible from anywhere
private int b;       // only inside same class
protected int c;     // inside same package + subclass
int d;               // default: only same package
```