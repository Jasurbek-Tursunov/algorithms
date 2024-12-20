## [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

- Time: ***O(n)***
- Memory: ***O(1)***

```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

func removeNthFromEnd(head *ListNode, n int) *ListNode {
    dummy := &ListNode{Val: 0, Next: head}
    fast := dummy
    slow := dummy

    for i := 0; i < n; i++ {
        fast = fast.Next
    }

    for fast.Next != nil {
        fast = fast.Next
        slow = slow.Next
    }

    slow.Next = slow.Next.Next

    return dummy.Next
}
```



## [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

- Time: ***O(n)***
- Memory: ***O(1)***

```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
 
func reverseList(head *ListNode) *ListNode {
    var prev *ListNode
    fast := head
    slow := head

    for fast != nil {
        fast = fast.Next
        slow.Next = prev
        prev = slow
        slow = fast
    }

    return prev
}
```