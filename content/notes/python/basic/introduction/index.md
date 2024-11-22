---
title: Introduction
weight: 10
menu:
  notes:
    name: Introduction
    identifier: notes-python-basics-intro
    parent: notes-python-basics
    weight: 10
---
<!-- A Sample Program -->
{{< note title="Hello World">}}
A sample Python program is shown here.

```python
def greet(name):
    return f"Hello, {name}!"

if __name__ == "__main__":
    message = greet("world")
    print(message)
```

Run the program as below:

```bash
$ python hello.py
```
{{< /note >}}