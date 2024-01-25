Category: Array, Sorting, Quick Sort

Level: Medium

[Prob definition](https://leetcode.com/problems/sort-an-array/description)

Solution:

```
var sortArray = function (nums) {
    /* 
        approach: quick sort
        - choose a pivot element (first one), place it to its proper position 
            i.e. elems <= pivot should be on left and elems > pivot must be on right
        - recurse on pivot's left side arr and right side arr
    */

    const partition = (nums, low, high) => {

        const pivot = nums[low];
        let i = low;
        let j = high;


        // identify pivot's place and swap elements smaller than pivot to its left 
        // & elements greater to its right
        while (i < j) {
            while (nums[i] <= pivot && i < high) {
                i++;
            }

            while (nums[j] > pivot && j > low) {
                j--;
            }

            if (i < j) {
                let temp = nums[j];
                nums[j] = nums[i];
                nums[i] = temp;
            }
        }

        // swap pivot at its place
        let temp = nums[j];
        nums[j] = nums[low];
        nums[low] = temp;


        console.log('j', j, nums)

        return j;
    }

    // primeagen's partition algo - we are taking the first elem as pivot, he takes last as pivot
    
    // const partition = (nums, low, high) => {
    //     let pivot = nums[high];

    //     let idx = low - 1;

    //     for (let i = low; i < high; i++) {
    //         if (nums[i] <= pivot) {
    //             idx++;
    //             let temp = nums[i];
    //             nums[i] = nums[idx];
    //             nums[idx] = temp;
    //         }
    //     }

    //     idx++;
    //     nums[high] = nums[idx];
    //     nums[idx] = pivot;

    //     return idx
    // }

    const quickSort = (nums, low, high) => {
        if (low >= high) return; // base condition

        let pivotIndex = partition(nums, low, high);
        quickSort(nums, low, pivotIndex - 1);
        quickSort(nums, pivotIndex + 1, high);
    }

    quickSort(nums, 0, nums.length - 1);

    return nums;
};
```

Learnings:

- Our and primeagen's algo says time execeeds for test case where an array of 50K size and same element (suppose: 2) is passed. e.g. [2,2,2,2,2 .... 50K times]. Debugged for some time couldn't definitely solve. I think the reason is, in such edge case, the array is not being divided properly (i.e. in two halves)... 
- [Community](https://leetcode.com/problems/sort-an-array/solutions/) has posted working quick sort solutions (slightly modified compared to our logic).
