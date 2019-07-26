# 100-Days-Of-Code ATTEMPT 1(FAILED)

## Day 1
For this day I'm going back from the basics of Java, and I've learned these new things.

### normal (&) vs Short circuit (&&);

### Postfix vs Prefix - 
    given x = 1
    Postfix = x++(return x; //returns 5 then increment 1 after returning)
    Prefix = ++x(return x; //increment x by 1 then returns 6)

### Using empty body for loop
    int[] arr = {1, 2, 3, 4, 5};
    int sum = 0;

    // just remove the console log make
    for (int i = -1; i < arr.length-1; sum += arr[++i])

    Output:
    15


### Static bodies:

    public class StaticBlock {
        static { // this is a static block
            // this can be used to provide a another way to initialise static variables
        }
    }

### varargs
    used to unknown number of parameters

    static varArgsTest(int ... v) {
        for (int i = 0; i < v.length; i++)
            System.out.println(" args " + i + ": " + v[i]);
    }

**NOTE** that varargs is operated as an array

## Day 2

### Superclass = Subclass
    I've learned that subclass and super class works somehow the same as interface
    Where in you can declare
    SuperClass sc = new SuperClass();
    SubClass sb = new SubClass();
    sc = sb;
    but the super class can't access variables/methods that are specific only to the subclass.

### Access Modifier
                    | highest precedence <---------> lowest precedence
    *———————————————+———————————————+———————————+———————————————+———————
    \ xCanBeSeenBy  | this          | any class | this subclass | any
    \__________     | class         | in same   | in another    | class
                \   | nonsubbed     | package   | package       |    
    Modifier of x \ |               |           |               |       
    ————————————————*———————————————+———————————+———————————————+———————
    public          |       ✔       |     ✔     |       ✔       |   ✔   
    ————————————————+———————————————+———————————+———————————————+———————
    protected       |       ✔       |     ✔     |       ✔       |   ✘   
    ————————————————+———————————————+———————————+———————————————+———————
    package-private |               |           |               |
    (no modifier)   |       ✔       |     ✔     |       ✘       |   ✘   
    ————————————————+———————————————+———————————+———————————————+———————
    private         |       ✔       |     ✘     |       ✘       |   ✘   

## Day 3

### Java 8 interface default methods
    With Java 8's default interface method, adding a new method in the interface wouldn't
    break all classes that implements that method, provided there is a default implementation
    on the interface.

    Methods that aren'nt provided in the interface can be used inside a default method
    E.x

    public interface Test {
        int getNext();

        default int[] getNextArray(int n){
            int[] vals = new int[n];

            /* NOTE that getNext was used
               getNext() implementation would be
               provided by the class that implements
               Test
            */
            for(int i = 0; i < n; i++) vals[i] = getNext();
            return vals;
        }
    }

    Summary
    ● It gives you a way to gracefully evolve interfaces over time without breaking existing code.
    ● It provides optional functionality without requiring that a class provide a placeholder implementation when that functionality is not needed.

### Interface - Multiple Inheritance Issues
    Given that there are 2 interfaces Alpha, and Beta
    both provide a default method reset(),
    Or when Alpha implements Beta, what would happen?
    Or if the class implementing the interface
    provides its own implementation of method.

    Java defines a set of rules that resolve such conflicts.

### Multiple Intehritance - RULES
    1. Class overrides the default method of interfaces,
    even if implementing both Alpha and Beta
    2. Class doesn't didn't provide method implementation for Alpha and Beta,
    an error will occur.
    3. If Beta extends Alpha, then Beta's version of reset will be used. Vice versa.
    REGARDLESS even if Beta's method is still abstract, the method would then be still abstract.
    The implementing class of Beta then needs
    to provide the implementation, disregarding Alpha's default method.

    It is possible to refer explicitly to a default implementation by using a new form of super. Its general form is shown here:
    InterfaceName.super.methodName( )

    For example, if Beta wants to refer to Alpha’s default for reset( ), it can use this statement:
    Alpha.super.reset();

### Using static method on an interface
    Static methods defined by an interface can be called independenly
    of any objects. Thus no implementation of the interface is requred.

    InterfaceName.staticMethodName

    Notice that this is similar to the way that a static method in a class is called.

    ONE LAST POINT: static interface methods are not inherited by either an implementing class or a subinterface.

### Private Interface Method
    Since Java 9, a private method can be used on an interface.
    The key benefit of a private interface method is that it lets
    two or more default methods use a common piece of code.

### Java Method Hiding and Overriding: Override Static Method in Java
    class A {
        void hi() {
            sout("Class parent");
        }

        static void canNotBeOverridden() {
            sout("Can only be hidden")
        }
    }

    // The hi from class A doesn't exist
    class B extends A {
        @Override
        void hi() {
            sout("Class child override");
        }

        // Error
        // @Override
        // void canNotBeOverridden() {
        //     sout("Trying to override");
        // }
    }

    // The hi from class A still exist
    // but merely being hidden
    class C extends A {
        void hi() {
            sout("Class child hide");
        }
        
        static void canNotBeOverridden() {
            sout("Class A method is Hidden");
        }
    }

### Java String Pool
    Thanks to the immutability of Strings in Java,
    the JVM can optimize the amount of memory allocated
    for them by storing only one copy of each literal String in the pool.
    This process is called interning.

    String first = "Baeldung"; 
    String second = "Baeldung";
    System.out.println(first == second); // true

    This is true because first and seconde are referencing from the
    same location in the String Pool

    String third = new String("Baeldung");
    String fourth = new String("Baeldung"); 
    System.out.println(third == fourth); // False

    False because using the new keyword will create not put it into
    the String Pool

    Similarly, when we compare a String literal with a String object created using new() operator using the == operator, it will return false:

    String fifth = "Baeldung";
    String sixth = new String("Baeldung");
    System.out.println(fifth == sixth); // False

    Still false, because sixth is not on the String Pool

    BUTTTT
    System.out.println(third.equals(fourth)); // true
    and
    System.out.println(fifth.equals(sixth)); // true

    because equals compare the object and if the object is string
    it would check it character per character;

## Day 4

### Throwable
    All exception classes are derived from a class called
    "Throwable". And there are two direct subclass of Throwable:
    "Exception" and "Error". Exceptions of type "Error" are related
    to errors that occur on JVM itself and not in program. These types
    of exceptions are beyond our control, and your program will not deal
    with 


### Exception Handling
    Benefits of exception handling is that the program will
    still run if the exception has been handled and also
    show an approriate error message, instead of letting
    JVM handle the error, which would stop the program,
    and show the stack trace of the error.