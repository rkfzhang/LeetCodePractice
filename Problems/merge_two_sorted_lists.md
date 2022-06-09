# Solution
```
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(list1, list2) {
    
    head = curr = new ListNode();
    
    while (list1 && list2) {
        
        if (list2.val < list1.val) {
            curr.next = list2;
            list2 = list2.next;
        }
        else {
            curr.next = list1;
            list1 = list1.next;
        }
        
        curr = curr.next;
    }
    
    curr.next = list1 != null ? list1 : list2;
    return head.next
};
```
# Explanation
- sew the linked lists together in a new linked list
