---
title: Basic Types
weight: 20
menu:
  notes:
    name: Basic Types
    identifier: notes-r-basics-types
    parent: notes-r-basics
    weight: 20
---

<!-- String Type -->
{{< note title="Strings">}}

```r
str_single <- "Hello"
str_multiline <- "Multiline\nstring"
toupper(str_multiline)
```

Useful string manipulation with `stringr`:

```r
library(stringr)

name <- "John Doe"
str_to_lower(name)  # "john doe"
str_split(name, " ")  # List of "John" and "Doe"
```

{{< /note >}}

<!-- Number Types -->
{{< note title="Numbers">}}

```r
integer <- 42L
floating_point <- 3.14
complex_number <- complex(real = 2, imaginary = 3)

# Converting between types
float_to_int <- as.integer(3.7)  # 3
```

Working with vectors:

```r
nums <- c(1, 2, 3, 4, 5)
mean(nums)  # 3
sum(nums)   # 15
```

{{< /note >}}
