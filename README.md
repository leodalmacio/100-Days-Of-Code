# 100-Days-Of-Code ATTEMPT 2
-- Introspect for a bit on what ways we can do to improve our previous attempt

1. Always leave a time to study, either after waking up, or going early on work, or on lunch break.
2. Don't overwork yourself.
3. Every Saturday(except the first week and first month), create an outline on what you want to finish/learn for this week, and set a major goal for the month.
4. No matter what, learn something first before lazing around.
5. Always commit what you learn, before leaving work, either it's done or not, so you can continue at home if ever.

So, for now that's what I can think about, so good luck with the second attempt.


## Month 1 (July 24, 2019 - Aug. 22, 2019)

*__Goals__*
1. Finish the Beginners Java book
---
 

### Week 1 (July 24, 2019 - July 30, 2019)

*__Goals__*
1. Learn and create a Multithreaded Program
2. Study Enumarations, Autoboxing, Static Import, and Annotations
---

 

#### Day 1 (July 24, 2019 - Wed)

*__Goals for the week__*
1. Learn and create a Multithreaded Program
2. Study Enumarations, Autoboxing, Static Import, and Annotations
---
**<u>Process-based vs Thread-based MULTITASKING</u>**

* __Process-based multitasking__
    > * the feature that allows a computer to run multiple programs concurrently.
    > * Smallest unit is a program.

* __Thread-based multitasking__
    > * allows a SINGLE programs to to perform multiple task, such as a text editor can be formatting a text at the same time that it is printing.
    > * Thread is the smallest unit of dispatchable code.

**<u>Thread Class and Runnable Interface(Creating threads in Java)</u>**

**NOTE** All process have atleast one thread of execution. Including the main method, which have the main thread of the program.


Both Thread and Runnable is packaged on **java.lang**.

Thread Class implements Runnable Interface

Using Runnable Interface, the run method needs to be implemented.
Just implement what you want the thread to do when it starts running inside the run method.

After that create a Thread Class that would accept the superclass that implements the run method.

Then use the start method of the thread class that would execute the run method that was implemented.

The example here uses the thread inside the class where Runnable is implemented, but it doesn't have to be.

```java
class MyThread implements Runnable {
    private Thread thread;

    // Construct a new thread and give it a name
    private MyThread(String name) {
        thread = new Thread(this, name);
    }

    public static MyThread createAndStart(String name) {
        MyThread myThread = new MyThread(name);

        myThread.thread.start(); // start the thread
        return myThread;
    }

    // abstract method of Runnale Interface
    // Entry point of thread
    public void run() {
        System.out.println(thread.getName() + " starting.");
        try {
            for (int i = 0; i < 10; i++) {
                Thread.sleep(400);
                System.out.println("In " + thread.getName() + ", count is " + i);
            }
        } catch (InterruptedException e) {
            System.out.println(thread.getName() + " interrupted.");
        }

        System.out.println(thread.getName() + " terminating.");
    }
}

class ThreadVariations {
    public static void main (String args[]) {
        System.out.println("Main Thread starting");

        //First, construct a MyThread Object.
        MyThread mt = MyThread.createAndStart("Child #1");

        for(int i = 0; i < 50; i++) {
            System.out.print(".");
            try {
                Thread.sleep(100);
            } catch (InterruptedException exc) {
                System.out.println("Main thread interrupted.");
            }
        }

        System.out.println("Main thread ending.");
    }
}

```

When using Thread Class, you would still need to provide implementation
for the run method();

**<u>Determining when a thread ends</u>**
* isAlive()
    > * used to check is thread is still alive
* join()
    > * a another way to wait for the child thread to finish
    > * the idea is when the child threads can finally join to the parent thread

#### Day 2 (July 25, 2019 - Thu)
*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. Study Enumarations, Autoboxing, Static Import, and Annotations
---
**<u>Setting Thread Priority</u>**

Thread priority determines how much the cpu time each thread would receive relative to the other active threads.
**NOTE** Just because a thread has a higher priority doesn't doesn't mean it would finish first.


MIN_PRIORITY = 1;

NORM_PRIORITY = 5; // default priority

MAX_PRIORITY = 10;

**<u>Synchronization</u>**

* Synchronized Method
    * synchronized int sumArray(int arr[]) {
        ..... // Code block
    }
* Synchronized Statement
    *  synchronized (args) {
        ... // Statementments to synchronize
    }

**<u>Inter-thread Communication</u>**
* notify();
    > * notify one thread that currently waits
* wait();
    > * stop the current thread from running and wait for a notify method to be called to the thread
* notifyAll();
    > * notify all threads that currently wait

**NOTE** take note of DeadLock where in all threads are waiting and nothing is running which would in turn seems like it hangs

**<u>SUSPENDING, RESUMING, AND STOPPING THREADS</u>**

These are depricated prior to Java 2 becuase of deadlocks(suspend, resume, stop)

To implement on Java 2 and above, you can impelement then on the thread itself and just have a variable that would hold the thread state.

**<u>Enumerations</u>**

In simple form, enumeration is a list of named constants that define a new data type with a fixed number of values.
Each enumeration constanst are implicitly public and static.

**<u>values() and valuesOf()</u>**

* values()
    > * used to get all the values of the enum
* valuesOf(arg)
    > * return the enum with the value of arg;

**<u>Constructors, Methods, Instance Variables, and Enumeration</u>**

> * Each enum constants is an object of its enum type. Thus, it can define constructor, add methods, and have instance variables.
> * Each enum constant can call any method defined by enum.
> * Each enum have its own copy of any instance var defined by the enum.

```java
enum Transport {
    CAR(65), Truck (55);
    private int speed;

    Transport(int s) {
        speed = s;
    }
    
    int getSpeed() {
        return speed;
    }
}
```

**<u>Two Important Restrictions Of Enumeration</u>**

> 1. Enumeration can't inherit from another class
> 2. An enum can't be a superclass, which means it can't be extended.

**<u>Java.lang.enum</u>**

Even though you can't inherit a superclass when declaring enum, all enumerations inherit from **java.lang.enum**

**<u>compareTo() and ordinal()</u>**

* ordinal()
    > * get the ordinal value of the enum type starting from 1
* compareTo()
    > * check if the ordinal value of enum type is greater than less than or equal to.

#### Day 3 (July 25, 2019 - Thu)
*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. ~~Study Enumarations, Autoboxing, Static Import,~~ and Annotations

**<u>Type Wrappers</u>**
Type Wrappers are classes that encapsulate the primitive data types.

Pre-Java 9

Integer (int num)

Integer (String str) thrown NumberFormatException

Double (double num)

Double (String str) throw NumberFormatException

E.i
int prim = 1;

Integer obj = new Integer(prim);

From Java 9

Type-wrapper constructors have been depricated, in favor of **valueOf()** as this would provide a cache for datas from (-128 to +127)

This works some how the same as String Pool where in:
``` 
Integer intObj = 127;
Integer intObj2 = 127;
System.out.println(intObj == intObj2); // true

Integer intObj = 128;
Integer intObj2 = 128;
System.out.println(intObj == intObj2); // false

Integer intObj = 128;
Integer intObj2 = 128;
System.out.println(intObj.equals(intObj2)); // true
```

**NOTE** Primitive data types are used instead of the Object because they are much faster.

**<u>Auto-boxing and Auto-unboxing</u>**
* Auto-boxing
    * The process which box(convert) a primitive data type to their corresponding data type.
* Auto-unboxing 
    * Vice versa, Object data type -> Primitive data type

Autoboxing and unboxing also occurs in method params and expressions
void sample (Integer intObj){
    .../
}
sample(123);// Auto-boxes the 123 primitive to Integer

Integer sampleObj = 123;
++sampleObj; // This would unbox the sampleObj, increment it, then rebox it.

**WARNING** even though you can use the Object representation of the Data Types(Double, Integer...)
you should still not use them when not needed, as they would add overhead that isn't needed.


**<u>Static Imports</u>**
Used to import static members by their name

So instead of ```Math.pow()```, and ```Math.sqrt()```

You can just import them by

```
import static java.lang.Math.sqrt;
import static java.lang.Math.pow;
// you can also use
// import static lang.Math.*;
// which would import all statics on Math

// then you can use them as

sqrt();
pow();
```
**NOTE** Just because it is convinient you shouldn't abuse it.
E.i.
import static java.lang.System.out;

// you can use it as
out.println("The out now is not that clear, because you do not know what out it is pertaining");


**<u>Annotations(Metadata)</u>**
Provides a way to embed supplemental information into a soure file.

They are created through a mechanism based on the interface

```
@interface MyAnnotation{
    String str();
    int val();
}
```

All annotations consists solely of method declartions.
However, you don't provide bodies to these methods.
Instead, Java does that.
Moreoever, the methods act much like fields.

All Annotations automatically extends from Annotation(java.lang.annotation) interface.

... to be continued


**<u></u>**
**<u></u>**



### Week 2
*Objectives*
1. Learn Generics














### Week 3
*Objectives*
1. Lambda Expressions and Method References
2. Modules










### Week 4
1. Swings? Still not sure













