---
title: Flow Control
weight: 30
menu:
  notes:
    name: Flow Control
    identifier: notes-python-basics-flow-control
    parent: notes-python-basics
    weight: 30
---

<!-- Condition -->
{{< note title="Condition">}}

```python
day = "sunday"

if day in ["sunday", "saturday"]:
    print("Rest!")
elif day == "monday" and is_tired():
    print("Groan!")
else:
    print("Work!")
```

Example with try/except:

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
finally:
    print("Cleanup complete.")
```
{{< /note >}}

<!-- Loops -->
{{< note title="Loops">}}

For loop example:

```python
for i in range(5):
    print(f"Iteration {i}")
```

While loop example:

```python
count = 0
while count < 5:
    print(f"Count is {count}")
    count += 1
```
{{< /note >}}