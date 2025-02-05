# Связанный список

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



## [143. Reorder List](https://leetcode.com/problems/reorder-list/)

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

func reorderList(head *ListNode) {
    dummy := &ListNode{Val: 0}

    point := dummy
    point1 := head
    point2 := Reverse(Middle(head))

    for point2 !=nil {
        if point1 == point2 {
            point.Next = point2
            point = point.Next

            point2 = point2.Next
        } else {
            point.Next = point1
            point = point.Next

            point.Next = point2
            point = point.Next

            point1 = point1.Next
            point2 = point2.Next
        }
    }

    *head = *dummy.Next
}
```

**Test Case 1:** <span style="color: red">Fail</span>

*Input `[1,2,3,4]`*<br>
*Output `[1,4,3]`*<br>
*Expected `[1,4,2,3]`*


**Test Case 2:** <span style="color: red">Fail</span>

*Input `[1,2,3,4,5]`*<br>
*Output `[1,5,4,3]`*<br>
*Expected `[1,5,2,4,3]`*


## [1019. Следующий Больший узел В Связанном списке](https://leetcode.com/problems/next-greater-node-in-linked-list/)

- Timeout




# Деревья

## [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

- Timeout


## [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/)

- Timeout


## [107. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

- Many error

## [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)

- Timeout
- Poorly mastered