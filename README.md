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

## Month 1 (July 24, 2019 - Aug. 22, 2019)

*__Goals__*
1. Finish the Beginners Java book

*__Emergency Goals__*
1. Learn Firebase
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
1. Learn Generics

### Day 1(8) (July 31, 2019 - Wed)

*__Emergency Goal__*
1. Learn Firebase - Firestore

*__Goals for the week__*
1. Generics

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

### Day 5(12)  (August 4, 2019 - Sun)

*__Emegency Goal__*
1. Learn Firebase - Firestore
2. Learn PWA

*__Goals for the week__*
1. Generic

---

Thoughts: When appliying a caching mechanism. It's also important to adda fallback page for incase the pages that are being accessed isn't cached yet. It's also important that you would only send the fallback page when the resource being requested is .html.

Study read all of these when there is time.

https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/












### Week 3
*Objectives*
1. Lambda Expressions and Method References
2. Modules










### Week 4
1. Swings? Still not sure













