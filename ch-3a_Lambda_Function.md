# Lambda Functions in Python

## What is a Lambda Function?

A **lambda function** in Python is a small anonymous function created using the `lambda` keyword.

Unlike normal functions defined with `def`, lambda functions:
- have no name
- are usually written in one line
- can take multiple arguments
- return a single expression automatically

---

## Syntax

```python
lambda arguments: expression
```

### Example

```python
square = lambda x: x * x

print(square(5))
```

### Output

```python
25
```

---

# Why Use Lambda Functions?

Lambda functions are useful when:
- you need a short function temporarily
- passing functions as arguments
- working with functions like `map()`, `filter()`, and `sorted()`

They make code concise and readable for simple operations.

---

# Basic Examples

## 1. Adding Two Numbers

```python
add = lambda a, b: a + b

print(add(3, 7))
```

### Output

```python
10
```

---

## 2. Checking Even Numbers

```python
is_even = lambda x: x % 2 == 0

print(is_even(8))
print(is_even(5))
```

### Output

```python
True
False
```

---

# Lambda with Built-in Functions

## 1. Using `map()`

`map()` applies a function to every item in an iterable.

```python
numbers = [1, 2, 3, 4]

squared = list(map(lambda x: x * x, numbers))

print(squared)
```

### Output

```python
[1, 4, 9, 16]
```

---

## 2. Using `filter()`

`filter()` keeps items that satisfy a condition.

```python
numbers = [1, 2, 3, 4, 5, 6]

evens = list(filter(lambda x: x % 2 == 0, numbers))

print(evens)
```

### Output

```python
[2, 4, 6]
```

---

## 3. Using `sorted()`

```python
students = [
    ("Rahul", 75),
    ("Anita", 92),
    ("Vikram", 85)
]

sorted_students = sorted(
    students,
    key=lambda student: student[1]
)

print(sorted_students)
```

### Output

```python
[('Rahul', 75), ('Vikram', 85), ('Anita', 92)]
```

---

# Lambda vs Normal Function

## Normal Function

```python
def multiply(x, y):
    return x * y
```

## Lambda Function

```python
multiply = lambda x, y: x * y
```

Both work similarly, but lambda is shorter.

---

# Advantages of Lambda Functions

- Short and concise
- Useful for quick operations
- Cleaner code in higher-order functions
- Avoids defining unnecessary named functions

---

# Limitations of Lambda Functions

- Only one expression allowed
- Cannot contain multiple statements
- Harder to debug if overused
- Not ideal for complex logic

---

# Best Practices

## Use Lambda Functions For

- Simple operations
- Short temporary functions
- Functional programming tasks

## Avoid Lambda Functions For

- Large logic blocks
- Complicated conditions
- Functions requiring documentation

---

# Practice Exercises

1. Create a lambda function to calculate the cube of a number.
2. Use `filter()` with lambda to find numbers greater than 10.
3. Sort a list of dictionaries by age using lambda.
4. Use `map()` with lambda to convert strings to uppercase.

---

# Summary

Lambda functions in Python:
- are anonymous functions
- are written using the `lambda` keyword
- are best for short, simple tasks
- work commonly with `map()`, `filter()`, and `sorted()`

They help make Python code compact and expressive when used properly.
