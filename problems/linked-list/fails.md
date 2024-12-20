## [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

1. `fast.next` и `fast.Next` ошибки при не внимательности на регисторы полей



## [`2. Add Two Numbers`](https://leetcode.com/problems/add-two-numbers/)

1. Медленная работа `55:07` вместо `30:00`

2. Ошибка при не внимательности в операторах `&&`, `||` и условиях 
`for l1 != nil && l2 != nil {` => `for l1 != nil || l2 != nil {`

3. Ошибка при не внимательности на  `*`, `&` (вместо ссылки использовал указатель)
`dummy := *ListNode{Val: 0}` => `dummy := &ListNode{Val: 0}`
