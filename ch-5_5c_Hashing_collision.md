# Hashing and Collision Search in Python

## Table of Contents

1. Introduction
2. Built-in Hashing in Python
3. Cryptographic Hashing with `hashlib`
4. Common Hash Algorithms
5. Understanding Hash Collisions
6. Collision Search
7. Collision Search Example
8. Birthday Paradox
9. Time Complexity of Collision Attacks
10. MD5 Collision Weakness
11. Secure Hashing Recommendations
12. File Hashing Example
13. Real-World Applications
14. Summary
15. References

---

# 1. Introduction

Hashing is the process of converting input data into a fixed-size output called a **hash value**, **digest**, or **checksum**.

A hash function:

- Accepts data of arbitrary size
- Produces fixed-size output
- Is deterministic
- Is designed to minimize collisions

Hashing is widely used in:

- Dictionaries and hash tables
- Password storage
- Data integrity verification
- Digital signatures
- Blockchain systems

Python supports hashing through:

- Built-in `hash()` function
- `hashlib` module

---

# 2. Built-in Hashing in Python

Python provides the built-in `hash()` function primarily for internal data structures such as dictionaries and sets.

## Example

```python
value = "hello"

print(hash(value))
```

## Characteristics

| Feature | Description |
|---|---|
| Speed | Very fast |
| Security | Not cryptographically secure |
| Use Case | Hash tables, dictionaries, caching |
| Stability | Hash may change between runs |

## Important Note

The built-in `hash()` function should **not** be used for:

- Password hashing
- Cryptographic operations
- Security-sensitive systems

---

# 3. Cryptographic Hashing with `hashlib`

Python's `hashlib` module provides implementations of secure cryptographic hash functions.

## Importing `hashlib`

```python
import hashlib
```

## SHA256 Example

```python
import hashlib

text = "hello"

digest = hashlib.sha256(text.encode()).hexdigest()

print(digest)
```

## Sample Output

```text
2cf24dba5fb0a30e26e83b2ac5b9e29e...
```

---

# 4. Common Hash Algorithms

| Algorithm | Output Size | Secure? | Status |
|---|---|---|---|
| MD5 | 128-bit | ❌ No | Broken |
| SHA1 | 160-bit | ⚠ Weak | Deprecated |
| SHA256 | 256-bit | ✅ Yes | Recommended |
| SHA512 | 512-bit | ✅ Yes | Recommended |
| SHA3 | Variable | ✅ Yes | Modern |
| BLAKE2 | Variable | ✅ Yes | Fast & Secure |

---

# 5. Understanding Hash Collisions

A **collision** occurs when two different inputs produce the same hash output.

## Mathematical Representation

\[
hash(A) = hash(B), \quad A \ne B
\]

A good hash function makes collisions computationally difficult to find.

---

# 6. Collision Search

A **collision search** attempts to find two distinct inputs that generate identical hashes.

Since hash outputs are finite, collisions are mathematically unavoidable.

The objective of secure cryptographic design is to make collision discovery computationally infeasible.

---

# 7. Collision Search Example

The following example intentionally reduces the hash size to make collisions easier to observe.

## Python Example

```python
import hashlib
import random
import string

seen = {}

while True:

    # Generate random string
    s = ''.join(random.choices(string.ascii_letters, k=8))

    # Truncate SHA256 hash to 16 bits
    h = hashlib.sha256(s.encode()).hexdigest()[:4]

    if h in seen:

        print("Collision Found!")
        print("Previous String :", seen[h])
        print("Current String  :", s)
        print("Hash Value      :", h)

        break

    seen[h] = s
```

## Explanation

```python
[:4]
```

means:

- Only first 4 hexadecimal characters are used
- 4 hex characters = 16 bits
- Total possible hashes:

\[
2^{16} = 65536
\]

Because the hash space is small, collisions appear quickly.

---

# 8. Birthday Paradox

The **Birthday Paradox** explains why collisions occur faster than intuition suggests.

For a hash space of size \(N\), collisions become likely after approximately:

\[
n \approx \sqrt{2N}
\]

Where:

- \(N\) = total possible hash outputs
- \(n\) = number of generated samples

## Example

For a 16-bit hash:

\[
N = 65536
\]

Expected collision threshold:

\[
n \approx 300
\]

This principle forms the basis of the **Birthday Attack**.

---

# 9. Time Complexity of Collision Attacks

For an \(n\)-bit cryptographic hash function, brute-force collision search complexity is approximately:

\[
O(2^{n/2})
\]

Examples:

| Hash Size | Collision Complexity |
|---|---|
| 64-bit | \(2^{32}\) |
| 128-bit | \(2^{64}\) |
| 256-bit | \(2^{128}\) |

This is why modern secure hashes use large output sizes.

---

# 10. MD5 Collision Weakness

MD5 is considered cryptographically broken because practical collision attacks exist.

## Demonstration

```python
import hashlib

a = b"message1"
b = b"message2"

ha = hashlib.md5(a).hexdigest()
hb = hashlib.md5(b).hexdigest()

print("Hash A:", ha)
print("Hash B:", hb)
```

Although normal inputs produce different hashes, researchers have successfully created distinct files with identical MD5 hashes.

## Risks of MD5

- Digital signature forgery
- Certificate spoofing
- Integrity verification bypass

---

# 11. Secure Hashing Recommendations

## Avoid

- MD5
- SHA1

## Recommended

- SHA256
- SHA3
- BLAKE2

## Example Using BLAKE2

```python
import hashlib

data = b"important data"

digest = hashlib.blake2b(data).hexdigest()

print(digest)
```

---

# 12. File Hashing Example

File hashing is commonly used for integrity verification.

## Example

```python
import hashlib

with open("file.txt", "rb") as f:
    data = f.read()

digest = hashlib.sha256(data).hexdigest()

print(digest)
```

## Common Use Cases

- Download verification
- Malware detection
- Backup validation

---

# 13. Real-World Applications

## Applications of Hashing

| Application | Purpose |
|---|---|
| Password Storage | Secure authentication |
| Blockchain | Data integrity |
| Digital Signatures | Authentication |
| File Verification | Integrity checks |
| Hash Tables | Fast lookup |
| Deduplication | Storage optimization |

---

# 14. Summary

| Concept | Description |
|---|---|
| Hashing | Converts data into fixed-size digest |
| Collision | Two inputs producing same hash |
| Collision Search | Finding matching hashes |
| Birthday Attack | Efficient collision discovery |
| Secure Hashes | SHA256, SHA3, BLAKE2 |

---

# 15. References

## Python Documentation

- https://docs.python.org/3/library/hashlib.html

## NIST Cryptography Standards

- https://csrc.nist.gov/

## Additional Reading

- https://en.wikipedia.org/wiki/Cryptographic_hash_function
- https://en.wikipedia.org/wiki/Birthday_attack

---
