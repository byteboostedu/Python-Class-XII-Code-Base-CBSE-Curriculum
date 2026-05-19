# Python Libraries  
## CBSE Class 12 Computer Science Notes

---

# Introduction to Python Libraries

A **library** in Python is a collection of pre-written programs or modules that help programmers perform tasks easily without writing code from scratch.

Python provides many built-in and external libraries for:
- Mathematics
- Data handling
- Graphics
- File operations
- Web development
- Data analysis

Libraries save time and make programming easier and faster.

---

# Types of Python Libraries

## 1. Built-in Libraries

These libraries come pre-installed with Python.

Examples:
- `math`
- `random`
- `statistics`
- `os`

---

## 2. External Libraries

These libraries need to be installed separately using `pip`.

Examples:
- `numpy`
- `pandas`
- `matplotlib`

---

# Importing a Library

Libraries are imported using the `import` keyword.

## Syntax

```python
import library_name
```

### Example

```python
import math

print(math.sqrt(25))
```

### Output

```python
5.0
```

---

# Common Python Libraries for CBSE Class 12

# 1. Math Library

The `math` library provides mathematical functions.

## Common Functions

| Function | Description |
|---|---|
| `sqrt()` | Finds square root |
| `pow()` | Calculates power |
| `ceil()` | Rounds upward |
| `floor()` | Rounds downward |

---

## Example

```python
import math

print(math.sqrt(64))
print(math.pow(2, 3))
```

### Output

```python
8.0
8.0
```

---

# 2. Random Library

The `random` library is used to generate random numbers.

## Common Functions

| Function | Description |
|---|---|
| `randint(a, b)` | Random integer between a and b |
| `choice()` | Selects random item |
| `shuffle()` | Shuffles list items |

---

## Example

```python
import random

print(random.randint(1, 10))
```

### Sample Output

```python
7
```

---

# 3. Statistics Library

The `statistics` library performs statistical calculations.

## Common Functions

| Function | Description |
|---|---|
| `mean()` | Average value |
| `median()` | Middle value |
| `mode()` | Most repeated value |

---

## Example

```python
import statistics

data = [10, 20, 30, 40]

print(statistics.mean(data))
```

### Output

```python
25
```

---

# 4. OS Library

The `os` library helps interact with the operating system.

## Uses

- Creating folders
- Renaming files
- Checking current directory

---

## Example

```python
import os

print(os.getcwd())
```

This displays the current working directory.

---

# Python Package Manager (pip)

`pip` is used to install external Python libraries.

## Syntax

```bash
pip install library_name
```

### Example

```bash
pip install numpy
```

---

# Advantages of Python Libraries

- Reduces coding effort
- Saves development time
- Provides reusable code
- Improves program efficiency
- Makes complex tasks easier

---

# Difference Between Module and Library

| Module | Library |
|---|---|
| Single Python file | Collection of modules |
| Smaller unit | Larger collection |
| Example: `math.py` | Example: `numpy` |

---

# Important Terms

| Term | Meaning |
|---|---|
| Module | A Python file containing code |
| Library | Collection of modules |
| Package | Organized collection of Python modules |

---

# Practice Questions

## Short Answer Questions

1. What is a Python library?
2. Write the syntax to import a library.
3. Name any two built-in Python libraries.
4. What is the use of the `random` library?

---

## Programming Questions

### 1. Find Square Root

```python
import math

num = 49
print(math.sqrt(num))
```

---

### 2. Generate Random Number

```python
import random

print(random.randint(1, 100))
```

---

### 3. Calculate Mean

```python
import statistics

numbers = [5, 10, 15, 20]

print(statistics.mean(numbers))
```

---

# Summary

- Python libraries are collections of reusable code.
- Libraries simplify programming tasks.
- Built-in libraries are available by default.
- External libraries can be installed using `pip`.
- Common CBSE libraries include:
  - `math`
  - `random`
  - `statistics`
  - `os`

Python libraries help programmers write efficient and powerful programs easily.
