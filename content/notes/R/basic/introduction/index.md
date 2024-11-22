---
title: Introduction
weight: 10
menu:
  notes:
    name: Introduction
    identifier: notes-r-basics-intro
    parent: notes-r-basics
    weight: 10
---
<!-- A Sample Program -->
{{< note title="Hello World">}}
A sample R program is shown here.

```R
greet <- function(name) {
  paste("Hello,", name, "!")
}

message <- greet("world")
print(message)
```
{{< /note >}}