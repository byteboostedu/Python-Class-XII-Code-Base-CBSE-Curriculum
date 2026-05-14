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
# Using `if __name__ == "__main__":` in Python

## Introduction

In Python, the statement:

```python
if __name__ == "__main__":
```

is one of the most commonly used patterns in professional Python development.

It helps control whether code should:

* Run directly
* Be imported safely into another file

This pattern improves:

* Code organization
* Reusability
* Testing
* Maintainability

---

# Understanding `__name__`

Every Python file automatically gets a built-in variable called:

```python
__name__
```

Python assigns a value to it depending on how the file is used.

---

## When a Python File Runs Directly

Example:

```bash
python app.py
```

Inside `app.py`:

```python
print(__name__)
```

Output:

```python
__main__
```

---

## When a Python File Is Imported

Example:

```python
import app
```

Now inside `app.py`:

```python
print(__name__)
```

Output:

```python
app
```

The filename becomes the module name.

---

# Basic Syntax

```python
def main():
    print("Program started")


if __name__ == "__main__":
    main()
```

---

# How It Works

Python executes files from top to bottom.

When Python reaches:

```python
if __name__ == "__main__":
```

it checks:

> “Am I running this file directly?”

If yes:

```python
main()
```

executes.

If no (the file was imported), the block is skipped.

---

# Why This Pattern Is Important

## 1. Prevents Automatic Execution During Import

Without protection:

```python
print("Application Started")
```

This runs immediately whenever the file is imported.

That can create unwanted side effects.

---

## 2. Makes Code Reusable

Functions can be imported without executing test or demo code.

---

## 3. Improves Project Structure

Professional Python applications organize execution inside `main()`.

---

# Example Without `if __name__ == "__main__"`

## File: `math_utils.py`

```python
print("Math module loaded")


def add(a, b):
    return a + b
```

## File: `test.py`

```python
import math_utils
```

## Output

```python
Math module loaded
```

Even though we only imported the module.

---

# Example With `if __name__ == "__main__"`

## File: `math_utils.py`

```python
def add(a, b):
    return a + b


def main():
    print("Testing add function")
    print(add(2, 3))


if __name__ == "__main__":
    main()
```

## File: `test.py`

```python
import math_utils
```

## Output

```python
# No output
```

The testing code is safely skipped.

---

# Understanding the `main()` Function

The `main()` function is not special in Python.

It is simply a developer convention.

Example:

```python
def main():
    print("Main function running")


if __name__ == "__main__":
    main()
```

---

# Why Use a `main()` Function?

Benefits:

* Cleaner structure
* Easier debugging
* Easier testing
* Better readability
* Avoids large blocks of global code

---

# Recommended Project Structure

```python
def load_data():
    print("Loading data")


def process_data():
    print("Processing data")


def save_results():
    print("Saving results")


def main():
    load_data()
    process_data()
    save_results()


if __name__ == "__main__":
    main()
```

---

# Execution Flow

## Step-by-Step

1. Python reads the file.
2. Functions are defined.
3. Python reaches:

```python
if __name__ == "__main__":
```

4. Python checks the value of `__name__`.
5. If true → `main()` runs.
6. If false → skipped.

---

# Real-World Use Cases

## Scripts

Automation scripts often use:

```python
if __name__ == "__main__":
    main()
```

Examples:

* Data processing
* File automation
* Web scraping
* Command-line tools

---

## Libraries

Libraries should not execute test code when imported.

---

## Unit Testing

```python
def run_tests():
    print("Running tests")


if __name__ == "__main__":
    run_tests()
```

---

# Common Beginner Mistakes

## Mistake 1 — Forgetting Double Underscores

Wrong:

```python
if name == "main":
```

Correct:

```python
if __name__ == "__main__":
```

---

## Mistake 2 — Misspelling `"__main__"`

Wrong:

```python
if __name__ == "__main":
```

Correct:

```python
if __name__ == "__main__":
```

---

## Mistake 3 — Calling `main()` Outside the Condition

Wrong:

```python
main()

if __name__ == "__main__":
```

Correct:

```python
if __name__ == "__main__":
    main()
```

---

# Intermediate Example

```python
def greet(name):
    return f"Hello, {name}"


def main():
    user = input("Enter your name: ")
    print(greet(user))


if __name__ == "__main__":
    main()
```

---

# Advanced Example — Reusable Module

## calculator.py

```python
def add(a, b):
    return a + b


def subtract(a, b):
    return a - b


def main():
    print("Calculator Test")
    print(add(10, 5))
    print(subtract(10, 5))


if __name__ == "__main__":
    main()
```

## another_file.py

```python
import calculator

print(calculator.add(2, 3))
```

## Output

```python
5
```

Notice that the test code inside `calculator.py` does not execute.

---

# Best Practices

## Always Use Functions

Good:

```python
def main():
    pass
```

Bad:

```python
print("Start")
print("Processing")
print("End")
```

---

## Keep `main()` Small

Good:

```python
def main():
    load()
    process()
    save()
```

The `main()` function should coordinate tasks, not contain all logic.

---

# Interview Question

## Question

Why do we use:

```python
if __name__ == "__main__":
```

## Answer

It ensures that specific code runs only when the Python file is executed directly, and not when the file is imported as a module.

---

# Practice Exercises

## Exercise 1

Create a Python file that:

* Defines a function `square(x)`
* Uses `main()` to test the function
* Uses `if __name__ == "__main__"`

---

## Exercise 2

Create:

* `calculator.py`
* `test.py`

Import functions from `calculator.py` into `test.py`.

---

## Exercise 3

Build a program that:

* Takes user input
* Checks whether a number is even or odd
* Uses a `main()` function

---

# Summary

| Concept          | Meaning                          |
| ---------------- | -------------------------------- |
| `__name__`       | Built-in Python variable         |
| `"__main__"`     | Value when file runs directly    |
| `main()`         | Developer-defined entry function |
| Import-safe code | Prevents unwanted execution      |

---

# Final Template

```python
def main():
    print("Application started")


if __name__ == "__main__":
    main()
```

---

# Recommended Learning Path

Next topics to learn:

1. Python modules
2. Python imports
3. Python packages
4. Virtual environments
5. Command-line applications
6. Unit testing
7. Object-oriented programming

---

# Quick Revision

```python
if __name__ == "__main__":
    main()
```

Means:

> “Run this code only if this file is executed directly.”

# Final Tip

> “Good programmers write code that humans can understand.”

Write clean, reusable, and well-documented functions.
