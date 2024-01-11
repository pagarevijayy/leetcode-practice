Category: Array, Math, Matrix

[Prob definition](https://leetcode.com/problems/rotate-image/description/)

Solution:

```
    /* 
        
        Approach/pattern/intuition: 
        
        Brute force
            - last array becomes first element of each sub array
            - second last array -> second element, so on.
            -- can easily create another matrix with required config then copy into this one.

        Observation/Optimal
            - transpose and then row reverse
    */

    // transpose matrix
    for (let i = 0; i < matrix.length; i++) {
        for (let j = 0; j < matrix[0].length; j++) {
            if (j > i) {
                let temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
    }

    // reverse row
    const row_reverse = (arr) => {
        let start = 0, end = arr.length - 1;

        while (start < end) {
            let temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    for (let i = 0; i < matrix.length; i++) {
        row_reverse(matrix[i]);
    }
```

Learnings:

- know the core math formulae/concepts by heart: matrix, PnC
