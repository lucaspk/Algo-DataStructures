
#Extended Euclidian Algorithm for GCD in Python - Recursive And Iterative

###Recursive Version
####This return c, such that c is : a*x + b*y = c = gcd(a, b)
```python
def egcd(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        c, x, y = egcd(b % a, a)
        return c
```
###If you want the values of x and y, you must do like this:
```python
def egcd(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        c, x, y = egcd(b % a, a)
        return (c, y - (a//b)*x, x)
```

##Iterative Version
###This is an iterative equivalent version of the recursive from above:
```python
def xgcd(b, n):
    x0, x1, y0, y1 = 1, 0, 0, 1
    while n != 0:
        q, b, n = b // n, n, b % n
        x0, x1 = x1, x0 - q * x1
        y0, y1 = y1, y0 - q * y1
    return  b
```

###Again!! If you want the values of x and y, you must do like this:
```python
def xgcd(b, n):
    x0, x1, y0, y1 = 1, 0, 0, 1
    while n != 0:
        q, b, n = b // n, n, b % n
        x0, x1 = x1, x0 - q * x1
        y0, y1 = y1, y0 - q * y1
    return  b, x0, y0
```

###If you what to figure out if some number G may be a solution of a Simple Linear Diophantine Equation:
####All you have to do is the MOD of this number with c. If the result is zero, G is a solution. Otherwise, the answer is no. So: 
```python
if G % c == 0 : 
  return True
else:
  return False
``` 
