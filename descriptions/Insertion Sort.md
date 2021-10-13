# Insertion Sort
In this article, we will discuss the Insertion sort Algorithm. The working procedure of insertion sort is also simple.

This is an in-place comparison-based sorting algorithm. Here, a sub-list is maintained which is always sorted. For example, the lower part of an array is maintained to be sorted. An element which is to be 'insert'ed in this sorted sub-list, has to find its appropriate place and then it has to be inserted there. Hence the name, **insertion sort**.

<b>Example</b>
----
Insertion sort works similar to the sorting of playing cards in hands. It is assumed that the first card is already sorted in the card game, and then we select an unsorted card. If the selected unsorted card is greater than the first card, it will be placed at the right side; otherwise, it will be placed at the left side. Similarly, all unsorted cards are taken and put in their exact place.

The same approach is applied in insertion sort. The idea behind the insertion sort is that first take one element, iterate it through the sorted array. Although it is simple to use, it is not appropriate for large data sets as the time complexity of insertion sort in the average case and worst case is O(n2), where n is the number of items. Insertion sort is **less** efficient than the other sorting algorithms like heap sort, quick sort, merge sort, etc.

## Glimpse:
1.	[Algorithm](#algorithm)
2.	[Working of Insertion sort Algorithm](#working-of-insertion-sort-algorithm)
3.	[Pseudo code](#pseudo-code)
4.	[Implementation of Insertion sort](#implementation-of-insertion-sort)
5.	[Insertion sort complexity](#insertion-sort-complexity)
6.	[Time complexity of insertion sort](#time-complexity)
7.	[Space complexity of insertion sort](#space-complexity)
8.	[Advantages of Insertion sort over other sorting techniques](#advantages-of-insertion-sort-over-other-sorting-techniques)
9.	[Disadvantages of Insertion sort over other sorting techniques](#disadvantages-of-insertion-sort-over-other-sorting-techniques)
