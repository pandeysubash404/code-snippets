# Java Sad Case Snippets

This document contains a set of sad case programs designed to highlight logical issues or errors that do not trigger explicit exceptions but lead to incorrect or unintended outcomes.

---

## 1. Incorrect Calculation (Logical Error)
The average is calculated incorrectly by dividing by a hard-coded number instead of the correct number of elements.

```java
public class IncorrectAverage {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30};
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        // Wrong: Dividing by a hard-coded number instead of numbers.length
        double average = total / 4.0;  // Should divide by numbers.length (3)
        if (average != 20) {
            System.out.println("Sad case: Incorrect average calculation!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 2. Off-By-One Error
The loop should iterate 5 times, but due to an off-by-one error, it iterates 4 times.

```java
public class OffByOne {
    public static void main(String[] args) {
        int count = 0;
        for (int i = 1; i < 5; i++) {  // Should be i <= 5
            count++;
        }
        if (count != 5) {
            System.out.println("Sad case: Off-by-one error!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 3. Wrong Comparison Operator
Using `>=` instead of `>` allows 10 to pass when it shouldn't.

```java
public class WrongComparison {
    public static void main(String[] args) {
        int num = 10;
        if (num >= 10) {  // Should be num > 10
            System.out.println("Sad case: Wrong comparison operator!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 4. Incorrect Use of Mutable Default Arguments
A mutable default argument (like a `List`) retains its value between function calls, leading to unintended side effects.

```java
import java.util.ArrayList;
import java.util.List;

public class MutableDefaultArgument {
    public static List<Integer> addItem(int item, List<Integer> lst) {
        lst.add(item);
        return lst;
    }

    public static void main(String[] args) {
        List<Integer> list1 = addItem(1, new ArrayList<>());
        List<Integer> list2 = addItem(2, new ArrayList<>());
        if (!list1.equals(List.of(1)) || !list2.equals(List.of(2))) {
            System.out.println("Sad case: Mutable default argument!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 5. Shadowing Built-In Functions
The variable `sum` shadows the built-in `sum()` function, causing errors when trying to use the built-in function.

```java
public class ShadowingBuiltIn {
    public static void main(String[] args) {
        int sum = 10;  // Shadows the built-in method `sum()`
        try {
            int result = sum(new int[]{1, 2, 3});  // This will fail due to shadowing
            System.out.println("Sad case failed!");
        } catch (Exception e) {
            System.out.println("Sad case: Shadowing built-in function!");
        }
    }
}
```

## 6. Floating-Point Precision Error
Floating-point comparisons may fail due to precision issues.

```java
public class FloatingPointError {
    public static void main(String[] args) {
        double result = 0.1 + 0.2;
        if (result != 0.3) {  // This may fail due to precision issues
            System.out.println("Sad case: Floating-point precision error! (Got " + result + ")");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 7. Incorrect Variable Scope
A variable defined inside an `if` block is not accessible outside, leading to a compile-time error.

```java
public class VariableScope {
    public static void main(String[] args) {
        try {
            int x = 10;  // Defined inside the try block
            if (true) {
                x = 20;
            }
            int y = x + 1;  // x is accessible here, no error in Java
            System.out.println("Sad case passed!");
        } catch (Exception e) {
            System.out.println("Sad case: Incorrect variable scope!");
        }
    }
}
```

## 8. Infinite Loop (Logical Error)
An infinite loop occurs because the counter is incremented instead of decremented.

```java
public class InfiniteLoop {
    public static void main(String[] args) {
        int counter = 10;
        while (counter > 0) {
            System.out.println("Sad case: Infinite loop " + counter + "!");
            counter++;  // Should decrement instead of incrementing
        }
    }
}
```

## 9. Logic Error in Conditional Statements
Using `and` instead of `or` in the conditional causes an incorrect logic flow.

```java
public class LogicError {
    public static void main(String[] args) {
        int num = 5;
        if (num < 10 && num > 20) {  // Should use `||` (or) instead of `&&` (and)
            System.out.println("Sad case: Logic error in conditional!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 10. Incorrect List Mutation During Iteration
Modifying a list during iteration causes elements to be skipped.

```java
import java.util.ArrayList;
import java.util.List;

public class ListMutationDuringIteration {
    public static void main(String[] args) {
        List<Integer> lst = new ArrayList<>();
        for (int i = 1; i <= 5; i++) {
            lst.add(i);
        }
        
        for (Integer i : lst) {
            if (i % 2 == 0) {
                lst.remove(i);  // Removing while iterating
            }
        }
        
        if (lst.equals(List.of(1, 3, 5))) {
            System.out.println("Sad case: List mutation during iteration!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 11. Incorrect Data Type Assumption
Assuming all list elements are integers leads to a runtime error when encountering a non-integer value.

```java
import java.util.List;

public class IncorrectDataType {
    public static void main(String[] args) {
        List<Object> lst = List.of(1, 2, "3", 4);  // Mixed data types
        int total = 0;
        for (Object item : lst) {
            total += (int) item;  // Will fail if the item is not an integer
        }
        if (total != 10) {
            System.out.println("Sad case: Incorrect data type assumption!");
        } else {
            System.out.println("Sad case passed!");
        }
    }
}
```

## 12. Using == Instead of .equals() for Object Comparison
Using `==` instead of `.equals()` compares object references instead of their values, leading to a failed comparison.

```java
import java.util.List;

public class IsVsEquals {
    public static void main(String[] args) {
        List<Integer> a = List.of(1, 2, 3);
        List<Integer> b = List.of(1, 2, 3);
        if (a == b) {  // Should use `.equals()` instead of `==`
            System.out.println("Sad case failed!");
        } else {
            System.out.println("Sad case: Incorrect use of `==` instead of `.equals()`");
        }
    }
}
```

## Conclusion
These Java snippets highlight various sad cases, where the code runs without errors but produces incorrect or unintended results due to logical issues, wrong assumptions, or subtle programming mistakes.