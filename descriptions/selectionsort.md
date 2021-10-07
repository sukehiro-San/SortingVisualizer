# Sorting
___
 Sorting of an array means arranging the elements of the array in a specified order i.e., either in ascending order or descending order. There are several sorting techniques available e.g., bubble sort, insertion sort, selection sort, shell short, shuttle sort, etc. Here in this part, we’ll be discussing about the Selection Sort.

### Topic to be covered:
---
1.	Basics of Selection Sort
2.	Algorithm and pseudo code of selection sort
3.	How does selection sort work with an example. 
4.	Time complexity of selection sort
5.	Space complexity of selection sort
6.	Advantages of selection sort over other sorting techniques
7.	Disadvantages of selection sort over other sorting techniques
8.  Selection Sort Applications

# Selection Sort
>## 1. Basics of Selection Sort

Selection sort is a simple sorting algorithm, specifically an in-place comparison sort. 
An in-place sorting algorithm uses constant extra space for producing the output (modifies the given array in-place). It sorts the list only by modifying the order of the elements within the list.
The idea of a selection sort is that the array is divided into two parts, the sorted part at the left end and the unsorted part at the right end. Initially, the sorted part is empty and the unsorted part is the entire list.
The basic idea of a selection sort is to repeatedly select the smallest key in the remaining unsorted array and swapping with the leftmost element, and that element becomes a part of the sorted array. This process continues moving unsorted array boundary by one element to the right till it reaches the end of the array.
 

>## 2.1 Algorithm

Step 1 − Set small to location 0

Step 2 − Search the smallest element in the list

Step 3 − Swap with value at location small

Step 4 − Increment small to point to next element

Step 5 − Repeat until list is sorted

>## 2.2 Pseudocode

Pseudo code for Selection sort:

small = array[L]                //initialise small with the first array element

for I=L to U do

{

small = array[I], pos = I

/*loop to find the smallest element and its position */

For J=I to U do

{

If array[J] < small then

{

Small= array[J]

Pos=J

}

J=J+1

}		//end of the inner loop

/* swap the smallest element with 1st element */

Temp=array[I]

Array[I] = small

Array[pos]=temp

}		//end of the outer loop

}

END.

>## 3. Working of Selection Sort

For example, consider the following unsorted array to be sorted using selection sort

	[unsorted array] [15	6	13	22	3	52 	 2]   (here 2 is smallest in unsorted array)

__Step1:__
Choose the smallest element from unsorted array which is 2; put this smallest element in sorted part at 1st position. Now array becomes as follows:

    [sorted array] [2]		[unsorted array] [15	6	13	22	3	52]	   (here 3 is smallest in unsorted array)

__Step2:__ The second pass identifies 3 as the smallest element in remaining unsorted array. Adding 3 also in sorted part at 2nd position we have the following array:
 
	[sorted array] [2	3]		[unsorted array] [15	6	13	22	52]		(here 6 is smallest in unsorted array)

__Step3:__ In third pass, 6 is chosen as smallest and put at position 3 and our array becomes

	[sorted array] [2	3	6]		[unsorted array] [15	13	22	52]	(here 13 is smallest in unsorted array)

__Step4:__ This time 13 is moved to sorted part at 4th position

	[sorted array] [2	3	6	13]		[unsorted array] [15	22	52]	(here 15 is smallest in unsorted array)
    
__Step5:__ Fifth pass adds 15 to sorted part at the next position.

	[sorted array] [2	3	6	13	15]		[unsorted array] [22	52]	(here 22 and 52 are added in the sorted array)

__Step6:__ Sixth pass adds 22 and seventh pass adds 52 to sorted list

	[sorted array] [2	3	6	13	15	22	52]

__Step7:__ Therefore after seven passes the array is sorted.

# Function:
## Running Tests

To run tests, run the following command
___
```C++

    //selection sort in C++

    //including header file for input and output

    #include <iostream>

    using namespace std;

    //funtion to calculate the smallest from the unsorted second half of the array

    int smallest(int arr[], int k, int n)

    {

	int pos = k, small = arr[k], i;
	for (i = k + 1; i < n; i++)
	{
		if (arr[i] < small)
		{
			small = arr[i];
			pos = i;
		}
	}
	return pos; //returning the position of the smallest number
    }

    void selectionsort(int arr[], int n)
    
    {
    
    int k, pos, temp;
	for (k = 0; k < n; k++)
	{
		pos = smallest(arr, k, n);
		//swapping smallest element into the sorted array
		temp = arr[k];
		arr[k] = arr[pos];
		arr[pos] = temp;
	}
    }

    int main() 
    //main function
    {
	cout << endl
		 << "-------------------------------------------------THIS PROGRAM IS ABOUT SELCETION SORT--------------------------------------------------" << endl
		 << endl;
	int n, i; //n is the number elements you want to enter in the array
	cout << "Enter the number of elements you want to enter in the array " << endl;
	cout << "n: ";
	cin >> n;
	int array[n]; //declaration of the array of size n
	cout << "Enter " << n << " numbers for the array" << endl;

	//taking input from the user one by one
	for (i = 0; i < n; i++)
		cin >> array[i];

	//calling the selection sort function
	selectionsort(array, n);

	//printing the sorted array
	cout << "The sorted array after Selection Sort is as follows: " << endl;
	for (i = 0; i < n; i++)
		cout << array[i] << " ";
	return 0;
    }
```

>## 4. Time Complexity	 
|Case    |Complexity|Description|
|--------|----------|-----------|
|Best	 |  O(n2)   |It occurs when the array is already sorted|
|Worst	 |  O(n2)   |If we want to sort in ascending order and the array is in descending order then, the worst case occurs.|
|Average |	O(n2)   |It occurs when the elements of the array are in jumbled order (neither ascending nor descending). The time complexity of the selection sort is the same in all cases. At every step, you have to find the minimum element and put it in the right place. The minimum element is not known until the end of the array is not reached.


>## Space Complexity	O(1)
Since an extra variable temp is used.

#### Stability	No

|Cycle|	Number of Comparison|
|-----|---------------------|
|1st |(n-1)|
|2nd	    |(n-2)|
|3rd	    |(n-3)|
|...|	...
|last|	1

Number of comparisons: (n - 1) + (n - 2) + (n - 3) + ..... + 1 = n(n - 1) / 2 nearly equals to n^2.

Also, we can analyze the complexity by simply observing the number of loops. There are 2 loops so the complexity is n*n = n^2.

>## 6. Advantages of Selection Sort over other sorting techniques
* The good thing about selection sort is it never makes more than O(n) swaps and can be useful when memory write is a costly operation.
* Complexity of Selection Sort Selection sort is a sorting algorithm that is independent of the original order of elements in the array. 
  * In Pass 1, selecting the element with the smallest value calls for scanning all n elements
Thus, n–1 comparisons are required in the first pass. Then, the smallest value is swapped with the element in the first position. In Pass 2, selecting the second smallest value requires scanning the remaining n – 1 elements and so on. Therefore, (n – 1) + (n – 2) + ... + 2 + 1 = n(n – 1) / 2 = O(n2 ) comparisons
It is noted for its simplicity and also has performance advantages over Searching and Sorting 441 more complicated algorithms in certain situations. Selection sort is generally used for sorting files with very large objects (records) and small keys.
Advantages of Selection Sort 
∑ It is simple and easy to implement. 
∑ It can be used for small data sets. 
∑ It is 60 per cent more efficient than bubble sort.


>## 7. Disadvantages of selection sort over other sorting techniques

* In case of large data sets, the efficiency of selection sort drops as compared to insertion sort.

* This algorithm is not suitable for large data sets as its average and worst case complexities are of Ο(n2), where n is the number of items.

>## Selection Sort Applications
The selection sort is used when

•	A small list is to be sorted

•	Cost of swapping does not matter

•	Checking of all the elements is compulsory

•	Cost of writing to a memory matters like in flash memory (number of writes/swaps is O(n) as compared to O(n2) of bubble sort)