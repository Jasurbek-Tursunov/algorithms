## [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

- <span style="color:red">**Time Limit Exceeded**</span>

```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

func Middle(head *ListNode) *ListNode {
    fast := head
    slow := head

    for fast != nil && fast.Next != nil {
        fast = fast.Next.Next
        slow = slow.Next
    }

    return slow
}


func Reverse(head *ListNode) *ListNode {
    var prev *ListNode
    point := head
    temp := head

    for point != nil {
        point = point.Next
        temp.Next = prev
        prev = temp
        temp = point
    }

    return prev
}


func isPalindrome(head *ListNode) bool {
    point1 := head
    point2 := Reverse(Middle(head))

    for point2 != nil {
        if point1.Val != point2.Val {
            return false
        }
    }

    return true
}
```