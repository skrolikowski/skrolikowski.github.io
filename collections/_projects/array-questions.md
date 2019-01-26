---
layout: page
title: Array Questions
excerpt: A selection of questions regarding the usage and knowhow of the array data structure.
image: /assets/covers/egg-white-food-protein-162712.jpeg
categories: data-structures
tags: [programming, indexing, array, data-structure, computer-science]
---

### Missing Numbers.

Finding the missing number(s) in an array of integers with expected length.

* The given array can contain integers between 1 and 100.
* The given array is sorted in ascending order starting at 1.
* The given array can never exceed a length of 100.
* The given array does not contain duplicate values.

#### Examples

```python
# python
missingNumbers([1, 2, 3, 4, 6], 6)       # Expected: [5]
missingNumbers([1, 2, 3, 4, 6, 8], 10)   # Expected: [5, 7, 9, 10]
```

#### Solution

```python
# python
def missingNumbers(nums, length):
    missing = []
    index   = 0

    for n in range(1, length + 1):
        if index < len(nums) and nums[index] == n:
            index += 1
        else:
            missing.append(n)

    return missing
```

### Duplicate Numbers.

Find the duplicate number(s) in an array of integers.

- The given array can contain integers between 1 and 100.
- The given array is sorted in ascending order starting at 1.

#### Examples

```python
# python
duplicateNumbers([1, 2, 2, 3, 3])   # Expected: [2, 3]
duplicateNumbers([1, 1, 1, 2, 3])   # Expected: [1]
```

#### Solution

```python
# python
def duplicateNumbers(nums):
    duplicates = {}
    previous   = None

    for n in nums:
        if previous == n and not n in duplicates:
            duplicates[n] = True

        previous = n

    return list(duplicates.keys())
```

> **Tip**: I'm using a `bool` dictionary to store recorded duplicates. The reason being, using Python's `in` operator is more costly for lists.
>
> **More information**: [Performance of Python Types](https://bradfieldcs.com/algos/analysis/performance-of-python-types/)

