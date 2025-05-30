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
Developed by: ASHWIN KUMAR S
Register Number: 212222240013
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
