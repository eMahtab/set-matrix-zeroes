# Set Matrix Zeroes
## https://leetcode.com/problems/set-matrix-zeroes

Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in-place.
```
Example 1:

Input: 
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
Output: 
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]

Example 2:

Input: 
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
Output: 
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]
```
**Follow up:**
1. A straight forward solution using O(mn) space is probably a bad idea.
2. A simple improvement uses O(m + n) space, but still not the best solution.
3. Could you devise a constant space solution?

## Implementation 1 : Naive , Time => O(rows * cols) , Space => (rows * cols)
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        if(matrix == null || matrix.length == 0)
            return;
        int rows = matrix.length;
        int columns = matrix[0].length;
        
        int[][] clone = new int[rows][columns];
        for(int i = 0; i < rows; i++)
            clone[i] = matrix[i].clone();
        
        for(int row = 0; row < rows; row++) 
            for(int col = 0; col < columns; col++) 
                if(clone[row][col] == 0) 
                    setZero(matrix, row, col);
    }
    
    private void setZero(int[][] matrix, int row, int column) {
        // Set all cells in that `column` to zero
        for(int i = 0; i < matrix.length; i++) 
            matrix[i][column] = 0;
        // Set all cells in that `row` to zero
        for(int j = 0; j < matrix[0].length; j++) 
            matrix[row][j] = 0;
    }
}
```


## Implementation 2 : Time => O(rows * cols) , Space => (rows + cols)
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        if(matrix == null || matrix.length == 0)
            return;
        int rows = matrix.length;
        int cols = matrix[0].length;
        Set<Integer> rowIndex = new HashSet<>();
        Set<Integer> colIndex = new HashSet<>();
        
        for(int i = 0; i < rows; i++) {
            for(int j = 0; j < cols; j++) {
                if(matrix[i][j] == 0) {
                   rowIndex.add(i);
                   colIndex.add(j); 
                }
            }
        }
        
        for(int i = 0; i < rows; i++) {
            for(int j = 0; j < cols; j++) {
                if(rowIndex.contains(i) || colIndex.contains(j))
                    matrix[i][j] = 0;
            }
        }
    }
}
```

# References :
1. https://leetcode.com/articles/set-matrix-zeroes/
