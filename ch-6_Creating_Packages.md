# Python Package Creation Guide

A beginner-friendly guide to creating a normal Python package using `__init__.py`, structured professionally for GitHub.

---

# Table of Contents

1. Introduction
2. What is a Python Package?
3. Package Structure
4. Understanding `__init__.py`
5. Creating Your First Package
6. Import Methods
7. Subpackages
8. Best Practices
9. Adding a README
10. Adding a License
11. Creating `.gitignore`
12. Virtual Environments
13. Creating `requirements.txt`
14. GitHub Repository Setup
15. Example Complete Project
16. Packaging for PyPI
17. Useful Commands
18. Conclusion

---

# 1. Introduction

Python packages help organize code into reusable modules.

Packages are used in:

* Web development
* Machine learning
* Automation
* APIs
* Scientific computing
* GUI applications

Examples of famous Python packages:

* NumPy
* Pandas
* Flask
* Django

---

# 2. What is a Python Package?

A Python package is a directory containing:

* Python modules (`.py` files)
* A special `__init__.py` file

Example:

```text
mypackage/
│
├── __init__.py
├── math_utils.py
└── string_utils.py
```

---

# 3. Package Structure

Recommended project structure:

```text
myproject/
│
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
├── setup.py
├── pyproject.toml
│
├── mypackage/
│   ├── __init__.py
│   ├── calculator.py
│   └── helper.py
│
└── tests/
    └── test_calculator.py
```

Explanation:

| File/Folder        | Purpose                      |
| ------------------ | ---------------------------- |
| `README.md`        | Project documentation        |
| `LICENSE`          | Open-source license          |
| `requirements.txt` | Dependencies                 |
| `.gitignore`       | Ignore unnecessary files     |
| `setup.py`         | Packaging script             |
| `pyproject.toml`   | Modern package configuration |
| `mypackage/`       | Main package                 |
| `tests/`           | Unit tests                   |

---

# 4. Understanding `__init__.py`

`__init__.py` is a special Python file.

It:

* Marks a directory as a package
* Executes package initialization code
* Controls package imports
* Exposes public APIs

Example:

```python
# mypackage/__init__.py

print("mypackage initialized")
```

When imported:

```python
import mypackage
```

Output:

```text
mypackage initialized
```

---

# 5. Creating Your First Package

## Step 1: Create Package Directory

```bash
mkdir mypackage
```

---

## Step 2: Create `__init__.py`

```bash
touch mypackage/__init__.py
```

---

## Step 3: Create Modules

### calculator.py

```python
# mypackage/calculator.py

def add(a, b):
    return a + b


def subtract(a, b):
    return a - b
```

---

## Step 4: Export Functions in `__init__.py`

```python
# mypackage/__init__.py

from .calculator import add, subtract
```

---

## Step 5: Use the Package

```python
from mypackage import add

print(add(10, 5))
```

Output:

```text
15
```

---

# 6. Import Methods

## Import Entire Module

```python
import mypackage.calculator

print(mypackage.calculator.add(1, 2))
```

---

## Import Specific Function

```python
from mypackage.calculator import add
```

---

## Import from Package

```python
from mypackage import add
```

Requires exports inside `__init__.py`.

---

# 7. Subpackages

Packages can contain subpackages.

Example:

```text
myapp/
│
├── __init__.py
│
├── database/
│   ├── __init__.py
│   └── db.py
│
├── api/
│   ├── __init__.py
│   └── routes.py
│
└── utils/
    ├── __init__.py
    └── helper.py
```

Usage:

```python
from myapp.database import db
```

---

# 8. Best Practices

## Use Meaningful Module Names

Good:

```text
calculator.py
file_handler.py
```

Avoid:

```text
abc.py
stuff.py
```

---

## Keep `__init__.py` Clean

Only expose necessary APIs.

Example:

```python
from .calculator import add
```

---

## Follow PEP 8

Use:

* snake_case for functions
* CamelCase for classes
* lowercase package names

---

## Add Documentation

Use docstrings.

```python
def add(a, b):
    """Return sum of two numbers."""
    return a + b
```

---

# 9. Adding a README

Create `README.md`.

Example:

```markdown
# MyPackage

A simple Python package.

## Installation

pip install mypackage

## Usage

from mypackage import add
```

---

# 10. Adding a License

Popular licenses:

* MIT
* Apache 2.0
* GPL

Example MIT License:

```text
MIT License

Copyright (c) 2026
```

---

# 11. Creating `.gitignore`

Example:

```gitignore
__pycache__/
*.pyc
venv/
.env
build/
dist/
*.egg-info/
```

---

# 12. Virtual Environments

Create virtual environment:

```bash
python -m venv venv
```

Activate:

## Windows

```bash
venv\Scripts\activate
```

## Linux/macOS

```bash
source venv/bin/activate
```

---

# 13. Creating `requirements.txt`

Install dependencies:

```bash
pip install requests
```

Generate requirements:

```bash
pip freeze > requirements.txt
```

Example:

```text
requests==2.32.0
```

---

# 14. GitHub Repository Setup

## Initialize Git

```bash
git init
```

---

## Add Files

```bash
git add .
```

---

## Commit

```bash
git commit -m "Initial commit"
```

---

## Connect GitHub Repository

```bash
git remote add origin https://github.com/username/repository.git
```

---

## Push Code

```bash
git push -u origin main
```

---

# 15. Example Complete Project

## Structure

```text
awesome_calculator/
│
├── README.md
├── LICENSE
├── requirements.txt
├── setup.py
├── pyproject.toml
├── .gitignore
│
├── awesome_calculator/
│   ├── __init__.py
│   ├── calculator.py
│   └── scientific.py
│
└── tests/
    └── test_calculator.py
```

---

## calculator.py

```python
# awesome_calculator/calculator.py


def add(a, b):
    return a + b


def multiply(a, b):
    return a * b
```

---

## **init**.py

```python
from .calculator import add, multiply

__version__ = "1.0.0"
```

---

## Using the Package

```python
from awesome_calculator import add

print(add(4, 5))
```

---

# 16. Packaging for PyPI

## setup.py

```python
from setuptools import setup, find_packages

setup(
    name="awesome_calculator",
    version="1.0.0",
    packages=find_packages(),
    install_requires=[],
    author="Your Name",
    description="Simple calculator package",
)
```

---

## pyproject.toml

```toml
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"
```

---

## Build Package

Install build tool:

```bash
pip install build
```

Build:

```bash
python -m build
```

Generated:

```text
dist/
├── awesome_calculator-1.0.0.tar.gz
└── awesome_calculator-1.0.0-py3-none-any.whl
```

---

# 17. Useful Commands

| Command                 | Purpose                 |
| ----------------------- | ----------------------- |
| `pip install package`   | Install package         |
| `pip uninstall package` | Remove package          |
| `pip list`              | List installed packages |
| `python -m build`       | Build package           |
| `pytest`                | Run tests               |
| `pip freeze`            | Export dependencies     |

---

# 18. Conclusion

Python packages help developers:

* Organize code
* Reuse functionality
* Share libraries
* Build scalable applications

The `__init__.py` file plays an important role in package initialization and API management.

A well-structured package with:

* documentation
* tests
* GitHub support
* packaging configuration

is considered professional and production-ready.

---

# Recommended Next Steps

Learn next:

1. Object-Oriented Programming
2. Unit Testing with `pytest`
3. Publishing to PyPI
4. GitHub Actions CI/CD
5. Semantic Versioning
6. Type Hinting
7. Documentation with Sphinx

---

# References

* Python Official Documentation
* Packaging Python Projects
* PyPI Documentation
* PEP 8 Style Guide
