
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
***Example 1:***

Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
***Example 2:***

Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]

```java
class Solution {
    private void dfs(int[] candidates, int target, List<Integer> list, List<List<Integer>> result, int sum, int pos){
        if(sum == target){
            result.add(list);
            return;
        }else if(sum > target){
            
            return;
        }
        for(int i = pos; i < candidates.length; i++){
            List<Integer> newList = new ArrayList<Integer>(list);
            int temp = sum + candidates[i];
            pos = i;
            newList.add(candidates[i]);
            dfs(candidates, target, newList, result, temp, pos);
        }
        
    }
    
    
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        List<Integer> list = new ArrayList<Integer>();
        dfs(candidates, target, list, result, 0 ,0);
        return result;
        
    }
}
```
