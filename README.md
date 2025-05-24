# DAA_Module_22

# EX 4A DYNAMIC PROGRAMMING - 1
## DATE: 
## AIM:
To find longest common subsequence using Dynamic Programming.

## Algorithm
1. Take two input strings str1 and str2.
The final answer (length of LCS) is in dp[len(str1)][len(str2)].
2. Create a 2D array dp of size (len(str1)+1) x (len(str2)+1) and initialize with 0.
3. Loop through each character of both strings:
      If characters match, set dp[i][j] = dp[i-1][j-1] + 1.
4. Continue filling the table using the above rule. 
5. Else, set dp[i][j] = max(dp[i-1][j], dp[i][j-1]).  

## Program:
```Python
/*
Program to implement the longest common subsequence using Dynamic Programming.
Developed by: Gokularamanan K
RegisterNumber: 212222230040
*/
def longest_common_subsequence(str1, str2):
    m = len(str1)
    n = len(str2)
    
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if str1[i - 1] == str2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
    
    return dp[m][n]

str1 = input()
str2 = input()

result = longest_common_subsequence(str1, str2)
print("Length of LCS is :",result)
```

## Output:

![image](https://github.com/user-attachments/assets/b971ae55-3f3b-4269-9b65-94dbef527aef)



## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.


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
Developed by: Gokularamanan K
RegisterNumber: 212222230040 
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


# EX 4D DYNAMIC PROGRAMMING – 4
## DATE:
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.

## Algorithm
1. Take two input strings str1 and str2.
2. If either string is empty, return the length of the other (insert all characters).
3. If the last characters of both strings match, move to the remaining substring (str1[:-1], str2[:-1]).
4. If they don’t match, recursively compute the minimum of:
      Insert operation: LD(str1, str2[:-1])
      Delete operation: LD(str1[:-1], str2)
      Replace operation: LD(str1[:-1], str2[:-1]) 
5. Return 1 + minimum of the above three values.  

## Program:
```
/*
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method.
Developed by: Gokularamanan K
RegisterNumber: 212222230040
*/
```
```python
def LD(s, t):
    m = len(s)
    n = len(t)
    
    if m == 0:
        return n
    if n == 0:
        return m
    
    if s[m - 1] == t[n - 1]:
        return LD(s[:-1], t[:-1])
    
    return 1 + min(LD(s, t[:-1]),        
                   LD(s[:-1], t),        
                   LD(s[:-1], t[:-1])    
                   )    
str1=input()
str2=input()
print('Edit Distance',LD(str1,str2)) 

```

## Output:

![image](https://github.com/user-attachments/assets/88c02568-349c-4180-bcdf-c0d62ee783bf)



## Result:
Thus the program was executed successfully for finding edit distance between two strings.
