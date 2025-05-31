# AOA_Module_20
# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1. Start at the top-left corner (0, 0) and mark it as visited.
2. Check if the current position is valid (inside bounds, open path, and unvisited).
3. Recursively explore all four possible directions (up, down, left, right) from the current position.
3. If moving in a direction leads to the destination (n-1, n-1), return True; otherwise, backtrack.
4. If the destination is reached, print the path; otherwise, declare that no solution exists.

## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
n=n = 4
def isValid(n, maze, x, y, res):
	if x >= 0 and y >= 0 and x < n and y < n and maze[x][y] == 1 and res[x][y] == 0:
		return True
	return False

def RatMaze(n, maze, move_x, move_y, x, y, res):
	if x == n-1 and y == n-1:
		return True
	for i in range(4):
		x_new = x + move_x[i]
		y_new = y + move_y[i]
		if isValid(n, maze, x_new, y_new, res):
			res[x_new][y_new] = 1
			if RatMaze(n, maze, move_x, move_y, x_new, y_new, res):
				return True
			res[x_new][y_new] = 0
	return False

def solveMaze(maze):
	res = [[0 for i in range(n)] for i in range(n)]
	res[0][0] = 1
	move_x = [-1, 1, 0, 0]
	move_y = [0, 0, -1, 1]

	if RatMaze(n, maze, move_x, move_y, 0, 0, res):
		for i in range(n):
			for j in range(n):
				print(res[i][j], end=' ')
			print()
	else:
		print('Solution does not exist')

maze = [[1, 0, 0, 0],
		[1, 1, 0, 1],
		[0, 1, 0, 0],
		[1, 1, 1, 1]]
solveMaze(maze)
```

## Output:
![Screenshot 2025-04-26 111028](https://github.com/user-attachments/assets/9735aec4-b09d-45f3-9d82-810486ec3736)




## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.

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
Developed by:  LOKESH RAHUL V V
Register Number:212222100024
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

# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE:
## AIM:
To demonstrate that the sum of the subset of a given set is equal to the given sum.


## Algorithm
1. Loop through all possible subset sizes from 0 to n.
2. For each size, generate all combinations (subsets) of that length.
3. Calculate the sum of each subset.
4. If the sum equals the target x, print the subset.
5. 5.Continue checking until all combinations are tested.

## Program:
```
/*
Program to implement Subset sum problem.
Developed by: LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
from itertools import combinations
def subsetSum(n, arr, x):
	for i in range(n+1):
		for subset in combinations(arr, i):
			if sum(subset) == x:
				print(list(subset))


n=int(input())
arr=[]
for i in range(0,n):
    a=int(input())
    arr.append(a)
x = int(input())

subsetSum(n, arr, x)
```

## Output:
![image](https://github.com/user-attachments/assets/2416919f-3ad4-4349-bcae-205c012ee885)




## Result:
The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.

# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:
## AIM:
To solve the Graph Coloring Problem using backtracking

## Algorithm
1. Start with the first vertex and try assigning each of the m colors to it.
2. For each vertex, check if assigning a color is safe (i.e., no adjacent vertex has the same color).
3. If it’s safe, assign the color and recursively try to color the next vertex.
4. If all vertices are colored without conflicts, print the color assignments.
5. If no valid coloring exists, return false.  

## Program:
```
/*
Program to implement Graph Coloring Problem using backtracking.
Developed by: LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
class Graph():
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0 for column in range(vertices)]for row in range(vertices)]
 
    def isSafe(self, v, colour, c):
        for i in range(self.V):
            if self.graph[v][i] == 1 and colour[i] == c:
                return False
        return True

    def graphColourUtil(self, m, colour, v):
        if v == self.V:
            return True
        for c in range(1, m + 1):
            if self.isSafe(v, colour, c) == True:
                colour[v] = c
                if self.graphColourUtil(m, colour, v + 1) == True:
                    return True
                colour[v] = 0

    def graphColouring(self, m):
        colour = [0] * self.V
        if self.graphColourUtil(m, colour, 0) == None:
            return False
        print ("Solution exist and Following are the assigned colours:")
        for c in colour:
            print (c,end=' ')
        return True
```

## Output:
![image](https://github.com/user-attachments/assets/5ae963ba-f4d8-4b18-a9aa-082e405796b6)




## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.ed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
