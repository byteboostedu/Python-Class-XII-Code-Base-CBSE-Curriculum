# Python Functions: From Zero to Hero

> A beginner-friendly guide to mastering Python functions, arguments, type hints, and annotations.

---

## Table of Contents

1. [Introduction to Functions](#1-introduction-to-functions)
2. [Why Functions Matter](#2-why-functions-matter)
3. [Creating Your First Function](#3-creating-your-first-function)
4. [Function Syntax](#4-function-syntax)
5. [Parameters vs Arguments](#5-parameters-vs-arguments)
6. [Positional Arguments](#6-positional-arguments)
7. [Keyword Arguments](#7-keyword-arguments)
8. [Default Arguments](#8-default-arguments)
9. [Combining Different Argument Types](#9-combining-different-argument-types)
10. [Return Values](#10-return-values)
11. [Scope and Lifetime of Variables](#11-scope-and-lifetime-of-variables)
12. [The isinstance() Function](#12-the-isinstance-function)
13. [Function Annotations](#13-function-annotations)
14. [Type Hints in Python](#14-type-hints-in-python)
15. [Advanced Function Techniques](#15-advanced-function-techniques)
16. [Best Practices](#16-best-practices)
17. [Common Mistakes](#17-common-mistakes)
18. [Real-World Examples](#18-real-world-examples)
19. [Mini Exercises](#19-mini-exercises)
20. [Conclusion](#20-conclusion)

---

# 1. Introduction to Functions

A **function** is a reusable block of code that performs a specific task.

Instead of writing the same code repeatedly, we define a function once and reuse it whenever needed.

## Example

```python
def greet():
    print("Hello, World!")

greet()
```

### Output

```text
Hello, World!
```

---

# 2. Why Functions Matter

Functions help:

- Reduce code duplication
- Improve readability
- Organize logic
- Simplify debugging
- Encourage code reuse

---

# 3. Creating Your First Function

## Syntax

```python
def function_name():
    # code block
```

## Example

```python
def say_hello():
    print("Hello Python!")

say_hello()
```

---

# 4. Function Syntax

A Python function consists of:

```python
def add(a, b):
    return a + b
```

## Breakdown

| Component | Meaning |
|------------|----------|
| `def` | Keyword to define a function |
| `add` | Function name |
| `(a, b)` | Parameters |
| `return` | Sends value back |

---

# 5. Parameters vs Arguments

## Parameters

Variables defined in the function declaration.

```python
def greet(name):
    print(name)
```

`name` is a parameter.

---

## Arguments

Actual values passed to the function.

```python
greet("Alice")
```

`"Alice"` is an argument.

---

# 6. Positional Arguments

Arguments assigned based on their position.

## Example

```python
def introduce(name, age):
    print(f"My name is {name} and I am {age} years old.")

introduce("Rahul", 25)
```

### Output

```text
My name is Rahul and I am 25 years old.
```

---

## Incorrect Order

```python
introduce(25, "Rahul")
```

### Output

```text
My name is 25 and I am Rahul years old.
```

Position matters.

---

# 7. Keyword Arguments

Keyword arguments specify parameter names explicitly.

## Example

```python
def introduce(name, age):
    print(f"{name} is {age} years old.")

introduce(age=25, name="Rahul")
```

### Output

```text
Rahul is 25 years old.
```

---

## Advantages

- Improves readability
- Avoids positional confusion
- Allows flexible ordering

---

# 8. Default Arguments

Default values are used when no argument is provided.

## Example

```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()
greet("Alice")
```

### Output

```text
Hello, Guest!
Hello, Alice!
```

---

## Multiple Default Arguments

```python
def power(base, exponent=2):
    return base ** exponent

print(power(5))
print(power(5, 3))
```

### Output

```text
25
125
```

---

# 9. Combining Different Argument Types

Python allows positional, keyword, and default arguments together.

## Example

```python
def order(item, quantity=1, price=100):
    print(item, quantity, price)

order("Laptop")
order("Mouse", 2)
order(item="Keyboard", quantity=3, price=500)
```

---

# 10. Return Values

Functions can return values using `return`.

## Example

```python
def multiply(a, b):
    return a * b

result = multiply(4, 5)

print(result)
```

### Output

```text
20
```

---

## Returning Multiple Values

```python
def calculate(a, b):
    return a + b, a - b

sum_result, diff_result = calculate(10, 5)

print(sum_result)
print(diff_result)
```

---

# 11. Scope and Lifetime of Variables

## Local Variables

Defined inside functions.

```python
def demo():
    x = 10
    print(x)

demo()
```

---

## Global Variables

Defined outside functions.

```python
x = 100

def show():
    print(x)

show()
```

---

# 12. The `isinstance()` Function

The `isinstance()` function checks whether an object belongs to a specific type.

## Syntax

```python
isinstance(object, classinfo)
```

---

## Example

```python
x = 10

print(isinstance(x, int))
```

### Output

```text
True
```

---

## Checking Multiple Types

```python
value = 3.14

print(isinstance(value, (int, float)))
```

### Output

```text
True
```

---

## Using `isinstance()` in Functions

```python
def process(data):
    if isinstance(data, str):
        print("String detected")
    elif isinstance(data, int):
        print("Integer detected")
    else:
        print("Unknown type")

process("Python")
process(100)
```

---

# 13. Function Annotations

Annotations provide metadata about parameters and return values.

## Example

```python
def add(a: int, b: int) -> int:
    return a + b
```

---

## Accessing Annotations

```python
print(add.__annotations__)
```

### Output

```python
{'a': <class 'int'>, 'b': <class 'int'>, 'return': <class 'int'>}
```

---

# 14. Type Hints in Python

Type hints improve readability and help IDEs/static analyzers.

## Basic Type Hints

```python
def greet(name: str) -> str:
    return f"Hello {name}"
```

---

## List Type Hints

```python
from typing import List

def total(numbers: List[int]) -> int:
    return sum(numbers)
```

---

## Dictionary Type Hints

```python
from typing import Dict

def student() -> Dict[str, int]:
    return {"Math": 90, "Science": 95}
```

---

## Optional Type

```python
from typing import Optional

def get_name(name: Optional[str] = None):
    print(name)
```

---

# 15. Advanced Function Techniques

## Arbitrary Positional Arguments (`*args`)

```python
def add(*numbers):
    return sum(numbers)

print(add(1, 2, 3, 4))
```

---

## Arbitrary Keyword Arguments (`**kwargs`)

```python
def details(**info):
    for key, value in info.items():
        print(key, value)

details(name="Alice", age=25)
```

---

## Lambda Functions

```python
square = lambda x: x * x

print(square(5))
```

---

# 16. Best Practices

## Use Meaningful Names

✅ Good

```python
def calculate_area():
    pass
```

❌ Bad

```python
def ca():
    pass
```

---

## Keep Functions Small

A function should do one task well.

---

## Add Documentation

```python
def add(a, b):
    """
    Returns sum of two numbers.
    """
    return a + b
```

---

## Use Type Hints

```python
def divide(a: float, b: float) -> float:
    return a / b
```

---

# 17. Common Mistakes

## Forgetting Return

```python
def add(a, b):
    a + b
```

This returns `None`.

---

## Mutable Default Arguments

❌ Dangerous

```python
def append_item(item, items=[]):
    items.append(item)
    return items
```

✅ Correct

```python
def append_item(item, items=None):
    if items is None:
        items = []

    items.append(item)
    return items
```

---

# 18. Real-World Examples

## Example: Calculator

```python
def calculator(a: float, b: float, operation: str = "+") -> float:

    if operation == "+":
        return a + b

    elif operation == "-":
        return a - b

    elif operation == "*":
        return a * b

    elif operation == "/":
        return a / b

    else:
        return 0
```

---

## Example: User Validation

```python
def validate_age(age):

    if not isinstance(age, int):
        return "Invalid type"

    if age < 18:
        return "Minor"

    return "Adult"
```

---

# 19. Mini Exercises

## Exercise 1

Create a function that returns the cube of a number.

---

## Exercise 2

Create a function using default arguments to greet users.

---

## Exercise 3

Write a function that accepts arbitrary keyword arguments.

---

## Exercise 4

Use `isinstance()` to validate input before division.

---

# 20. Conclusion

You have learned:

- Function basics
- Positional arguments
- Keyword arguments
- Default arguments
- `isinstance()`
- Function annotations
- Type hints
- Advanced argument handling
- Best practices

Mastering functions is one of the most important steps toward becoming a strong Python developer.

---

# Bonus Challenge

Build a mini project using everything learned:

- User input
- Functions
- Type hints
- Validation
- Default arguments
- `isinstance()`

## Ideas

- Calculator
- Student Management System
- Expense Tracker
- Quiz App
- Banking System

---

# Final Tip

> “Good programmers write code that humans can understand.”

Write clean, reusable, and well-documented functions.
