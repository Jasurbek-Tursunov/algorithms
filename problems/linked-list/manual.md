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



## [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

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

func firstMin(point1, point2 *ListNode) bool {
    if point1 == nil {
        return false
    } else if point2 == nil {
        return true
    } else {
        return point1.Val < point2.Val 
    }
}


func mergeTwoLists(list1 *ListNode, list2 *ListNode) *ListNode {
    dummy := &ListNode{Val: 0}
    point := dummy

    point1 := list1
    point2 := list2

    for point1 != nil || point2 != nil {
        if firstMin(point1, point2) {
            point.Next = point1
            point1 = point1.Next
        } else {
            point.Next = point2
            point2 = point2.Next
        }
        point = point.Next
    }

    return dummy.Next
}
```



## [23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

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

func getMinIndex(lists []*ListNode) (int, bool) {
    minIndex := 0
    flag := false

    length := len(lists)

    for i := 0; i < length; i++ {
        if lists[i] != nil {
            flag = true
            if lists[minIndex] == nil || lists[minIndex].Val > lists[i].Val {
                minIndex = i
            }
        }
    }

    return minIndex, flag
}

func mergeKLists(lists []*ListNode) *ListNode {
    dummy := &ListNode{Val: 0}

    point := dummy

    minIndex, notEmpty := getMinIndex(lists)

    for notEmpty {
        point.Next = lists[minIndex]
        lists[minIndex] = lists[minIndex].Next
        point = point.Next
        minIndex, notEmpty = getMinIndex(lists)
    }

    return dummy.Next
}
```



## [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

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

func getIntersectionNode(headA, headB *ListNode) *ListNode {
    table := map[*ListNode]bool{}
    p1 := headA
    p2 := headB

    for p1 != nil {
        table[p1] = true
        p1 = p1.Next
    }

    for p2 != nil {
        if table[p2]{
            return p2
        }
        p2 = p2.Next
    }

    return nil
}
```



## [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

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

func hasCycle(head *ListNode) bool {
    p := head
    data := make(map[*ListNode]bool)

    for p != nil {
        if data[p] {
            return true
        } else {
            data[p] = true
            p = p.Next
        }
    }

    return false    
}
```



## [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii)

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

func detectCycle(head *ListNode) *ListNode {
    p := head
    data := make(map[*ListNode]bool)

    for p != nil {
        if data[p] {
            return p
        } else {
            data[p] = true
            p = p.Next
        }
    }

    return nil
}
```