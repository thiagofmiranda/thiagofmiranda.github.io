---
title: Flow Control
weight: 30
menu:
  notes:
    name: Flow Control
    identifier: notes-r-basics-flow-control
    parent: notes-r-basics
    weight: 30
---
<!-- Condition -->
{{< note title="Condition">}}

```r
day <- "sunday"

if (day %in% c("sunday", "saturday")) {
  print("Rest!")
} else if (day == "monday") {
  print("Groan!")
} else {
  print("Work!")
}
```

Using `tryCatch` for error handling:

```r
result <- tryCatch({
  10 / 0
}, warning = function(w) {
  "Warning occurred!"
}, error = function(e) {
  "Error occurred!"
}, finally = {
  print("Cleanup complete.")
})

print(result)
```
{{< /note >}}

<!-- Loops -->
{{< note title="Loops">}}

For loop example:

```r
for (i in 1:5) {
  print(paste("Iteration", i))
}
```

While loop example:

```r
count <- 0
while (count < 5) {
  print(paste("Count is", count))
  count <- count + 1
}
```
{{< /note >}}
