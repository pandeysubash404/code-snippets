# Console Input Snippets

It is a list of common Python input-related snippets. `Input snippets` cover various ways to gather input from the user using Python's built-in functions and some common variations and practices:

---

## 1. Basic Input with `input()`  
The `input()` function reads a line from input (usually the user typing into the terminal or console).

```python
user_input = input("Enter something: ")
print(f"You entered: {user_input}")
```
**Example Run**
```text
Enter something: abc123
You entered: abc123
```

## 2. Converting Input to Integer
To convert the input to an integer:

```python
user_input = int(input("Enter an integer: "))
print(f"You entered the integer: {user_input}")
```
**Example Run**
```text
Enter an integer: 123
You entered the integer: 123
```

## 3. Converting Input to Float
To convert the input to a float:

```python
user_input = float(input("Enter a float number: "))
print(f"You entered the float: {user_input}")
```
**Example Run**
```text
Enter an float number: 123.456
You entered the float: 123.456
```

## 4. Reading Multiple Inputs on a Single Line  
You can ask for multiple inputs separated by spaces and split them into a list:

```python
user_input = input("Enter space-separated values: ").split()
print(f"You entered: {user_input}")
```
**Example Run**
```text
Enter space-separated values: Hello World
You entered: ['Hello', 'World']
```

## 5. Convert Multiple Inputs to Integers
This example takes multiple numbers and converts them to integers:

```python
user_input = list(map(int, input("Enter space-separated integers: ").split()))
print(f"You entered the integers: {user_input}")
```
**Example Run**
```text
Enter space-separated integers: 1 2 3
You entered the integers: [1, 2, 3]
```

## 6. Using `input()` in a Loop  
You can repeatedly ask the user for input in a loop:

```python
while True:
    user_input = input("Enter something (or 'exit' to quit): ")
    if user_input.lower() == 'exit':
        break
    print(f"You entered: {user_input}")
```
**Example Run**
```text
Enter something (or 'exit' to quit): hello
You entered: hello
Enter something (or 'exit' to quit): Ex  
You entered: Ex
Enter something (or 'exit' to quit): EXIT
```

## 7. Input with Validation  
You can add input validation to ensure the user provides a valid type of input:

```python
while True:
    try:
        user_input = int(input("Enter a valid integer: "))
        break
    except ValueError:
        print("That's not a valid integer. Try again.")
print(f"You entered the integer: {user_input}")
```
**Example Run**
```text
Enter a valid integer: hello
That's not a valid integer. Try again.
Enter a valid integer: 1234
You entered the integer: 1234
```

## 8. Asking for Input with Default Value  
If no input is provided, you can set a default value:

```python
user_input = input("Enter a value (default is 'Hello'): ") or 'Hello'
print(f"You entered: {user_input}")
```
**Example Run**
```text
Enter a value (default is 'Hello'): 
You entered: Hello
```

## 9. Reading Input from a File  
This snippet reads user input from a file instead of the terminal:

Create a `input.txt` file containing some data.
```text
This is test input file data.
```
`main.py` file program :
```python
with open("input.txt", "r") as file:
    user_input = file.read()
    print(f"File content: {user_input}")
```
**Example Run**
```text
File content: This is test input file data.
```

## 10. Accepting Password Input  
To securely take password input without displaying the characters:

```python
import getpass
password = getpass.getpass("Enter your password: ")
print("Password accepted.")
```
**Example Run**
```text
Enter your password:         
Password accepted.
```

## 11. Input with Multiple Values and Split by Delimiter  
Read values separated by a comma (or other delimiters):

```python
user_input = input("Enter values separated by commas: ").split(',')
print(f"You entered: {user_input}")
```
**Example Run**
```text
Enter values separated by commas: Hello, World
You entered: ['Hello', ' World']
```

## 12. Handling Input with Error Handling  
This snippet uses error handling to manage multiple input types:

```python
def get_int_input():
    while True:
        try:
            user_input = int(input("Please enter a number: "))
            return user_input
        except ValueError:
            print("Invalid input. Please enter a valid number.")

number = get_int_input()
print(f"Your number: {number}")
```
**Example Run**
```text
Please enter a number: hello    
Invalid input. Please enter a valid number.
Please enter a number: 1234
Your number: 1234
```

## 13. Input with Timeout  
For more advanced use cases, you can create an input prompt that times out after a given period (using `signal` library on Unix-like systems):

```python
import signal

def handler(signum, frame):
    raise TimeoutError("Input timed out.")

signal.signal(signal.SIGALRM, handler)
signal.alarm(5)  # Set timeout to 5 seconds

try:
    user_input = input("Enter something (you have 5 seconds): ")
    print(f"You entered: {user_input}")
except TimeoutError as e:
    print(e)
```
**Example Run**
```text
Enter something (you have 5 seconds): Input timed out.
```

## 14. Reading Input from User with `input()` and List Comprehension  
Using list comprehension to process input:

```python
user_input = [int(x) for x in input("Enter a list of integers separated by spaces: ").split()]
print(f"You entered: {user_input}")
```
**Example Run**
```text
Enter a list of integers separated by spaces: 1 2 3 4 5 6 7 8
You entered: [1, 2, 3, 4, 5, 6, 7, 8]
```

## 15. Using `input()` with Conditions  
Ask for input and apply conditions on the result:

```python
user_input = input("Enter a number between 1 and 10: ")
if user_input.isdigit() and 1 <= int(user_input) <= 10:
    print(f"Valid input: {user_input}")
else:
    print("Invalid input. Please enter a number between 1 and 10.")
```
**Example Run**
```text
Enter a number between 1 and 10: 23
Invalid input. Please enter a number between 1 and 10.
```

## 16. Accepting Date Input from the User  
Prompt the user to enter a date and convert it to a `datetime` object:

```python
from datetime import datetime

date_str = input("Enter a date (YYYY-MM-DD): ")
try:
    date = datetime.strptime(date_str, "%Y-%m-%d")
    print(f"Date entered: {date}")
except ValueError:
    print("Invalid date format. Please use YYYY-MM-DD.")
```
**Example Run**
```text
Enter a date (YYYY-MM-DD): 2025-01-21
Date entered: 2025-01-21 00:00:00
```

## 17. Input Using `eval()` (Caution with Security)  
Evaluating Python expressions from user input (use with care):

```python
user_input = input("Enter a Python expression: ")
result = eval(user_input)
print(f"The result of your expression is: {result}")
```
**Example Run**
```text
Enter a date (YYYY-MM-DD): 2025-01-21
Date entered: 2025-01-21 00:00:00
```

> **Caution**: `eval()` can execute arbitrary code, so be very careful when using it with untrusted input.

## 18. Right Angle Triangle  
Print a right-angled triangle of stars based on user input for both `rows` and `columns`.

```python
rows = int(input("Enter the number of rows: "))
cols = int(input("Enter the number of columns: "))

# Print the triangle
for i in range(1, rows + 1):
    for j in range(1, i + 1):
        print("*", end=" ")
    print()
```
**Example Run**
```text
Enter the number of rows: 5
Enter the number of columns: 5
* 
* * 
* * * 
* * * * 
* * * * *
```
---

These snippets should cover a wide variety of common input-related tasks in Python. To explore how different forms of user input can be handled.