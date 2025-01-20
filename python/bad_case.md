# Bad Case: Syntax Error

This bad case checks if the Python compiler correctly flags a syntax error.

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

## 13. Assertion Error
Raises an `AssertionError` if the condition is `False`.

```python
def assertion_error():
    try:
        assert False, "This is an AssertionError"
    except AssertionError:
        print("AssertionError operation passed!")
    else:
        print("AssertionError operation failed!")

assertion_error()
```

## 14. File Not Found Error
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

## Conclusion
These bad case programs verify a wide variety of common errors that can occur during Python execution. They are designed to fail and raise exceptions such as `ZeroDivisionError`, `IndexError`, `TypeError`, `ValueError`, and others. 