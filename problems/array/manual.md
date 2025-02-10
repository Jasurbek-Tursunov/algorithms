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



## [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/description/)

- Time: ***O(n)***
- Memory: ***O(1)***

```golang
    func pivotIndex(nums []int) int {
        sum := 0
        
        for _, v := range nums {
            sum += v
        }
    
        preSum := 0
    
        for i, v := range nums {
            if sum - preSum - v == preSum {
                return i
            }
            preSum += v
        }
    
        return -1
    }
```



## [268. Missing Number](https://leetcode.com/problems/missing-number/)

- Time: ***O(n)***
- Memory: ***O(1)***

```golang
    func missingNumber(nums []int) int {
        n := len(nums)
        progress := (0 + n) * (n+1) / 2
        sum := 0
    
        for _, v := range nums {
            sum += v
        }
    
        return progress - sum
    }
```



## [189. Rotate Array](https://leetcode.com/problems/rotate-array/)

- Time: ***O(n)***
- Memory: ***O(1)***

```golang
    func reverse(nums []int, left, right int) {
        for left < right {
            nums[left], nums[right] = nums[right], nums[left]
            left++
            right--
        }
    }
    
    func rotate(nums []int, k int) {
        n := len(nums)
        k = k % n
        reverse(nums, 0, n - 1)
        reverse(nums, 0, k - 1)
        reverse(nums, k, n - 1)
    }
```



## []()

- Time: ***O(n)***
- Memory: ***O(1)***

```golang
    func findLengthOfLCIS(nums []int) int {
        maxCount := 1
        subCount := 1
    
        for i:= 0; i < len(nums) -1; i++ {
            if nums[i] < nums[i+1] {
                subCount++
            } else {
                subCount = 1
            }
    
            if subCount > maxCount {
                maxCount = subCount
            }
        }
    
        return maxCount
    }
```



## [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)

- Time: ***O(n log n)***
- Memory: ***O(n)***

```golang
    func isIntersect(a, b []int) bool {
        return max(a[0], b[0]) <= min(a[1], b[1])
    }
    
    func merge(intervals [][]int) [][]int {
        sort.Slice(intervals, func(i, j int) bool{
            return intervals[i][0] < intervals[j][0]
        })
    
        result := make([][]int, 0, len(intervals))
        result = append(result, intervals[0])
        lastIndex := 0
    
        for i := 0; i<len(intervals); i++ {
            lastIndex = len(result) - 1
            if isIntersect(result[lastIndex], intervals[i]) {
                result[lastIndex][0] = min(result[lastIndex][0], intervals[i][0])
                result[lastIndex][1] = max(result[lastIndex][1], intervals[i][1])
            } else {
                result = append(result, intervals[i])
            }
        }
    
        return result
    }
```