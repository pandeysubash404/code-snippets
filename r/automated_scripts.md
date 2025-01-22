# Automated Programming Scripts

This document contains 16 automated R programming snippets that demonstrate various automation tasks such as data manipulation, file handling, visualization, and more.

---

## 1. Automating Data Import from CSV
Automatically read CSV files from a specified directory.

Create a file `data.csv` in same directory.
```csv
   Name Age Gender
1  Ram  28   Male
2  Sita  22 Female
3  Gita  31 Female
```
`main.r` file program:
```r
# Define file path
file_path <- "data.csv"

# Read CSV file
data <- read.csv(file_path)
print(head(data))
```
**Example Run**
```text
   Name Age Gender
1  Ram  28   Male
2  Sita  22 Female
3  Gita  31 Female
```

## 2. Automating Data Export to CSV
Export a data frame to a CSV file.

```r
# Define data frame
data <- data.frame(Name = c("Ram", "Sita", "Gita"), Age = c(28, 22, 31), Gender = c("Male", "Female", "Female"))

# Write to CSV
tryCatch({
  write.csv(data, "output.csv", row.names = FALSE)
  print("File created output.csv")
}, error = function(e) {
  print("Cannot create file output.csv")
})
```
**Example Run**
```text
File created output.csv
```

## 3. Automated Plot Creation
Automatically generate and save a plot from a dataset.

```r
# Install ggplot2 if not installed
# install.packages("ggplot2")

# Load necessary library
library(ggplot2)

# Generate a plot
ggplot(data, aes(x = Age, y = Gender)) + 
  geom_point() + 
  labs(title = "Age vs Gender")

# Save plot to file
ggsave("plot.png")
```
**Example Run**
```text
A PNG file named "plot.png" is saved in the working directory.
```

## 4. Automating Email Notifications
Automate the process of sending email notifications.

```r
# Install and load mailR package
# install.packages("mailR")
library(mailR)

# Send email
send.mail(from = "your_email@example.com",
          to = "recipient@example.com",
          subject = "Automated R Script Execution",
          body = "Your R script has completed successfully.",
          smtp = list(host.name = "smtp.example.com", port = 25, user.name = "your_email@example.com", passwd = "password", ssl = TRUE),
          authenticate = TRUE,
          send = TRUE)
```
**Example Run**
```text
An email notification is sent to the recipient.
```

## 5. Automating Data Cleaning
Automate missing value handling in datasets.

```r
# Define data frame
data <- data.frame(Name = c("Ram", "Sita", "Gita"), Age = c(28, NA, 31), Gender = c("Male", "Female", "Female"))

# Replace missing NA values with mean
data$Age[is.na(data$Age)] <- mean(data$Age, na.rm = TRUE)
print(data)
```
**Example Run**
```text
  Name  Age Gender
1  Ram 28.0   Male
2 Sita 29.5 Female
3 Gita 31.0 Female
```

## 6. Automating Data Transformation
Automating data transformation with `dplyr` functions.

```r
# Install and load dplyr (uncomment if necessary)
# install.packages("dplyr")
library(dplyr)

# Define data frame
data <- data.frame(Name = c("Ram", "Sita", "Gita"), Age = c(28, 29, 31), Gender = c("Male", "Female", "Female"))

# Automate data transformation
data_transformed <- data %>%
  mutate(Age = ifelse(is.na(Age), 0, Age) * 2) %>%
  filter(Age > 50)

print(data_transformed)
```
**Example Run**
```text
Transformed data with Age column multiplied by 2 and filtered by Age > 50.
```

## 7. Automated Web Scraping
Automate web scraping to collect data from a website.

```r
# Install rvest package
# install.packages("rvest")
library(rvest)

# Scrape data from a website
url <- "https://example.com"
web_page <- read_html(url)
data <- web_page %>%
  html_nodes("p") %>%
  html_text()

print(data)
```
**Example Run**
```text
Text data from all <p> tags on the webpage is printed.
```

## 8. Automating Data Aggregation
Summarizing and aggregating data automatically.

```r
# Define data frame
data <- data.frame(Name = c("Ram", "Sita", "Gita"), Age = c(28, NA, 31), Gender = c("Male", "Female", "Female"))

# Aggregate data
agg_data <- data %>%
  group_by(Gender) %>%
  summarize(Average_Age = mean(Age))

print(agg_data)
```
**Example Run**
```text
  Gender Average_Age
1 Female        26.5
2   Male        28.0
```

## 9. Automating Report Generation
Automatically generate a PDF report with summary statistics.

```r
# Install rmarkdown
# install.packages("rmarkdown")
library(rmarkdown)

# Render report
rmarkdown::render("report.Rmd", output_format = "pdf_document")
```
**Example Run**
```text
A PDF report named "report.pdf" is generated with summary statistics.
```

## 10. Automating Data Merging
Automatically merge two datasets by a common key.

```r
# Merge two data frames
data1 <- data.frame(ID = 1:3, Name = c("Ram", "Sita", "Gita"))
data2 <- data.frame(ID = 1:3, Age = c(28, 22, 31))

merged_data <- merge(data1, data2, by = "ID")
print(merged_data)
```
**Example Run**
```text
  ID  Name Age
1  1  Ram  28
2  2  Sita  22
3  3  Gita  31
```

## 11. Automating Data Sampling
Automate random sampling of data from a larger dataset.

```r
# Create a larger dataset
large_data <- data.frame(ID = 1:1000, Name = sample(letters, 1000, replace = TRUE))

# Random sample of 100 rows
sampled_data <- large_data[sample(1:nrow(large_data), 100), ]
print(head(sampled_data))
```
**Example Run**
```text
ID    Name
21     r
1      u
```

## 12. Automating Model Training
Automating the training of a machine learning model.

```r
# Install and load caret (uncomment if necessary)
# install.packages("caret")
library(caret)

# Sample data
data(iris)

# Train a model
model <- train(Species ~ ., data = iris, method = "rf")
print(model)
```
**Example Run**
```text
Trained Random Forest model for classification of Species in the iris dataset.
```

## 13. Automating Backtesting a Strategy
Automating backtesting of a simple trading strategy.

```r
# Sample data
data <- data.frame(Date = as.Date('2025-01-01') + 0:10, Price = rnorm(11, 100, 5))

# Backtesting strategy: Buy if Price > 100, sell if Price < 95
data$Action <- ifelse(data$Price > 100, "Buy", ifelse(data$Price < 95, "Sell", "Hold"))
print(data)
```
**Example Run**
```text
  Date       Price  Action
1 2025-01-01 100.33 Hold
2 2025-01-02 98.15 Hold
3 2025-01-03 102.87 Buy
...
```

## 14. Automating Report Analysis
Automatically analyze a report.

```r
# Create sample data
report <- data.frame(
  ID = c(1, 2, 3, 4, 5),
  Name = c("Ram", "Shyam", "Hari", "Sita", "Gita"),
  Age = c(28, 22, 35, 40, 26),
  Score = c(88, 92, 85, 76, 95)
)

# Write data to CSV
write.csv(report, "report.csv", row.names = FALSE)

# Read the report data
report <- read.csv("report.csv")

# Automate analysis
summary_stats <- summary(report)
print(summary_stats)
```
**Example Run**
```text
       ID        Name                Age           Score     
 Min.   :1   Length:5           Min.   :22.0   Min.   :76.0  
 1st Qu.:2   Class :character   1st Qu.:26.0   1st Qu.:85.0  
 Median :3   Mode  :character   Median :28.0   Median :88.0  
 Mean   :3                      Mean   :30.2   Mean   :87.2  
 3rd Qu.:4                      3rd Qu.:35.0   3rd Qu.:92.0  
 Max.   :5                      Max.   :40.0   Max.   :95.0 
```

## 15. Automating Log File Monitoring
Automatically monitor and analyze a log file for specific events.

```r
# Create sample data (as a vector of strings)
report <- c(
  "INFO: Starting the process.",
  "ERROR: Could not connect to the database.",
  "INFO: Process completed successfully.",
  "ERROR: File not found.",
  "WARNING: Low disk space.",
  "ERROR: Permission denied.",
  "INFO: Process finished."
)

# Write data to a text file (log.txt)
writeLines(report, "log.txt")

# Read log file
log_data <- readLines("log.txt")

# Check for errors (lines containing "ERROR")
errors <- grep("ERROR", log_data, value = TRUE)

# Print the errors
print(errors)
```
**Example Run**
```text
[1] "ERROR: Could not connect to the database."
[2] "ERROR: File not found."
[3] "ERROR: Permission denied."
```

## 16. Automating Data Export to Excel
Automate data export to Excel file.

```r
# Install and load openxlsx package
# install.packages("openxlsx")
library(openxlsx)

# Create a workbook and add data
wb <- createWorkbook()
addWorksheet(wb, "Sheet1")
writeData(wb, "Sheet1", data)

# Save workbook to file
saveWorkbook(wb, "output.xlsx", overwrite = TRUE)
```
**Example Run**
```text
An Excel file named "output.xlsx" is created and saved.
```
