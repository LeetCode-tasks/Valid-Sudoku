# Valid Sudoku

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

**Note**:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.

**Example:**

**_Input:_** 

```board = 

[["5","3",".",".","7",".",".",".","."]

,["6",".",".","1","9","5",".",".","."]

,[".","9","8",".",".",".",".","6","."]

,["8",".",".",".","6",".",".",".","3"]

,["4",".",".","8",".","3",".",".","1"]

,["7",".",".",".","2",".",".",".","6"]

,[".","6",".",".",".",".","2","8","."]

,[".",".",".","4","1","9",".",".","5"]

,[".",".",".",".","8",".",".","7","9"]]
```

![image](https://user-images.githubusercontent.com/68459485/126862337-508eaa46-217d-4de5-9c0e-bb879a9d5eb1.png)

**_Output:_** `true`

**Constraints:**

`board.length == 9`

`board[i].length == 9`

`board[i][j] is a digit or '.'`

## Solution in JavaScript:

```
var isValidSudoku = function(board) {
     for (let i = 0; i < board.length; i++) {
        
        let horizontalSet = new Set()
        let verticalSet = new Set()
        
        for (let j = 0; j < board.length; j++) {
            if (horizontalSet.has(board[i][j]) || verticalSet.has(board[j][i])) {
                return false
            }
            
            if (board[i][j] !== ".") {
                horizontalSet.add(board[i][j])
            }
            
            if (board[j][i] !== ".") {
                verticalSet.add(board[j][i])
            }
        }
    }
     
     for(let i = 0; i < 9; i = i+3){
        for(let j = 0; j < 9; j = j+3){

            const gridSet = new Set()
            let h = i;

            while(h < i + 3) {
                let k = j;

                while(k < j + 3) {
                    if(gridSet.has(board[h][k])) return false

                    if(board[h][k] !== '.') gridSet.add(board[h][k])

                    k++
                }
                h++
            }
        }
    }
     
    return true
};
```
