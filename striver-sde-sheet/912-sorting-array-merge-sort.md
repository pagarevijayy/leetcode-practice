Category: Array, Divide & Conquer, Sorting, Merge Sort

[Prob definition](https://leetcode.com/problems/sort-an-array/)

Solution:

```
var sortArray = function (nums) {
    /* 
        merge sort: divide & conquer
        - divide: logically divide using low & high pointers, calc mid & recurse [base, pre, post]
        - conquer: use merge func [compare left sub & right sub, sort using temp arr]
    */

    const merge = (arr, low, mid, high) => {
        let temp = [];
        let left = low;
        let right = mid + 1;

        // compare two divided arrays & place them in sorted order in temp 
        // (first compare & fill the temp arr, then if length of any one arr is greater, push remaining elements)

        while (left <= mid && right <= high) {
            if (arr[left] <= arr[right]) {
                temp.push(arr[left]);
                left++;
            } else {
                temp.push(arr[right]);
                right++;
            }
        }

        while (left <= mid) {
            temp.push(arr[left]);
            left++;
        }

        while (right <= high) {
            temp.push(arr[right]);
            right++;
        }

        // transfer from temp to og arr
        for(let i = low; i <= high; i++){
            arr[i] = temp[i - low]; // i starts from og arr index (ie. low), temp starts from 0
        }
    }

    const mergeSort = (nums, low, high) => {
        if (low >= high) return;
        const mid = Math.floor((low + high) / 2); // javascript division gives decimal results | *
        mergeSort(nums, low, mid);
        mergeSort(nums, mid + 1, high)
        merge(nums, low, mid, high)
    }

    mergeSort(nums, 0, nums.length - 1);

    return nums;
};
```

Learnings:
- Merge sort [algorithm](https://takeuforward.org/data-structure/merge-sort-algorithm/)
- remember: Math.floor() for mid calculation in js.
