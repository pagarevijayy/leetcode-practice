Category: Array, Bit Manipulation

[Prob definition](https://leetcode.com/problems/single-number/?envType=study-plan&id=data-structure-ii)

Solution:

```
var singleNumber = function(nums) {
    return nums.reduce((acc, curr) => acc ^ curr)
};
```

Learnings:

- using XOR (^) logic and reduce.
- XOR with self is 0, with different item is 1 (in this case that item itself.)
