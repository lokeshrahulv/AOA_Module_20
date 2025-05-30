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
Developed by: ASHWIN KUMAR S
Register Number: 212222240013
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
