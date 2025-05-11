+++
date = '2025-04-24T16:22:13+07:00'
draft = false
toc = true
tags = ["python"]
title = 'Python Function Fundamentals'
+++

## Basic function

How to create and call function in Python?

```python
# create function greet
def greet():
   print("Hello Python!")

# call the greet() function
greet()
```

## Function parameters and arguments

Function take parameters and arguments for flexibility and usability.

```python
# name => the parameter
def greet(name):
   print(f"Hello {name}")

# call greet() function
# with argument => "ndlrfz"
greet("ndlrfz")
```

## Function with return value

Difference between `print` and `return` in Python:

* `print`: Display information to the console for users to see.
* `return`: Instead of printing, you can pass the **output** to the caller, or use `return` to exit a function or return value.

_Example function with `print`_:

```python
# function with print()
def jumlah(a, b):
   print(a + b)

test1 = jumlah(5, 10)

test2 = jumlah(test1, 5)
```

**Result**: **_TypeError_**

_Example function with `return`_:

```python
def jumlah(a, b):
   return a +_ b

test1 = jumlah(5, 15)

test2 = jumlah(test1, 10)
print(test2)
```

**Result**: **_30_**

## Function with default parameters

* Define default parameter and argument within the function.
* When function get called, the default parameter will be executed if no argument provided by users.

_Example_:

```python
def greet(name="world"):
   print(f"Hello {name}!")

greet() #output: Hello world!
greet("ndlrfz") #output: Hello ndlrfz!
```

## Function with *args (non-keyword arguments) and **kwargs(keyword arguments)

* Function with `*args` and `*kwargs` can take any numbers of arguments.
* The `*args` or _non-keyword arguments_ such as _string_ and _int_.
* The `**kwargs` or _keyword arguments_ is key value arguments.
* The `*` and `**` or asterisks that enabled the functionality in Python.
* You can replace `args` or `kwargs` with the name as you want.

_Example of _*args_ or non-keyword arguments_:

```python
def jumlah_semua(*args):
   return sum(args)

print(jumlah_semua(1, 5, 10, 15, 20, 25, 30)) #output: 106
```

_Example of _**kwargs_ or keyword arguments_:

```python
def user_info(**kwargs):
   for key, value in kwargs.items():
      print(f"{key}: {value}")

user_info(name="admin", age=25, born=2000)

#output:
#name: admin
#age: 25
#born: 2000
```

## Todo

* _High-order function, Lambda, Decorators_
