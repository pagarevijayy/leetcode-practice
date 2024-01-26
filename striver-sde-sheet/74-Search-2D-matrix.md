Category: Matrix, Array, Binary Search

Level: Medium

[Prob definition](https://leetcode.com/problems/search-a-2d-matrix/description/)

Solution:

```
var searchMatrix = function (matrix, target) {
    // javascript hack:
    // let flatten = matrix.flat()
    // return flatten.includes(target)

    // -----------------------------

    // approach: implement using binary search
    // - identify the matrix
    // - search in that particular matrix

    let m = matrix.length, n = matrix[0].length;

    if (target < matrix[0][0] || target > matrix[m - 1][n - 1]) {
        return false; // target mentioned is out of range
    }

    if (target == matrix[0][0] || target == matrix[m - 1][n - 1]) {
        return true; // target is at the boundary
    }

    // identify the probable row
    const findRelevantRow = (matrix, low, high) => {
        if(low > high) return -1;

        let mid = Math.floor((low + high) / 2);
    
        if (target < matrix[mid][0]) {
            return findRelevantRow(matrix, low, mid - 1);
        } else if (target > matrix[mid][n - 1]) {
            return findRelevantRow(matrix, mid + 1, high);
        } else {
            return mid; // current row index
        }
    }

    let rowIndex = findRelevantRow(matrix, 0, m - 1);

    if (rowIndex == -1) return false

    // binary search the relevant row
    const binarySearch = (arr, low, high) => {
        const mid = Math.floor((low + high) / 2);

        if(low > high) return false;
        if (target == arr[mid]) return true;

        if (target < arr[mid]) {
            return binarySearch(arr, low, mid - 1);
        } else if (target > arr[mid]) {
            return binarySearch(arr, mid + 1, high);
        }
    }

    return binarySearch(matrix[rowIndex], 0, n - 1);

};
```

Learnings:

- Binary search logic to identity the row as well as the element
