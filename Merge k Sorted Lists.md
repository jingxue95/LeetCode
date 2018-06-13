Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

***Example:***

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```
``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    private ListNode mergeTwoList (ListNode list1, ListNode list2){
        if(list1 == null){
            return list2;
            
        }
        if(list2 == null){
            return list1;
        }
        
        ListNode newNode = new ListNode(0);
        ListNode temp = newNode;
        while(list1!= null && list2 != null){
            ListNode newTemp = new ListNode(0);
            if(list1.val <= list2.val){
                newTemp.val = list1.val;
                temp.next = list1;
                list1 = list1.next;
            }
            else{
                newTemp.val = list2.val;
                temp.next = list2;
                list2 = list2.next;
            }
            temp.next = newTemp;
            temp = temp.next;
        }
        
        if(list1 != null){
            temp.next = list1;
        }else{
            temp.next = list2;
        }
        return newNode.next;
    }
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists == null || lists.length == 0){
            return null;
        }
        if(lists.length == 1){
            return lists[0];
        }
        int len = lists.length;
        while(len > 1){
            int mid = (len + 1)/2;
            for(int i = 0; i < mid ; i ++){
                if(i + mid <= len-1){
                    lists[i] = mergeTwoList(lists[i],lists[mid+i]);    
                }
            }
            len = mid;
        }
        
        
        
        return lists[0];
        
        
    }
}
```
