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
