# happy Test Cases

This document contains a set of basic test cases to validate that the Python compiler handles various operations correctly. Each test case includes a short description and a corresponding Python function.

---

## 1. Basic Arithmetic
Arithmetic operations like addition, subtraction, multiplication, division, and modulus.

```python
def test_arithmetic():
    print("2 + 2 =", 2 + 2)
    print("10 - 5 =", 10 - 5)
    print("10 * 3 =", 10 * 3)
    print("100 / 5 =", 100 / 5)
    print("2 ** 3 =", 2 ** 3)
    print("9 // 2 =", 9 // 2)
    print("9 % 2 =", 9 % 2)

test_arithmetic()
print("Arithmetic test completed!")
```

## 2. String Manupulation
String operations like concatenation, multiplication, length, case conversion, and slicing.

```python
def test_strings():
    print('"Hello" + " " + "World" =', "Hello" + " " + "World")
    print('"abc" * 3 =', "abc" * 3)
    print('len("test") =', len("test"))
    print('"Python".upper() =', "Python".upper())
    print('"PYTHON".lower() =', "PYTHON".lower())
    print('"racecar"[::-1] =', "racecar"[::-1])  # Palindrome check

test_strings()
print("String manipulation test completed!")
```

## 3. List Operation
List operations like concatenation, appending, indexing, and popping elements.

```python
def test_lists():
    lst = [1, 2, 3]
    print("List concatenation:", lst + [4, 5])
    print("Length of list:", len(lst))
    lst.append(4)
    print("After appending:", lst)
    print("First element:", lst[0])
    print("Last element:", lst[-1])
    lst.pop()
    print("After popping:", lst)

test_lists()
print("List operations test completed!")
```

## 4. Dictionary Operations
Python dictionaries, including accessing, modifying, and checking elements.

```python
def test_dictionaries():
    d = {"key1": "value1", "key2": "value2"}
    print('Value for "key1":', d["key1"])
    print("Length of dictionary:", len(d))
    d["key3"] = "value3"
    print("Is 'key3' in dictionary?", "key3" in d)
    print('Value for "key2":', d.get("key2"))

test_dictionaries()
print("Dictionary operations test completed!")
```

## 5. Boolean Logic
Boolean logic operations like and, or, not, and comparisons.

```python
def test_boolean_logic():
    print("True and True =", True and True)
    print("True or False =", True or False)
    print("not False =", not False)
    print("5 > 3 =", 5 > 3)
    print("3 < 1 =", 3 < 1)
    print("5 == 5 and 2 == 2 =", 5 == 5 and 2 == 2)

test_boolean_logic()
print("Boolean logic test completed!")
```

## 6. Tuple Operation
Tuple operations like indexing, concatenation, and repetition.

```python
def test_tuples():
    t = (1, 2, 3)
    print("Tuple concatenation:", t + (4, 5))
    print("First element:", t[0])
    print("Repetition of tuple:", t * 2)

test_tuples()
print("Tuple operations test completed!")
```

## 7. Set Operation
Set operations like union, intersection, and difference.

```python
def test_sets():
    s1 = {1, 2, 3}
    s2 = {3, 4, 5}
    print("Union of sets:", s1 | s2)
    print("Intersection of sets:", s1 & s2)
    print("Difference of sets:", s1 - s2)

test_sets()
print("Set operations test completed!")
```

## 8. Control Flow
Control flow constructs, including if-else statements, for loops, and while loops.

```python
def test_control_flow():
    x = 10
    if x > 5:
        print("x is greater than 5")
    else:
        print("x is less than or equal to 5")
    
    print("Sum of first 5 numbers:", sum([i for i in range(5)]))

    print("For loop result:")
    for i in range(3):
        print(i)

    while x > 0:
        x -= 1
    print("x after while loop:", x)

test_control_flow()
print("Control flow test completed!")
```

## 9. Function Test
Function definition and invocation. It tests whether a simple function returns the correct results.

```python
def add(a, b):
    return a + b

def test_functions():
    print("add(2, 3) =", add(2, 3))
    print("add(10, -5) =", add(10, -5))
    print("add(0, 0) =", add(0, 0))

test_functions()
print("Function testing completed!")
```

## 10. List Comprehension
Validates the correct execution of list comprehensions for creating lists and filtering values.

```python
def test_list_comprehension():
    squares = [x**2 for x in range(5)]
    print("Squares:", squares)
    
    even_numbers = [x for x in range(10) if x % 2 == 0]
    print("Even numbers:", even_numbers)

test_list_comprehension()
print("List comprehension test completed!")
```

## Conclusion
These tests cover a wide variety of basic operations in Python, ensuring that compiler handles common cases correctly.