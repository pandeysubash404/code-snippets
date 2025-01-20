# Logical Error Case Snippets

This document contains a set of `logical error case programs` designed to highlight logical issues or errors that do not trigger explicit exceptions but lead to incorrect or unintended outcomes.

---

## 1. Incorrect Calculation
The average is calculated incorrectly by dividing by a hard-coded number instead of the correct number of elements.

```java
class IncorrectAverage {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30};
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        // Wrong: Dividing by a hard-coded number instead of numbers.length
        double average = total / 4.0;  // Should divide by numbers.length (3)
        if (average != 20) {
            System.out.println("Logical error case: Incorrect average calculation!");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case: Incorrect average calculation!
```

## 2. Off-By-One Error
The loop should iterate 5 times, but due to an off-by-one error, it iterates 4 times.

```java
class OffByOne {
    public static void main(String[] args) {
        int count = 0;
        for (int i = 1; i < 5; i++) {  // Should be i <= 5
            count++;
        }
        if (count != 5) {
            System.out.println("Logical error case: Off-by-one error!");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case: Off-by-one error!
```

## 3. Wrong Comparison Operator
Using `>=` instead of `>` allows 10 to pass when it shouldn't.

```java
class WrongComparison {
    public static void main(String[] args) {
        int num = 10;
        if (num >= 10) {  // Should be num > 10
            System.out.println("Logical error case: Wrong comparison operator!");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case: Wrong comparison operator!
```

## 4. Incorrect Use of Mutable Default Arguments
A mutable default argument (like a `List`) retains its value between function calls, leading to unintended side effects.

```java
import java.util.ArrayList;
import java.util.List;

class MutableDefaultArgument {
    public static List<Integer> addItem(int item, List<Integer> lst) {
        lst.add(item);
        return lst;
    }

    public static void main(String[] args) {
        List<Integer> list1 = addItem(1, new ArrayList<>());
        List<Integer> list2 = addItem(2, new ArrayList<>());
        if (!list1.equals(List.of(1)) || !list2.equals(List.of(2))) {
            System.out.println("Logical error case: Mutable default argument!");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case passed!
```

## 5. Floating-Point Precision Error
Floating-point comparisons may fail due to precision issues.

```java
class FloatingPointError {
    public static void main(String[] args) {
        double result = 0.1 + 0.2;
        if (result != 0.3) {  // This may fail due to precision issues
            System.out.println("Logical error case: Floating-point precision error! (Got " + result + ")");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case: Floating-point precision error! (Got 0.30000000000000004)
```

## 6. Incorrect Variable Scope
A variable defined inside an `if` block is not accessible outside, leading to a compile-time error.

```java
class VariableScopeExample {
    public static void main(String[] args) {
        try {
            for (int i = 0; i < 3; i++) {
                int temp = i * 10;  // `temp` is declared inside the loop
                System.out.println("Inside loop: temp = " + temp);
            }
            // Trying to access `temp` outside the loop
            System.out.println("Outside loop: temp = " + temp);  // This will cause an error
        } catch (Exception e) {
            System.out.println("Error: Variable 'temp' is out of scope!");
        }
    }
}
```
Expected Output:
```text
error: cannot find symbol
            System.out.println("Outside loop: temp = " + temp);  // This will cause an error
                                                         ^
```

## 8. Infinite Loop (Logical Error)
An infinite loop occurs because the counter is incremented instead of decremented.

```java
class InfiniteLoop {
    public static void main(String[] args) {
        int counter = 10;
        while (counter > 0) {
            System.out.println("Logical error case: Infinite loop " + counter + "!");
            counter++;  // Should decrement instead of incrementing
        }
    }
}
```
Expected Output:
```text
Logical error case: Infinite loop 1!
Logical error case: Infinite loop 2!
Logical error case: Infinite loop 3!
Logical error case: Infinite loop 4!

```

## 9. Conditional Statements
Using `and` instead of `or` in the conditional causes an incorrect logic flow.

```java
class ControlStatement {
    public static void main(String[] args) {
        int num = 5;
        if (num < 10 && num > 20) {  // Should use `||` (or) instead of `&&` (and)
            System.out.println("Logical error case: Logic error in conditional!");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case passed!
```

## 10. Incorrect List Mutation During Iteration
Modifying a list during iteration causes elements to be skipped.

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

class ListMutationDuringIteration {
    public static void main(String[] args) {
        List<Integer> lst = new ArrayList<>();
        for (int i = 1; i <= 5; i++) {
            lst.add(i);
        }

        Iterator<Integer> iterator = lst.iterator();
        while (iterator.hasNext()) {
            Integer i = iterator.next();
            if (i % 2 == 0) {
                iterator.remove();  // remove the element
            }
        }

        if (lst.equals(List.of(1, 3, 5))) {
            System.out.println("Logical error case: List mutation during iteration handled correctly!");
        } else {
            System.out.println("Logical error case passed!");
        }
    }
}
```
Expected Output:
```text
Logical error case: List mutation during iteration handled correctly!
```

## 11. Incorrect Data Type Assumption
Assuming all list elements are integers leads to a runtime error when encountering a non-integer value.

```java
import java.util.List;

class IncorrectDataType {
    public static void main(String[] args) {
        List<Object> lst = List.of(1, 2, "3", 4);  // Mixed data types
        int total = 0;
        try {
            for (Object item : lst) {
                if (item instanceof Integer) {
                    total += (int) item;  // Safely cast to int
                } else {
                    throw new IllegalArgumentException("Non-integer value found: " + item);
                }
            }
            if (total != 10) {
                System.out.println("Logical error case: Incorrect data type assumption!");
            } else {
                System.out.println("Logical error case passed!");
            }
        } catch (ClassCastException | IllegalArgumentException e) {
            System.out.println("Logical error case: " + e.getMessage());
        }
    }
}
```
Expected Output:
```text
Logical error case: Non-integer value found: 3
```

## 12. Using == Instead of .equals() for Object Comparison
Using `==` instead of `.equals()` compares object references instead of their values, leading to a failed comparison.

```java
import java.util.List;

class IsVsEquals {
    public static void main(String[] args) {
        List<Integer> a = List.of(1, 2, 3);
        List<Integer> b = List.of(1, 2, 3);
        if (a == b) {  // Should use `.equals()` instead of `==`
            System.out.println("Logical error case failed!");
        } else {
            System.out.println("Logical error case: Incorrect use of `==` instead of `.equals()`");
        }
    }
}
```
Expected Output:
```text
Logical error case: Incorrect use of `==` instead of `.equals()`
```

## Conclusion
These Java snippets highlight various Logical error cases, where the code runs without errors but produces incorrect or unintended results due to logical issues, wrong assumptions, or subtle programming mistakes.