---
title: Selection Sort
author: shane
description: Learn about the Selection Sort algorithm.
categories: ['Data Algorithms', 'Sorting']

image:
  path: /assets/img/covers/pexels-photo-278887.jpeg
  alt: Photo by Pixabay from Pexels

mermaid: true
toc: true
comments: false
---

**Selection Sort** is an in-place sorting algorithm that succeeds in sorting smaller arrays of values, but suffers with larger arrays.

## How It Works?

**Selection Sort** works in-place, meaning it doesn't require a separate array for storing the sorted values. Instead we perform a series of swaps, finding lowest value (usually indicated by index `j`) to index `i`. Index `i` moves from left to right, shrinking the array at each pass.

## Implementation

Below is a more traditional implementation where only one swap occurs, if and only if, a value is found to be smaller than `nums[i]`:

```python
def traditionalSelectionSort(nums: list) -> list:
  for i in range(len(nums) - 1):
    minIndex = i

    for j in range(i, len(nums)):
      if nums[j] < nums[minIndex]:
        minIndex = j
        
    if minIndex != i:
      nums[i], nums[minIndex] = nums[minIndex], nums[i]
      
  return nums
  
print(selectionSort([3, 8, 2, 5, 7, 4]))
# => [2, 3, 4, 5, 7, 8]
```

Below is a modified version of implementation that will swap *every* value (`nums[j]`) less than `nums[i]`. I prefer this approach since it's more condensed and swapping values in an array is a constant operation (e.g. `O(1)`):

```python
def modifiedSelectionSort(nums: list) -> list:
  for i in range(len(nums) - 1):    # i = receiving min value
    for j in range(i, len(nums)):   # j = searches for min values
      if nums[j] < nums[i]:         # swap with values < nums[i]
        nums[i], nums[j] = nums[j], nums[i]

  return nums

print(selectionSort([3, 8, 2, 5, 7, 4]))
# => [2, 3, 4, 5, 7, 8]
```

## Visual Representation

![](/assets/img/data-algorithms/Sort_Selection.jpg)

## Analysis

**Selection Sort** is similar to [Insertion Sort](/wiki/data-algorithms/sort-selection) (except for when comparing best-case performances, in which **Insertion Sort** is better).

```python
Time:
  Worst:   O(n^2)
  Best:    O(n^2)
  Average: O(n^2)

Space: O(1) - swapping in place
```

## Further Reading

[Selection Sort](https://en.wikipedia.org/wiki/Selection_sort) - Wikipedia article on **Selection Sort**.

---
Photo by [Photo by Pixabay from Pexels](https://www.pexels.com/photo/brown-scrabble-boards-with-letters-278887/)