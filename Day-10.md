# Flipping an Image
Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

link: https://leetcode.com/problems/flipping-an-image/

Problem type : Easy
## Code
```java
class Solution {
    public int[][] flipAndInvertImage(int[][] A) {
        
        int temp;
        int l= A.length;
        
        if(l==1){
            
            if(A[0][0]==0)
                A[0][0]=1;
            else
                A[0][0]=0;
            return A;
        }
        
        //System.out.println(l);
        
        for(int i=0;i<A.length;i++){
            
             l= A[i].length;
           // System.out.printf(l+" ");
            
            for(int j=0;j<l/2;j++){
                
                temp= A[i][j];
                
                A[i][j]=A[i][l-j-1];
                
                A[i][j] = (A[i][j]==0) ? 1:0;
                
                A[i][l-j-1]=temp;
                
                A[i][l-j-1]=(A[i][l-j-1]==0) ?1:0;
                
            }
            
            if(l%2!=0){
                
                    if(A[i][l/2]==0)
                        A[i][l/2]=1;
                    else
                        A[i][l/2]=0;
                }
        }   
        return A;
    }
}
```
