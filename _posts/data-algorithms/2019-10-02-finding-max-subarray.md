---
title: Finding Maximum Subarray
description: Learning how to find the maximum contiguous sum of integers within an array.
categories: ['Data Algorithms', 'Problems']

image:
  path: /assets/img/covers/pexels-photo-258063.jpeg
  alt: Photo by Pixabay from Pexels

# mermaid: true
toc: true
comments: false
---

We are given an array of integers and are asked to find the maximum contiguous sum of values within the array, returning it's sum.

## What's Being Asked?

Let's say we are given an array of integers: `[1, -1, 3, -1, 0, 2, -3, 1]`. Integers are non-floating point values that can be either positive or negative (including zero). What makes this problem difficult is our array includes negative numbers. Consider for a moment if we were asked to find the **maximum subarray** of positive numbers only. This could easily be answered by summing the entire array, however this is not the case (and would make for a boring problem).

We can visually see the **maximum subarray** is equal to `4` (the subarray being `[3, -1, 0, 2]`), but how would we solve this programmatically? You may have came to this conclusion the same way I did by scanning the array for larger positive numbers or maybe groupings of positive numbers and scanning it's neighbors until coming to an answer.

## Naive Approach

Let's start with a **naive approach** first, and then consider a more optimized solution. The first idea that comes to mind is testing for every single combination. This may sound daunting, but remember that we are only looking for the maximum sum of contiguous values. Observe:

![](/assets/img/data-algorithms/Maximum%20Subarray%20-%20Part%20I.png)

This approach requires two `for` loops: one starting at the beginning and one at the end, shrinking the array with each pass and updating the `maxVal`.

Here's the code following the diagram above:

```python
def maxSubArray(nums: list) -> int:
  maxVal = 0

  for i in range(len(nums)):
    for j in range(len(nums), i, -1):
      maxVal = max(maxVal, sum(nums[i:j]))

  return maxVal
```

## Linear Approach

Next, let's move on to a more optimized approach where we move from left to right, maintaining the maximum value as we go. This approach is very similar to [Kandane's Algorithm](https://en.wikipedia.org/wiki/Maximum_subarray_problem#Kadane%27s_algorithm), except we'll store the maximum value in a separate array as we go. Observe:

![](/assets/img/data-algorithms/Maximum%20Subarray%20-%20Part%20II.png)

Finally, we take the maximum value of our auxiliary array to get our answer of `4`.

Here's the code:

```python
def maxSubArray(nums: list) -> int:
  arr = [0] * len(nums)

  for i in range(len(nums)):
    arr[i] = max(nums[i], nums[i] + arr[i-1])

  return max(arr)
```

## Analysis

The following graph shows the time comparisons vs input of both approaches described above. It may not look it, but the optimized approach appears to look constant (`O(1)`) however it's actually linear (`O(n)`).

![](/assets/img/data-algorithms/Maximum%20Subarray%20-%20Part%20III.png)

Below is the optimized approach graphed separately, showing it's linear (`O(n)`) nature.

![](/assets/img/data-algorithms/Maximum%20Subarray%20-%20Part%20IV.png)

## Conclusion

This article touches on two different approaches to solving the **Maximum Subarray Problem**. There is also a divide & conquer approach that I hope to include in a second part to this post.

## Further Reading

[Maximum Subarray Problem](https://en.wikipedia.org/wiki/Maximum_subarray_problem) - Wikipedia article.

---
Photo by [Pixabay from Pexels](https://www.pexels.com/photo/mind-the-gap-signage-258063/)