* In order to solve this problem, we need to follow **Two Pointers** approach with Dummy Node

``` c#
public class Solution {
    public ListNode RemoveNthFromEnd(ListNode head, int n) {
        var dummy = new ListNode
        {
            val = 0,
            next = head
        };

        var left = dummy;
        var right = dummy;

        while (n > 0)
        {
            right = right.next;
            n--;
        }

        while (right.next != null)
        {
            left = left.next;
            right = right.next;
        }

        left.next = left.next.next;
        return dummy.next;
    }
}
```

![[Nth-Node-Linked-List-1.png]]