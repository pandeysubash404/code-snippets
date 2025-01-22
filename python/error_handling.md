# Error Handling Case Snippets

This error handling case checks if the Python compiler correctly flags a syntax error.

## 1. Division By Zero
Raise a `ZeroDivisionError` since division by zero is undefined.

```python
def division_by_zero():
    try:
        result = 10 / 0
    except ZeroDivisionError:
        print("Division by zero operation passed!")
    else:
        print("Division by zero operation failed!")

division_by_zero()
```
Expected Output:
```text
Division by zero operation passed!
```


## 2. Index Out of Range
Tries to access an index that doesn't exist in a list, causing an `IndexError`.

```python
def index_out_of_range():
    lst = [1, 2, 3]
    try:
        value = lst[10]
    except IndexError:
        print("Index out of range operation passed!")
    else:
        print("Index out of range operation failed!")

index_out_of_range()
```
Expected Output:
```text
Index out of range operation passed!
```

## 3. Key Error in Dictionary
Tries to access a key in a dictionary that doesn’t exist, which should raise a `KeyError`.

```python
def key_error():
    d = {"name": "Alice"}
    try:
        value = d["age"]
    except KeyError:
        print("KeyError operation passed!")
    else:
        print("KeyError operation failed!")

key_error()
```
Expected Output:
```text
KeyError operation passed!
```

## 4. Type Mismatch
Adding an integer and a string, which should raise a `TypeError`.

```python
def type_mismatch():
    try:
        result = 5 + "five"
    except TypeError:
        print("Type mismatch operation passed!")
    else:
        print("Type mismatch operation failed!")

type_mismatch()
```
Expected Output:
```text
Type mismatch operation passed!
```

## 5. Invalid Syntax
Invalid Python syntax. The compiler should throw a `SyntaxError`.

```python
def invalid_syntax():
    try:
        eval("if True print('Hello')")
    except SyntaxError:
        print("SyntaxError operation passed!")
    else:
        print("SyntaxError operation failed!")

invalid_syntax()
```
Expected Output:
```text
SyntaxError operation passed!
```

## 6. Name Error (Undefined Variable)
Tries to use a variable that hasn’t been defined, which should raise a `NameError`.

```python
def name_error():
    try:
        print(undefined_variable)
    except NameError:
        print("NameError operation passed!")
    else:
        print("NameError operation failed!")

name_error()
```
Expected Output:
```text
NameError operation passed!
```

## 7. Attribute Error
Tries to call a non-existent method on a data type, raising an `AttributeError`.

```python
def attribute_error():
    try:
        value = "Hello".non_existing_method()
    except AttributeError:
        print("AttributeError operation passed!")
    else:
        print("AttributeError operation failed!")

attribute_error()
```
Expected Output:
```text
AttributeError operation passed!
```

## 8. Value Error
Attempts to convert an invalid string to an integer, which should raise a `ValueError`.

```python
def value_error():
    try:
        value = int("invalid_int")
    except ValueError:
        print("ValueError operation passed!")
    else:
        print("ValueError operation failed!")

value_error()
```
Expected Output:
```text
ValueError operation passed!
```

## 9. Import Error
Tries to import a non-existent module, which should raise an `ImportError`.

```python
def import_error():
    try:
        import non_existing_module
    except ImportError:
        print("ImportError operation passed!")
    else:
        print("ImportError operation failed!")

import_error()
```
Expected Output:
```text
ImportError operation passed!
```

## 10. Overflow Error
Raises an OverflowError when attempting to calculate a value that is too large.

```python
import math

def overflow_error():
    try:
        result = math.exp(1000)  # Exponential of a large number
    except OverflowError:
        print("OverflowError operation passed!")
    else:
        print("OverflowError operation failed!")

overflow_error()
```
Expected Output:
```text
OverflowError operation passed!
```

## 11. Recursion Limit Exceeded
Infinite recursion that will exceed Python’s recursion limit, resulting in a `RecursionError`.

```python
def infinite_recursion():
    return infinite_recursion()

def recursion_error():
    try:
        infinite_recursion()
    except RecursionError:
        print("RecursionError operation passed!")
    else:
        print("RecursionError operation failed!")

recursion_error()
```
Expected Output:
```text
RecursionError operation passed!
```

## 12. Memory Error
Create an extremely large list, which may raise a MemoryError if the system runs out of memory.

```python
def memory_error():
    try:
        huge_list = [1] * (10**10)  # Allocate a very large list
    except MemoryError:
        print("MemoryError operation passed!")
    else:
        print("MemoryError operation failed!")

memory_error()
```
Expected Output:
```text
MemoryError operation passed!
```

## 13. File Not Found Error
Attempts to open a non-existent file, which should raise a `FileNotFoundError`.

```python
def file_not_found_error():
    try:
        with open("non_existent_file.txt", "r") as file:
            pass
    except FileNotFoundError:
        print("FileNotFoundError operation passed!")
    else:
        print("FileNotFoundError operation failed!")

file_not_found_error()
```
Expected Output:
```text
FileNotFoundError operation passed!
```
