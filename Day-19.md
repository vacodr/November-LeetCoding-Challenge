# 81. Search in Rotated Sorted Array II
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,0,1,2,2,5,6] might become [2,5,6,0,0,1,2]).

You are given a target value to search. If found in the array return true, otherwise return false.

Link: https://leetcode.com/problems/search-in-rotated-sorted-array-ii/

Problem type: Medium
## Code
```java
class Solution {
    public boolean search(int[] A, int target) {
    int start = 0;
    int end = A.length - 1;
    while (start <= end) {
        int mid = start + (end - start) ;
        if (A[mid] == target) 
            return true;
        
        else if (A[start] == A[mid])
            start++;
        else if (A[end] == A[mid])
            end--;
        else if (A[start] <= target && target <= A[mid]) 
            end = mid;
        else if (A[mid] < target && target <= A[end])
            start = mid + 1;
        else if (A[start] > A[mid]) 
            end = mid;
        else   
            start = mid + 1;
    }
    return false;
}
}
```
