---
title: Finding Median Value of an Array
author: shane
description: Ever wonder how to find the Median Value of an Array? We'll read this!!
categories: ['Data Algorithms', 'Problems']

image:
  path: /assets/img/covers/pexels-photo-394377.jpeg
  alt: Photo by Isaque Pereira from Pexels

# mermaid: true
toc: true
comments: false
published: true
---

We are given a problem where we are supposed to find the **median** value of an **unsorted** array of size `n`. Let's get started.

## What's Being Asked?

First off it's important to make clear what is being asked. The **median** is simply defined as the middle. This is different than finding the **mean**. To get the mean we would simply have to add up all the values and divide by the number of values in the array:

```python
def mean(nums: list):
  return sum(nums) / len(nums)
```

Or written another way:

```python
def mean(nums: list):
  total, length = 0, 0
  
  for n in nums:
    total += n
    length += 1
    
  return total / length
```

Both calls to `mean([3, -1, 2, 4, 1, -4, 6, 5])`, for example, will return value `2.0`.

Another important piece of information we are given is that the array is **unsorted**. Why is this imporant? Well because if the array was guaranteed to be sorted we could easily obtain the **median** (middle value)  by:

```python
def median(sorted_nums: list):
  midpoint = len(sorted_nums) // 2 - 1

  return sorted_nums[midpoint]
```

Calling `median([-4, -1, 1, 2, 3, 4, 5, 6])` will give you `2`.

> **Note:** when referring to the "middle" of an array of even length it's possible to consider a hi- and lo-middle, however we'll only consider the lo-middle in this article.

We're done right? Unfortunately not, because our input array is not sorted. Does it make sense to first sort it? Maybe for a small input, but this could take some serious processing time if your input is very large. Let's discuss a few approaches we could take.

## Naive Approach

To get the median value of the array `[3, -1, 2, 4, 1, -4, 6, 5]` we could use knowledge we touched upon in the previous section. We know how to find the index in the middle position. Remember:

```python
midpoint = len(sorted_nums) // 2 - 1

print(midpoint)
# => 3
```

So now we know the 3rd index of our array is where the **median** is, if and only if, our array is sorted already. But our array isn't sorted, so how does this help us? Well we know that the fourth largest value (since the index starts at 0) will be the **median** value.

```python
def median(nums: list):
  target = len(nums) // 2 - 1
  count  = 0

  while count < target:
    # find smallest value and remove it..
    nums.remove(min(nums))

    # keep track of removals..
    count += 1

    return min(nums)

print(median([3, -1, 2, 4, 1, -4, 6, 5]))
# => 2
```

Let's walk through what we did.

1. First, we define and set a `target` variable, which will tell us how many minimum values we will have to discard from the array before returning with the correct result.
2. Next, we set a `count` variable to 0 to keep track of how many values we have discarded.
3. Then we enter a while loop, removing the smallest value each time until `count == target`.
4. Finally we return the minimum value of `nums`, which is `min(nums)`.

This is a viable approach that will work with any array with a length greater than 1, but we could do better.

## Divide & Conquer Approach?

What would happen if we used a divide & conquer approach? In other words, dividing the array in half then searching for the 3rd largest value in our array. Writing it out we get:

![](/assets/img/data-algorithms/Sort_Merge.jpg)

But now what? It looks like the first steps of **Merge Sort**, doesn't it? Since we know having a sorted array will help us, let's continue with this approach in implementing **Merge Sort** in order to access the **median** value.

```python
def median(nums: list):
  sorted_nums = mergeSort(nums)
  midpoint    = len(sorted_nums) // 2 - 1

  return sorted_nums[midpoint]

def mergeSort(nums: list):
  if len(nums) == 1:
    return nums

  mid   = len(nums) // 2
  left  = mergeSort(nums[:mid])
  right = mergeSort(nums[mid:])

  return merge(left, right)

def merge(left: list, right: list):
  lLen, rLen  = len(left), len(right)
  sorted_nums = [0] * (lLen + rLen)
  lIdx, rIdx  = 0, 0
  pIdx        = 0

  while lIdx < lLen and rIdx < rLen:
    if left[lIdx] < right[rIdx]:
      sorted_nums[pIdx] = left[lIdx]
      lIdx += 1
    else:
      sorted_nums[pIdx] = right[rIdx]
      rIdx += 1

    pIdx += 1

  while lIdx < lLen:
    sorted_nums[pIdx] = left[lIdx]
    lIdx += 1
    pIdx += 1

  while rIdx < rLen:
    sorted_nums[pIdx] = right[rIdx]
    rIdx += 1
    pIdx += 1

  return sorted_nums
  
print(median([3, -1, 2, 4, 1, -4, 6, 5]))
# => 2
```

This took a lot more work, but in the end we have a sorted array and can easily obtain the **median** value.

**Merge Sort** is an efficient divide & conquer algorithm with the following time/space analysis:

```python
Time:
  Worst:   O(n * log n)
  Best:    O(n * log n)
  Average: O(n * log n)

Space: O(n)
```

The additional space involved can be found in the `merge` function when we create a brand new array to hold the sorted values. However, where Merge Sort excels over Quick Sort is in how it divides the array in half for every level. The bulk of the work is in the `merge` function.

> **Note:** Analyzing a divide & conquer algorithms isn't as straight forward as analyzing non-rescursive algorithms where everything is contained in one function. In order to analyze the time complexity you can use either [Recursion Tree](https://en.wikipedia.org/wiki/Recursive_tree) or the [Master Theorem](https://en.wikipedia.org/wiki/Master_theorem_(analysis_of_algorithms)).

## Modified QuickSort Approach

Let's take a look at another sorting algorithm and exploit a feature that it has over **Merge Sort**. This feature is the **partition** step, in which the **pivot** is moved into the correct position before we split the array to continue the algorithm. Therefore if we know what index the target is (explained above), and we know the pivots position after one partition then this should give us information on how to proceed. There are 1 of 3 cases:

| Case                          | What this means...                         |
| ----------------------------- | ------------------------------------------ |
| `Target index == Pivot index` | We have found the target index!            |
| `Target index < Pivot index`  | We can partition the left-hand partition.  |
| `Target index > Pivot index`  | We can partition the right-hand partition. |
{: .table .table-striped .w-75 .mx-auto  }

Here's a diagram showing the first paritioning:

![](/assets/img/data-algorithms/Finding%20Median%20-_%20QuickSort%20-%20Part%20I.jpg)

The next step in **QuickSort** is to divide the array into two smaller arrays (left and right ends, excluding the pivot). However since we only care about the target position we only have to consider the right half and continue until the pivot equals the target. Let's continue with our example:

![](/assets/img/data-algorithms/Finding%20Median%20-_%20QuickSort%20-%20Part%20II.jpg)

And we're finished! Try it yourself with our original example `[3, -1, 2, 4, 1, -4, 6, 5]` and see if you get `2` as the answer.

Finally, here is the code used:

```python
def median(nums: list):
  """
  a = left-most index
  z = right-most index
  """
  a, z   = 0, len(nums) - 1
  target = z // 2
	
  return medianQuickSort(nums, a, z, target) 

def medianQuickSort(nums: list, a: int, z: int, target: int):
  if a < z:
    pIdx = partition(nums, a, z)

    if target == pIdx:
      # pivot == target, so return value
      return nums[pIdx]
    elif target < pIdx:
      # target < pivot; => inspect left
      return medianQuickSort(nums, a, pIdx - 1, target)
    else:
      # pivot > target; => inspect right
      return medianQuickSort(nums, pIdx, z, target)

def partition(nums: list, a: int, z: int):
  i = a - 1

  for j in range(a, z):
    if nums[j] < nums[z]:
      nums[j], nums[i + 1] = nums[i + 1], nums[j]
      i += 1 

  nums[z], nums[i + 1] = nums[i + 1], nums[z]

  return i + 1

print(median([3, -1, 2, 4, 1, -4, 6, 5]))
# => 2
```

## Conclusion

**QuickSort** is a divide & conquer sorting algorithm, which can be considered faster than it's competitors (e.g **Merge Sort** or **Heap Sort**) provided you get lucky in pivot selection. Let's quickly compare the three:

```python
Merge Sort:           Heap Sort:            QuickSort:
-------------------   -------------------   -------------------
High:  O(n * log n)   High:  O(n * log n)   High:  O(n^2)
Mean:  O(n * log n)   Mean:  O(n)           Mean:  O(n * log n)
Low:   O(n * log n)   Low:   O(n * log n)   Low:   O(n * log n)
Space: O(n)           Space: O(1)           Space: O(log n)
```

The gotcha with **QuickSort** is in picking a **pivot** efficiently. We also picked a pivot using **Merge Sort**. Where you may ask? The answer is right down the middle, which explains the `log n` part of the `O(n * log n)` analysis above.

The main difference between **QuickSort** and **Merge Sort** is the stage in when you perform the sort. **Merge Sort** will sort during the merge stage, while **QuickSort** sorts during the partition stage (before the dividing). We found this to be useful as it gives us an opportunity to choose which halve to pursue when looking for the **median**.

## References

- [BigO Cheat Sheet](https://bigocheatsheet.io/) - Good reference for checking your work, however it's good to know why you get these results.
- [Algorithm Lecture 11: Median (Part 1)](https://www.youtube.com/watch?v=oXdgED3Gdek) - Guided walkthrough of finding Median using modified QuickSort - Part 1.
- [Algorithm Lecture 12: Median (Part 2)](https://www.youtube.com/watch?v=vemvIEoXC8A) - Guided walkthrough of finding Median using modified QuickSort - Part 2.

---
Photo by [Photo by Isaque Pereira from Pexels](https://www.pexels.com/photo/yellow-arrow-led-signage-394377/)