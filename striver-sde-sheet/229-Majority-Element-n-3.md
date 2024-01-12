Category: Array, Hash Table, Sorting, Counting


[Prob definition](https://leetcode.com/problems/majority-element-ii/description/)

Solution:

```
var majorityElement = function (nums) {
    /*
         approach/intuition - based on majority element n/2 BF
         - create a map and count occurrences of each element by looping through
         - get highest 3 count from the map (sort decr, slice)
         - if those top 3 count is more than total/3 then valid ans 
    */
    let map = {}

    for (let num of nums) {
        map[num] ? map[num]++ : map[num] = 1;
    }

    let major = Object.entries(map)
        .sort((a, b) => (b[1] - a[1]))
        .slice(0, 3);

    let res = [];

    major.forEach(elm => {
        if (elm[1] > Math.floor(nums.length / 3)) {
            res.push(elm[0])
        }
    })

    return res

};
```

Learnings:

- create a map, count occurrences, ans amongst highest 3
- insight: max only 3 numbers can be total/3
