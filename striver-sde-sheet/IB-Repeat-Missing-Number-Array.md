Category: Array

[Prob definition](https://www.interviewbit.com/problems/repeat-and-missing-number-array/)

You are given a read only array of n integers from 1 to n.

Each integer appears exactly once except A which appears twice and B which is missing.

Return A and B.

Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Note that in your output A should precede B.

Example:

Input:[3 1 2 5 3] 

Output:[3, 4] 

A = 3, B = 4

---

Solution:

```
    function repeatedNumber (A){
        let map = new Map();
        let myset = new Set();
        let result = [];
        
        A.forEach((elm, index) => {
            map.set(index + 1, true);    
        })
        
        for(let i = 0; i < A.length; i++){
            let elm = A[i]
            if(myset.has(elm)){
                result[0] = elm;
            } else {
                myset.add(elm);
            }
            map.delete(elm);
        }
        
        for(let key of map.keys()){
            result[1] = key;
        }
        
        return result;
    }
```

Learnings:

- Solved using map and set. Refer solutions later to learn other (ideal/optimal) ways. 
