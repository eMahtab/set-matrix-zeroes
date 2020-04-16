# Set Matrix Zeroes


## Implementation :
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
