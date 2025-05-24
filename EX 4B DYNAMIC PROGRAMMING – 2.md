# EX 4B DYNAMIC PROGRAMMING – 2
## DATE:
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings..



## Algorithm
1. Take two input strings X and Y of lengths m and n.
2. Create a 2D array LCSuff of size (m+1) x (n+1) and initialize all values to 0.
3.Traverse each character of both strings:
    If X[i-1] == Y[j-1], then set LCSuff[i][j] = LCSuff[i-1][j-1] + 1.
4.Otherwise, set LCSuff[i][j] = 0.
5. Keep track of the maximum value in LCSuff, which indicates the length of the longest common substring.
6. After filling the table, return the maximum value found.  

## Program:
```python
/*
Program to implement the longest common substring problem.
Developed by: Gokularamanan K
RegisterNumber: 212222230040  
*/
def LCSubStr(X,Y,m,n):
    LCSuff = [[0 for k in range(n+1)] for l in range(m+1)]
    result = 0
    for i in range(m+1):
        for j in range(n+1):
            if (i==0 or j==0):
                LCSuff[i][j] = 0
            elif (X[i-1] == Y[j-1]):
                LCSuff[i][j] = LCSuff[i-1][j-1] + 1
                result = max(result,LCSuff[i][j])
            else:
                LCSuff[i][j] = 0
    return result
X = input()
Y = input()
m = len(X)
n = len(Y)
print('Length of Longest Common Substring is',LCSubStr(X,Y,m,n))


```

## Output:

![image](https://github.com/user-attachments/assets/102e4403-f0ed-4c9c-b8fb-ed75f5057562)


## Result:
Thus the program was executed successfully for finding the longest common substring .
