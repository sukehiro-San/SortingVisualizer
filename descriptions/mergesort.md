[# Merge Sort.]


Merge sort is one of the most efficient sorting algorithms.
Merge sort is the algorithm which follows divide and conquer approach. Consider an array A of n number of elements. The algorithm processes the elements in 3 steps.

If A Contains 0 or 1 elements then it is already sorted, otherwise, Divide A into two sub-array of equal number of elements.
Conquer means sort the two sub-arrays recursively using the merge sort.
Combine the sub-arrays to form a single final sorted array maintaining the ordering of the array.
The main idea behind merge sort is that, the short list takes less time to be sorted.

[**Complexity**]

Complexity	      Best case	  Average Case	 Worst Case
Time Complexity  	O(n log n)	 O(n log n)	   O(n log n)
Space Complexity		O(n)

[**Comparison with other sort algorithms**]

Although heapsort has the same time bounds as merge sort, it requires only Θ(1) auxiliary space instead of merge sort's Θ(n). 
On typical modern architectures, efficient quicksort implementations generally outperform merge sort for sorting RAM-based arrays.
On the other hand, merge sort is a stable sort and is more efficient at handling slow-to-access sequential media. Merge sort is often the best choice 
for sorting a linked list: in this situation it is relatively easy to implement a merge sort in such a way that it requires only Θ(1) extra space, and
the slow random-access performance of a linked list makes some other algorithms (such as quicksort) perform poorly, and others (such as heapsort) completely impossible.

As of Perl 5.8, merge sort is its default sorting algorithm (it was quicksort in previous versions of Perl). In Java, the Arrays.sort() methods use 
merge sort or a tuned quicksort depending on the datatypes and for implementation efficiency switch to insertion sort when fewer than seven array elements are
being sorted. The Linux kernel uses merge sort for its linked lists.Python uses Timsort, another tuned hybrid of merge sort and insertion sort, that has
become the standard sort algorithm in Java SE 7 (for arrays of non-primitive types), on the Android platform, and in GNU Octave.
