Category: Math, Dynamic Programming, Combinatorics


[Prob definition](https://leetcode.com/problems/unique-paths/description/)

Solution:

```
var uniquePaths = function (m, n) {

    /* approach: DP recursive
        - as at any given point of time we have two options (left / right) 
          the resulting solution structure would be a tree.
        - recursively traverse in bottom and right direction till solution is reached
        - base cases: 
            - solution reached = return 1; as this is one of the solution path
            - out of bound = return 0;
        - sum all the values from LST (left sub tree) and RST (right sub tree) as result
        - DP solution: cache value of sub tree (ie. sub problem)
    */

    let gridMap = Array.from({ length: m }, () => {
        return Array.from({ length: n }, () => -1)
    });

    const traverse_recursive = (i, j) => {
        // base cases
        if (i > m - 1 || j > n - 1) return 0; // out of bound - bottom/right
        if (i == m - 1 && j == n - 1) return 1; // success

        if (gridMap[i][j] !== -1) return gridMap[i][j]; // cached value | sub-tree.

        return gridMap[i][j] = traverse_recursive(i + 1, j) + traverse_recursive(i, j + 1);
    }


    return traverse_recursive(0, 0);
};
```

Learnings:

- DP has subproblems in it who answers can be cached and used in final computation of result
- Keep an eye on call by reference in js otherwise can introduce bug. (made similar mistake while creating gridMap)
