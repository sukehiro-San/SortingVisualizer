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

### 3. Working

For an array with **N** elements there will be **N-1** iterations and **N-1** sub-iterations for comparing adjacent elements thus making the time complexity **O(n<sup>2</sup>)**.
The working of bubble sort algorithm is explained with following example .
_Array_:  
| 8 | 6 | 2 | 1 | 9 |
|:-:|:-:|:-:|:-:|:-:|

**_Iteration 1:_**
_Step 1:_ Starting from first element as current index. Since _eight_ is greater than the element on the right which is _six_ i.e. **8 > 6**. Therefore _8_ will be swapped with _6_. Thus making the array:
| 6 | 8 | 2 | 1 | 9 |
|:-:|:-:|:-:|:-:|:-:|

_Step 2:_ Now that _eight_ and _six_ have been swapped, now moving the current index to _second_ element that is now _8_ after swapping. Since _eight_ is greater than the element on the right which is _two_ i.e. **8 > 2**. Therefore _8_ will be swapped with _2_ Thus making the array:
| 6 | 2 | 8 | 1 | 9 |
|:-:|:-:|:-:|:-:|:-:|

_Step 3:_ Now that _eight_ and _two_ have been swapped, now moving the current index to _third_ element that is now _8_ after swapping. Since _eight_ is greater than the element on the right which is _one_ i.e. **8 > 1**. Therefore _8_ will be swapped with _1_ Thus making the array:
| 6 | 2 | 1 | 8 | 9 |
|:-:|:-:|:-:|:-:|:-:|

_Step 4:_ Now that _eight_ and _one_ have been swapped, now moving the current index to _fourth_ element that is now _8_ after swapping. Since _eight_ is smaller than the element on the right which is _nine_ i.e. **8 < 9**. Therefore no swaps will be made. Thus the array remain the same.
| 6 | 2 | 1 | 8 | 9 |
|:-:|:-:|:-:|:-:|:-:|

_Step 5:_ Now moving the current index to _fifth_ element that is now _9_, but there are no more elements on the _right_ index. We observe that _9_ is the _greatest_ element in the array and has now been moved to the _last_ index. Now Steps 1-4 need to be repeated until all elements are in correct order i.e. ascending order. That can be achieved in further _3_ iterations. The end result of each iteration is given below.

**_Iteration 2:_**
| 6 | 2 | 1 | 8 | 9 |
|:-:|:-:|:-:|:-:|:-:|

**_Iteration 3:_**
| 2 | 1 | 6 | 8 | 9 |
|:-:|:-:|:-:|:-:|:-:|

**_Iteration 4:_**
| 1 | 2 | 6 | 8 | 9 |
|:-:|:-:|:-:|:-:|:-:|

After the **4<sup>th </sup>** iteration we can observe that the array is perfectly sorted. Thus bubble sort requires **(N-1)** iterations, where **N** is the number of elements.
The above working can be tested with the following **C++ program** for bubble sort algorithm.

// Optimized bubble sort in C++

```
#include <iostream>
using namespace std;

// perform bubble sort
void bubbleSort(int array[], int size) {

  // loop to access each array element
  for (int step = 0; step < (size-1); ++step) {

    // check if swapping occurs
    int swapped = 0;

    // loop to compare two elements
    for (int i = 0; i < (size-step-1); ++i) {

      // compare two array elements
      // change > to < to sort in descending order
      if (array[i] > array[i + 1]) {

        // swapping occurs if elements
        // are not in intended order
        int temp = array[i];
        array[i] = array[i + 1];
        array[i + 1] = temp;

        swapped = 1;
      }
    }

    // no swapping means the array is already sorted
    // so no need of further comparison
    if (swapped == 0)
      break;
  }
}

// print an array
void printArray(int array[], int size) {
  for (int i = 0; i < size; ++i) {
    cout << "  " << array[i];
  }
  cout << "\n";
}

int main() {
  int data[] = {-2, 45, 0, 11, -9};

  // find the array's length
  int size = sizeof(data) / sizeof(data[0]);

  bubbleSort(data, size);

  cout << "Sorted Array in Ascending Order:\n";
  printArray(data, size);
}
```

_Output:_

```
Sorted Array in Ascending Order:
1  2  6  8  9
```

---

### 4. Space and Time Complexity Analysis

#### Space Complexity

Auxiliary Space Complexity : **O(1)**

#### Time Complexities

|      Case      | Time Complexities |               Situation                |
| :------------: | :---------------: | :------------------------------------: |
|  _Best Case_   |       O(n)        |   Array Elements are already Sorted.   |
| _Average Case_ | O(n<sup>2</sup>)  | Few Array Elements are in wrong order. |
|  _Worst Case_  | O(n<sup>2</sup>)  | All Array Elements are in wrong order. |

---

### 5. Advantages and Disadvantages

#### Advantages:

- The primary advantage of the bubble sort is that it is popular and easy to implement.
- Furthermore, in the bubble sort, elements are swapped in place without using additional temporary storage, so the space requirement is at a minimum

#### Disadvantages:

- The main disadvantage of the bubble sort is the fact that it does not deal well with a list containing a huge number of items. This is because the bubble sort requires n-squared processing steps for every n number of elements to be sorted. As such, the bubble sort is mostly suitable for academic teaching but not for real-life applications.

---

### 6. Applications

Bubble sort is used if

- complexity does not matter
- short and simple code is preferred
- demonstration of different types of time complexities i.e. O(n), O(n<sup>2</sup>) within a single algorithm.
