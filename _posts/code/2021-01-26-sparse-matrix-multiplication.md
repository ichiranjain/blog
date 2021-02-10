---
title: 311. Sparse Matrix Multiplication
date: 2021-01-26 00:00:00 PST
category: code
---

Given two sparse matrices A and B, return the result of AB.

You may assume that A's column number is equal to B's row number.

Example:

Input:

```
A = [
  [ 1, 0, 0],
  [-1, 0, 3]
]

B = [
  [ 7, 0, 0 ],
  [ 0, 0, 0 ],
  [ 0, 0, 1 ]
]

Output:

     |  1 0 0 |   | 7 0 0 |   |  7 0 0 |
AB = | -1 0 3 | x | 0 0 0 | = | -7 0 3 |
                  | 0 0 1 |
```

1. Key

```
multiply each element with every row and do a summation of every C[i][k] for A[i][j] and B[i][j]

```

2. Solution


```
    class Solution {
    public int[][] multiply(int[][] A, int[][] B) {


        int rowA = A.length;
        int colA = A[0].length;
        int rowB = B.length;
        int colB = B[0].length;
        int[][] C = new int[rowA][colB];

        if(colA != rowB){
            return new int[][]{};
        }

        for(int i = 0; i < rowA; i++){
            for(int j = 0; j < colA; j++){
                if(A[i][j] != 0){
                    //each element of Matrix A
                    for(int k = 0; k < colB; k++){
                        if(B[j][k] != 0){
                            C[i][k] += A[i][j] * B[j][k] ;
                        }
                    }    
                }

            }
        }

        return C;
    }
}
```
