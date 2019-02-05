---
layout: wiki
title: Array
excerpt: All about the array data structure.
image: /assets/covers/fashion-red-yellow-designer-5872.jpg
categories: ['data-structures']
tags: ['array', 'collections', 'big-o', 'sorting']
---

# Array

An array is a simple data structure consisting of one or more elements usually of one data type (depending on the language). It is stored as a contiguous block of memory, and thus is commonly pictured as such:

{: .text-center .p-3 }

<img src="..\..\assets\collections\array_blank.svg" width="75%">

### Insertion

```c++
# C++
int capcity = 6;
int arr     = new int[capcity];
int size    = sizeof(arr) / sizeof(arr[0]);
...
```

When declaring your array you will need to define a *capacity*, in other words, how many elements your array can hold. Since arrays are contiguous blocks of memory, adding additional elements past this *capacity* can be costly depending on how many elements there are. This is because in order to add past the capacity a new array will have to be created of the new required capacity, then all elements will need to be copied over to a new array. The previous block of memory is essentially released back to the CPU.

{: .text-center .p-3 }

<img src="..\..\assets\collections\array_resizing.svg" width="75%">

{: .ludwig}

> **Size vs capacity**: *size* refers to how many elements the array contains, while *capacity* refers to how many elements the array can hold in total.

### Indexing

```c++
# C++
...
int val1 = arr[0];  // Access the first element of the array.
int val2 = arr[2];  // Access the third element of the array.
...
```

Some languages won't complain when you attempt to access elements that don't exist, while some may give you an **Index-Out-of-Range** Exception.

### Search

## Big O

**Average Time**

{: .table .table-striped .w-50 .float-left}

| Average Time            |      |
| ----------------------- | :--: |
| [Indexing](#indexing)   | 0(1) |
| [Search](#search)       | 0(n) |
| [Insertion](#insertion) |  -   |
| [Deletion](#deletion)   |  -   |

{: .table .table-striped .w-50 .float-right }

| Worst Time              |      |
| ----------------------- | :--: |
| [Indexing](#indexing)   | 0(1) |
| [Search](#search)       | 0(n) |
| [Insertion](#insertion) |  -   |
| [Deletion](#deletion)   |  -   |



## Sorting



## As a Heap



## Useful Functions

## Terminology

* **Index** - refers to the order location of an array element.
* **Element/value** - a single element in the array.
* **Capacity** - how many elements the array can hold in total.
* **Size** - how many elements are currently in the array.

## References

* [Big O Reference](http://bigoref.com/) - Big O Reference of common algorithms and data structures.