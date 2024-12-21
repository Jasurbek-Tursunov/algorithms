## [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

1. `fast.next` и `fast.Next` ошибки при не внимательности на регисторы полей



## [`2. Add Two Numbers`](https://leetcode.com/problems/add-two-numbers/)

1. Медленная работа `55:07` вместо `30:00`

2. Ошибка при не внимательности в операторах `&&`, `||` и условиях 
`for l1 != nil && l2 != nil {` => `for l1 != nil || l2 != nil {`

3. Ошибка при не внимательности на  `*`, `&` (вместо ссылки использовал указатель)
`dummy := *ListNode{Val: 0}` => `dummy := &ListNode{Val: 0}`



## [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

- Не внимательность к сдвигам указателей

<span style="color: red">**Ошибка**</span>

```golang
for point2 != nil {
    if point1.Val != point2.Val {
        return false 
		// Ошибка
    }
}
```

<span style="color: green">**Ошибка**</span>
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
		point1 = point1.Next
		point2 = point2.Next
    }

    return true
}
```