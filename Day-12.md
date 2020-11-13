# 47. Permutations II
Given a collection of numbers, nums, that might contain duplicates, return all possible unique permutations in any order.

link: https://leetcode.com/problems/permutations-ii/

Problem type: Medium
## Code
```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        helper(res, nums, 0, new ArrayList<Integer>());
        return res;
    }
    
    private void helper(List<List<Integer>> list, int[] nums, int pos, List<Integer> curList) {
        if (pos >= nums.length) {
            list.add(new ArrayList<Integer>(curList));
            return;
        } 
        for (int i = pos; i < nums.length; i++) {
            if(i != pos && nums[i] == nums[pos]) continue;
            boolean found = false;
            for(int j = pos+1; j < i; j++) {
                if(nums[j] == nums[i]) {
                    found = true;
                    break;
                }
            }
            if(found) continue;
            // exchange
            int temp = nums[pos];
            nums[pos] = nums[i];
            nums[i] = temp;
            curList.add(nums[pos]);
            // call next;
            helper(list, nums, pos+1, curList);
            // exchange back;
            temp = nums[pos];
            nums[pos] = nums[i];
            nums[i] = temp;
            curList.remove(curList.size()-1);
        }
    } 
}
```
