# Error Handling Case Snippets

This file contains snippets of Java code that demonstrate handling various common exceptions such as `ArithmeticException`, `ArrayIndexOutOfBoundsException`, `NullPointerException`, and more. Each snippet intentionally triggers an error to showcase how exceptions can be caught in Java.

## 1. Division By Zero
Raises an `ArithmeticException` since division by zero is undefined.

```java
class DivisionByZero {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  
            System.out.println("Division operation successful!");
        } catch (ArithmeticException e) {
            System.out.println("Division by zero operation failed!");
        }
    }
}
```
Expected Output:
```text
Division by zero operation failed!
```

## 2. Index Out of range
Tries to access an index that doesn't exist in an array, causing an `ArrayIndexOutOfBoundsException`.

```java
class IndexOutOfRange {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};  // Array of size 3
        try {
            int value = arr[10];  // throw ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Index out of range operation passed!");
        } finally {
            System.out.println("Finished checking index out of range.");
        }
    }
}
```
Expected Output:
```text
Index out of range operation passed!
Finished checking index out of range.
```

## 3. Key Error in HashMap
Tries to access a key in a HashMap that doesn’t exist, which should raise a `NullPointerException`.

```java
import java.util.HashMap;

class KeyError {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("name", "Alice");

        // Try to retrieve a value for a non-existent key
        String value = map.get("age");

        if (value == null) {
            System.out.println("KeyError operation passed!"); 
        } else {
            System.out.println("KeyError operation failed!"); 
        }
    }
}
```
Expected Output:
```text
KeyError operation passed!
```

## 4. Type Mismatch
Adding an integer and a string, which should raise a `Compile-Time Error`.

```java
class TypeMismatch {
    public static void main(String[] args) {
        // raise a compile-time error
        int result = 5 + "five"; 
    }
}
```
Expected Output:
```text
error: incompatible types: String cannot be converted to int
        int result = 5 + "five"; 
                       ^
```

## 5. Invalid Syntax
Invalid Java syntax. The compiler should throw a `SyntaxError`.

```java
class InvalidSyntax {
    public static void main(String[] args) {
        if (true) System.out.println("Hello"; // missing bracket is a syntax error.
    }
}
```
Expected Output:
```text
error: ')' expected
        if (true) System.out.println("Hello"; // missing bracket is a syntax error.
                                            ^
```

## 6. Name Error (Undefined Variable)
Tries to use a variable that hasn’t been defined, which should raise a `Compile-Time Error`.

```java
class NameError {
    public static void main(String[] args) {
        // 'undefinedVariable' is not defined.
         System.out.println(undefinedVariable);
    }
}
```
Expected Output:
```text
error: cannot find symbol
         System.out.println(undefinedVariable);
                            ^
```

## 7. Attribute Error
Tries to call a non-existent method on a data type, raising a `NoSuchMethodError`.

```java
class AttributeError {
    public static void main(String[] args) {
        String text = "Hello";
        try {
            text.nonExistingMethod(); // this method doesn't exist.
        } catch (NoSuchMethodError e) {
            System.out.println("AttributeError operation passed!");
        }
    }
}
```
Expected Output:
```text
error: cannot find symbol
            text.nonExistingMethod(); // this method doesn't exist.
                ^
```

## 8. Value Error
Attempts to parse an invalid string into an integer, which should raise a `NumberFormatException`.

```java
class ValueError {
    public static void main(String[] args) {
        try {
            int value = Integer.parseInt("invalid_int");
        } catch (NumberFormatException e) {
            System.out.println("ValueError operation passed!");
        }
    }
}
```
Expected Output:
```text
ValueError operation passed!
```

## 9. Import Error
Tries to import a non-existent class, which will raise a `Compile-Time Error`.

```java
// the module `non_existing_module` does not exist.
import non_existing_module;

class ImportError {
    public static void main(String[] args) {
       // this would be a compile error.
    }
}
```
Expected Output:
```text
error: '.' expected
import non_existing_module;
                          ^
```

## 10. Overflow Error
Raises an `ArithmeticException` when attempting to calculate a value that is too large for an integer.

```java
class OverflowError {
    public static void main(String[] args) {
        try {
            int result = Math.multiplyExact(Integer.MAX_VALUE, 2);
        } catch (ArithmeticException e) {
            System.out.println("OverflowError operation passed!");
        }
    }
}
```
Expected Output:
```text
OverflowError operation passed!
```

## 11. Recursion Limit Exceeded
Infinite recursion that will exceed Java’s stack limit, resulting in a `StackOverflowError`.

```java
class RecursionError {
    public static void infiniteRecursion() {
        infiniteRecursion();
    }

    public static void main(String[] args) {
        try {
            infiniteRecursion();
        } catch (StackOverflowError e) {
            System.out.println("RecursionError operation passed!");
        }
    }
}
```
Expected Output:
```text
RecursionError operation passed!
```

## 12. Memory Error
Create an extremely large array, which may raise an `OutOfMemoryError`.

```java
class MemoryError {
    public static void main(String[] args) {
        try {
            int[] largeArray = new int[Integer.MAX_VALUE];
        } catch (OutOfMemoryError e) {
            System.out.println("MemoryError operation passed!");
        }
    }
}
```
Expected Output:
```text
MemoryError operation passed!
```

## 13. File Not Found Error
Attempts to open a non-existent file, which should raise a `FileNotFoundException`.

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;

class FileNotFoundError {
    public static void main(String[] args) {
        try {
            File file = new File("non_existent_file.txt");
            FileReader reader = new FileReader(file);
        } catch (FileNotFoundException e) {
            System.out.println("FileNotFoundError operation passed!");
        }
    }
}
```
Expected Output:
```text
FileNotFoundError operation passed!
```

## Conclusion
These Java examples demonstrate how various exceptions can be handled in Java using try-catch blocks.