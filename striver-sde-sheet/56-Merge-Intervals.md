Category: Array, Sorting

[Prob definition](https://leetcode.com/problems/merge-intervals/description/)

Solution:

```
    let result = [];

    /* 
        approach
        - sort the array in asc so that overlapping intervals come near-by (becomes easier to merge)
        - fill the results array 
            - merge the current interval in result if applicable, else push as new block

    */

    // sort
    intervals.sort((a, b) => {
        if (a[0] == b[0]) {
            return a[1] - b[1];
        } else {
            return a[0] - b[0];
        }
    });

    result.push(intervals[0]);

    for (let i = 1; i < intervals.length; i++) {
        let curr = intervals[i];
        let prev = result[result.length - 1];

        if (prev[1] < curr[0]) {
            result.push(curr); // if not mergeable
        } else if (prev[1] <= curr[1]) {
            result[result.length - 1][1] = curr[1]; //update results ending coord with largest ending.
        }
    }

    return result;
```

Learnings:

- be confident in your intuition
- concepts: sorting & pattern observation