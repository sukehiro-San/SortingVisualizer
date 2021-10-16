# Quick Sort

## Topics to be covered:

- [Basics](#Basics)
- [Algorithm](#Algos)
- [Working](#Working)
- [Space-Time Complexity Analysis](#Space-TimeComplexityAnalysis)
- [Advantages and Disadvantages](#Advantages/Disadvantages)
- [Applications](#Applications)

---
### 1. Basics of Quick Sort

**QuickSort** is a Divide and Conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot.
There are many different versions of quickSort that pick pivot in different ways. 

---
### 2. Algorithm

_Step 1_. An array is divided into subarrays by selecting a pivot element (element selected from the array).

While dividing the array, the pivot element should be positioned in such a way that elements less than pivot are 
kept on the left side and elements greater than pivot are on the right side of the pivot.

_Step 2_. The left and right subarrays are also divided using the same approach. This process continues until each subarray contains a single element.

_Step 3_. At this point, elements are already sorted. Finally, elements are combined to form a sorted array.

**_Pseudocode :_**
```
quickSort(array, leftmostIndex, rightmostIndex)
  if (leftmostIndex < rightmostIndex)
    pivotIndex <- partition(array,leftmostIndex, rightmostIndex)
    quickSort(array, leftmostIndex, pivotIndex - 1)
    quickSort(array, pivotIndex, rightmostIndex)

partition(array, leftmostIndex, rightmostIndex)
  set rightmostIndex as pivotIndex
  storeIndex <- leftmostIndex - 1
  for i <- leftmostIndex + 1 to rightmostIndex
  if element[i] < pivotElement
    swap element[i] and element[storeIndex]
    storeIndex++
  swap pivotElement and element[storeIndex+1]
return storeIndex + 1
```
---
### 3. Working

- **Select the Pivot Element**

There are different variations of quicksort where the pivot element is selected from different positions.
Here, we will be selecting the rightmost element of the array as the pivot element.

| 8 | 7 | 6 | 1 | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

_**select pivot element**_


- **Rearrange the Array**

Now the elements of the array are rearranged so that elements that are smaller than the pivot are put on 
the left and the elements greater than the pivot are put on the right.

| 1 | 0 | (2) | 8 | 7 | 9 | 6 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

_**Put all the smaller elements on the left and greater on the right of pivot element.**_

**Here's how we rearrange the array**:

**1**. A pointer is fixed at the pivot element. The pivot element is compared with the elements beginning from the first index.

| 8 | 7 | 6 | 1 | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

**2**. If the element is greater than the pivot element, a second pointer is set for that element.

| 8 | 7 | 6 | 1 | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

**3**. Now, pivot is compared with other elements. If an element smaller than the pivot element is reached, the smaller element is
   swapped with the greater element found earlier.
   
| 8 | 7 | 6 | 1 | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
    
| 8 | 7 | 6 | 1 | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

| (1) | 7 | 6 | (8) | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
   
   _Pivot is compared with other elements._

**4**. Again, the process is repeated to set the next greater element as the second pointer. And, swap it with another smaller element.

| 1 | 7 | 6 | 8 | 0 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

| 1 | (7) | 6 | 8 | (0) | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

**5**. The process goes on until the second last element is reached.

| 1 | 0 | 6 | 8 | 7 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

| 1 | 0 | (6) | (8) | 7 | 9 | (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

**6**. Finally, the pivot element is swapped with the second pointer.

| 1 | 0 | (2) | 8 | 7 | 9 | 6 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|


- **Divide Subarrays**

Pivot elements are again chosen for the left and the right sub-parts separately. And, step 2 is repeated.
The subarrays are divided until each subarray is formed of a single element. At this point, the array is already sorted.

| 0 | 1 | (2) | 8 | 7 | 9 | 6 |                  
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

:arrow_down:

| 0 | 1 | 2 | 8 | 7 | 9 | 6 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:| 

| 8 | 7 | 9 | (6) |
|:-:|:-:|:-:|:-:|

| 6 | 7 | 9 | (8) |              
|:-:|:-:|:-:|:-:|                  

:arrow_down:

| 0 | 1 | 2 | 6 | 7 | 9 | 8 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

| 7 | 9 | (8) |
|:-:|:-:|:-:|

| 7 | (8) | 9 |               
|:-:|:-:|:-:|  

:arrow_down:

| 0 | 1 | 2 | 6 | 7 | 8 | 9 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:| 


### Code

```C++
// Quick sort in C++
#include <iostream>  
  
using namespace std;  
  
/* function that consider last element as pivot,  
place the pivot at its exact position, and place  
smaller elements to left of pivot and greater  
elements to right of pivot.  */  
int partition (int a[], int start, int end)  
{  
    int pivot = a[end]; // pivot element  
    int i = (start - 1);  
  
    for (int j = start; j <= end - 1; j++)  
    {  
        // If current element is smaller than the pivot  
        if (a[j] < pivot)  
        {  
            i++; // increment index of smaller element  
            int t = a[i];  
            a[i] = a[j];  
            a[j] = t;  
        }  
    }  
    int t = a[i+1];  
    a[i+1] = a[end];  
    a[end] = t;  
    return (i + 1);  
}  
  
/* function to implement quick sort */  
void quick(int a[], int start, int end) /* a[] = array to be sorted, start = Starting index, end = Ending index */  
{  
    if (start < end)  
    {  
        int p = partition(a, start, end);  //p is the partitioning index  
        quick(a, start, p - 1);  
        quick(a, p + 1, end);  
    }  
}  
  
/* function to print an array */  
void printArr(int a[], int n)  
{  
    int i;  
    for (i = 0; i < n; i++)  
        cout<<a[i]<< " ";  
}  
int main()  
{  
    int a[] = { 23, 8, 28, 13, 18, 26 };  
    int n = sizeof(a) / sizeof(a[0]);  
    cout<<"Before sorting array elements are - \n";  
    printArr(a, n);  
    quick(a, 0, n - 1);  
    cout<<"\nAfter sorting array elements are - \n";    
    printArr(a, n);  
      
    return 0;  
}  
```
_**Output**_:
```
Before Sorting array elements are -
23  8  28  13  18  26

After sorting array elements are -
8  13  18  23  26  28
```
---
### 4. Space-Time Complexity Analysis

**Space Complexity**

The **space complexity** for quicksort:  **O(log n)**.

**Time Complexities**

|      Case      | Time Complexities |               Situation                |
| :------------: | :---------------: | :------------------------------------: |
|  _Best Case_   |    O(n*log n)     |  the pivot element is always the middle element or near to the middle element.    |
| _Average Case_ |    O(n*log n)     |  the array elements are in jumbled order that is not properly ascending and not properly descending. |
|  _Worst Case_  |    O(n<sup>2</sup>)  |  the pivot element picked is either the greatest or the smallest element. |


---
### 5. Advantages and Disadvantages

#### Advantages:

- It is in-place since it uses only a small auxiliary stack.
- It requires only n (log n) time to sort n items.
- It has an extremely short inner loop.
- This algorithm has been subjected to a thorough mathematical analysis, a very precise statement can be made about performance issues.

#### Disadvantages:

- It is recursive. Especially, if recursion is not available, the implementation is extremely complicated.
- It requires quadratic (i.e., n2) time in the worst-case.
- It is fragile, i.e. a simple mistake in the implementation can go unnoticed and cause it to perform badly.

---

### 6. Applications

Quicksort works in the following way
Before diving into any algorithm, its very much necessary for us to understand what are the real world applications of it.
Quick sort provides a fast and methodical approach to sort any lists of things. Following are some of the applications where quick sort is used.

- **Commercial computing**: Used in various government and private organizations for the purpose of sorting various data like sorting of
accounts/profiles by name or any given ID, sorting transactions by time or locations, sorting files by name or date of creation etc.
- **Numerical computations**: Most of the efficiently developed algorithms use priority queues and inturn sorting to achieve accuracy in all the calculations.
- **Information search**: Sorting algorithms aid in better search of information and what faster way exists than to achieve sorting using quick sort.

Basically, quick sort is used everywhere for faster results and in the cases where there are space constraints.
