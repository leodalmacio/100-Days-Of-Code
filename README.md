# 100-Days-Of-Code ATTEMPT 2

-- Introspect for a bit on what ways we can do to improve our previous attempt

1. Always leave a time to study, either after waking up, or going early on work, or on lunch break.
2. Don't overwork yourself.
3. Every Saturday(except the first week and first month), create an outline on what you want to finish/learn for this week, and set a major goal for the month.
4. No matter what, learn something first before lazing around.
5. Always commit what you learn, before leaving work, either it's done or not, so you can continue at home if ever.

So, for now that's what I can think about, so good luck with the second attempt.

## FUTURE TO DOs:

1. Improve upon what you've learned about Annotations, specially Marker Annotation
2. Go beyod the basics of Generics

## Month 1 (July 24, 2019 - August 20, 2019)

*__Goals__*

1. ~~Finish the Beginners Java book~~

*__Emergency Goals__*

1. ~~Learn Firebase~~
2. ~~Learn PWA~~

*__NEW GOAL__*
1. Clean Code

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

#### Day 3 (July 26, 2019 - Fri)
*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. ~~Study Enumarations, Autoboxing, Static Import,~~ and Annotations

---

**<u>Type Wrappers</u>**
Type Wrappers are classes that encapsulate the primitive data types.

* Pre-Java 9

    * Integer (int num)

    * Integer (String str) thrown NumberFormatException

    * Double (double num)

    * Double (String str) throw NumberFormatException

``` java
E.i
int prim = 1;


Integer obj = new Integer(prim);
```

* From Java 9

    * Type-wrapper constructors have been depricated, in favor of **valueOf()** as this would provide a cache for datas from (-128 to +127)

    * This works some how the same as String Pool where in:
``` java
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
```java
void sample (Integer intObj){
    .../
}
sample(123);// Auto-boxes the 123 primitive to Integer

Integer sampleObj = 123;
++sampleObj; // This would unbox the sampleObj, increment it, then rebox it.
```

**WARNING** even though you can use the Object representation of the Data Types(Double, Integer...)
you should still not use them when not needed, as they would add overhead that isn't needed.


**<u>Static Imports</u>**

Used to import static members by their name

So instead of ```Math.pow()```, and ```Math.sqrt()```

You can just import them by

``` java
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

E.g.
``` java
import static java.lang.System.out;

// you can use it as
out.println("The out now is not that clear, because you do not know what out it is pertaining");
```


**<u>Annotations(Metadata)</u>**

Provides a way to embed supplemental information into a soure file.

They are created through a mechanism based on the interface

``` java
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

#### Day 4 (July 27, 2019 - Sat)
*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. ~~Study Enumarations, Autoboxing, Static Import, and Annotations~~

*__New Goals__*
1. Generics
---

**<u>Annotations(Metadata)</u>**

To provide value to an annotation (from day 3)

```java
// Annotate a method.
@MyAnnotation(str = "Annotation Example", val = 100)
public static void myMeth() {
    //... 
}
```

**<u>Marker Annotations</u>**
> * These are specified w/o passing passing any arguments and w/o using parentheses.
> * Their sole purpose is to mark an item with some attributes.

**<u>Generics</u>**

> * at its core _generics_ means _parameterized types_.

```java
public class Gen<T> {
	T obj; 

	Gen(T o) {
		obj = o;
	}
	
	T getob() {
		return obj;
	}
	
	void showType() {
		System.out.println("Type of T is " + obj.getClass().getName());
	}
}

class GenDemo {
	public static void main(String[] args) {
		Gen<Integer> iObj;
		iObj = new Gen<Integer>(88);
		iObj.showType();
		int v = iObj.getob();
		System.out.println("value: " + v);

		System.out.println();

		Gen<String> strObj = new Gen<String>("Generics Test");
		strObj.showType();
		String str = strObj.getob();
		System.out.println("value: " + str);
	}
}

```

Notice the <T>, the T acts as the name of the **type PARAMETER**.
Thus T can be changed to ASD -> <ASD> if you want but it's traditional to use a Single Capital Letter as the type paramter name.
Other commonly used is **V** and **E**.

**NOTE** Java compiler doesn't actually create different versions of **Gen**, or of any other generic classes. Although it is helpful to think in these terms, it is not what actually happens.
Instead, the compiler removes all generic type information, substituting necessary casts, to make the code behave as if a specific version of Gen was created.
Thus, there is really only one version of **Gen** that actually exists in the program.
The process of removing generic type of information is called _erasure_.

**<u>Two type Parameter</u>**

``` java
public class TwoGen<T, V> {
    T obj1;
    V obj2;

    TwoGen(T o1, V o2) {
        obj1 = o1;
        obj2 = o2;
    }
}
```

**<u>Bounded Types</u>**

Are used to implement type safety to the generics.

``` java
public class BoundedTypes<T, V extends Number> {
    // code goes here
}
```
With this, the only objects that the **V** Type Parameter would take is the Super Class Number or all subclasses of Number.

This would also work:

``` java
public class Pair<T, V extends T> {
    // ... code goes here
}

public static void main {
    // Okay because both T and V are Integer
    Pair<Integer, Integer> x = new Pair<Integer, Integer>(1, 2);

    // Also Okay because Integer is sublcass of Number
    Pair<Number, Integer> y = new Pair<Number, Integer>(10.4, 2);

    // Not valid because String is not subclass of Number
    Pair<Number, String> z = new Pair<Number, string>(10.4, "2");
}
```

#### Day 5 (July 28, 2019 - Sun)
*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. ~~Study Enumarations, Autoboxing, Static Import, and Annotations~~

*__New Goals__*
1. Generics
2. Finish week two of LHTL
---

**<u>Using wild card arguments</u>**

``` java
public class NumericFns<T extends Number> {
	T num;

	NumericFns(T o) {
		num = o;
	}

	boolean absoluteEqual(NumericFns<?> ob) {
		return Math.abs(num.doubleValue()) == Math.abs(ob.num.doubleValue());
	}
}
```

The **?** is used to accept all types of Objects that uses the Generic NumericFns, but because the NumericFns is
bounded by <T extends Number> the type safety is still there.

**<u>Bounded Wild Cards</u>**

Based from the above you can also use this

``` java
NumericFns<? extends Number> ob) {}
```

So that you can also bound the wild card.

**<u>Generic Methods</u>**

As learned previously generic method can make use of the type parameter of the class.

However, it's also possible to declare a generic method on it's own.

``` java
public class GenericMethodDemo {
	static <T extends Comparable<T>, V extends T> boolean arraysEqual(T[] x, V[] y) {
		if (x.length != y.length) return false;

		for (int i = 0; i < x.length; i++)
			if (!x[i].equals(y[i])) return false;

		return true;
	}

	public static void main(String[] args) {
		Integer nums[] = { 1, 2, 3, 4, 5 };
		Integer nums2[] = { 1, 2, 3, 4, 5};
		Integer nums3[] = { 1, 2, 7, 4, 5};
		Integer nums4[] = { 1, 2, 7, 4, 5, 6};

		System.out.println(arraysEqual(nums, nums)); // true
		System.out.println(arraysEqual(nums, nums2)); // true
		System.out.println(arraysEqual(nums, nums3)); // false
		System.out.println(arraysEqual(nums, nums4)); // false

		// This won't compile because nums and dvals are not the same type
		// Double dvals[] = { 1.1, 2.2, 3.3, 4.4, 5.5 };
		//System.out.println(arraysEqual(nums, nums4));
	}
}

```

**NOTICE** that the Type Parameter ```<T extends Comparable<T>, V extends T>``` is declared before the return type ```boolean```.

**<u>Generic Constructor </u>**

``` java
public class GenericConstructor {
	private int sum;

	<T extends Number> GenericConstructor(T args) {
		sum = 0;
		for (int i = 0; i < args.intValue(); i++)
			sum++;
	}

	int getSum() {
		return sum;
	}
}

class GenConsDemo {
	public static void main(String[] args) {
		GenericConstructor sum = new GenericConstructor(4.0);
		System.out.println("Summation of 4.0 is " + sum.getSum());
	}
}
```

**<u>Generic Interface</u>**

These are used the same way as classes

``` java
interface Containment<T>{
    boolean contais(T o);
}

class MyClass<T> implements Containment<T>{
    T[] arrayRef;
    MyClass(T[] o) {
        arrayRef = 0;
    }

    public boolean contains(T o) {
        for (T x : arrayRef)
            if (x.equals(o)) return true;
        return false
    }
}
```

The <T> from the class would be also used as the type parameter for the interface.

**NOTE** because the interface is generic, the class also needs to be generic as you can't then pass the type paramter to the interface. Unless you would immediately declare the type parameter.
``` java
class MyClass<T> implements Containment<T>{} // this is correct
class MyClass implements Containment<T>{} // this is wrong
class MyClass implements Containment<Double>{} // this is correct
```

You can also bound the interface

``` java
public interface GenericInterface <T extends Number> {
	boolean contains(T o);
}

// This is wrong because you don't need to extend the Number on the GenericInterface anymore.
// public class GenericInterfaceImp<T extends Number> implements GenericInterface<T extends Number> {
public class GenericInterfaceImp<T extends Number> implements GenericInterface<T> {
	@Override
	public boolean contains(T o) {
		return false;
	}
}
```

**<u>Raw Types</u>**

Because Generics are not implemented prior to JDK 5.
Java allows the Generics to transtion from the old implementation. Thus you can do something like this

``` java
class Gen<T>{
    // ...
}
main {
    Gen<Integer> notRaw = new Gen<Integer>(10); // this would work
    Gen raw = new Gen (10); // This would also work, but the type safety is lost
    notRaw = raw; // This would also work, but the raw type would override the type safety of not raw.
}
```

**<u>Diamond Operator</u>**

``` java
// Without the the diamond operator
HashMap<Integer, String> hashMap = new HashMap<Integer, String>();

// With diamond operator
HashMap<Integer, String> hashMap = new HashMap<>();
```

**<u>Local Variable Type Inferance and Generics</u>**

``` java
TwoGen<Integer, String> tgObj = new TwoGen<Integer, String>(42, "testing");

var tgObj = new TwoGen<Integer, String>(42, "testing");
```

**<u>Type Erasure</u>**

During compilation, generic information are removed(erased). And would be replace by the bound type of the Type Parameter.
Or the **_Object_** if the there is none, and applying the appropriate cast.

**NOTE** Errors from Type Erasure

``` java
interface IGenQ<T extends Number>{}

class GenQueue<T extends Integer> implements IGenQ<T>{}


// This is an error you can't overload the method because of type erasure.
void sad (List<IGenQ<Integer>> sample){
    return;
}

void sad (List<GenQueue<Integer>> sample){
    return;
}

// The reason is that the List is implemented with
// List<E> extends Collection <E>
// Because of type erasure the List<IGenQ<Integer>> would be just List with type paramter as an Object
// So even if you add List<String>, it would still be type erased to an Object

// This won't also work
class MyGenClass<T, V>{
    void set(T o) {}
    void set(V o) {}
}
// because what if you do
// MyGenClass<String, String>
// It won't be able to differentiate these two.

```

**<u>Some Generic Restirctions</u>**

* Type Parameters can't be instantiated
```java
class Gen<T> {
    T obj;
    Gen() {
        obj = new T(); // won't work
    }
} 
```

* Static Members can't use Type Parameter Declared by Class

```java
class Wrong<T> {
    static T ob; // won't work, as the type of T is not yet defined

    static <T> boolean sample(T o) {} // but this would work;
}

public interface IGenQ <T> {
	static <T> void sample(T o) { } // This would also work
}
```

#### Day 6 (July 29, 2019 - Mon)

*__Emergency Goal__*
1. Learn Firebase - Firestore

*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. ~~Study Enumarations, Autoboxing, Static Import, and Annotations~~

*__New Goals__*
1. Generics
2. Finish week two of LHTL
---

Thoughts: firebase/firestore is somehow just the same as Mongo, but firestore is much easier to scale horizontally than Mongo. They also have functions and request that can directly query to the database using firebase's own API without creating your own API. But I'm still unsure if that is a good idea instead of creating an API to manage the users.

### Day 7 (July 30, 2019 - Tue)

*__Emergency Goal__*
1. Learn Firebase - Firestore

*__Goals for the week__*
1. ~~Learn and create a Multithreaded Program~~
2. ~~Study Enumarations, Autoboxing, Static Import, and Annotations~~

*__New Goals__*
1. Generics
2. Finish week two of LHTL

---

**<u>NoSQL vs SQL</u>**

* SQL
    * faster write
    * Mostly scales vertically
* NoSQl
    * faster read
    * Easy to scale horizontally

**<u>Cloud Firestore Structure</u>**
* NoSQL
* Horizontally Scaling
* Document Model Database
* Exists in Cloud

**<u>How query works on Firestore</u>**

> * Queries that we're run on Cloud Firestore could only be used to find Documents within one specific collection or subcollection.
    > * you can also do a subcollection group query using collection group query, to apply this, you need to define indexes on the cloud firestore console.
> * Query results are shallow, meaning the subgroups aren't included by itself.


**<u>Setting up Firebase</u>**
1. npm install -g firebase-tools
2. firebase login
3. firebase init
4. firebase serve --host 0.0.0.0 // accepts requests to any host
5. or firebase deploy -m "Message"

**<u>Using Firebase</u>**
``` javascript
// index.js
const functions = require('firebase-functions');
const firebase = require('firebase');
const app = require('express')();

// config.js
const firebaseConfig = {
    apiKey: "AIzaSyDvQC8b6QS9RBiE5vbMJAaHHhjKYvu9MaU",
    authDomain: "socialape-3ed53.firebaseapp.com",
    databaseURL: "https://socialape-3ed53.firebaseio.com",
    projectId: "socialape-3ed53",
    storageBucket: "socialape-3ed53.appspot.com",
    messagingSenderId: "975840971715",
    appId: "1:975840971715:web:5bffce1b32363bad"
};

// firebase
const { firebaseConfig } = require('../util/config');
const firebase = require('firebase');
firebase.initializeApp(firebaseConfig)

// admin.js
const admin = require('firebase-admin');
admin.initializeApp();
const db = admin.firestore();
```

##



### Week 2
*Objectives*
1. ~~Learn Generics~~

### Day 1(8) (July 31, 2019 - Wed)

*__Emergency Goal__*
1. ~~Learn Firebase - Firestore~~
2. ~~Learn PWA~~

*__Goals for the week__*
1. ~~Generics~~

---

Thoughts: Right now, I'm still having trouble trying to understand what scope the Admin SDK have.
Because I've tried disabling all access to the database via rules but, the API can still fetch data.
But using the simulation with direct access to the with an unauthenticated user, fails.
It I think the one that's causing it is the Admin SDK, but I'm still unsure, as I've already tried
removing the config for the Admin SDK, but to no avail. Hopefully I can find an answer for this.

Problem: It seems like server client libraries uses a different validation as the db rules.
(Search for IAM[Identity and Access Manager])g 

... To be continue (Generic Array Restriction)

**<u></u>**
**<u></u>**

### Day 2(9) (August 1, 2019 - Thu)

*__Emegency Goal__*
1. Learn Firebase - Firestore
2. Learn PWA

*__Goals for the week__*
1. Generic

---


*__What is PWA?__*
PWA stands for **Progressive Web Apps**.
It is a capability by a website to provide an App-like experience for the user.
They also prove an offline capabilities to a website, by caching some datas, via Service Worker.



*__ How To Implement a PWA?__*
A PWA can be declared by adding a manifesto.json.
and importing it as a link.

```json
{
    "name": "Food Ninja",
    "short_name": "FoodNinja",
    "start_url": "/index.html",
    "display": "standalone",
    "background_color": "#FFE9D2",
    "theme_color": "#FFE1C4",
    "orientation": "portrait-primary",
    "icons": [
        {
            "src": "/img/icons/icon-72x72.png",
            "type": "image/png",
            "sizes": "72x72"
        },
        {
            "src": "/img/icons/icon-96x96.png",
            "type": "image/png",
            "sizes": "96x96"
        },
        {
            "src": "/img/icons/icon-128x128.png",
            "type": "image/png",
            "sizes": "128x128"
        },
        {
            "src": "/img/icons/icon-144x144.png",
            "type": "image/png",
            "sizes": "144x144"
        },
        {
            "src": "/img/icons/icon-192x192.png",
            "type": "image/png",
            "sizes": "192x192"
        },
        {
            "src": "/img/icons/icon-384x384.png",
            "type": "image/png",
            "sizes": "384x384"
        },
        {
            "src": "/img/icons/icon-512x512.png",
            "type": "image/png",
            "sizes": "512x512"
        }
    ]
}
```
```html
<link rel="manifest" href="/manifest.json">
```

But currently some fields of the manifest are not supported by iOS.

To provide support to iOS, you need to manualy import some settings of manifest
``` html
<!-- iOS Support -->
<link rel="apple-touch-icon" href="/icons/icon-96x96.png">
<meta name="apple-mobile-web-app-status-bar" content="#aa7700">
```

*__Intro to Service Workers__*
Service workers are the reason how awesome are PWA.

* Basically javascript files, but not the same js as the one we're used to coding.
* Run on a different thread, their own thread. Separate from the main thread of the web app.
* Doesn't have access to the DOM, unline the normal js that is running on the main thread. So they can't DIRECTLY read or write a content on the page.
* Running on background.
* Their purpose is to listen and react to events that occur in the browser
    * Push Notifications
    * Fetch HTTP Request
* They can only access files on their directory and sub-directory, but not outside their directory
    * Thus they are placed on the root directory of the project.
* They only work on Secure protocol, like https, except, localhost.

*__Service Worker Life-Cycle Events__*
Create Service Worker(sw.js) on the index(because they are limited to their directory and sub-directory)
Register the Service Worker(sw.js) on the app.js, when the browser detect the sw.js, it would fire an:
1. (Register the Service Worker) -> Fires Install Event
2. (Service becomes active) -> Fires Active Event -> (Service worker listens for events)

Once active the service worker can then access all the different pages and files inside its scope.

BUTTTT, what if you refresh a page.

If you refresh a page, the previous service worker would still be used and it won't create a new one.

Unless there is a code change on the service worker.

If there is a code change on the service worker, a new service worker would be created.
But even though it was created, it would still wait for the old instance of the service worker to finish.
So if you then reload the page again, that's when the new service worker would be active.


### Day 3(10) (August 2, 2019 - Fri)

*__Emegency Goal__*
1. Learn Firebase - Firestore
2. Learn PWA

*__Goals for the week__*
1. Generic

---

Thoughts: I've realize how amazingly useful service workers are. So yesterday I've learned that service workers work via event listeners which would intercept appropriate events to handle.

I've learned that you can cache important details on the 'install' event of the life cycle of an SW. The Fetch those cache, data via the 'fetch' event of the SW life cycle. The fetch event will automatically trigger as long as there are request to servers, either internal or external css, js, etc.

### Day 4(11)  (August 3, 2019 - Sat)

*__Emegency Goal__*
1. Learn Firebase - Firestore
2. Learn PWA

*__Goals for the week__*
1. Generic

---

*__Maintaining a proper cache version__*

When you cache datas, it's important to provide versioning to them so that when there is a code change, we can remove the previous version of the cache, thus removing unnecessary datas.

*__Static Caching__*

Static caching is caching default resources at the start of the application life cycle.

```javascript
const staticCacheName = 'site-static-v2';
const assets = [
  '/',
  '/index.html',
  '/js/app.js',
  '/js/ui.js',
  '/js/materialize.min.js',
  '/css/styles.css',
  '/css/materialize.min.css',
  '/img/dish.png',
  'https://fonts.googleapis.com/icon?family=Material+Icons',
  'https://fonts.gstatic.com/s/materialicons/v47/flUhRq6tzZclQEJ-Vdg-IuiaDsNcIhQ8tQ.woff2'
];

// install event
self.addEventListener('install', evt => {
  //console.log('service worker installed');
  evt.waitUntil(
    caches.open(staticCacheName).then((cache) => {
      console.log('caching shell assets');
      cache.addAll(assets);
    })
  );
});
```

*__Dynamic Caching__*

Dynamic caching provides a way to cache, resources that are visited by the user.
Usually done, after a fetch event was triggered.

```javascript
const dynamicCacheName = 'site-dynamic-v1';

self.addEventListener('fetch', evt => {
  //console.log('fetch event', evt);
  evt.respondWith(
    caches.match(evt.request).then(cacheRes => {
      return cacheRes || fetch(evt.request).then(fetchRes => {
        return caches.open(dynamicCacheName).then(cache => {
          cache.put(evt.request.url, fetchRes.clone());
          return fetchRes
        });
      });
    })
  );
});
```

### Day 5(12) (August 4, 2019 - Sun)

*__Emegency Goal__*
1. Learn Firebase - Firestore
2. Learn PWA

*__Goals for the week__*
1. Generic

---

Thoughts: When appliying a caching mechanism. It's also important to adda fallback page for incase the pages that are being accessed isn't cached yet. It's also important that you would only send the fallback page when the resource being requested is .html.

Study read all of these when there is time.

https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/


### Day 6(13) (August 5, 2019 - Mon)

*__Emegency Goal__*
1. Learn Firebase - Firestore
2. Learn PWA

*__Goals for the week__*
1. Generic

---

*__Fetch Event__*

Occurs when app request a resource on the server.

If available the service worker would then just get a data from cache, instead of
fetchinga another data from the server.

*__Add to Home Screen(Pop-up)__*

To make google automatically Pop up an Add To Home screen, the following criteria must be met

* The web app is not already installed.
    * and prefer_related_applications is not true.
* Meets a user engagement heuristic (previously, the user had to interact with the domain for at least 30 seconds, this is not a requirement anymore)
* Includes a web app manifest that includes:
    * short_name or name
    * icons must include a 192px and a 512px sized icons
    * start_url
    * display must be one of: fullscreen, standalone, or minimal-ui
* Served over HTTPS (required for service workers)
* Has registered a service worker with a fetch event handler

When these criteria are met, will fire a ```beforeinstallprompt``` event that you can use to prompt the user to install your Progressive Web App, and may show a mini-info bar.

Link: https://developers.google.com/web/fundamentals/app-install-banners/

### Day 7(14) (August 6, 2019 - Tue)

*__Emegency Goal__*
1. ~~Learn Firebase - Firestore~~
2. ~~Learn PWA~~

*__Goals for the week__*
1. ~~Generic~~

---

PWA and Firebase Thoughts: Finally managed to finish the app! I'm still amazed on how seemless the offline experience of the PWA is when using Firestore and PWA.
As when you're offline the firebase would automatically use the offline db of the browser to make it seems like it's still working.

https://socialapes-78d5e.firebaseapp.com/

To enable offline db just use:
```javascript
db.enablePersistence()
    .catch(err => {
        if (err.code === 'failed-precondition ') {
            // Probably multiple tabs open at once
            console.log('Persistance Failed');
        } else if  (err.code === 'unimplemented') {
            // lack of browser support
            console.log('Persistence is not available')
        }
    });
```

### Week 3
*Objectives*
1. Lambda Expressions and Method References
2. Modules

---

### Day 1(15) (August 7, 2019 - Wed)

*__Goals for the week__*
1. Lambda Expressions and Method References
2. Modules

---


*__Lambda Expression__*
* Anonymous Method
    * executed by a method defined by Functional Interface
* Functional Interface
    * interfaces contain only one abstract method.

```java
interface SampleInterface {
    void printNumber(int x);
}
class Test {
    public static void main (String[] args) {
        SampleInterface si = (n) -> System.out.print(n);
    }
}
```

*__Block Lambda Expressions__*
* consists of more than single expression

```java
interface SampleInterface {
    void printNumber(int x);
}
class Test {
    public static void main (String[] args) {
        SampleInterface si = (n) ->  {
            System.out.print(n);
            System.out.print(n*10);
        }
    }
}
```

*__Generic Functional Interfaces__*

* lambda expressions cannot be generic. However, functional interface associated with a lambda expression can be generic.

``` java
interface SampleInterface<T> {
    boolean printNumber(T n, T m);
}
class Test {
    public static void main (String[] args) {
        SampleInterface<Integer> si = (a, b) ->  {
            System.out.print("This is int" + a);
            System.out.print("This is int" + b*10);
        }
        SampleInterface<String> si = (a, b) ->  {
            System.out.print("This is string" + a);
            System.out.print("This is string" + b);
        }
    }
}
```

### Day 2(16) (August 8, 2019 - Thu)

*__Goals for the week__*

1. Lambda Expressions and Method References
2. Modules

---

Thoughts: I learned more regarding Lamda Expressions, particularly about closures and variable capture, where in those variables would be implicitly final when used inside the lamda. But I'm still wrapping around my mind regarding method referencing. Hopefully I can finish it yesterday.

### Day 3(17) (August 9, 2019 - Fri)

*__Goals for the week__*

1. Lambda Expressions and Method References
2. Modules

---

Thoughts: I've learned how to use method referencing, and how useful they can be. Still I'm still not confident on using them. I need to practice more.

Sample code

```java
interface NumberInterface {
    boolean process(int x);
}

class NumberUtil {
    static boolean isEven(int x) {
        return x % 2 == 0;
    }
}

class NumberRunner {
    boolean run(NumberInterface ni, int x) {
        ni.process(x);
    }
}

class TestDrive {
    public static void main (String[] args) {
        NumberRunner numberRunner = new NumberRunner();
        System.out.println(numberRunner.run(NumberUtil::isEven, 2)); // true
    }
}

```

### Day 4(18) (August 10, 2019 - Sat)

*__Goals for the week__*
1. Lambda Expressions and Method References
2. Modules

---

Thoughts: For today, I still studied regarding Method Referencing and I'm kinda getting the hang of it, but I still need some practice. I've learned about a new Method Reference via instance method where in the functional interface needs to accept the class where the function would be referenced as an argument. And also method referencing via Constructor using ClassName::new.

Instance method using ClassName::instanceMethodName

``` java
interface SampleInterface {
    boolean test (SampleClass s, int x);
}
class SampleClass {
    int x;
    public SampleClass(int x) {
        this.x = x;
    }
    boolean isFactor(int n) {
        return x % n == 0;
    }
}
class TestDrive {
    public static void main (String[] args) {
        SampleClass sampleClass = new SampleClass(12);
        SampleClass sampleClass2 = new SampleClass(15);

        SampleInterface sampleInterface = SampleClass::isFactor;

        sampleInterface.test(sampleClass, 4); // true
        sampleInterface.test(sampleClass2, 4); // false
    }
}
```

Sample for Constructor Referencing ClassName::new

```java
interface SampleInterface {
    public construct(String s);
}

class SampleClass {
    private String str;

    public SampleClass(String str) {
        this.str = str;
    }

    String getStr() {
        return str;
    }
}

class TestDrive {
    SampleInterface sampleInterface = SampleClass::new;
    System.out.println(sampleInterface.construct("Method Refed Constructor!").getStr); // Method Refed Constructor!
}


```

### Day 5(19) (August 11, 2019 - Sun)

*__Goals for the week__*
1. ~~Lambda Expressions and Method References~~
2. Modules

---

Thoughts: So today, I've finished the Method Referencing, and I'm slightly more confident on using them, and I've proceed with learning modules.
My understand right now is pretty simple, but it seems like modules are just away to restrict access to some packages, which would be great for huge projects.
But except for that, I don't see any other use for now. Need to continue learning more.

To grant access to modules, you need to create a ```module-info.java```


Sample
```java
module sample { //sample is the name of module
    requires leo.samplepackage; // sample package is package from a different module/
}
```

### Day 6(20) (August 12, 2019 - Mon)

*__Goals for the week__*
1. ~~Lambda Expressions and Method References~~
2. Modules

---

Thoughts: So far I kinda understand how module works, because it's concept kinda reminds of ES6 imports. But when I'm trying it, seems like I can't create a module-info.java when I'm create a new Module on IntelliJ, and I'm left utterly confused on why it's not working. I think that I might need to create two projects and try to do that there implement the modules there? Still unsure, I need to verify it tomorrow.

### Day 7(21) (August 13, 2019 - Tue)

*__Goals for the week__*
1. ~~Lambda Expressions and Method References~~
2. Modules

---

Thoughts: I've finally managed to require and export modules. I've learned more regarding transitive modules and the to keyword when exporting packages. I've also learned regarding Service and Service Provider, which for a pluggable architecture such as translating a language to another Language. I'm acutally quite curious on how they are implemented, but I would focus first on the modules.

### Week 4

*__Goals for the week__*
1. Modules
2. Clean Code

---

### Day 1(22) (August 14, 2019 - Wed)

*__Goals for the week__*
1. Modules

*__NEW GOALS FOR THE WEEK__*
1. Naming And Functions (Clean Code)

---

Thoughts: Today I've got a glimpse on how Service an Service Provider works with the context of Modules. It seems to work just like a factory, but kinda different. Because it seems like the ServiceLoader would fetch all Classes that Implements the interface provided to the type parameter of Service Provider. But I still need to verify it tomorrow.

### Day 2(23) (August 15, 2019 - Thu)

*__Goals for the week__*
1. ~~Modules~~

---

Thoughts: For today, I've learn regarding open packages which would inturn make the packages accessible by default but only on run time, which is use for Reflaction, which I still haven't understand yet. I've also learned regarding requires static, which would only require the package when needed. And with that I've managed to finish My First Book regarding Java. I'm still unsure on how I would proceed after this book. I'll just think about it tomorrow.

### Day 3(24) (August 16, 2019 - Friday)

*__Goals for the week__*
1. ~~Modules~~
2. Naming And Functions (Clean Code)

---

Thoughts: Today, I've started reading regarding Pragmatic Thinking and watched the First Episode of The Clean Code.

Regarding the Pragmatic Thinking, I was given a tip to ```Always Consider The Context```, to always think that small things make up for the larger things, and not a single entity disconnected from other things, thus those small things greatly affects the bigger view of things. This kinda reminds of the The Slight Edge, his thoughts regarding compounding actions, and the stoics view of the world.

Regarding the Clean Code, the first episode really hits me hard. Even though its quite hard to admit, I'm one of the reason why our code base isn't really clean, and specially when I'm rushing and being given deadlines that just increases the pressure that I'm feeling. That's when I really code poorly, and it sucks right now, but Uncle Bob inspires me to write better code. And I'll try me best to do just that. What ever happens, I'll always care for my code.

### Day 4(25) (August 17, 2019 - Saturday)

*__Goals for the week__*
1. ~~Modules~~
2. Naming And Functions (Clean Code)

---

Thoughts: For today, I've watched the episode 2 of the Clean Code.

I've learned that a variable should carry its intent. If it needed a comment, it's probably not a good variable name.

I've also learned that a programmer should avoid disinformation. As that can be the worst sin a programmer can make.

I should also use prounanceable name.

And a clean code should always read like a well written prose. Choose parts of speech well.

Variables and Classes should be nouns. Function be verbs, unless it returns a boolean, which would then inturn be a predicate. Boolean Variables should also be predicate. And enums are often Adjectives.

And lastly, I've learned regarding The Scope Rule.

Variables should have short name on short scope, and long name on long scope.

Functions and Classes should have long name on short scop, and short name on big scope. As they would be use on a large part of application as they are probably declared as public.

### Day 5(26) (August 18, 2019 - Sunday)

*__Goals for the week__*
1. ~~Modules~~
2. Naming And Functions (Clean Code)

---

Thoughts: Today, I've watched the Episode 3 of the clean code, and learned that 10 lines of code in a function is already too big. I've also learned some shortcuts on refactoring using IntelliJ, and I'm trying to understand Uncle Bob's thought process when refactoring a code, hopefully I would be able to understand it in a week.

### Day 6(27) (August 19, 2019 - Monday)

*__Goals for the week__*
1. ~~Modules~~
2. ~~Naming And Functions (Clean Code)~~

---

Thoughts: Today I've managed to finish the Episode 3 of clean code. I'm still amazed how awesome Uncle Bob have managed to refactor that very long code. And he even manage to remove the switch case, which I'm still unaware how he had done that. That's why I would watch the fullscreen cast for that example after finishing the Function Structure, because they are kinda related.

As for today I've learned if a function is very large, more likely than not, that is a class that is hidden on a large function. That's why you need to refactor it. Before refactoring, make sure to create test cases so you would be sure that you didn't break anything. I've also learned that for a function to do only one thing, you should extract and extract the function, until the implementation would not just be a restatement of it's name.

### Day 7(28) (August 20, 2019 - Tuesday)

*__Goals for the week__*
1. ~~Modules~~
2. ~~Naming And Functions (Clean Code)~~
3. Function Structure

---

Thoughts: Today I've learned some stuffs, but I'm still wondering about them. I guess it's because I'm coming from the point of view of not actually implementing TDD. I guess I should make it a habit to implement TDD. I guess it also kinda hurts to know that defensive programming is actualy a code smell.
So with regard to that null checks should be avoided as much as possible because that would be covered by test, unless they are from public apis, where you're unsure what the user would put.

I've also learned regarding stepdown rule, where in the most important function(usually a public) is put at the top of the class, sorted by their importants, or how much details they provide.

Another one is regarding arguments, where in 3 arguments is max but 2/1/0 is ideal. I've also learned not to pass boolean as a parameter. As that would contain two state for that method, where in you should've just created 2 methods instead of passing a boolean.

And there shouldn't be any output arguments. I'm actually kinda confused what output arguments is. I need to clarify it with someone knowledge, but from my understanding it is an argument in a function where in it is also the one being returned.

E.i

```java

outputArguments(String sample) {
    return sample;
}
```

## Month 1 (August 21, 2019 - September ??, 2019)

So somehow, I've managed to finish a month of this. and I've also manage to finish my main goal the Beginner Java book, and also managed to finish some extra goals. Like the Firebase - Firestore, PWA, and also a few episode on Clean Code. Hopefully we can continue this one and finish this 100 days of code.

*__Goals__*

1. Clean Code

### Month 2 Week 1

*__Goals for the week__*
1. Function Structure
2. Form
3. Test Driven Development
4. Architecture Use Cases and High Level Designs

### Day 1(29) (August 22, 2019 - Wednesday)

Thoughts: For today I've read the book from Clean Code, and I'm quite conflicted on whether I would continue with the book or the video, as the book seems to have some problems that I can try to solve. Or maybe I can just do them concurrently, hopefully that would be better.

I've manage to finish the screen cast of Uncle Bob regarding the stepdown rule. And he explains that he is having a dilemma, as he really wants to indent those child functions so that there are alot more information being given. But it's not a convention and that's why he's having a dilemma. But for me it seems like the idea was really good. Hopefully there would be a functionality like that, even just for the IDE.


### Day 2 (30) (August 24, 2019, Saturday)

Thoughts: I've learned about two Programming Paradigms, the Functional and the Structured. The Functional paradigm  writes program w/o statements and values are passed as an arguments. Thus, eliminatin side effects??? But side effects must not be eliminated, they should just be managed properly with discipline. With the use of Command Query Separation. In Command Query Separation, functions that modifies a value should not return a state. Functions that returns state should not mutate/modify a state. Thus preventing side effects, such as, maybe calling getAmount() but that getAmount was implemented in a way that modifies a state.

With that I've learned about Tell Don't Ask, you will just tell a function what to do, but don't ask for it's state, because we aren't the one who would manage it's state, the object can sufficiently manage its own state.

I've also learn about Law of Demeter. The Law of Demeter states that, you should only call methods of objects that are, global, passed as an arguments, locally declared and instance variables. BUT NOT METHODS OF OBJECTS THAT ARE RETURNED FROM A PREVIOUS METHOD CALL (```o.getX().getY().getZ().doSomething();```).

I've managed to finish the video, BUT I think I might need to repeat the episode because there are somethings that I still don't understand. Specially the lesson after the Structured Programming.

### Day 3 (31) (August 25, 2019, Sunday)

Thoughts: I've rewatched the video of uncle bob creating a code from scratch. I've got a glimpse on how to properly do a TDD. And also learned that you should do errors first before proceeding with the code. I've also seen Uncle Bob implement the null object pattern, where in instead of throwing an error when requesting for a null, you would return an object with it's own null implementation. But I still don't understand it's use. Uncle Bob says that the purpose is that when you push to a stack it would return an overflow, if you pop it would return an underflow. But I don't know its uses. But I think the reason he made that so he can separate the null if scenarios on a different object instead of clugging the push and pop of the main object. But I would still rewatch this for 3rd time, I still have something that I still quite don't understand. Hopefully I can finish it.