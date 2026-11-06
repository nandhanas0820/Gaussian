# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Start and read the number of unknowns and the augmented matrix
2. Perform forward elimination to convert the matrix into an upper triangular matrix
3. Use back substitution to calculate all the unknowns
4. Display the values of the unknowns up to two decimal places amd stop

## Program:
```
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: Nandhana S
RegisterNumber: 26011506
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
import sys

#reading number of unknowns
n=int(input())
#making numpy array nxn+1 size and initializing to zero for storing solution vector
a=np.zeros((n,n+1))
#making numpy array of n size and initializing to zero for storing solution vector
x=np.zeros(n)
#reading augmented matrix coefficients 
for i in range(n):
    for j in range(n+1):
        a[i][j]=float(input())
#applying gauss elimination 
for i in range(n):
    if a[i][i]==0.0:
        sys.exit('Divide by zero detected!')
    for j in range(i+1,n):
        ratio=a[j][i]/a[i][i]
        for k in range(n+1):
            a[j][k]=a[j][k]-ratio*a[i][k]
#back substitution
x[n-1]=a[n-1][n]/a[n-1][n-1]
for i in range(n-2,-1,-1):
    x[i]=a[i][n]
    for j in range(i+1,n):
        x[i]=x[i]-a[i][j]*x[j]
    x[i]=x[i]/a[i][i]
#display solution 
for i in range(n):
    print('X%d = %0.2f'%(i,x[i]),end=' ')
```

## Output:
<img width="1102" height="847" alt="Screenshot 2026-11-06 082123" src="https://github.com/user-attachments/assets/9d9e9d6c-a466-4b7b-8f47-713f989bd785" />

<img width="1132" height="845" alt="Screenshot 2026-11-06 082144" src="https://github.com/user-attachments/assets/f378a641-61eb-4314-bf7b-005fb73ca57a" />


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

