# 📘 File Handling in Python — `seek()`, `tell()`, `pickle`, and `unpickle`

---

# 1. Introduction to File Handling

File handling allows Python programs to:
- Store data permanently
- Read saved data later
- Modify existing files

Python provides built-in functions for file operations.

---

# 2. Opening a File

## Syntax
```python
file_object = open(file_name, mode)
```

### Example
```python
f = open("data.txt", "r")
```

---

# 🧠 Mnemonic
> **OPEN = Obtain Permission Entering Now**

---

# 3. Closing a File

## Syntax
```python
file_object.close()
```

### Example
```python
f.close()
```

---

# 4. File Pointer

When a file is opened, Python maintains a **file pointer**.

📍 The pointer tells:
- where reading starts
- where writing happens

---

# 🧠 Mnemonic
> **Pointer = Current location inside file**

---

# 5. `tell()` Method

## Purpose
Returns the current position of the file pointer.

---

## Syntax
```python
file_object.tell()
```

---

## Example
```python
f = open("sample.txt", "r")

print(f.tell())

f.close()
```

### Output
```python
0
```

👉 `0` means pointer is at the beginning.

---

# Example with Reading

```python
f = open("sample.txt", "r")

data = f.read(5)

print(data)
print(f.tell())

f.close()
```

### Suppose file contains:
```text
Hello Python
```

### Output
```python
Hello
5
```

👉 After reading 5 characters, pointer moves to position 5.

---

# 🧠 Mnemonic
> **tell() tells the current position**

---

# 6. `seek()` Method

## Purpose
Moves the file pointer to a specific position.

---

## Syntax
```python
file_object.seek(offset)
```

---

## Example
```python
f = open("sample.txt", "r")

f.seek(6)

print(f.read())

f.close()
```

### Suppose file contains:
```text
Hello Python
```

### Output
```python
Python
```

👉 Pointer jumps to position 6.

---

# 🧠 Mnemonic
> **seek() = Search & move**

---

# 7. `seek()` Reference Positions

| Reference Point | Value |
|---|---|
| Beginning of file | `0` |
| Current position | `1` |
| End of file | `2` |

---

# Example

```python
f.seek(0)
```

Moves pointer to beginning.

---

# 8. Difference Between `seek()` and `tell()`

| Function | Purpose |
|---|---|
| `tell()` | Shows current position |
| `seek()` | Changes current position |

---

# 🧠 Quick Trick

```text
tell() → WHERE am I?
seek() → GO THERE
```

---

# 9. What is Pickling?

## Definition
Pickling means converting a Python object into binary form and storing it in a file.

Python uses the `pickle` module for this.

---

# 🧠 Mnemonic
> **Pickle = Pack Python object**

---

# 10. Importing Pickle Module

```python
import pickle
```

---

# 11. `dump()` Method — Pickling

## Purpose
Stores Python object into a binary file.

---

## Syntax
```python
pickle.dump(object, file)
```

---

# Example: Pickling

```python
import pickle

data = [10, 20, 30, 40]

f = open("data.dat", "wb")

pickle.dump(data, f)

f.close()
```

---

# Explanation

| Part | Meaning |
|---|---|
| `wb` | Write binary mode |
| `dump()` | Stores object |

---

# 🧠 Mnemonic
> **dump() dumps object into file**

---

# 12. What is Unpickling?

## Definition
Unpickling means retrieving Python objects from a binary file.

---

# 🧠 Mnemonic
> **Unpickle = Unpack object**

---

# 13. `load()` Method — Unpickling

## Syntax
```python
pickle.load(file)
```

---

# Example: Unpickling

```python
import pickle

f = open("data.dat", "rb")

data = pickle.load(f)

print(data)

f.close()
```

---

## Output
```python
[10, 20, 30, 40]
```

---

# Explanation

| Part | Meaning |
|---|---|
| `rb` | Read binary mode |
| `load()` | Reads object |

---

# 🧠 Mnemonic
> **load() loads object from file**

---

# 14. Complete Pickle Program ⭐

## Writing Data

```python
import pickle

student = {
    "name": "Rahul",
    "marks": 95
}

f = open("student.dat", "wb")

pickle.dump(student, f)

f.close()
```

---

## Reading Data

```python
import pickle

f = open("student.dat", "rb")

data = pickle.load(f)

print(data)

f.close()
```

---

## Output

```python
{'name': 'Rahul', 'marks': 95}
```

---

# 15. Binary Modes Used in Pickling

| Mode | Meaning |
|---|---|
| `wb` | Write binary |
| `rb` | Read binary |
| `ab` | Append binary |

---

# 16. Important Notes

✅ Pickle works only with binary files  
✅ Use `wb` while writing  
✅ Use `rb` while reading  
✅ Any Python object can be pickled:
- list
- tuple
- dictionary
- class object

---

# 17. Common Errors

| Error | Reason |
|---|---|
| `EOFError` | File empty |
| `FileNotFoundError` | File missing |
| `TypeError` | Wrong mode used |

---

# 18. Best Practice — Using `with`

## Example

```python
import pickle

data = [1, 2, 3]

with open("data.dat", "wb") as f:
    pickle.dump(data, f)
```

👉 File closes automatically.

---

# 🧠 Mnemonic
> **WITH = Work Inside Then Handle closes**

---

# 19. One-Line Revision Sheet 🚀

| Topic | Key Point |
|---|---|
| `tell()` | Current pointer position |
| `seek()` | Move pointer |
| `pickle` | Store object in binary |
| `unpickle` | Retrieve object |
| `dump()` | Write object |
| `load()` | Read object |
| `wb` | Write binary |
| `rb` | Read binary |

---

# 20. Ultimate Memory Trick 🔥

```text
tell()  → Tell position
seek()  → Search position
dump()  → Put object into file
load()  → Bring object from file
pickle  → Pack object
unpickle → Unpack object
```

---

# 21. Mini Practice Questions 📝

## Q1. Which function moves the file pointer?
✅ `seek()`

---

## Q2. Which function returns current position?
✅ `tell()`

---

## Q3. Which module is used for pickling?
✅ `pickle`

---

## Q4. Which method stores object in file?
✅ `dump()`

---

## Q5. Which method retrieves object?
✅ `load()`

---

# 🎯 Exam Tips

✅ `seek()` changes position  
✅ `tell()` shows position  
✅ Pickle uses binary files  
✅ `dump()` → write object  
✅ `load()` → read object  
✅ Remember:
```text
wb → write binary
rb → read binary
```
