---
title: File Manipulation
weight: 40
menu:
  notes:
    name: File Manipulation
    identifier: notes-python-advanced-file-manipulation
    parent: notes-python-advanced
    weight: 10
---

<!-- File Operations -->
{{< note title="File Operations">}}

Reading and writing text files:

```python
with open("example.txt", "w") as file:
    file.write("Hello, File!")

with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

Handling CSV files with pandas:

```python
import pandas as pd

# Reading a CSV file
data = pd.read_csv("data.csv")
print(data.head())

# Writing a CSV file
data.to_csv("output.csv", index=False)
```

{{< /note >}}