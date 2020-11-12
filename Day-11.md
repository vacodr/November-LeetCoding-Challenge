# Valid Square
Given the coordinates of four points in 2D space, return whether the four points could construct a square.

The coordinate (x,y) of a point is represented by an integer array with two integers.

link: https://leetcode.com/problems/valid-square/

Problem type: Medium
## Code
```java
class Solution {
    public boolean validSquare(int[] p1, int[] p2, int[] p3, int[] p4) {
        
        Set<Integer> h = new HashSet<>();
        
       h.add(distance(p1,p2));
       h.add(distance(p1,p3));
       h.add(distance(p1,p4));
       h.add(distance(p2,p3));
       h.add(distance(p2,p4));
       h.add(distance(p3,p4));
        
        return !h.contains(0) && h.size()==2;     
    }
    
   private int distance(int a[], int b[]){
       
       return (a[0]-b[0])*(a[0]-b[0]) + (a[1]-b[1])*(a[1]-b[1]) ;        
    }
        
}
```
