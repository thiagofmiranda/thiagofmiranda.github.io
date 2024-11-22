---
title: Basic Types
weight: 20
menu:
  notes:
    name: Basic Types
    identifier: notes-python-basics-types
    parent: notes-python-basics
    weight: 20
---

<!-- String Type -->
{{< note title="Strings">}}

```python
str_single = "Hello"
str_multiline = """Multiline
string"""
print(str_multiline.upper())
```

Useful string methods:

```python
name = "John Doe"
print(name.lower())  # john doe
print(name.split())  # ['John', 'Doe']
```

{{< /note >}}

<!-- Number Types -->
{{< note title="Numbers">}}

```python
integer = 42
floating_point = 3.14
complex_number = 2 + 3j

# Converting between types
float_to_int = int(3.7)  # 3
```

Working with NumPy for advanced number manipulation:

```python
import numpy as np
array = np.array([1, 2, 3])
print(array.mean())  # 2.0
```

{{< /note >}}