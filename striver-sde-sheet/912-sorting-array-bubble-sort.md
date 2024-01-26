Category: Array, Sorting, Bubble Sort

Level: Easy

[Prob definition](https://leetcode.com/problems/sort-an-array/description/)

Solution:

```
// -------- bubble sort implementation --------
var sortArray = function (nums) {
    /* 
        approach: optimised bubble sort
        - go through the array - if next element is smaller than current - swap
        - repeat
        - optimisation: 
            - while inner looping, skip already sorted elements during subsequent iterations (present at the end)
            - don't reloop if the elements are already sorted
        - time complexity: n^2
    */

    for (let i = 0; i < nums.length - 1; i++) {
        let swapped = false;
        for (let j = 0; j < nums.length - 1 - i; j++){
            if(nums[j+1] < nums[j]){
                let temp = nums[j+1];
                nums[j+1] = nums[j];
                nums[j] = temp;
                swapped = true;
            }
        }
        if (!swapped) break
    }

    return nums;
};

// -------- bubble sort implementation end --------
```

Learnings:

- there's a bit of optimised approach to bubble sort
