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

**note** that var