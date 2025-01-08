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

<span style="color: green">**Верно**</span>
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



## [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

1. Ошибка при не внимательности к операторам условий `&&`, `||`

```golang
for point1 != nil && point2 != nil {}
// Заменен на ->
for point1 != nil || point2 != nil {}
```



## [23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

1. Ошибка при не внимательности синтаксиса
2. Ошибка сравнения! (сравнение указателей вместо значений) `lists[minIndex] > lists[i]` вместо `lists[minIndex].Val > lists[i].Val`
3. Ошибка условия изменения
```golang
if lists[minIndex].Val > lists[i].Val {
    minIndex = i
}
// Заменен на ->
if lists[minIndex] == nil || lists[minIndex].Val > lists[i].Val {
    minIndex = i
}

// Так как lists[minIndex] может указать на nil если первый *ListNode пустой (nil)
```

## [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

1. Обдумать все крайние случаи в тестах
2. Нельзя добавлять или изменять значение в nil хеш-таблице, используйте пустую хеш-таблицу

<span style="color: red">**Ошибка**</span>
```golang
var table map[*ListNode]bool
table[p1] = true
```

<span style="color: green">**Верно**</span>
```golang
table := map[*ListNode]bool{}
table[p1] = true
```

<span style="color: green">**Верно**</span>
```golang
table := make(map[*ListNode]bool)
table[p1] = true
```