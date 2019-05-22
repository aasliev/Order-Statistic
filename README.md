# Order-Statistic
Implement Order Statistic Algorithms

In part one we had to implement Order Statistic algorithm and run various array to calculate CPU time.

1. What is Order Statistic?
2. Pseudo code
3. Results
4. Comparing Median Order Statistic, QuickSort and Randomized QuickSort.
5. Summary 

> What is Order Statistic?

Suppose we have an array and we want to find how does elements of the array behave. For instance, we want to find if the kth 
(k in range of number of elements) element is smaller than P(any number). There are multiples ways to find out. 
a. Sort up to kth element using bubble or selection sort. 
b. Sort array completely using quick, heap or merge sort. 
c. Order statistic algorithm 

Part a: First option is good when you have small number of elements. However, this algorithm become slower when array is big and k 
is closer to n/2 (n is number of elements). We will have O(n^2). 

Part b: Using quick, heap or merge sort the best time we can get is O(nlogn). Just sort the array and return (k-1)th element. 

Part c. Using Order Statistic we can find the kth element in O(n ) time . We know that partition function in QuickSort divides array 
into two sub-arrays, left side will be less than or equal to pivot, and the right side is always greater than pivot. 
Using this concept we can drop half of the array and save the time. You can write this algorithm in many ways, Randomized Pivot or 
you choose a pivot(deterministic solution).

For the deterministic solution, first we divide the array into n/5 subarrays. Second, find the median of all subarrays. Third, find median
of all medians. Finally, use it as the pivot. After each iteration you will have at least n/4 elements less than the pivot and 
at most 3n/4 elements greater than pivot.

> Pseudo Code (Order Statistic)

findKthElement(arr, left, right,k)
if(right-left+1>=k){ 
	indexPivot = partition(arr, left, right)
	if(indexPivot+1==k)
		return arr[indexPivot]
	if(indexPivot+1 > k) // k is inside the left subarray
		return findKthElement(arr,left,indexPivot-1,k)
	if (indexPivot+1<k) //k is inside the right sub-array
		return findKthElement(arr, indexPivot+1, right, k-indexPivot-1)

> Results

We ran Order Statistics algorithm 5 times for [100, 300, 500, 1000, 2000, 4000] number of elements in a range of [5000, 8000, 10000]. 
We are using microsecond as a unit of time.

5000					
	     1st	      2nd	   3rd	      4th	     5th
100	  263.86	  241.26	227.85	  181.58	  212.03
300	  814.01	  740.89	709.76	  702.84    719.94
500	  1385.68	  1422.16	1584.97	  1409.09	  1445.8
1000	3035.94	  2839.49	1562.38	  2724.12	  2867.08
2000	6391.34	  6143.39	6193.01	  5957.76	  5906.26
4000	13736.24	15493.4	13881.42	13413.73	13095.81


8000					
	      1st	     2nd	      3rd	      4th	      5th
100	  227.52	  233.5	    214.56	  219.77	  157.04
300	  699.63	  722.45	  850.76	  735.33	  720.14
500	  1486.71	  1216.18	  1411.81	  1352.36	  1472.53
1000	2926.27	  3151.43	  2770.97	  2898.74	  2799.87
2000	5751.06	  6034.64	  5790.94	  5652.29	  6123.19
4000	13096.33	13106.56	13073.46	11990.49	12720.73


10000					
	1st	2nd	3rd	4th	5th
100	  227.62	  230.35	  209.42	  219.51	  240.23
300	  776.18	  767.9	    807.81	  824.88	  667.53
500	  1365	    1427.97	  1546.26	  1485.67	  1448.25
1000	2705.93	  2836.42	  2771.29	  2879.84	  2720.82
2000	5877.16	  6456.71	  6825.24	  6337.59	  6604.35
4000	11966.05	12943.04	12790.29	12865.97	13341.76


> Summary

Order Statistic algorithms have best running time for finding the ith element when we have big arrays. 
From the algorithms that we have above the Randomized QuickSort would be the best to find ith element, 
however Deterministic Solution (Median Selection Algorithm) would be better to find the median of the array.
