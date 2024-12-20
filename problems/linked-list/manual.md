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



## [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

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

func middleNode(head *ListNode) *ListNode {
    fast := head
    slow := head
    
    for fast != nil && fast.Next != nil {
    fast = fast.Next.Next
    slow = slow.Next
    }
    
    return slow
}
```



## [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

- Time: ***O(n)***
- Memory: ***O(n)***

```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    dummy := &ListNode{Val: 0}
    point := dummy

    var temp int
    var sum int

    for l1 != nil || l2 != nil {
        localTemp := 0

        if l1 == nil {
            sum = l2.Val
            l2 = l2.Next
        } else if l2 == nil {
            sum = l1.Val
            l1 = l1.Next
        } else {
            sum = l1.Val + l2.Val
            l1 = l1.Next
            l2 = l2.Next
        }

        localTemp = (temp + sum) / 10
        sum = (temp + sum) % 10
        
        temp = localTemp

        point.Next = &ListNode{Val: sum}
        point = point.Next
    }

    if temp != 0 {
        point.Next = &ListNode{Val: temp}
    }

    return dummy.Next
}
```