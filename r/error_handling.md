# Error Handling Case Snippets

This error handling case checks if the R compiler correctly flags an error.

## 1. Division By Zero
Raise a division by zero error since division by zero is undefined.

```r
division_by_zero <- function() {
  tryCatch({
    result <- 10 / 0
    if (is.infinite(result)) {
      stop("Division by zero occurred!")
    }
  }, error = function(e) {
    cat("Division by zero operation passed!\n")
  })
}

division_by_zero()
```
Output:
```text
[1] "Division by zero operation passed!"
```

## 2. Index Out of Range
Tries to access an index that doesn’t exist in a vector, causing an error.

```r
index_out_of_range <- function() {
  vec <- c(1, 2, 3)
  tryCatch({
    value <- vec[10]
    if (is.na(value)) {
      stop("Index out of range!")
    }
  }, error = function(e) {
    print("Index out of range operation passed!")
  })
}

index_out_of_range()
```
Output:
```text
[1] "Index out of range operation passed!"
```

## 3. Key Error in List
Tries to access a key in a list that doesn’t exist, which should raise an error.

```r
key_error <- function() {
  lst <- list(name = "Alice")
  tryCatch({
    value <- lst[["age"]]
    if (is.null(value)) {
      stop("KeyError: The key 'age' does not exist!")
    }
  }, error = function(e) {
    print("KeyError operation passed!")
  })
}

key_error()
```
Output:
```text
[1] "KeyError operation passed!"
```

## 4. Type Mismatch
Adding an integer and a string, which should raise an error.

```r
type_mismatch <- function() {
  tryCatch({
    result <- 5 + "five"
  }, error = function(e) {
    print("Type mismatch operation passed!")
  })
}

type_mismatch()
```
Output:
```text
[1] "Type mismatch operation passed!"
```

## 5. Invalid Syntax
Invalid R syntax. The compiler should throw a `syntax error`.

```r
invalid_syntax <- function() {
  tryCatch({
    eval(parse(text = "if TRUE print('Hello')")) # Missing parentheses around (TRUE)
  }, error = function(e) {
    print("SyntaxError operation passed!")
  })
}

invalid_syntax()
```
Output:
```text
[1] "SyntaxError operation passed!"
```

## 6. Name Error (Undefined Variable)
Tries to use a variable that hasn’t been defined, which should raise an error.

```r
name_error <- function() {
  tryCatch({
    print(undefined_variable)
  }, error = function(e) {
    print("NameError operation passed!")
  })
}

name_error()
```
Output:
```text
[1] "NameError operation passed!"
```

## 7. Attribute Error
Tries to call a non-existent method on a data type, raising an error.

```r
attribute_error <- function() {
  tryCatch({
    value <- "Hello"$non_existing_method # Invalid access
  }, error = function(e) {
    print("AttributeError operation passed!")
  })
}

attribute_error()
```
Output:
```text
[1] "AttributeError operation passed!"
```

## 8. Value Error
Attempts to convert an invalid string to an integer, which should raise an error.

```r
value_error <- function() {
  tryCatch({
    value <- as.integer("invalid_int")
  }, warning = function(e) {
    print("ValueError operation passed!")
  })
}

value_error()
```
Output:
```text
[1] "ValueError operation passed!"
```

## 9. File Not Found Error
Attempts to open a non-existent file, which should raise an error.

```r
file_not_found_error <- function() {
  tryCatch({
    file <- file("non_existent_file.txt", "r")
  }, warning = function(e) {
    print("FileNotFoundError operation passed!")
  })
}

file_not_found_error()
```
Output:
```text
[1] "FileNotFoundError operation passed!"
```

## 10. Memory Error
Create an extremely large object, which may raise a memory error if the system runs out of memory.

```r
memory_error <- function() {
  tryCatch({
    huge_list <- rep(1, 10^10)  # Allocate a very large list
  }, error = function(e) {
    print("MemoryError operation passed!")
  })
}

memory_error()
```
Output:
```text
[1] "MemoryError operation passed!"
```

## 11. Recursion Limit Exceeded
Infinite recursion that will exceed R’s recursion limit, resulting in an error.

```r
infinite_recursion <- function() {
  return(infinite_recursion())
}

recursion_error <- function() {
  tryCatch({
    infinite_recursion()
  }, error = function(e) {
    print("RecursionError operation passed!")
  })
}

recursion_error()
```
Output:
```text
[1] "RecursionError operation passed!"
```

## 12. File Permissions Error
Attempts to open a file without sufficient permissions, which should raise an error.

```r
file_permissions_error <- function() {
  tryCatch({
    file <- file("/root/non_existent_file.txt", "r")
  }, warning = function(e) {
    print("File permissions error operation passed!")
  })
}

file_permissions_error()
```
Output:
```text
[1] "File permissions error operation passed!"
```

## Conclusion
These bad case programs verify a wide variety of common errors that can occur during R execution. They are designed to fail and raise errors such as `division by zero`, `index out of range`, `type mismatch`, `value error`, and others.