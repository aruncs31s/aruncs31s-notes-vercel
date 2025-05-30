---
{"dg-publish":true,"permalink":"/03-coding/python/python-note-for-students/"}
---

# Python Note For Students
 *Note #for_students* 
**Should Contain**
- [[#First Program|Intro]]
- 

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


## Input/Output


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/02-academics/btech/s7/python-for-engineers/class-notes/#ca3a12" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Class Notes

</div>


```python
name=input("Enter Your Name")
print(name)
print("Hi " + name);
```

</div></div>


- This is simple enugh but here just one thing to note is that 


```python
number=input("Enter a Number")
if(number == 5):
	print("Number is 5")
```

