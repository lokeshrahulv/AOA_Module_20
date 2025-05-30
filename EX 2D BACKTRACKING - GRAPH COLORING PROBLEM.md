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
Developed by: ASHWIN KUMAR S
Register Number: 212222240013
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
