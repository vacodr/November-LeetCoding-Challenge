# 804. Unique Morse Code Words
International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: "a" maps to ".-", "b" maps to "-...", "c" maps to "-.-.", and so on.

For convenience, the full table for the 26 letters of the English alphabet is given below:

[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cab" can be written as "-.-..--...", (which is the concatenation "-.-." + ".-" + "-..."). We'll call such a concatenation, the transformation of a word.

Return the number of different transformations among all words we have.

Link: https://leetcode.com/problems/unique-morse-code-words/

Problem Type: Easy

## Code
```java
class Solution {
    public int uniqueMorseRepresentations(String[] words) {
        
        String[] morse = new String[]{".-","-...","-.-.","-..",".","..-.",
                                      "--.","....","..",".---","-.-",".-..","--",
                                      "-.","---",".--.","--.-",".-.","...","-","..-",
                                      "...-",".--","-..-","-.--","--.."};
        
        
        Set<String> hash = new HashSet<>();
        
        for(String f : words){
            
           StringBuffer s = new StringBuffer();
            
            for(char c:f.toCharArray()){
                
              s.append(morse[c-'a']);  
            }
            
            hash.add(s.toString());
                     
        }
        
        
        return hash.size();
        
    }
}
```
