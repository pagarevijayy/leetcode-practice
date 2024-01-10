Category: Array, Two Pointers

[Prob definition](https://leetcode.com/problems/next-permutation/description/)

Solution:

```

    /* 
        approach (based on intuition/algo)
            if non-largeest perm:
            - find breaking point (smaller number at a[i] compared to a[i+1] traversed from back side)
            - swap breakpoint number (bp_num) with the farthest on right but greater than bp_num
            - reverse the right side portion of breakpoint
            else: reverse the array (descending --> ascending)
    */

    let j = nums.length - 1; // last index
    let break_point;

    // in-place swap & reverse used.
    const swap_bp_num = () => {
        // swap breakpoint number with the farthest on right 
        // but greater than bp_num

        for (let k = nums.length - 1; k >= break_point; k--) {
            if (nums[k] > nums[break_point]) {
                //swap logic
                let temp = nums[k];
                nums[k] = nums[break_point];
                nums[break_point] = temp;
                break
            }
        }
    }

    const reverse_fill = (start, end) => {
        while (start < end) {
            //swap logic
            let temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp; 
            start++;
            end--;
        }
    }


    for (let i = nums.length - 2; i >= 0; i--) {
        if (nums[i] < nums[j]) {
            break_point = i;
            swap_bp_num(); 
            reverse_fill(break_point + 1, nums.length - 1); // portion on right of bp 
            break;
        }
        j--;
    }

    
    if(j == 0) {
        // edge case - greatest one. (reverse in sorted order)
        reverse_fill(0, nums.length - 1); 
    }
```

Learnings:

- [striver sde solution](https://takeuforward.org/data-structure/next_permutation-find-next-lexicographically-greater-permutation/)
- pattern observation (sub logic refreshers: inplace swapping, two pointers)
