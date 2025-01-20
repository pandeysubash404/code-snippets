# Multi-File Python Program with CSV Input/Output

This document demonstrates the structure and usage of multi-file Python programs that handle CSV files for input/output.

## Python Program Structure

Create the following files: `main.py`, `person.py`, `student.py`, and `input.csv`.

`main.py` file contains the main logic where the program reads student data from a CSV file, processes it, and writes the information to another file.

```python
import csv
from person import create_person
from student import create_student, display_students

def read_students_from_file(filename):
    students = []
    with open(filename, mode='r') as file:
        reader = csv.reader(file)
        for row in reader:
            name = row[0]
            age = int(row[1])
            student = create_student(name, age)
            students.append(student)
    return students

def write_students_to_file(students, filename):
    with open(filename, mode='w', newline='') as file:
        writer = csv.writer(file)
        for student in students:
            writer.writerow([student['name'], student['age']])

def main():
    input_file = 'input.csv'
    output_file = 'output.csv'

    # Read students from input.csv
    students = read_students_from_file(input_file)

    # Display students
    display_students(students)

    # Write students to output.csv
    write_students_to_file(students, output_file)
    print("Data has been written to", output_file)

if __name__ == "__main__":
    main()
```

`person.py` file contains the logic for creating a basic person (similar to the `Person` class in Java).

```python
def create_person(name, age):
    return {
        'name': name,
        'age': age
    }
```

`student.py` file contains logic for creating a student and displaying their information.

```python
from person import create_person

def create_student(name, age):
    # In this example, a student is simply a person
    return create_person(name, age)

def display_students(students):
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}")
```

`input.csv` file contains the student data, with each line representing a student with their name and age.

```
Ram,20
Shyam,22
Hari,21
```
---

## Expected Output

```text
Name: Ram, Age: 20
Name: Shyam, Age: 22
Name: Hari, Age: 21
Data has been written to output.csv
```

`output.csv` (Generated File):

```
Ram,20
Shyam,22
Hari,21
```
---

## Conclusion

It demonstrates how to structure a Python project across multiple files, separating the logic for handling persons, students, and file operations.