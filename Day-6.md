1283. Find the Smallest Divisor Given a Threshold
Given an array of integers nums and an integer threshold, we will choose a positive integer divisor and divide all the array by it and sum the result of the division. Find the smallest divisor such that the result mentioned above is less than or equal to threshold.

Each result of division is rounded to the nearest integer greater than or equal to that element. (For example: 7/3 = 3 and 10/2 = 5).

It is guaranteed that there will be an answer.

link: https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/

Problem type: Medium

# Code
```java
class Solution {
    public int smallestDivisor(int[] nums, int threshold) {
        int l = 1, r = 1000001;
        while(l <= r) {
            int mid = l + (r - l) / 2;
            long sum = getSum(nums, mid);
            if(sum > threshold)
                l = mid + 1;
            else 
                r = mid - 1;
        }
        
        return l;
    }
    
    private long getSum(int[] nums, int d) {
        long sum = 0;
        for(int num : nums)
            sum += (num - 1) / d + 1;
        return sum;
    }
}
```
