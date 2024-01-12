Category: Array

[Prob definition](https://leetcode.com/problems/find-the-duplicate-number/description/)

Solution:

```
    let set = new Set();

    for(let i = 0; i <nums.length; i++){
        const elm = nums[i];
        if(set.has(elm)){
            return elm
        } else {
            set.add(elm)
        }
    }
```

Learnings:

- solved using js knowledge and sets.
