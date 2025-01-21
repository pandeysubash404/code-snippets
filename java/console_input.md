# Console Input Snippets

It is a list of common Java input-related snippets. `Input snippets` cover various ways to gather input from the user using Java's built-in functions and some common variations and practices:

---

## 1. Basic Input with `Scanner`
We use `Scanner` to read input from the user:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter something: ");
        String userInput = scanner.nextLine();
        System.out.println("You entered: " + userInput);
    }
}
```
**Example Run**
```text
Enter something: abc123
You entered: abc123
```

## 2. Converting Input to Integer
To convert the input to an integer:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter an integer: ");
        int userInput = scanner.nextInt();
        System.out.println("You entered the integer: " + userInput);
    }
}
```
**Example Run**
```text
Enter an integer: 123
You entered the integer: 123
```

## 3. Converting Input to Float
To convert the input to a float:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a float number: ");
        float userInput = scanner.nextFloat();
        System.out.println("You entered the float: " + userInput);
    }
}
```
**Example Run**
```text
Enter a float number: 123.456
You entered the float: 123.456
```

## 4. Reading Multiple Inputs on a Single Line  
You can ask for multiple inputs separated by spaces and split them into an array:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter space-separated values: ");
        String[] userInput = scanner.nextLine().split(" ");
        System.out.println("You entered: ");
        for (String value : userInput) {
            System.out.println(value);
        }
    }
}
```
**Example Run**
```text
Enter space-separated values: Hello World
You entered:
Hello
World
```

## 5. Convert Multiple Inputs to Integers
This example takes multiple numbers and converts them to integers:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter space-separated integers: ");
        String[] inputs = scanner.nextLine().split(" ");
        int[] numbers = new int[inputs.length];
        for (int i = 0; i < inputs.length; i++) {
            numbers[i] = Integer.parseInt(inputs[i]);
        }
        System.out.print("You entered the integers: ");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}
```
**Example Run**
```text
Enter space-separated integers: 1 2 3
You entered the integers: 1 2 3
```

## 6. Using `input()` in a Loop  
You can repeatedly ask the user for input in a loop:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.print("Enter something (or 'exit' to quit): ");
            String userInput = scanner.nextLine();
            if (userInput.equalsIgnoreCase("exit")) {
                break;
            }
            System.out.println("You entered: " + userInput);
        }
    }
}
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

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int userInput;
        while (true) {
            try {
                System.out.print("Enter a valid integer: ");
                userInput = Integer.parseInt(scanner.nextLine());
                break;
            } catch (NumberFormatException e) {
                System.out.println("That's not a valid integer. Try again.");
            }
        }
        System.out.println("You entered the integer: " + userInput);
    }
}
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

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a value (default is 'Hello'): ");
        String userInput = scanner.nextLine();
        if (userInput.isEmpty()) {
            userInput = "Hello";
        }
        System.out.println("You entered: " + userInput);
    }
}
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
`Main.java` file program :

```java
import java.io.File;
import java.io.IOException;
import java.util.Scanner;

class Main {
    public static void main(String[] args) throws IOException {
        File file = new File("input.txt");
        Scanner scanner = new Scanner(file);
        StringBuilder fileContent = new StringBuilder();
        while (scanner.hasNextLine()) {
            fileContent.append(scanner.nextLine()).append("\n");
        }
        System.out.println("File content: " + fileContent.toString());
    }
}
```
**Example Run**
```text
File content: This is test input file data.
```

## 10. Accepting Password Input  
To securely take password input without displaying the characters:

```java
import java.io.Console;

class Main {
    public static void main(String[] args) {
        Console console = System.console();
        if (console == null) {
            System.out.println("No console available");
            return;
        }
        char[] passwordArray = console.readPassword("Enter your password: ");
        System.out.println("Password accepted.");
    }
}
```
**Example Run**
```text
Enter your password:         
Password accepted.
```

## 11. Input with Multiple Values and Split by Delimiter  
Read values separated by a comma (or other delimiters):

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter values separated by commas: ");
        String[] userInput = scanner.nextLine().split(",");
        System.out.println("You entered: ");
        for (String value : userInput) {
            System.out.println(value);
        }
    }
}
```
**Example Run**
```text
Enter values separated by commas: Hello, World
You entered:
Hello
 World
```

## 12. Handling Input with Error Handling  
This snippet uses error handling to manage multiple input types:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int number = getIntInput(scanner);
        System.out.println("Your number: " + number);
    }

    public static int getIntInput(Scanner scanner) {
        while (true) {
            try {
                System.out.print("Please enter a number: ");
                return Integer.parseInt(scanner.nextLine());
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a valid number.");
            }
        }
    }
}
```
**Example Run**
```text
Please enter a number: hello    
Invalid input. Please enter a valid number.
Please enter a number: 1234
Your number: 1234
```

## 13. Input with Timeout  
For more advanced use cases, you can create an input prompt that times out after a given period (using `Timer`, & `TimerTask`):

```java
import java.util.Scanner;
import java.util.Timer;
import java.util.TimerTask;

class Main {
    public static void main(String[] args) {
        Timer timer = new Timer();
        TimerTask task = new TimerTask() {
            public void run() {
                System.out.println("Input timed out.");
                System.exit(0);
            }
        };
        timer.schedule(task, 5000); // Set timeout to 5 seconds

        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter something (you have 5 seconds): ");
        String userInput = scanner.nextLine();
        timer.cancel();
        System.out.println("You entered: " + userInput);
    }
}
```
**Example Run**
```text
Enter something (you have 5 seconds): Input timed out.
```

## 14. Reading Input from User with `Scanner()` and List Comprehension  
Using list comprehension to process input:

```java
import java.util.Scanner;
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a list of integers separated by spaces: ");
        String[] userInput = scanner.nextLine().split(" ");
        int[] numbers = Arrays.stream(userInput).mapToInt(Integer::parseInt).toArray();
        System.out.println("You entered: " + Arrays.toString(numbers));
    }
}
```
**Example Run**
```text
Enter a list of integers separated by spaces: 1 2 3 4 5 6 7 8
You entered: [1, 2, 3, 4, 5, 6, 7, 8]
```

## 15. Using `Scanner()` with Conditions  
Ask for input and apply conditions on the result:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number between 1 and 10: ");
        String userInput = scanner.nextLine();
        if (userInput.matches("[1-9]") && Integer.parseInt(userInput) >= 1 && Integer.parseInt(userInput) <= 10) {
            System.out.println("Valid input: " + userInput);
        } else {
            System.out.println("Invalid input. Please enter a number between 1 and 10.");
        }
    }
}
```
**Example Run**
```text
Enter a number between 1 and 10: 23
Invalid input. Please enter a number between 1 and 10.
```

## 16. Accepting Date Input from the User  
Prompt the user to enter a date and convert it to a `Date` object with `SimpleDateFormat`:

```java
import java.text.SimpleDateFormat;
import java.util.Scanner;
import java.util.Date;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a date (YYYY-MM-DD): ");
        String dateStr = scanner.nextLine();
        try {
            SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
            Date date = dateFormat.parse(dateStr);
            System.out.println("Date entered: " + date);
        } catch (Exception e) {
            System.out.println("Invalid date format. Please use YYYY-MM-DD.");
        }
    }
}
```
**Example Run**
```text
Enter a date (YYYY-MM-DD): 2025-01-21
Date entered: Mon Jan 21 00:00:00 UTC 2025
```

## 17. Right Angle Triangle  
Print a right-angled triangle of stars based on user input for both `rows` and `columns`.

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the number of rows: ");
        int rows = scanner.nextInt();
        System.out.print("Enter the number of columns: ");
        int cols = scanner.nextInt();

        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
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

These snippets should cover a wide variety of common input-related tasks in Java. To explore how different forms of user input can be handled.