---
{"dg-publish":true,"permalink":"/03-coding/python/object-oriented-programming-python/"}
---

# Object Oriented Programming Python

*This will be entirely focused on object oriented python.*

>[!info]- What is Object Oriented Programming?
>In treats real-world entities as objects and groups related data and functionality together. In traditional programming languages like [[03 Coding/01 C/C\|C]] the data and functions are seperate and treated differently but in OOP they are grouped together as objects. 

>[!info]- Why Object Oriented Programming?
>In my personal opinion when dealing with real word entities or *things* in general oop makes so much sense. Consider the following 
>You have these functions  
>```c
>int get_age();
>string get_name();
>void get_date_of_birth();
>void print_details();
>```
>In functional programming languages like **C** you will pass a reference to a struct , which will be like follows
>```c
>struct Person {
>	int age;
>	string name;
>	string place_of_birth;
>	date date_of_birth;
>};
>```
>In **C** you will do like 
>```c
>get_name(&person1)
>get_age(&person1)
>get_date_of_birth(&person1)
>print_details(&person1)
>```
>And in oop we do something like, trust me dealing with pointers is hard for starters
>```python
>person.get_name()
>person.get_age()
>person.get_date_of_birth()
>person.print_details()
>```
>Using functional language with something to group together data like `struct` is great but some like to group functions too like c++ structs which allows to pack functions too. . and i do like the features comes with Object Oriented Programming like **inheritance**, **polymorphism** etc. Which makes sense and updating the codebase much easier. You can always change the logic of the function without changing the interface. It is possible in functional programming languages too but it is not as easy as in OOP.


**Class**: Is a blueprint for creating objects
**Object**: Is an instance of a class

## Class  and Objects
A class consists of set of attributes and methods. 
#example :

```python
class Person:
	def __init__(self, name, age):
		self.name = name  # Attributes
		self.age = age    # Attributes
	def print_age(self):
		print(f"Age is {self.age}")  # Method
```
Here `Person` is a class  and `name` and `age` are attributes. `print_age` is a method of the class.

**How to create an object?**

```python
P1 = Person("Arun",23)
P2 = Person("Arun Again",24)
```
You can create objects in this manner , and in the first creationm (P1) the `"Arun"` is passed as `name` and `23` is passed as `age`  and they will be assigned to `self.name` and `self.age` respectively.

**`self`**: `self` is a reference to the current instance of the class. It allows you to access attributes and methods of the class in Python.
You will learn about `__init__` method in detail below.

**Now how to access a method**:
```python
P1.print_age()  # This will print "Age is 23"
```

**Complete Program** #completeCode
```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Attributes
        self.age = age    # Attributes
    def print_age(self):
        print(f"Age is {self.age}")  # Method
P1 = Person("Arun",23)
P2 = Person("Arun Again",24)
P1.print_age()  
```
{ #caffc4}


### Initializer 
The `__init__` method is a special method in Python classes. It is called when an object of the class is instantiated. It initializes the attributes of the class.
Now consider the same code
![[#^caffc4]]

and consider the first **method** `__init__`:
```python
def __init__(self, name, age):
	self.name = name  # Attributes
	self.age = age    # Attributes
```
This function will be called when the object is created and it will take `name` and `age` as parameters and assign them to `self.name` and `self.age` respectively. You can do other things too here for example ;
#completeCode
```python
class Rectangle:
	def __init__(self, length, breadth):
		self.length = length
		self.breadth = breadth
		self.area = self.length * self.breadth 
	def print_area(self):
		print(f"Area is {self.area}")
R1 = Rectangle(2, 5)
R1.print_area() 
```

>[!success]- **Output**
>```
>Area is 10
>```


See , the `__init__` is just like a regular function and it can call another function etc . But it will have an aditional argument `self`  and it will be called when the object is created. So you do the essential things there like initializing attributes which will be used later.

>[!question]- **Can you create a class without `__init__`**?
> Yes
>```python
>class Empty:
>	pass
>	def print_something(self):
>		print("Something")
>E = Empty()
>E.print_something() 
>```


>[!question]- **Can you initialize without `__init__`** ? 
> Yes
>```python
>class Empty:
>	def print_something(self):
>		print("Something")
>	def initialize_attributes(self):
>		self.name = "Arun"
>		self.age = 23
>E = Empty()
>E.initialize_attributes()
>print(E.name)  #  "Arun"
>```

### `__str__` Method
The `__str__` method is a special method in Python that is used to define a string representation of an object. When you call `print()` on an object, Python will automatically call the `__str__` method to get the string representation of that object.
First try running this
```python
print(P1)
```
>[!success]- **Output**
>```
><__main__.Person object at 0x7bc68371da90>
>```

you will get something like `<__main__.Person object at 0x7bc68371da90>` but what if you can get something helpfull by printing the object itself. 

Now check this code.
#completeCode
```python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age
	def __str__(self):
		return f"Person Name: {self.name}"
Arun = Person("Arun", 23)
print(Arun) 
```

>[!success]- **Output**
> ```
> Person Name: Arun
>```

Here we have defined a `__str__` method which returns a string when called. 

[^1]: parent class in the sense that from where it is inheriting. 

## Inheritance
As the name says it **inherits** the attributes and methods of the parent class.[^1]
>[!question]- **Why**
> Because it is like the inheritance in the realworld and makes sense. Like a real chile often inherits the properties of the parent. if not consider money as a property , their chile will inherit the money too.😅

#example  


