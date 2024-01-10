Category: Array, Two Pointers, Sorting

[Prob definition](https://leetcode.com/problems/sort-colors/description/)

Solution:

```
    let low = mid = 0, high = nums.length - 1;

    /* 
        - approach: 3 pointers - high, mid, low
        - if mid == 2, swap with high and decr high
        - if mid == 1, incr mid
        - if mid == 0, swap with low, incr both mid & low
        - repeat till mid crosses high
    */
    while(mid <= high){
        if(nums[mid] == 0){
            nums[mid] = nums[low];
            nums[low] = 0;
            low++;
            mid++;
        } else if (nums[mid] == 2){
            nums[mid] = nums[high];
            nums[high] = 2;
            high--;
        } else if (nums[mid] == 1) {
            mid++;
        }
    }
```

Learnings:

- 3 pointers logic
