# happy Test Cases

This document contains a set of basic test cases to validate that the Python compiler handles various operations correctly. Each test case includes a short description and a corresponding Python function.

---

## 1. Basic Arithmetic
Arithmetic operations like addition, subtraction, multiplication, division, and modulus.

```python
def test_arithmetic():
    assert 2 + 2 == 4
    assert 10 - 5 == 5
    assert 10 * 3 == 30
    assert 100 / 5 == 20
    assert 2 ** 3 == 8
    assert 9 // 2 == 4
    assert 9 % 2 == 1

test_arithmetic()
print("Arithmetic test passed!")
```

## 2. String Manupulation
String operations like concatenation, multiplication, length, case conversion, and slicing.

```python
def test_strings():
    assert "Hello" + " " + "World" == "Hello World"
    assert "abc" * 3 == "abcabcabc"
    assert len("test") == 4
    assert "Python".upper() == "PYTHON"
    assert "PYTHON".lower() == "python"
    assert "racecar"[::-1] == "racecar"  # Palindrome check

test_strings()
print("String manipulation test passed!")
```

## 3. List Operation
List operations like concatenation, appending, indexing, and popping elements.

```python
def test_lists():
    lst = [1, 2, 3]
    assert lst + [4, 5] == [1, 2, 3, 4, 5]
    assert len(lst) == 3
    lst.append(4)
    assert lst == [1, 2, 3, 4]
    assert lst[0] == 1
    assert lst[-1] == 4
    lst.pop()
    assert lst == [1, 2, 3]

test_lists()
print("List operations test passed!")
```

## 4. Dictionary Operations
Python dictionaries, including accessing, modifying, and checking elements.

```python
def test_dictionaries():
    d = {"key1": "value1", "key2": "value2"}
    assert d["key1"] == "value1"
    assert len(d) == 2
    d["key3"] = "value3"
    assert "key3" in d
    assert d.get("key2") == "value2"

test_dictionaries()
print("Dictionary operations test passed!")
```

## 5. Boolean Logic
Boolean logic operations like and, or, not, and comparisons.

```python
def test_boolean_logic():
    assert True and True == True
    assert True or False == True
    assert not False == True
    assert (5 > 3) == True
    assert (3 < 1) == False
    assert (5 == 5 and 2 == 2) == True

test_boolean_logic()
print("Boolean logic test passed!")
```

## 6. Tuple Operation
Tuple operations like indexing, concatenation, and repetition.

```python
def test_boolean_logic():
    assert True and True == True
    assert True or False == True
    assert not False == True
    assert (5 > 3) == True
    assert (3 < 1) == False
    assert (5 == 5 and 2 == 2) == True

test_boolean_logic()
print("Boolean logic test passed!")
```

## 7. Set Operation
Set operations like union, intersection, and difference.

```python
def test_sets():
    s1 = {1, 2, 3}
    s2 = {3, 4, 5}
    assert s1 | s2 == {1, 2, 3, 4, 5}  # Union
    assert s1 & s2 == {3}              # Intersection
    assert s1 - s2 == {1, 2}           # Difference

test_sets()
print("Set operations test passed!")
```

## 8. Control Flow
Control flow constructs, including if-else statements, for loops, and while loops.

```python
def test_control_flow():
    x = 10
    if x > 5:
        assert True
    else:
        assert False
    
    assert sum([i for i in range(5)]) == 10  # 0 + 1 + 2 + 3 + 4

    for i in range(3):
        assert i in [0, 1, 2]
    
    while x > 0:
        x -= 1
    assert x == 0

test_control_flow()
print("Control flow test passed!")
```

## 9. Function Test
Function definition and invocation. It tests whether a simple function returns the correct results.

```python
def add(a, b):
    return a + b

def test_functions():
    assert add(2, 3) == 5
    assert add(10, -5) == 5
    assert add(0, 0) == 0

test_functions()
print("Function testing passed!")
```

## 10. List Comprehension
Validates the correct execution of list comprehensions for creating lists and filtering values.

```python
def test_list_comprehension():
    squares = [x**2 for x in range(5)]
    assert squares == [0, 1, 4, 9, 16]
    
    even_numbers = [x for x in range(10) if x % 2 == 0]
    assert even_numbers == [0, 2, 4, 6, 8]

test_list_comprehension()
print("List comprehension test passed!")
```

## Conclusion
These tests cover a wide variety of basic operations in Python, ensuring that compiler handles common cases correctly.