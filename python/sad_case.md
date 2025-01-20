# Sad Case Test

This test case is designed to check `sad case programs` that contain logical issues or errors that do not trigger explicit exceptions but lead to incorrect or unintended outcomes.

## 1. Incorrect calculation (Logical Error)
Function incorrectly calculates the average by summing the values but dividing by the wrong number.

```python
def test_incorrect_average():
    numbers = [10, 20, 30]
    total = sum(numbers)
    # Wrong: Dividing by a hard-coded number instead of len(numbers)
    average = total / 4  # Should divide by len(numbers), i.e., 3
    if average != 20:
        print("Sad case: Incorrect average calculation!")
    else:
        print("Sad case passed!")

test_incorrect_average()
```

## 2. Off-By-One Error
Loop should iterate 5 times, but due to an off-by-one error, it iterates 4 times.

```python
def test_off_by_one():
    count = 0
    for i in range(1, 5):  # Should be range(1, 6)
        count += 1
    if count != 5:
        print("Sad case: Off-by-one error!")
    else:
        print("Sad case passed!")

test_off_by_one()
```

## 3. Wrong Comparison Operator
Check if the number is greater than 10, but the code uses `>=` instead of `>`, allowing 10 to pass when it shouldn’t.

```python
def test_wrong_comparison():
    num = 10
    if num >= 10:  # Should be num > 10
        print("Sad case: Wrong comparison operator!")
    else:
        print("Sad case passed!")

test_wrong_comparison()
```

## 4. Incorrect Use of Mutable Default Arguments
List `lst` retains values from previous function calls, which can lead to unexpected results.

```python
def add_item(item, lst=[]):
    lst.append(item)
    return lst

def test_mutable_default_argument():
    list1 = add_item(1)
    list2 = add_item(2)
    if list1 != [1] or list2 != [2]:
        print("Sad case: Mutable default argument!")
    else:
        print("Sad case passed!")

test_mutable_default_argument()
```

## 5. Shadowing Built-In Functions
variable `sum` shadows the built-in `sum()` function, causing the program to fail when trying to use the built-in later.

```python
def test_shadowing_builtin():
    sum = 10  # Shadows the built-in function 'sum'
    try:
        result = sum([1, 2, 3])
        print("Sad case failed!")
    except TypeError:
        print("Sad case: Shadowing built-in function!")

test_shadowing_builtin()
```

## 6. Floating-Point Precision Error
Result of this comparison may be `False` due to precision issues in floating-point arithmetic.

```python
def test_floating_point_error():
    result = 0.1 + 0.2
    if result != 0.3:  # This may fail due to precision issues
        print(f"Sad case: Floating-point precision error! (Got {result})")
    else:
        print("Sad case passed!")

test_floating_point_error()
```

## 7. Incorrect Variable Scope
Variable `x` is only defined inside the `if` block and is not accessible afterward, resulting in an `UnboundLocalError`.

```python
def test_variable_scope():
    if True:
        x = 10  # Defined inside the block
    try:
        y = x + 1  # Using `x` outside the block
        print("Sad case passed!")
    except UnboundLocalError:
        print("Sad case: Incorrect variable scope!")

test_variable_scope()
```

## 8. Infinite Loop (Logical Error)
Loop condition is never met, causing the loop to run infinitely.

```python
def test_infinite_loop():
    counter = 10
    while counter > 0:
        print("Sad case: Infinite loop!")
        counter += 1  # Should decrement to reach the end

test_infinite_loop()
```

## 9. Logic Error in Conditional Statements
Program uses `and  ` instead of `or`, leading to incorrect logic in the conditional.

```python
def test_logic_error():
    num = 5
    if num < 10 and num > 20:  # Should be `or` to check for invalid values
        print("Sad case: Logic error in conditional!")
    else:
        print("Sad case passed!")

test_logic_error()
```

## 10. Incorrect List Mutation During Iteration
Removes items from the list while iterating over it, which leads to skipping some elements.

```python
def test_list_mutation_during_iteration():
    lst = [1, 2, 3, 4, 5]
    for i in lst:
        if i % 2 == 0:
            lst.remove(i)  # Mutating the list during iteration
    if lst != [1, 3, 5]:
        print("Sad case: List mutation during iteration!")
    else:
        print("Sad case passed!")

test_list_mutation_during_iteration()
```

## 11. Incorrect Data Type Assumption
Program assumes that all elements in the list are integers, but a string sneaks in, leading to an incorrect sum.

```python
def test_incorrect_data_type():
    lst = [1, 2, '3', 4]  # Incorrect data type
    total = 0
    for item in lst:
        total += item  # Will fail when trying to add '3'
    if total != 10:
        print("Sad case: Incorrect data type assumption!")
    else:
        print("Sad case passed!")

test_incorrect_data_type()
```

## 12. Using is Instead of == for Value Comparison
Program uses `is` instead of `==` to compare two lists with the same content, leading to a failed comparison.

```python
def test_is_vs_equals():
    a = [1, 2, 3]
    b = [1, 2, 3]
    if a is b:  # Should use `==` instead of `is`
        print("Sad case failed!")
    else:
        print("Sad case: Incorrect use of `is` instead of `==`")

test_is_vs_equals()
```

## Conclusion
These sad cases demonstrate how programs can execute successfully but yield unintended or incorrect results due to logic flaws, wrong assumptions, or subtle issues that don’t result in exceptions or errors. 