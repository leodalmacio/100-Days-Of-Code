# 100-Days-Of-Code

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