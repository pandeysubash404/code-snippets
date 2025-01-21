# Multi-File Programming Snippets with TXT Input/Output

This document demonstrates the structure and usage of multi-file Java programs.


## 1. Simple Multi-File Program

Create `Main.java` & `Person.java` file in root directory.

`Main.java` file contains the main method and creates instances of the `Person` class defined in a separate file.

```java
class Main {
    public static void main(String[] args) {
        Person p = new Person("Ram", 25);
        p.displayInfo();
    }
}
```

`Person.java` file defines the Person class, which has attributes for the name and age of the person and a method to display the information.

```java
class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}
```
Expected Output:
```text
Name: Ram
Age: 25
```

## 2. Simple File input/output.

Create `Main.java`, `Person.java`, `Student.java` & `input.txt` file in root directory.

`Main.java` file contains the main method, where the program reads student data from a file, creates student objects, and writes the information to an output file.

```java
import java.io.*;
import java.util.ArrayList;

class Main {
    public static void main(String[] args) {
        try {
            // Read students from input.txt
            ArrayList<Student> students = readStudentsFromFile("input.txt");

            // Write student details to output.txt
            writeStudentsToFile(students, "output.txt");

        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    // Reads students' information from a text file
    public static ArrayList<Student> readStudentsFromFile(String filename) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filename));
        ArrayList<Student> students = new ArrayList<>();
        String line;
        while ((line = reader.readLine()) != null) {
            String[] parts = line.split(",");
            String name = parts[0];
            int age = Integer.parseInt(parts[1]);
            students.add(new Student(name, age));
        }
        reader.close();
        return students;
    }

    // Writes students' information to a text file
    public static void writeStudentsToFile(ArrayList<Student> students, String filename) throws IOException {
        BufferedWriter writer = new BufferedWriter(new FileWriter(filename));
        for (Student student : students) {
            writer.write("Name: " + student.getName() + ", Age: " + student.getAge());
            writer.newLine();
        }
        writer.close();
    }
}
```

`Person.java` file defines the base class `Person`, with basic attributes like `name` and `age`.

```java
class Person {
    protected String name;
    protected int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```

`Student.java` file defines the `Student` class that extends the `Person` class. In this simple version, it doesn't add new attributes, but it can be expanded in the future.

```java
class Student extends Person {
    public Student(String name, int age) {
        super(name, age);
    }
}
```

Create `input.txt` file contains student data, with each student on a new line. The format is `name,age`.

```
Ram,20
Shyam,22
Hari,21
```
---

Expected Output:

```text
Data read from file successfully.
```

`output.txt` (Generated File):

```text
Name: Ram, Age: 20
Name: Shyam, Age: 22
Name: Hari, Age: 21
```

---

## Conclusion

This simplified multi-file Java program focuses on basic inheritance and simple file input/output, making it much easier to understand and use.