* In order to solve this problem, we can take two approaches:

1/. Create a new dummy node:

``` c#
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */

public class Solution {
    public ListNode MergeTwoLists(ListNode list1, ListNode list2) {
        var dummy = new ListNode();
        var dummyPointer = dummy;

        while(list1 != null && list2 != null)
        {
            if (list1.val <= list2.val)
            {
                dummyPointer.next = list1;
                list1 = list1.next;
            }

            else
            {
                dummyPointer.next = list2;
                list2 = list2.next;
            }
            dummyPointer = dummyPointer.next;
        }

        dummyPointer.next = list1 ?? list2;
        return dummy.next;
    }
}
```


2/. Recursive:
``` c#
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */

public class Solution {
    public ListNode MergeTwoLists(ListNode list1, ListNode list2) {
        if (list1 == null) return list2;

        else if (list2 == null) return list1;

        else if (list1.val <= list2.val)
        {
            list1.next = MergeTwoLists(list1.next, list2);
            return list1;
        }

        else
        {
            list2.next = MergeTwoLists(list1, list2.next);
            return list2;
        }
    }
}
```