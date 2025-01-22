# Interactive Programming Snippets

A collection of 18 interactive R programming snippets that showcase common operations, functions, and concepts in R programming.

---

## 1. Basic Arithmetic Operations
Performing basic arithmetic calculations.

```r
# Addition
result <- 5 + 3
print(result)

# Subtraction
result <- 8 - 2
print(result)

# Multiplication
result <- 6 * 4
print(result)

# Division
result <- 10 / 2
print(result)
```
Expected Output:
```text
8
6
24
5
```

## 2. Data Frame Creation
Create and manipulate a simple data frame.

```r
# Create a DataFrame
data <- data.frame(
  Name = c("Ram", "Sita", "Gita"),
  Age = c(28, 22, 31),
  Gender = c("Male", "Female", "Female")
)

# View the DataFrame
print(data)
```
Expected Output:
```text
  Name Age Gender
1 Ram  28   Male
2 Sita  22 Female
3 Gita  31 Female
```

## 3. Summarizing Data
Using summary functions to summarize data frames.

```r
# Create a DataFrame
data <- data.frame(
  Name = c("Ram", "Sita", "Gita"),
  Age = c(28, 22, 31),
  Gender = c("Male", "Female", "Female")
)

# Summarize the data
summary(data)
```
Expected Output:
```text
      Name                Age          Gender         
 Length:3           Min.   :22.0   Length:3          
 Class :character   1st Qu.:25.0   Class :character  
 Mode  :character   Median :28.0   Mode  :character  
                    Mean   :27.0                     
                    3rd Qu.:29.5                     
                    Max.   :31.0                     
```

## 4. Vector Operations
Creating and performing operations on vectors.

```r
# Create a vector
v <- c(1, 2, 3, 4, 5)

# Sum of elements
sum_v <- sum(v)
print(sum_v)

# Mean of elements
mean_v <- mean(v)
print(mean_v)
```
Expected Output:
```text
15
3
```

## 5. Plotting with ggplot2
Creating a simple scatter plot using the `ggplot2` library.

```r
# Install ggplot2 if not installed
# install.packages("ggplot2")

# Load library
library(ggplot2)

# Create a scatter plot
ggplot(data, aes(x = Age, y = Gender)) +
  geom_point()
```
Expected Output:
```text
A scatter plot is displayed with Age on the X-axis and Gender on the Y-axis.
```

## 6. Apply Functions
Using the `apply()` function to perform operations on rows or columns of a matrix.

```r
# Create a matrix
mat <- matrix(1:9, nrow = 3)

# Apply sum function by rows
row_sum <- apply(mat, 1, sum)
print(row_sum)

# Apply sum function by columns
col_sum <- apply(mat, 2, sum)
print(col_sum)
```
Expected Output:
```text
[12 15 18]
[ 6 15 24 ]
```

## 7. Reading and Writing CSV Files
Write and read CSV files.

```r
data <- "This is test data."

# Writing data to CSV
write.csv(data, "output.csv")

# Reading data from CSV
new_data <- read.csv("output.csv")
print(new_data)
```
Expected Output:
```text
This is test data.
```

## 8. Creating Functions
Defining and using custom functions.

```r
# Define a function to calculate square
square <- function(x) {
  return(x^2)
}

# Use the function
result <- square(5)
print(result)
```
Expected Output:
```text
25
```

## 9. Conditional Statements
Using `if` statements for conditional logic.

```r
# Conditional check
num <- 7
if (num > 5) {
  print("Number is greater than 5")
} else {
  print("Number is 5 or less")
}
```
Expected Output:
```text
Number is greater than 5
```

## 10. Loops in R
Using `for` loop to iterate over elements.

```r
# For loop example
for (i in 1:5) {
  print(i)
}
```
Expected Output:
```text
1
2
3
4
5
```

## 11. Generating Random Numbers
Generating random numbers using `runif()` and `rnorm()` functions.

```r
# Generate 5 random uniform numbers between 0 and 1
random_nums <- runif(5)
print(random_nums)

# Generate 5 random numbers from a normal distribution
normal_nums <- rnorm(5)
print(normal_nums)
```
Expected Output:
```text
[0.729 0.365 0.225 0.890 0.110]
[ 0.587 -1.120  1.349 -0.151  0.370]
```

## 12. Matrix Multiplication
Performing matrix multiplication.

```r
# Create two matrices
A <- matrix(1:4, nrow = 2)
B <- matrix(5:8, nrow = 2)

# Multiply matrices
C <- A %*% B
print(C)
```
Expected Output:
```text
     [,1] [,2]
[1,]   23   31
[2,]   34   46
```

## 13. Handling NA Values
Identifying and removing NA (missing) values.

```r
# Create a vector with NAs
v <- c(1, 2, NA, 4, 5)

# Remove NA values
clean_v <- na.omit(v)
print(clean_v)
```
Expected Output:
```text
[1] 1 2 4 5
```

## 14. Date Manipulation
Working with dates.

```r
# Current date
current_date <- Sys.Date()
print(current_date)

# Convert string to Date
date_str <- "2025-01-22"
date_obj <- as.Date(date_str)
print(date_obj)
```
Expected Output:
```text
2025-01-25
2025-01-22
```

## 15. String Manipulation
Manipulating strings.

```r
# String operations
str <- "Hello, R Programming!"
substring_str <- substr(str, 1, 5)
upper_str <- toupper(str)

print(substring_str)
print(upper_str)
```
Expected Output:
```text
Hello
HELLO, R PROGRAMMING!
```

## 16. Factor Variables
Creating and manipulating factor variables.

```r
# Create a factor variable
factor_var <- factor(c("Low", "High", "Medium", "Low", "High"))

# Print the factor variable
print(factor_var)
```
Expected Output:
```text
[1] Low   High  Medium Low   High 
Levels: High Low Medium
```

## 17. Creating a Bar Plot
Creating a simple bar plot in R.

```r
# Data for bar plot
data <- c(10, 15, 20, 25)

# Bar plot
barplot(data)
```
Expected Output:
```text
A bar plot is displayed with the provided data.
```

## 18. Basic Linear Regression
Performing linear regression in R.

```r
# Simple linear regression
x <- c(1, 2, 3, 4, 5)
y <- c(2, 4, 6, 8, 10)

model <- lm(y ~ x)
summary(model)
```
Expected Output:
```text
Call:
lm(formula = y ~ x)

Residuals:
         1          2          3          4          5 
 4.367e-16 -8.276e-16  3.028e-16  1.303e-16 -4.222e-17 

Coefficients:
              Estimate Std. Error    t value Pr(>|t|)    
(Intercept) -1.589e-15  6.013e-16 -2.642e+00   0.0775 .  
x            2.000e+00  1.813e-16  1.103e+16   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 5.733e-16 on 3 degrees of freedom
Multiple R-squared:      1,     Adjusted R-squared:      1 
F-statistic: 1.217e+32 on 1 and 3 DF,  p-value: < 2.2e-16
```
