## Sort Method, Sorted Function, Map Function, Filter Method, and Lambda Function Part 4

# Sort Method

Syntax:

```python

some_list.sort(reverse=True, key=some_func)

```

Sort method sorts elements of a given iterable in Ascending or descending order.

The reverse is optional, if it is true the sorted list is reversed (or sorted in Descending order).

The key is an optional, function that serves as a key for the sort comparison.

### Examples:

```python 

# sorting by ascending order

names_in_list = ['Anna', 'Sam', 'Henry', 'Jhon']
names_in_list.sort()
print(names_in_list) # ['Anna', 'Henry', 'Jhon', 'Sam']

# sorting by descending order

names_in_list = ['Anna', 'Sam', 'Henry', 'Jhon']
names_in_list.sort(reverse=True)
print(names_in_list) # ['Sam', 'Jhon', 'Henry', 'Anna']

# sorting by the length 

names_in_list = ['Anna', 'Sam', 'Henry', 'Jhon']
names_in_list.sort(key=len)
print(names_in_list) # ['Sam', 'Anna', 'Jhon', 'Henry']

# sorting by the salary

def get_salary(emp):
    return emp['salary']

employee = [
    {'name': 'Anna', 'salary': 1200},
    {'name': 'Sam', 'salary': 1330},
    {'name': 'Henry', 'salary': 1600},
    {'name': 'Jhon', 'salary': 1000}
]

employee.sort(key=get_salary)
print(employee) #[{'name': 'Jhon', 'salary': 1000}, {'name': 'Anna', 'salary': 1200}, {'name': 'Sam', 'salary': 1330}, {'name': 'Henry', 'salary': 1600}]

```

# Sorted Function

The sorted function returns a sorted list of iterable
With sorted function also can specify to sort them in ascending or descending order or specify the key for the sort comparison.

```python

names_in_list = ['Anna', 'Sam', 'Henry', 'Jhon']
print(sorted(names_in_list))  # ['Anna', 'Henry', 'Jhon', 'Sam']

# sorting by descending order

names_in_list = ['Anna', 'Sam', 'Henry', 'Jhon']
print(sorted(names_in_list, reverse=True))  # ['Sam', 'Jhon', 'Henry', 'Anna']

# sorting by the length

names_in_list = ['Anna', 'Sam', 'Henry', 'Jhon']
print(sorted(names_in_list, key=len))  # ['Sam', 'Anna', 'Jhon', 'Henry']


# sorting by the salary

def get_salary(emp):
    return emp['salary']


employee = [
    {'name': 'Anna', 'salary': 1200},
    {'name': 'Sam', 'salary': 1330},
    {'name': 'Henry', 'salary': 1600},
    {'name': 'Jhon', 'salary': 1000}
]

print(
    sorted(employee, key=get_salary))  # [{'name': 'Jhon', 'salary': 1000}, {'name': 'Anna', 'salary': 1200}, {'name': 'Sam', 'salary': 1330}, {'name': 'Henry', 'salary': 1600}]


```

# Map Function

Syntax :

``` python
map(some_fun, iterable)
```

**some_fun**: It is a function to which a map passes each element of a given iterable.

**iterable**: It is iterable which is to be mapped.


Map() is a function that allows you to process and transform all the elements in an iterable without using for a loop.
When you need to apply a transformation function to each item in an iterable and transform them into a new iterable.

### Example

Using the map() method to convert a list of strings to a list of integers
The map() function returns an iterator map object so you need to convert it into a list

```python

string_number = ['1', '2', '3']

numbers = map(int, string_number)

print(list(numbers)) # [1, 2, 3]


# Using the map() method to apply a custom function 

def addition(n):
    return n + n

numbers = (1, 2, 3, 4)
result = map(addition, numbers)
print(list(result)) # [2, 4, 6, 8]

```


# Filter Method

Syntax:

```python

filter(func, iterable)

```
The filter() method filters the given iterable with the help of a function that tests each element in the iterable to be true or not and returns a new iterator that is already filtered.
The filter() method returns an iterator filter object so you need to convert it into a list



### Example 

```python

salary = [1000, 1200, 3000, 1700, 900, 2200]

def func(x):
    if x >= 1700:
        return False
    else:
        return True


adults = filter(func, salary)

print(list(adults)) # [1000, 1200, 900]

```

# Lambda Function

Syntax :

```python

lambda arguments : expression

```
Lambda operator is used for creating small one time and anonymous function objects in python
A lambda function can take any number of arguments, but can only have one expression.


### Example

```python

lambda_func = lambda x: x + 1
print(var(5)) # 6


string_list = ['1', '2', '3']
number_list = list(map(lambda x: int(x), string_list))
print(number_list) # [1, 2, 3]

```

