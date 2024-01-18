Category: Array, Divide & Conquer, Merge Sort, Ordered Set

Difficuilty Level: Hard

[Prob definition](https://leetcode.com/problems/reverse-pairs/description/)

Solution:

```
var reversePairs = function (nums) {

    /*
        algorithm:
         - merge sort approach
         - before merging apply the intuition (https://takeuforward.org/data-structure/count-reverse-pairs/)
    */

    let pairCount = 0;

    let merge = (arr, low, mid, high) => {
        let temp = [];
        let left = low;
        let right = mid + 1;

        // comparing and merging
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

        // temp to og arr
        for (let i = low; i <= high; i++) {
            arr[i] = temp[i - low];
        }
    }

    let countPairs = (arr, low, mid, high) => {
        let right = mid + 1;
        for (let i = low; i <= mid; i++) {
            while (right <= high && arr[i] > 2 * arr[right]) {
                right++;
            }
            pairCount +=  right - (mid+1);
        }
    }

    let mergeSort = (nums, low, high) => {
        if (low >= high) return;
        let mid = Math.floor((low + high) / 2);
        mergeSort(nums, low, mid);
        mergeSort(nums, mid + 1, high);
        countPairs(nums, low, mid, high); // count reverse pairs logic
        merge(nums, low, mid, high);
    }

    mergeSort(nums, 0, nums.length - 1);

    return pairCount;
};
```

Learnings:

- solution is mixture of merge sort and the highlighted intuition
