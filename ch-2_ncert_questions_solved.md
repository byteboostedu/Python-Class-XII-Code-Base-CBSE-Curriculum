# Python Exception Handling Exercises — Answers

---

# 1. “Every syntax error is an exception but every exception cannot be a syntax error.” Justify the statement.

## Answer

A **Syntax Error** occurs when the rules of Python grammar are violated.

### Example

```python
if True
    print("Hello")
```

### Output

```text
SyntaxError: expected ':'
```

Syntax errors are detected before program execution.

---

An **Exception** occurs during program execution (runtime).

### Example

```python
print(10 / 0)
```

### Output

```text
ZeroDivisionError: division by zero
```

---

## Justification

- Every syntax error is treated as an exception by Python.
- But all exceptions are not syntax errors because many exceptions occur during runtime.

### Examples of Runtime Exceptions

- `ZeroDivisionError`
- `ValueError`
- `NameError`
- `TypeError`

Therefore:

> Every syntax error is an exception, but every exception is not a syntax error.

---

# 2. When are the following built-in exceptions raised? Give examples.

---

# a) ImportError

## Definition

Raised when Python cannot import a module.

## Example

```python
import abcxyz
```

### Output

```text
ModuleNotFoundError: No module named 'abcxyz'
```

---

# b) IOError

## Definition

Raised when input/output operation fails.

## Example

```python
file = open("unknown.txt")
```

### Output

```text
FileNotFoundError: [Errno 2] No such file or directory
```

---

# c) NameError

## Definition

Raised when a variable is not defined.

## Example

```python
print(total)
```

### Output

```text
NameError: name 'total' is not defined
```

---

# d) ZeroDivisionError

## Definition

Raised when division by zero occurs.

## Example

```python
print(100 / 0)
```

### Output

```text
ZeroDivisionError: division by zero
```

---

# 3. What is the use of a `raise` statement? Write a code to accept two numbers and display the quotient. Appropriate exception should be raised if denominator is zero.

---

# Answer

The `raise` statement is used to manually generate an exception.

It helps programmers:

- Validate conditions
- Prevent invalid operations
- Create custom error handling

---

# Program

```python
try:

    num1 = int(input("Enter numerator: "))
    num2 = int(input("Enter denominator: "))

    if num2 == 0:
        raise ZeroDivisionError("Denominator cannot be zero")

    quotient = num1 / num2

    print("Quotient:", quotient)

except ZeroDivisionError as e:
    print(e)
```

---

# Output

```text
Enter numerator: 10
Enter denominator: 0
Denominator cannot be zero
```

---

# 4. Use `assert` statement in Question No. 3 to test the division expression in the program.

---

# Answer

## Program Using `assert`

```python
try:

    num1 = int(input("Enter numerator: "))
    num2 = int(input("Enter denominator: "))

    assert num2 != 0, "Denominator cannot be zero"

    quotient = num1 / num2

    print("Quotient:", quotient)

except AssertionError as e:
    print(e)
```

---

# Output

```text
Enter numerator: 20
Enter denominator: 0
Denominator cannot be zero
```

---

# 5. Define the following

---

# a) Exception Handling

## Definition

Exception handling is the process of detecting and managing runtime errors to prevent program crashes.

---

# b) Throwing an Exception

## Definition

Throwing an exception means generating an error intentionally using the `raise` statement.

## Example

```python
raise ValueError("Invalid value")
```

---

# c) Catching an Exception

## Definition

Catching an exception means handling the error using `try-except` blocks.

## Example

```python
try:
    print(10 / 0)

except ZeroDivisionError:
    print("Cannot divide by zero")
```

---

# 6. Explain catching exceptions using `try` and `except` block.

---

# Answer

The `try` block contains risky code that may generate exceptions.

The `except` block handles the exception safely.

---

# Syntax

```python
try:
    # risky code

except ExceptionName:
    # handling code
```

---

# Example

```python
try:

    number = int(input("Enter number: "))
    result = 100 / number

    print(result)

except ZeroDivisionError:
    print("Division by zero is not allowed")

except ValueError:
    print("Please enter valid integer")
```

---

# Working

1. Python executes code inside `try`
2. If error occurs:
   - Remaining code stops
   - Matching `except` block executes
3. Program continues normally

---

# 7. Fill in the blanks

---

# Correct Program

```python
print("Learning Exceptions...")

try:

    num1 = int(input("Enter the first number: "))
    num2 = int(input("Enter the second number: "))

    quotient = (num1 / num2)

    print("Both the numbers entered were correct")

except ValueError:
    print("Please enter only numbers")

except ZeroDivisionError:
    print("Number 2 should not be zero")

else:
    print("Great... you are a good programmer")

finally:
    print("JOB OVER... GO GET SOME REST")
```

---

# Filled Answers

| Blank | Correct Answer |
|-------|----------------|
| `except ________:` | `ValueError` |
| `except ________:` | `ZeroDivisionError` |
| `________:` | `finally` |

---

# 8. Write a code where wrong numbers are given to methods like `sqrt()` or `pow()`. Use exception handling to catch `ValueError`.

---

# Answer

## Program

```python
import math

try:

    number = int(input("Enter a number: "))

    result = math.sqrt(number)

    print("Square Root:", result)

except ValueError:
    print("Cannot find square root of negative number")
```

---

# Output

```text
Enter a number: -25
Cannot find square root of negative number
```

---

# Another Example with `pow()`

```python
import math

try:

    result = math.pow("a", 2)

    print(result)

except TypeError:
    print("Invalid arguments for pow()")
```

---

# 9. What is the use of `finally` clause? Use `finally` clause in Question No. 7.

---

# Answer

The `finally` block is used to execute important code regardless of whether exception occurs or not.

It is commonly used for:

- Closing files
- Releasing resources
- Database cleanup
- Final execution steps

---

# Example Using `finally`

```python
try:

    num1 = int(input("Enter first number: "))
    num2 = int(input("Enter second number: "))

    result = num1 / num2

    print("Result:", result)

except ZeroDivisionError:
    print("Cannot divide by zero")

except ValueError:
    print("Invalid input")

finally:
    print("Program execution completed")
```

---

# Key Point

The `finally` block always executes whether:

- Exception occurs
- Exception does not occur
- Program succeeds
- Program fails

---

# Final Summary

In these exercises, you learned:

- Syntax errors
- Runtime exceptions
- Built-in exceptions
- `try-except`
- `raise`
- `assert`
- `finally`
- Exception handling techniques
- Mathematical exceptions

---

# Final Tip

> “Exception handling makes programs robust, reliable, and user-friendly.”

Always write safe code that can gracefully handle unexpected situations.
