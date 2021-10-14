# Bubble Sort

## Topics to be covered:

- [Basics](#basics-of-bubble-sort)
- [Algorithm](#algorithm)
- [Working](#working)
- [Space-Time Complexity Analysis](#space-and-time-complexity-analysis)
- [Advantages and Disadvantages](#advantages-and-disadvantages)
- [Applications](#applications)

---

### 1. Basics of Bubble Sort

**Bubble Sort** is a sorting algorithm that compares two adjacent elements and swaps them until they are in the correct order.
Just as in water the bigger bubble rise up first, in a similar fashion the elements with the biggest values shift to the end of the array one-by-one until the array is in correct order.

---

### 2. Algorithm

The algorithm & pseudocode for bubble sort is given below :-

**_Algorithm :_**

_Step 1:_ Starting from first index of the array.

_Step 2:_ Compare the current index element with the element on the right. If it is greater than the element on the right, move to step 3 else to step 4.

_Step 3:_ Swap the current element with the one on the right.

_Step 4:_ Make the element on the right as current element and move to step 2 until there is no more elements on the right index i.e. current ==n<sup>th</sup> element , thus move to Step 5.

_Step 5:_ Move to Step 1 and repeat steps from 1 to 4 until the array is in correct order but now for (n-1), (n-2), (n-3) .. and so on for further iterations.

**_Pseudocode :_**

```
bubbleSort(array)
  for i <- 1 to indexOfLastUnsortedElement-1
    if leftElement > rightElement
      swap leftElement and rightElement
end bubbleSort
```

---
