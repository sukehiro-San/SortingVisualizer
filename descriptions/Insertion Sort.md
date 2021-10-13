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

## Algorithm
Now we have a bigger picture of how this sorting technique works, so we can derive simple steps by which we can achieve insertion sort.
```sh
Step 1 − If it is the first element, it is already sorted. return 1;

Step 2 − Pick next element

Step 3 − Compare with all elements in the sorted sub-list

Step 4 − Shift all the elements in the sorted sub-list that is greater than the 
         value to be sorted
         
Step 5 − Insert the value

Step 6 − Repeat until list is sorted
```

## Working of Insertion sort Algorithm
* <b>We take an unsorted array for our example.</b>

![image](https://user-images.githubusercontent.com/59999317/137070380-1e334d01-ceee-4821-8032-e78f52e51539.png)

* <b>Insertion sort compares the first two elements.</b>

![image](https://user-images.githubusercontent.com/59999317/137071317-4cb3ba05-20e8-4e50-8195-6fa6e01ae5b1.png)

* <b>It finds that both 14 and 33 are already in ascending order. For now, 14 is in sorted sub-list.</b>

![image](https://user-images.githubusercontent.com/59999317/137071342-83a8dd88-9cff-4cc4-a9a4-7b89609d4a2c.png)

* <b>Insertion sort moves ahead and compares 33 with 27.</b>

![image](https://user-images.githubusercontent.com/59999317/137071421-5192a6d2-445d-4bd7-b77c-a7b07eae65a8.png)

* <b>And finds that 33 is not in the correct position.</b>

![image](https://user-images.githubusercontent.com/59999317/137071433-593556c0-11ee-4f21-a201-7adf5b8f4680.png)

* <b>It swaps 33 with 27. It also checks with all the elements of sorted sub-list. Here we see that the sorted sub-list has only one element 14, and 27 is greater than 14. Hence, the sorted sub-list remains sorted after swapping.</b>

![image](https://user-images.githubusercontent.com/59999317/137071448-21886256-a021-45c3-9410-12066723502f.png)

* <b>By now we have 14 and 27 in the sorted sub-list. Next, it compares 33 with 10.</b>

![image](https://user-images.githubusercontent.com/59999317/137071459-02057ea8-6271-4a44-88d1-8db545962be0.png)

* <b>These values are not in a sorted order.</b>

![image](https://user-images.githubusercontent.com/59999317/137071483-2abe14b9-d025-4187-9c52-58f47c91e15d.png)

* <b>So we swap them.</b>

![image](https://user-images.githubusercontent.com/59999317/137071514-855f53f1-2473-4159-a3a9-24de68985f90.png)

* <b>However, swapping makes 27 and 10 unsorted.</b>

![image](https://user-images.githubusercontent.com/59999317/137071536-abb806f5-c8e7-4477-b6ce-993c72347687.png)

* <b>Hence, we swap them too.</b>

![image](https://user-images.githubusercontent.com/59999317/137071548-4d667524-f8b5-4ce4-b213-47809f4d5c2a.png)

* <b>Again we find 14 and 10 in an unsorted order.</b>

![image](https://user-images.githubusercontent.com/59999317/137071563-2a5d9810-454a-4463-84ac-7dade2df8629.png)

* <b>We swap them again. By the end of third iteration, we have a sorted sub-list of 4 items.</b>

![image](https://user-images.githubusercontent.com/59999317/137071572-fda62b1d-bde9-4d24-8b33-caf16db32d23.png)

><b>This process goes on until all the unsorted values are covered in a sorted sub-list. Now we shall see some programming aspects of insertion sort.</b>

---

## Pseudo code
```js
procedure insertionSort( A : array of items )
   int holePosition
   int valueToInsert
	
   for i = 1 to length(A) inclusive do:
	
      /* select value to be inserted */
      valueToInsert = A[i]
      holePosition = i
      
      /*locate hole position for the element to be inserted */
		
      while holePosition > 0 and A[holePosition-1] > valueToInsert do:
         A[holePosition] = A[holePosition-1]
         holePosition = holePosition -1
      end while
		
      /* insert the number at hole position */
      A[holePosition] = valueToInsert
      
   end for
	
end procedure
```
---

## Implementation of Insertion sort
```java
// Java program for implementation of Insertion Sort
class InsertionSort {
	/*Function to sort array using insertion sort*/
	void sort(int arr[])
	{
		int n = arr.length;
		for (int i = 1; i < n; ++i) {
			int key = arr[i];
			int j = i - 1;

			/* Move elements of arr[0..i-1], that are
			greater than key, to one position ahead
			of their current position */
			while (j >= 0 && arr[j] > key) {
				arr[j + 1] = arr[j];
				j = j - 1;
			}
			arr[j + 1] = key;
		}
	}

	/* A utility function to print array of size n*/
	static void printArray(int arr[])
	{
		int n = arr.length;
		for (int i = 0; i < n; ++i)
			System.out.print(arr[i] + " ");

		System.out.println();
	}

	// Driver method
	public static void main(String args[])
	{
		int arr[] = { 12, 11, 13, 5, 6 };

		InsertionSort ob = new InsertionSort();
		ob.sort(arr);

		printArray(arr);
	}
} 
```
---

## Insertion sort complexity
Now, let's see the time complexity of insertion sort in best case, average case, and in worst case. We will also see the space complexity of insertion sort.


> ## Time Complexity	 
|Case    |Complexity|Description|
|--------|----------|-----------|
|Best	 |  O(n)   |It occurs when there is no sorting required, i.e. the array is already sorted. The best-case time complexity of insertion sort is O(n).|
|Worst	 |  O(n<sup>2</sup>)   |It occurs when the array elements are in jumbled order that is not properly ascending and not properly descending. The average case time complexity of insertion sort is O(n<sup>2</sup>).|
|Average |  O(n<sup>2</sup>)   |It occurs when the array elements are required to be sorted in reverse order. That means suppose you have to sort the array elements in ascending order, but its elements are in descending order. The worst-case time complexity of insertion sort is O(n<sup>2</sup>).|

> ## Space Complexity
| Space Complexity  | Stable |
| ------------- |:-------------:|
| O(1)      | YES     |
* The space complexity of insertion sort is O(1). It is because, in insertion sort, an extra variable is required for swapping.
---

## Advantages of Insertion sort over other sorting techniques
* The pure simplicity of the algorithm.
* The relative order of items with equal keys does not change.
* The ability to sort a list as it is being received.
* Efficient for small data sets, especially in practice than other quadratic algorithms — i.e. O(n²).
* It only requires a constant amount of additional memory space — O(1).

## Disadvantages of Insertion sort over other sorting techniques
* It is less efficient on list containing more number of elements.As the number of elements increases the performance of the program would be slow.There is a single disadvantage: it is  O(N<sup>2</sup>). on average, and so for large  N  it is usually very slow.
* Insertion sort needs a large number of element shifts.
