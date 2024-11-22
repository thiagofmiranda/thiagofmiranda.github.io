---
title: File Manipulation
weight: 40
menu:
  notes:
    name: File Manipulation
    identifier: notes-r-advanced-file-manipulation
    parent: notes-r-advanced
    weight: 10
---
<!-- File Operations -->
{{< note title="File Operations">}}

Reading and writing text files:

```r
# Writing to a file
writeLines("Hello, File!", "example.txt")

# Reading from a file
content <- readLines("example.txt")
print(content)
```

Handling CSV files:

```r
# Reading a CSV file
data <- read.csv("data.csv")
head(data)

# Writing a CSV file
write.csv(data, "output.csv", row.names = FALSE)
```

Working with Excel files using `readxl` and `writexl`:

```r
library(readxl)
library(writexl)

# Reading Excel
data <- read_excel("data.xlsx")
print(data)

# Writing Excel
write_xlsx(data, "output.xlsx")
```

{{< /note >}}
