Category: array, hash table, matrix

[Prob definition](https://leetcode.com/problems/set-matrix-zeroes/description/)

Solution:

```
var setZeroes = function(matrix) {

// approach
// note occurences of i,j where 0 is present in the first go
// to replace loop i,j
//   where i == found_i, replace elements
//   where i !== found_i check j == found_j replace elements

let i_array = [];
let j_array = [];

// identify occurence of 0s
for (i = 0; i < matrix.length; i++) {
    for (j = 0;  j < matrix[0].length; j++){
        if(matrix[i][j] == 0){
            i_array.push(i);
            j_array.push(j);
        }
    }
}

// replace row/column by 0
for (i = 0; i < matrix.length;  i++) {
    for (j = 0;  j < matrix[0].length; j++){
        if(i_array.includes(i)){
            matrix[i][j] = 0;
        } else if (j_array.includes(j)) {
            matrix[i][j] = 0;
        }
    }
}

};
```

Learnings:

- basic looping and array logic.

Comment:
- don't fear!
