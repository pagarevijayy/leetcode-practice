Category: Array, Hash Table

[Prob definition](https://leetcode.com/problems/majority-element/?envType=study-plan&id=data-structure-ii)

Solution:

```
var majorityElement = function(nums) {
    // BF approach:
    // - loop through array and keep count of each occurence in HM
    // - loop through HM and return the max occured num
    // - Time: O(n)but practically looped twice. Space: O(n)?

    let HM = {}; // using object as a hashmap here, can be a Map() or weak Map

    for (item of nums){
        HM[item] ? HM[item]+=1 : HM[item] = 1;
    }

    let max = 0, num;

    for ([key, value] of Object.entries(HM)){

        if(value >= max){
            max = value;
            num = key;
        }
    }

    return num;

};
```

```
    // optimised one
    nums.sort((a,b) => a - b );
    return nums[Math.floor(nums.length/2)];
```

Learnings:

- solved using hashmap, ternary operator, for…of loop with Object.entries()
- sorta BF

- optimised solution leverages the constraint of the problem (majority element occurs at least floor(array.length/2) times, so DnC sort then return middle element)

- ideally, in such cases lib sort fn is not allowed so you need to implement your own sort (revise it)

- too many [solutions](https://leetcode.com/problems/majority-element/solutions/127412/majority-element/) (hashmap, sort, bit manipulation, Boyer-Moore voting algo)
