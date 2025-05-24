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
