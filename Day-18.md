# 394. Decode String
Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there won't be input like 3a or 2[4].

Link: https://leetcode.com/problems/decode-string/

Problem type: Medium
## Code
```java
class Solution {
    public String decodeString(String s) {
        
        Stack <StringBuilder> str = new Stack<>();
        Stack <Integer> in = new Stack<>();
        
        StringBuilder curr = new StringBuilder();
        int m=0;
        
        for(char c:s.toCharArray()){
            
            if(Character.isDigit(c)){
                
                m= m*10+(c-'0');
            }else if (Character.isLetter(c)){
                
                curr.append(c);
            }else if (c=='['){
                
                str.push(curr);
                in.push(m);
                
                curr= new StringBuilder();
                m=0;
            }else if (c==']'){
                
                StringBuilder temp = curr;
                int freq = in.pop();
                curr= str.pop();
                
                while(freq-->0){
                    
                    curr.append(temp);
                }
                
                m=0;
            }
            
            
        }
        
        return curr.toString();
        
        
        
    }
}
```
