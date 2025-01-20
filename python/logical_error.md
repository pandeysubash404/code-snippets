# Python Logical Error Case Snippets

This Logical error  Case is designed to check `logical error case programs` that contain logical issues or errors that do not trigger explicit exceptions but lead to incorrect or unintended outcomes.

## 1. Incorrect calculation (Logical Error)
Function incorrectly calculates the average by summing the values but dividing by the wrong number.

```python
def incorrect_average():
    numbers = [10, 20, 30]
    total = sum(numbers)
    # Wrong: Dividing by a hard-coded number instead of len(numbers)
    average = total / 4  # Should divide by len(numbers), i.e., 3
    if average != 20:
        print("Logical error case: Incorrect average calculation!")
    else:
        print("Logical error case passed!")

incorrect_average()
```
Output:
```text
Logical error case: Incorrect average calculation!
```

## 2. Off-By-One Error
Loop should iterate 5 times, but due to an off-by-one error, it iterates 4 times.

```python
def off_by_one():
    count = 0
    for i in range(1, 5):  # Should be range(1, 6)
        count += 1
    if count != 5:
        print("Logical error case: Off-by-one error!")
    else:
        print("Logical error case passed!")

off_by_one()
```
Output:
```text
Logical error case: Off-by-one error!
```

## 3. Wrong Comparison Operator
Check if the number is greater than 10, but the code uses `>=` instead of `>`, allowing 10 to pass when it shouldn’t.

```python
def wrong_comparison():
    num = 10
    if num >= 10:  # Should be num > 10
        print("Logical error case: Wrong comparison operator!")
    else:
        print("Logical error case passed!")

wrong_comparison()
```
Output:
```text
Logical error case: Wrong comparison operator!
```

## 4. Incorrect Use of Mutable Default Arguments
List `lst` retains values from previous function calls, which can lead to unexpected results.

```python
def add_item(item, lst=[]):
    lst.append(item)
    return lst

def mutable_default_argument():
    list1 = add_item(1)
    list2 = add_item(2)
    if list1 != [1] or list2 != [2]:
        print("Logical error case: Mutable default argument!")
    else:
        print("Logical error case passed!")

mutable_default_argument()
```
Output:
```text
Logical error case: Mutable default argument!
```

## 5. Shadowing Built-In Functions
Variable `sum` shadows the built-in `sum()` function, causing the program to fail when trying to use the built-in later.

```python
def shadowing_builtin():
    sum = 10  # Shadows the built-in function 'sum'
    try:
        result = sum([1, 2, 3])
        print("Logical error case failed!")
    except TypeError:
        print("Logical error case: Shadowing built-in function!")

shadowing_builtin()
```
Output:
```text
Logical error case: Shadowing built-in function!
```

## 6. Floating-Point Precision Error
Result of this comparison may be `False` due to precision issues in floating-point arithmetic.

```python
def floating_point_error():
    result = 0.1 + 0.2
    if result != 0.3:  # This may fail due to precision issues
        print(f"Logical erro case: Floating-point precision error! (Got {result})")
    else:
        print("Logical erro case passed!")

floating_point_error()
```
Output:
```text
Logical error case: Floating-point precision error! (Got 0.30000000000000004)
```

## 7. Undefined Variable
Variable `x` is not defined inside the `try` block and so, could not accessible afterward, resulting in an `NameError`.

```python
def variable_scope():
    try:
        y = x + 1  # `x` has not been defined yet in the function scope
        print("Logical error case passed!")
    except NameError:
        print("Logical error case: Undefined variable!")

variable_scope()
```
Output:
```text
Logical error case: Undefined variable!
```

## 8. Infinite Loop
Loop condition is never met, causing the loop to run infinitely.

```python
def infinite_loop():
    counter = 10
    while counter > 0:
        print(f"Logical error case: Infinite loop {counter}!")
        counter += 1  # Should decrement to reach the end

infinite_loop()
```
Output:
```text
Logical error case: Infinite loop 1!
Logical error case: Infinite loop 2!
Logical error case: Infinite loop 3!
Logical error case: Infinite loop 4!

```

## 9. Conditional Statements
Program uses `and  ` instead of `or`, leading to incorrect logic in the conditional.

```python
def conditional_statement():
    num = 5
    if num < 10 and num > 20:  # Should be `or` to check for invalid values
        print("Logical error case: Conditional statements!")
    else:
        print("Logical error case passed!")

conditional_statement()
```
Output:
```text
Logical error case passed!
```

## 10. Incorrect List Mutation During Iteration
Removes items from the list while iterating over it, which leads to skipping some elements.

```python
def list_mutation_during_iteration():
    lst = [1, 2, 3, 4, 5]
    for i in lst:
        if i % 2 == 0:
            lst.remove(i)  # Mutating the list during iteration
    if lst != [1, 3, 5]:
        print("Logical error case: List mutation during iteration!")
    else:
        print("Logical error case passed!")

list_mutation_during_iteration()
```
Output:
```text
Logical error case passed!
```

## 11. Incorrect Data Type Assumption
Program assumes that all elements in the list are integers, but a string sneaks in, leading to an incorrect sum.

```python
def incorrect_data_type():
    lst = [1, 2, '3', 4]  # Incorrect data type (string in a list of integers)
    total = 0
    try:
        for item in lst:
            total += item  # This will raise a TypeError when it reaches '3'
    except TypeError:
        print("Logical error case: Incorrect data type assumption!")
    else:
        if total != 10:
            print("Logical error case: Total is not as expected!")
        else:
            print("Logical error case passed!")

incorrect_data_type()
```
Output:
```text
Logical error case: Incorrect data type assumption!
```

## 12. Using is Instead of == for Value Comparison
Program uses `is` instead of `==` to compare two lists with the same content, leading to a failed comparison.

```python
def is_vs_equals():
    a = [1, 2, 3]
    b = [1, 2, 3]
    if a is b:  # Should use `==` instead of `is`
        print("Logical error case failed!")
    else:
        print("Logical error case: Incorrect use of `is` instead of `==`")

is_vs_equals()
```
Output:
```text
Logical error case: Incorrect use of `is` instead of `==`
```

## Conclusion
These Logical error  cases demonstrate how programs can execute successfully but yield unintended or incorrect results due to logic flaws, wrong assumptions, or subtle issues that don’t result in exceptions or errors. 