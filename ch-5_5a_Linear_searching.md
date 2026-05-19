```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i   # return index if found
    return -1          # return -1 if not found


# Example list
numbers = [10, 25, 30, 45, 50]

# Element to search
target = 45

# Function call
result = linear_search(numbers, target)

# Output
if result != -1:
    print(f"Element found at index {result}")
else:
    print("Element not found")
```
