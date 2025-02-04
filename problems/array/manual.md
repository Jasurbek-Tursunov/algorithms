## [303. Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/)

Constructor
- Time: ***O(n)***
- Memory: ***O(n)***

SumRange
- Time: ***O(1)***
- Memory: ***O(1)***

```golang
    type NumArray struct {
        elem []int
    }
    
    
    func Constructor(nums []int) NumArray {
        result := make([]int, len(nums)+1)
    
        for i, v := range nums {
            result[i+1] = result[i] + v
        }
    
        return NumArray{result}
    }
    
    
    func (this *NumArray) SumRange(left int, right int) int {
        return this.elem[right + 1] - this.elem[left]
    }
    
    
    /**
     * Your NumArray object will be instantiated and called as such:
     * obj := Constructor(nums);
     * param_1 := obj.SumRange(left,right);
     */
```