# Java Happy Case Snippets

This document contains a set of basic operation cases to validate that Java correctly handles various basic operations, similar to Python.

---

## 1. Basic Arithmetic
Arithmetic operations like addition, subtraction, multiplication, division, and modulus.

```java
public class Arithmetic {
    public static void main(String[] args) {
        System.out.println("2 + 2 = " + (2 + 2));
        System.out.println("10 - 5 = " + (10 - 5));
        System.out.println("10 * 3 = " + (10 * 3));
        System.out.println("100 / 5 = " + (100 / 5));
        System.out.println("2 ** 3 = " + Math.pow(2, 3));
        System.out.println("9 // 2 = " + (9 / 2));  // Integer division
        System.out.println("9 % 2 = " + (9 % 2));
        
        System.out.println("Arithmetic operation completed!");
    }
}
```

## 2. String Manupulation
String operations like concatenation, length, case conversion, and slicing.

```java
public class StringManipulation {
    public static void main(String[] args) {
        System.out.println("\"Hello\" + \" \" + \"World\" = " + "Hello" + " " + "World");
        System.out.println("\"abc\" repeated 3 times = " + "abc".repeat(3));
        System.out.println("Length of \"hello\" = " + "hello".length());
        System.out.println("\"Python\".toUpperCase() = " + "Python".toUpperCase());
        System.out.println("\"PYTHON\".toLowerCase() = " + "PYTHON".toLowerCase());
        System.out.println("Reverse of \"racecar\" = " + new StringBuilder("racecar").reverse().toString());

        System.out.println("String manipulation operation completed!");
    }
}
```

## 3. List Operations (Using ArrayList)
List operations like concatenation, appending, indexing, and popping elements (similar to Python's list).

```java
import java.util.ArrayList;

public class ListOperations {
    public static void main(String[] args) {
        ArrayList<Integer> lst = new ArrayList<>();
        lst.add(1);
        lst.add(2);
        lst.add(3);
        
        ArrayList<Integer> concatList = new ArrayList<>(lst);
        concatList.add(4);
        concatList.add(5);
        System.out.println("List concatenation: " + concatList);

        System.out.println("Length of list: " + lst.size());

        lst.add(4);
        System.out.println("After appending: " + lst);

        System.out.println("First element: " + lst.get(0));
        System.out.println("Last element: " + lst.get(lst.size() - 1));

        lst.remove(lst.size() - 1);  // Popping last element
        System.out.println("After popping: " + lst);

        System.out.println("List operations completed!");
    }
}
```

## 4. Dictionary Operations (Using HashMap)
HashMap operations such as accessing, modifying, and checking elements.

```java
import java.util.HashMap;

public class DictionaryOperations {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("key1", "value1");
        map.put("key2", "value2");
        
        System.out.println("Value for \"key1\": " + map.get("key1"));
        System.out.println("Length of dictionary: " + map.size());

        map.put("key3", "value3");
        System.out.println("Is 'key3' in dictionary? " + map.containsKey("key3"));

        System.out.println("Value for \"key2\": " + map.get("key2"));

        System.out.println("Dictionary operations completed!");
    }
}
```

## 5. Boolean Logic
Boolean logic operations such as AND, OR, NOT, and comparisons.

```java
public class BooleanLogic {
    public static void main(String[] args) {
        System.out.println("True && True = " + (true && true));
        System.out.println("True || False = " + (true || false));
        System.out.println("!False = " + (!false));
        System.out.println("5 > 3 = " + (5 > 3));
        System.out.println("3 < 1 = " + (3 < 1));
        System.out.println("5 == 5 && 2 == 2 = " + (5 == 5 && 2 == 2));

        System.out.println("Boolean logic operation completed!");
    }
}
```

## 6. Tuple Operation (Using Arrays)
Since Java doesn't have a built-in tuple type, we use arrays to mimic this behavior.

```java
public class TupleOperations {
    public static void main(String[] args) {
        int[] tuple = {1, 2, 3};
        
        int[] concatenatedTuple = {tuple[0], tuple[1], tuple[2], 4, 5};
        System.out.println("Tuple concatenation: " + java.util.Arrays.toString(concatenatedTuple));
        
        System.out.println("First element: " + tuple[0]);

        int[] repeatedTuple = new int[tuple.length * 2];
        System.arraycopy(tuple, 0, repeatedTuple, 0, tuple.length);
        System.arraycopy(tuple, 0, repeatedTuple, tuple.length, tuple.length);
        System.out.println("Repetition of tuple: " + java.util.Arrays.toString(repeatedTuple));

        System.out.println("Tuple operations completed!");
    }
}
```

## 7. Set Operations (Using HashSet)
Set operations like union, intersection, and difference using HashSet.

```java
import java.util.HashSet;

public class SetOperations {
    public static void main(String[] args) {
        HashSet<Integer> s1 = new HashSet<>();
        HashSet<Integer> s2 = new HashSet<>();
        
        s1.add(1);
        s1.add(2);
        s1.add(3);

        s2.add(3);
        s2.add(4);
        s2.add(5);

        HashSet<Integer> union = new HashSet<>(s1);
        union.addAll(s2);
        System.out.println("Union of sets: " + union);

        HashSet<Integer> intersection = new HashSet<>(s1);
        intersection.retainAll(s2);
        System.out.println("Intersection of sets: " + intersection);

        HashSet<Integer> difference = new HashSet<>(s1);
        difference.removeAll(s2);
        System.out.println("Difference of sets: " + difference);

        System.out.println("Set operations completed!");
    }
}
```

## 8. Control Flow
Demonstrates control flow constructs such as if-else statements, for loops, and while loops.

```java
public class ControlFlow {
    public static void main(String[] args) {
        int x = 10;
        if (x > 5) {
            System.out.println("x is greater than 5");
        } else {
            System.out.println("x is less than or equal to 5");
        }

        int sum = 0;
        for (int i = 0; i < 5; i++) {
            sum += i;
        }
        System.out.println("Sum of first 5 numbers: " + sum);

        System.out.println("For loop result:");
        for (int i = 0; i < 3; i++) {
            System.out.println(i);
        }

        while (x > 0) {
            x--;
        }
        System.out.println("x after while loop: " + x);

        System.out.println("Control flow operation completed!");
    }
}
```

## 9. Function
Function definition and invocation to verify whether a simple function returns the correct results.

```java
public class Functions {
    public static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        System.out.println("add(2, 3) = " + add(2, 3));
        System.out.println("add(10, -5) = " + add(10, -5));
        System.out.println("add(0, 0) = " + add(0, 0));

        System.out.println("Function operation completed!");
    }
}
```

## 10. List Comprehension (Using Loops)
Java doesn't have list comprehensions like Python, but we can achieve similar functionality using loops.

```java
import java.util.ArrayList;

public class ListComprehension {
    public static void main(String[] args) {
        ArrayList<Integer> squares = new ArrayList<>();
        for (int i = 0; i < 5; i++) {
            squares.add(i * i);
        }
        System.out.println("Squares: " + squares);

        ArrayList<Integer> evenNumbers = new ArrayList<>();
        for (int i = 0; i < 10; i++) {
            if (i % 2 == 0) {
                evenNumbers.add(i);
            }
        }
        System.out.println("Even numbers: " + evenNumbers);

        System.out.println("List comprehension operation completed!");
    }
}
```

## Conclusion
These Java snippets cover a wide variety of basic operations, ensuring that Java handles common cases correctly.