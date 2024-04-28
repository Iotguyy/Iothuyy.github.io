---
title: Merge Sort
date: 2022-05-21 12:00:00 -500
categories: [algorithms,computer science,sorting]
tags: [algorithms,computer science,sorting]     # TAG names should always be lowercase
---

# Whats Merge sort

Merge sort is a divide-and-conquer algorithm based on the idea of breaking down a list into several sub-lists until each sublist consists of a single element and merging those sublists in a manner that results into a sorted list.



- **Divide:** Recursively divide the list or array into two halves until each sublist contains only one element.
- **Conquer:** Each sublist is sorted individually using the merge sort algorithm.
- **Merge:** The sorted sublists are merged back together in sorted order. This merging process continues until all elements from both sublists have been merged.





<img src="https://www.programiz.com/sites/tutorial2program/files/merge-sort-example_0.png" width="350" height="350"/>

## Code Implementation



```javascript
// Function to merge two sorted parts of array
function merge(arr, left, middle, right) {
    
    // Length of both sorted aub arrays
    let l1 = middle - left + 1;
    let l2 = right - middle;
    // Create new subarrays
    let arr1 = new Array(l1);
    let arr2 = new Array(l2);
    
    // Assign values in subarrays
    for (let i = 0; i < l1; ++i) {
        arr1[i] = arr[left + i];
    }
    for (let i = 0; i < l2; ++i) {
        arr2[i] = arr[middle + 1 + i];
    }

    // To travesrse and modify main array
    let i = 0,
        j = 0,
        k = left;
        
    // Assign the smaller value for sorted output
    while (i < l1 && j < l2) {
        if (arr1[i] < arr2[j]) {
            arr[k] = arr1[i];
            ++i;
        } else {
            arr[k] = arr2[j];
            j++;
        }
        k++;
    }
    // Update the remaining elements
    while (i < l1) {
        arr[k] = arr1[i];
        i++;
        k++;
    }
    while (j < l2) {
        arr[k] = arr2[j];
        j++;
        k++;
    }
}

// Function to implement merger sort in javaScript
function mergeSort(arr, left, right) {
    if (left >= right) {
        return;
    }
    
    // Middle index to create subarray halves
    let middle = left + parseInt((right - left) / 2);
    
    // Apply mergeSort to both the halves
    mergeSort(arr, left, middle);
    mergeSort(arr, middle + 1, right);
    
    // Merge both sorted parts
    merge(arr, left, middle, right);
}

// Input array
const arr =  [ 38, 27, 43, 10]

// Display input array
console.log("Original array: " + arr);

// Apply merge sort function
mergeSort(arr, 0, arr.length - 1);

// Display output
console.log("After sorting: " + arr);

```

---

![meme](https://prepinstadotcom.s3.ap-south-1.amazonaws.com/wp-content/uploads/2020/07/Merge-sort-in-Java-Meme.jpg)