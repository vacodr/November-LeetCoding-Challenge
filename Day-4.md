# 310. Minimum Height Trees
A tree is an undirected graph in which any two vertices are connected by exactly one path. In other words, any connected graph without simple cycles is a tree.

Given a tree of n nodes labelled from 0 to n - 1, and an array of n - 1 edges where edges[i] = [ai, bi] indicates that there is an undirected edge between the two nodes ai and bi in the tree, you can choose any node of the tree as the root. When you select a node x as the root, the result tree has height h. Among all possible rooted trees, those with minimum height (i.e. min(h))  are called minimum height trees (MHTs).

Return a list of all MHTs' root labels. You can return the answer in any order.

The height of a rooted tree is the number of edges on the longest downward path between the root and a leaf.

 

link: https://leetcode.com/problems/minimum-height-trees/

Problem type: Medium

## Code
```java
class Solution {
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
      if(n==1)
        return Arrays.asList(0);
      
      //create a map
      List<Integer>[] map = new List[n];
      for(int i=0;i<n;i++)
        map[i] = new ArrayList<>();
      
      int[] indegree = new int[n];
        
      for(int edge[]:edges){
        int a=edge[0], b=edge[1];
        map[a].add(b);indegree[a]++;
        map[b].add(a);indegree[b]++;
      }
      
      Queue<Integer> queue = new LinkedList<>();
      
      for(int i=0;i<n;i++)
        if(indegree[i]==1)
          queue.add(i);
       
      List<Integer> result = new ArrayList<>();
      
      while(!queue.isEmpty()){
        result = new ArrayList<>();
        int size = queue.size();
        while(size--!=0){
          int node = queue.remove();
          result.add(node);
          for(int nebour: map[node]){
            if(--indegree[nebour]==1)
              queue.add(nebour);
          }
        }
      }
      
      return result;
    }
}
```
