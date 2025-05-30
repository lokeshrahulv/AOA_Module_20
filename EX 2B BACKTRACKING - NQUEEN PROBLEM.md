# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm
1. Start with an empty board of size N x N and attempt to place a queen in each column, one by one.
2. For each row in the current column, check if placing a queen is safe (i.e., no queens threaten each other).
3. If the placement is safe, place the queen and move to the next column recursively.
4. If a valid solution is found (all queens placed), return True; otherwise, backtrack by removing the queen and trying the next row.
5. If all queens are placed successfully, print the board; if not, print "Solution does not exist."  

## Program:
```
/*
Program to implement N-Queen problem using backtracking.
Developed by: ASHWIN KUMAR S
Register Number: 212222240013
*/
```
```
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    for i in range(col):
        if board[row][i] == 1:
            return False
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
    if col >=N:
        return True
    for i in range(N):
        if isSafe(board,i,col):
            board[i][col] = 1
            if solveNQUtil(board,col+1) == True:
                return True
            board[i][col] = 0
    return False
      
def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]
              
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
```

## Output:
![Screenshot 2025-04-26 111406](https://github.com/user-attachments/assets/1cd485dd-2d4c-4e9b-9bde-4cb428942965)




## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
