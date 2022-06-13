## Function in Python Part 5

# Function

A function is a named piece of code that can take parameters and return results.
The purpose of the function is to split large problems into pieces, better organization of the program, readability, understandability, 
avoids repeating code also improve code maintainability, and code reusability (Using existing functions several times).

### Example

```python

names_students = ['Anna', 'Sammy', 'John', 'Petter']

def order_names_by_alphabetical(name_list):
    return sorted(name_list)

print(order_names_by_alphabetical(names_students)) # ['Anna', 'John', 'Petter', 'Sammy']

```

# Parameter

A parameter is variable defined in the function's definition

### Example

```python

def some_function(parameter):
    return parameter

```

# Argument 

The argument is the actual value that we pass to the function

### Example

```python 

def some_function(parameter):
     return parameter

some_argument = []
some_function(some_argument)

```

function arguments can have a default value

### Example

```python

def some_function(age=30):
    return age

```

# Packing arguments (*args, **kwargs)

```python

def some_function(*args, **kwargs)
    pass

```

This operation is called packing.
We pack all arguments into one single variable.
Using packing when we need to be passed to a function

## *Args

We use *args to pack arguments into a tuple.

### Example

```python 

def some_function(*args):
    return args

print(some_function(2, 3, 4)) # (2, 3, 4)

```

## **Kwargs

The **kwargs allows us to pass a keyworded variable to a function

### Example

```python

def some_function(**kwargs):
    for key, value in kwargs.items():
        print(f'{key} : {value}')


some_function(name='Anna', age=25, country='Bulgaria')

# name : Anna
# age : 25
# country : Bulgaria

```

# Unpacking

We can use '*' to unpack the list so that all elements of it can be passed as different parameters and '**' to unpack a dictionary so all of its elements are passed as worded arguments.
The length of the list that we unpack must be the same as the number of parameters in the function.

### Example

```python

def print_numbers(num_one, num_two, num_three):
    print(num_one, num_two, num_three)

numbers = [1, 2 ,3]

print_numbers(*numbers) # 1 2 3

``` 

When we unpack the dictionary, the keys of the dictionary must match the names of the parameters of the function.
The order of the keys does not matter.

### Example

```python

def print_student(name, age, grade):
    print(f'{name} is {age} old and have grade of {grade}')


student = {'age': 25, 'grade': 5.5, 'name': 'Anna'}
print_student(**student) # Anna is 25 old and have grade of 5.5

```
 
# Recursion

Recursion is a process in which a function calls itself.
A recursion function  has the following structure:

- A base case
- A recursive case

### Example

```python

def recursion_function(n):
    if n == 1:
        return 1
    return n + recursion_function(n - 1)


print(recursion_function(5)) # 15

```

Recursion is a very powerful tool for writing an algorithm like a Fibonacci problem:

Example:

```python

def fibonacci(n):
    if n == 1 or n == 2:
        return 1 
    else:
        return(fibonacci(n-1) + fibonacci(n-2))
        
n = 6
for i in range(1,n+1):
    print(fibonacci(i))

# 1
# 1
# 2
# 3
# 5
# 8

```