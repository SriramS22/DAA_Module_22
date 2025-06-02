# EX 4C DYNAMIC PROGRAMMING – 3
## DATE:
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.


## Algorithm
1. Take the input string X of length n.
2. Create a 2D array dp of size n x n, where dp[i][j] will store the LPS length from index i to j.
3. Initialize all dp[i][i] = 1 since every single character is a palindrome of length 1.
4. Fill the table for substrings of length 2 to n:
      If X[i] == X[j], then dp[i][j] = dp[i+1][j-1] + 2.
      Else, dp[i][j] = max(dp[i+1][j], dp[i][j-1]). 
5. The value at dp[0][n-1] is the length of the longest palindromic subsequence.  

## Program:
```python
/*
Program to implement to find the length of the longest palindromic subsequence in it.
Developed by: sriram s
RegisterNumber: 212222240105
*/
def Lps(X):
    n=len(X)
    dp=[[0 for _ in range(n)] for _ in range(n)]
    for x in range(n):
        dp[x][x]=1
    for l in range(2,n+1):
        for i in range(n-l+1):
            j=i+l-1
            if X[i]==X[j]:
                dp[i][j]=dp[i+1][j-1]+2
            else:
                dp[i][j]=max(dp[i+1][j],dp[i][j-1])
    return dp[0][n-1]
X=input()
print("The length of the LPS is",Lps(X))
```

## Output:

![image](https://github.com/user-attachments/assets/da730460-8772-4010-a19f-be7747710fff)



## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.
