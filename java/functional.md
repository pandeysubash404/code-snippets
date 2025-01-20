# Functional Case Snippets

This document contains a set of basic operation cases to validate that Java correctly handles various basic operations.

---

## 1. Basic Arithmetic
Arithmetic operations like addition, subtraction, multiplication, division, and modulus.

```java
class Arithmetic {
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
Expected Output:
```text
2 + 2 = 4
10 - 5 = 5
10 * 3 = 30
100 / 5 = 20
2 ** 3 = 8.0
9 // 2 = 4
9 % 2 = 1
Arithmetic operation completed!
```

## 2. String Manupulation
String operations like concatenation, length, case conversion, and slicing.

```java
class StringManipulation {
    public static void main(String[] args) {
        System.out.println("\"Hello\" + \" \" + \"World\" = " + "Hello" + " " + "World");
        System.out.println("\"abc\" repeated 3 times = " + "abc".repeat(3));
        System.out.println("Length of \"hello\" = " + "hello".length());
        System.out.println("\"Java\".toUpperCase() = " + "Java".toUpperCase());
        System.out.println("\"JAVA\".toLowerCase() = " + "JAVA".toLowerCase());
        System.out.println("Reverse of \"racecar\" = " + new StringBuilder("racecar").reverse().toString());

        System.out.println("String manipulation operation completed!");
    }
}
```
Expected Output:
```text
"Hello" + " " + "World" = Hello World
"abc" repeated 3 times = abcabcabc
Length of "hello" = 5
"Java".toUpperCase() = JAVA
"JAVA".toLowerCase() = java
Reverse of "racecar" = racecar
String manipulation operation completed!
```

## 3. ArrayList Operations
List operations like concatenation, appending, indexing, and popping elements (similar to Python's list).

```java
import java.util.ArrayList;

class ListOperations {
    public static void main(String[] args) {
        ArrayList<Integer> lst = new ArrayList<>();
        lst.add(1);
        lst.add(2);
        lst.add(3);
        // lst = [1, 2, 3] 
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
Expected Output:
```text
List concatenation: [1, 2, 3, 4, 5]
Length of list: 3
After appending: [1, 2, 3, 4]
First element: 1
Last element: 4
After popping: [1, 2, 3]
List operations completed!
```

## 4. HashMap Operations
HashMap operations such as accessing, modifying, and checking elements.

```java
import java.util.HashMap;

class HashMapOperations {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("key1", "value1");
        map.put("key2", "value2");
        
        System.out.println("Value for \"key1\": " + map.get("key1"));
        System.out.println("Length of hashmap: " + map.size());

        map.put("key3", "value3");
        System.out.println("Is 'key3' in hashmap? " + map.containsKey("key3"));

        System.out.println("Value for \"key2\": " + map.get("key2"));

        System.out.println("HashMap operations completed!");
    }
}
```
Expected Output:
```text
Value for "key1": value1
Length of hashmap: 2
Is 'key3' in hashmap? true
Value for "key2": value2
HashMap operations completed!
```

## 5. Boolean Logic
Boolean logic operations such as AND, OR, NOT, and comparisons.

```java
class BooleanLogic {
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
Expected Output:
```text
True && True = true
True || False = true
!False = true
5 > 3 = true
3 < 1 = false
5 == 5 && 2 == 2 = true
Boolean logic operation completed!
```

## 6. Array Operation
Array operations such as accessing, modifying, and checking elements.

```java
class ArrayOperations {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        
        int[] concatenatedArray = {arr[0], arr[1], arr[2], 4, 5};
        System.out.println("Array concatenation: " + java.util.Arrays.toString(concatenatedArray));
        
        System.out.println("First element: " + arr[0]);

        int[] repeatedArray = new int[arr.length * 2];
        System.arraycopy(arr, 0, repeatedArray, 0, arr.length);
        System.arraycopy(arr, 0, repeatedArray, arr.length, arr.length);
        System.out.println("Repetition of array: " + java.util.Arrays.toString(repeatedArray));

        System.out.println("Array operations completed!");
    }
}
```
Expected Output:
```text
Array concatenation: [1, 2, 3, 4, 5]
First element: 1
Repetition of array: [1, 2, 3, 1, 2, 3]
Array operations completed!
```

## 7. Set Operations (Using HashSet)
Set operations like union, intersection, and difference using HashSet.

```java
import java.util.HashSet;

class SetOperations {
    public static void main(String[] args) {
        HashSet<Integer> s1 = new HashSet<>();
        HashSet<Integer> s2 = new HashSet<>();
        
        s1.add(1);
        s1.add(2);
        s1.add(3);
        // s1 = {1, 2, 3}    

        s2.add(3);
        s2.add(4);
        s2.add(5);
        // s2 = {3, 4, 5}

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
Expected Output:
```text
Union of sets: [1, 2, 3, 4, 5]
Intersection of sets: [3]
Difference of sets: [1, 2]
Set operations completed!
```

## 8. Control Flow
Demonstrates control flow constructs such as if-else statements, for loops, and while loops.

```java
class ControlFlow {
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
Expected Output:
```text
x is greater than 5
Sum of first 5 numbers: 10
For loop result:
0
1
2
x after while loop: 0
Control flow operation completed!
```

## 9. Function
Function definition and invocation to verify whether a simple function returns the correct results.

```java
class Functions {
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
Expected Output:
```text
add(2, 3) = 5
add(10, -5) = 5
add(0, 0) = 0
Function operation completed!
```

## 10. Loops
Using Loops for List comprehension.

```java
import java.util.ArrayList;

class LoopComprehension {
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
Expected Output:
```text
Squares: [0, 1, 4, 9, 16]
Even numbers: [0, 2, 4, 6, 8]
List comprehension operation completed!
```

## Conclusion
These Java snippets cover a wide variety of basic operations, ensuring that Java handles common cases correctly.