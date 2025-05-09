+++
date = '2025-04-24T16:22:13+07:00'
draft = true
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

```python
# function with print()
def jumlah(a, b):
   print(a + b)

def new_jumlah(a, b):
   return a + b

test_print = jumlah(5, 10)

new_jumlah(test_print, 5)
```
