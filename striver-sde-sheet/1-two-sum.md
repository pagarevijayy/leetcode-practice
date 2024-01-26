Category: Array, Hash Table

Difficulty: Easy

[Prob definition](https://leetcode.com/problems/two-sum/description/)

Solution:

```
var twoSum = function(nums, target) {

    let temp = {};
    
    for (let i = 0; i < nums.length; i++) {
        let pair = target - nums[i]
        
        if(temp.hasOwnProperty(pair)){
            return [temp[pair], i]
        } else {
            temp[nums[i]] = i;
        }
    }
    
};
```

Learnings:
- using map/object
