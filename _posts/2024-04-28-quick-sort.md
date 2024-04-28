---
title: Quick Sort
date: 2022-05-21 12:00:00 -500
categories: [algorithms,computer science,sorting]
tags: [algorithms,computer science,sorting]     # TAG names should always be lowercase
---

# Whats Quick sort

QuickSort is a sorting algorithm based on the Divide and Conquer algorithm that picks an element as a pivot and partitions the given array around the picked pivot by placing the pivot in its correct position in the sorted array.


## How does QuickSort work?
- The key process in QuickSort is the `partition()` function.
- The goal of partitioning is to place the pivot (any element can be chosen) at its correct position in the sorted array.
- All smaller elements are placed to the left of the pivot, and all greater elements are placed to the right.
- Partitioning is done recursively on each side of the pivot after it's correctly positioned.
- This recursive partitioning ultimately sorts the array.




---

  



![example](https://www.geeksforgeeks.org/wp-content/uploads/gq/2014/01/QuickSort2.png)
## Code Implementation



```javascript
function partition(arr, low, high) { 
	let pivot = arr[high]; 
	let i = low - 1; 

	for (let j = low; j <= high - 1; j++) { 
		// If current element is smaller than the pivot 
		if (arr[j] < pivot) { 
			// Increment index of smaller element 
			i++; 
			// Swap elements 
			[arr[i], arr[j]] = [arr[j], arr[i]]; 
		} 
	} 
	// Swap pivot to its correct position 
	[arr[i + 1], arr[high]] = [arr[high], arr[i + 1]]; 
	return i + 1; // Return the partition index 
} 

function quickSort(arr, low, high) { 
	if (low >= high) return; 
	let pi = partition(arr, low, high); 

	quickSort(arr, low, pi - 1); 
	quickSort(arr, pi + 1, high); 
} 

let arr = [10, 80, 30, 90, 40]; 
console.log("Original array: " + arr); 

quickSort(arr, 0, arr.length - 1); 
console.log("Sorted array: " + arr);

```

---

![meme](https://prepinstadotcom.s3.ap-south-1.amazonaws.com/wp-content/uploads/2020/07/Quick-sort-Meme-C.png)

