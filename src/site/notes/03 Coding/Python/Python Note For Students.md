---
{"dg-publish":true,"permalink":"/03-coding/python/python-note-for-students/"}
---

# Python Note For Students
 *Note #for_students* 
**Should Contain**
-  [ ] Simple intro
-  Basics
	- [x] Variables , Datatypes, Comment ✅ 2025-05-30
	- [x] Loops ✅ 2025-05-30
	- [x] Control Statements ✅ 2025-05-30
	- [x] Functions ✅ 2025-05-30
	- [ ] Scope 


## First Program

```python
print("Hello World!")
```
{ #504014}


**What do you need?** 
- You will need the python interpreter installed and it's path should be in the `PATH` env variable 
	- Go [Here](https://www.python.org/) and install the python 
- there must be an option in the installer wizard for adding the python binary path to environment variables 

**How to run it**?
- Open a text editor 
- type the first program ![[#^504014]] and save with `.py` extension
- run it using python
```bash
python first_program.py
```

>[!Note] 
>The weird thing with python is that it is a scipting language yet most of the python programs are not scripts. And it is not like older programming languages it requres only very few lines eg:
>```python
>"Hello World!"
>``` 
>This will also print `Hello World!` to the terminal


## Basics

### Input/Output

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



#### Input , output , processing


```python
# input
a = input("Enter a number")

# output
print(a)
```

- One thing to note here that the default type will be a string from the `input()` and you may need to type cast it to work as expected for example 
```python
a = input("Enter a number")
if a==5:
	print("HI")
```
- this program will not work as expected (run and find out) (happens because `int(5)` is not same as `str(5)`)
```python
a = int(input("Enter a number"))
if a==5:
	print("HI")
```


</div></div>


### Datatype

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



#### Data types

| Integer          | `int`, `long` | 1,2,3, -1 , 0       |
| ---------------- | ------------- | ------------------- |
| Real Numbers     | `float`       | 1.2 , -1.2          |
| Character strngs | str           | "HI" , "" , "Hello" |


</div></div>


### Operators

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



### Operators
1. Arithmetic

#### Arithmetic Operators
```python
a , b  = 1 , 2 
a + b  # 3 "#" is the single line comment
a - b  # -1  
a * b  # 2 
a / b  # .5 
a % b  #  1 
b ** 2 # 4
a // b # 0
```

#### Comparison Operator

```python
a, b = 5, 10

# Equal to
a == b  # False

# Not equal to
a != b  # True

# Greater than
a > b   # False

# Less than
a < b   # True

# Greater than or equal to
a >= b  # False

# Less than or equal to
a <= b  # True
```
#### Logical Operators

```python
x, y = True, False

# AND - True if both operands are True
x and y  # False

# OR - True if at least one operand is True
x or y   # True

# NOT - Inverts the Boolean value 0 -> 1 , 1 -> 0
not x    # False
not y    # True
```

#### Membership Operators
```python
lst = [1, 2, 3, 4]
name = "Arun"

# IN - True if value is found in sequence
2 in lst       # True
"run" in name  # True
5 in lst       # False

# NOT IN - True if value is not found in sequence
5 not in lst   # True
"y" not in name # True
```

#### Identity Operators
```python
m = [1, 2]
n = [1, 2]
p = m

# IS - True if both variables point to same object
m is p    # True

m is n    # False (same values but different objects)

# IS NOT - True if variables point to different objects
m is not n  # True
```

```python
print(m is n) # False , different objects even if values are sae
print(m == n) # True same value even if different objects
``` 

#### Bitwise Operators

```python 
a , b = 1, 2  # 01 , 10

''' Bitwise AND 
  01
& 10 '''
a & b  # 0

#Bitwise OR
# 11 
a | b  # 3

# Bitwise XOR
 
a ^ b  # 3

# Bitwise NOT
# this might be confusing explain later.
~a     # -2

#  Left Shift (<<)

a << 1  # 2

#Right Shift (>>)
a >> 1  # 0
```

- [ ] explain biwise `not` 🏁 delete 

#### Assignment Operators
```python
x = 10

x += 3  # x = x + 3 → 13
x -= 2  # 11
x *= 2  #  22
x /= 4  # 5.5
x %= 3  #  2.5
x **= 2 #   6.25
x //= 2 #  3.0
```


</div></div>



### Functions

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## Functions and Modules
#syntax 


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/02-academics/btech/s7/python-for-engineers/class-notes/#8ae1a2" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Class Notes

</div>


```python
def function_name(parameters):
	.
	.
	.
	return
```

</div></div>



#example 


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/02-academics/btech/s7/python-for-engineers/class-notes/#06cc71" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Class Notes

</div>


```python
def sum(a, b):
    return a + b
def differece(a, b):
    return a - b
def division(a, b):
    return a / b
def multiplication(a, b):
    return a * b
print("Sum = ", sum(10, 20))
print("Difference  = ", differece(10, 20))
print("Division = ", division(10, 20))
print("Multiplication = ", multiplication(10, 20))
```

</div></div>





</div></div>



>[!Note]- 
>Closed Note



