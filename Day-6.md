## 1217. Minimum Cost to Move Chips to The Same Position
We have n chips, where the position of the ith chip is position[i].

We need to move all the chips to the same position. In one step, we can change the position of the ith chip from position[i] to:

position[i] + 2 or position[i] - 2 with cost = 0.
position[i] + 1 or position[i] - 1 with cost = 1.
Return the minimum cost needed to move all the chips to the same position.

link: https://leetcode.com/problems/minimum-cost-to-move-chips-to-the-same-position/

Problem type: Easy

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
