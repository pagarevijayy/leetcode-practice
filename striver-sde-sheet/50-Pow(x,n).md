Category: Math, Recursion

[Prob definition](https://leetcode.com/problems/powx-n/)

Solution:

```
var myPow = function (x, n) {

    // approach: common-sense math knowledge

    // solution using loop - time limit exceeds for an edge case.
    
    // if(n == 0) return 1;
    // if(x == 0) return 0;
    // if(x == 1) return 1;

    // if(x == -1) {
    //     return (Math.abs(n) % 2 == 0) ? 1 : -1;
    // };

    // let mul = 1;

    // for(let i = 0; i < Math.abs(n); i++){
    //     mul*= x;
    // }

    // if(n < 0){
    //     return 1/mul;
    // } else {
    //     return mul;
    // }

    // Recursive solution
    // base condition
    if (n == 0) return 1;

    // negative power
    if (n < 0) {
        x = 1 / x;
        n = -n;
    }

    // return x * myPow(x, n-1); // simple recursion - exceeds call stack

    if (n % 2 === 0) {
        let halfPower = myPow(x, n / 2); // insight - halving callstack
        return halfPower * halfPower;
    }
    else {
        return x * myPow(x, n - 1);
    }

};
```

Learnings:

- For loop solution exceeds time, normal recursion exceeds call stack
- Key insight: even power can be split into two halves & multiplied.
