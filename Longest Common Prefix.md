Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

***Example 1:***

Input: ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
Note:

All given inputs are in lowercase letters a-z.

Solution:
```java
class Solution {
    private String commonPrefix(String a, String b){
        int len = 0;
        String result = "";
        if(a.length() < b.length()){
            len = a.length();
        }else{
            len = b.length();
        }
        for(int i = 0; i < len; i ++){
            if(a.charAt(i) == b.charAt(i)){
                result = result + a.charAt(i);
            }else{
                return result;
            }
        }
        return result;
    }
    public String longestCommonPrefix(String[] strs) {
        if(strs == null || strs.length == 0){
            return "";
        }
        if(strs.length == 1){
            return strs[0];
        }
        String result = strs[0];
        for(int i = 0; i < strs.length; i ++){
            result = commonPrefix(result, strs[i]);
        }
        
        return result;
    }
}
```
