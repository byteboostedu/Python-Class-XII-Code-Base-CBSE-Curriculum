# Binary Search
> Works only on sorted lists. Repeatedly divides the list into halves.

```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1

    return -1

arr = [10, 20, 30, 40, 50]
print(binary_search(arr, 40))
```

# Binary Search Complexity Explained (Baby Steps)

## What is Binary Search?

Binary search is a searching algorithm that works on a **sorted array**.

Instead of checking elements one by one, it:

1. Finds the middle element
2. Compares it with the target
3. Removes half of the remaining elements

That is why binary search is very fast.

---

# Example

Suppose we have:

```python
arr = [1, 3, 5, 7, 9, 11, 13]
```

We want to find:

```python
9
```

---

## Step 1

Middle element:

```python
7
```

Since:

```python
9 > 7
```

Ignore the left half.

Remaining:

```python
[9, 11, 13]
```

---

## Step 2

Middle element:

```python
11
```

Since:

```python
9 < 11
```

Ignore the right half.

Remaining:

```python
[9]
```

---

## Step 3

Found:

```python
9
```

---

# Binary Search Python Code

```python
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid

        elif arr[mid] < target:
            left = mid + 1

        else:
            right = mid - 1

    return -1
```

---

# Understanding Complexity Step by Step

---

# Step 1 — Observe the Pattern

Binary search keeps dividing the array into half.

Suppose:

```text
16 elements
```

After each step:

```text
16 → 8 → 4 → 2 → 1
```

Count the divisions:

```text
4 steps
```

---

# Step 2 — Another Example

Suppose:

```text
32 elements
```

Binary search divides:

```text
32 → 16 → 8 → 4 → 2 → 1
```

Count:

```text
5 steps
```

---

# Step 3 — Pattern Table

| Number of Elements (n) | Steps |
|---|---|
| 2 | 1 |
| 4 | 2 |
| 8 | 3 |
| 16 | 4 |
| 32 | 5 |
| 64 | 6 |

Notice:

Each step divides by 2.

---

# Step 4 — Understanding log₂(n)

The number of times we can divide by 2 is called:

```text
log₂(n)
```

Example:

```text
log₂(16) = 4
```

Because:

```text
2 × 2 × 2 × 2 = 16
```

or:

```text
2⁴ = 16
```

Another example:

```text
log₂(32) = 5
```

Because:

```text
2⁵ = 32
```

---

# Step 5 — Final Complexity

Binary search keeps halving the data.

Therefore its time complexity is:

```text
O(log₂ n)
```

Usually written as:

```text
O(log n)
```

---

# Real Example

Suppose:

```text
n = 1024
```

Binary search steps:

```text
1024
512
256
128
64
32
16
8
4
2
1
```

Total checks:

```text
10
```

Because:

```text
log₂(1024) = 10
```

---

# Comparison with Linear Search

| Algorithm | Worst Case Checks |
|---|---|
| Linear Search | 1024 |
| Binary Search | 10 |

Binary search is much faster for large data.

---

# Best, Average, Worst Cases

| Case | Complexity |
|---|---|
| Best Case | O(1) |
| Average Case | O(log n) |
| Worst Case | O(log n) |

---

# Space Complexity

Iterative binary search uses:

```text
O(1)
```

extra space.

---

# Simple Intuition

## Linear Search

```text
Remove 1 item each step
```

## Binary Search

```text
Remove HALF the items each step
```

That is why binary search becomes logarithmic.

---

# Final Formula

Binary Search Time Complexity:

```text
O(log₂ n)
```

because the problem size becomes half after every step.

