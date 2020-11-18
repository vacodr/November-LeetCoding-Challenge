# 56. Merge Intervals
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

link: https://leetcode.com/problems/merge-intervals/

Problem type: Medium
## Code
```java
class Solution {
    public int[][] merge(int[][] intervals) {
        
        if(intervals.length<=1)
            return intervals;
        
        List<int[]> list = new ArrayList();
        
        Arrays.sort(intervals,(a,b)->a[0]-b[0]);
        
       int arr[] = intervals[0];
        
        int i=1;
        
        while(i<intervals.length){
            
            if(arr[1]<intervals[i][0]){
                
                list.add(arr);
                arr=intervals[i];
            }
            else{
                
                arr[1]=Math.max(arr[1],intervals[i][1]);
            }
            
            i++;
        }
        
        list.add(arr);
        
        return list.toArray(new int[list.size()][]);
        
    }
}
```
