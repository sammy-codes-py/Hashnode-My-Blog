## Python Methods in Collection Data Types
(List, Tuple, Set, and Dictionary) Part 3

# What is a collection? 

Collections are containers used for storing data and it is known as data structures.
There are four collection data types in Python:
- list: ordered and changeable 
- tuple: ordered and unchangeable
- set: unordered, unchangeable, and not allow duplicate value
- dictionary: ordered, unchangeable, and not allow duplicate keys

# Methods in List

In python, there are a lot of methods in a list:

- **append()**: adding an element to the end of the list
- **extend()**: adding all elements of iterable to list
- **insert()**: accept two arguments, the first is the index that we want to insert the element, and the second is the argument element that we want to insert
- **remove()**: accept the argument as an element and remove it from the list on the first occurrence of the element
- **pop()**: by default return the element to the end of the list and remove it from the list or accept the argument as an index to pop the element in that index from the list
- **index()**: accept the argument as an element and returns the index of the element
- **count()**: accept the argument as an element and return the number of occurrences of the element in the list 
- **reverse()**: reverse elements of the list
- **sort()**: by default sorts the list in ascending order or can assign reverse = False to sort it in descending order also we can assign the key with some function to specify the sorting comparison
- **copy()**: return a shallow copy of the list
- **clear()**: delete all elements in the list 

```python

names_in_list = ['Anna', 'Marty', 'Sammy']

names_in_list.append('Jhon') # ['Anna', 'Marty', 'Sammy', 'Jhon']

names_in_list.extend(['Anna', 'Hanry']) # ['Anna', 'Hanry', 'Anna', 'Marty', 'Sammy', 'Jhon']

names_in_list.insert(0, 'Maria') # ['Maria', 'Anna', 'Hanry', 'Anna', 'Marty', 'Sammy', 'Jhon']

names_in_list.remove('Anna') # ['Maria', 'Hanry', 'Anna', 'Marty', 'Sammy', 'Jhon']

names_in_list.pop() # ['Maria', 'Hanry', 'Anna', 'Marty', 'Sammy']

names_in_list.pop(0) #  ['Hanry', 'Anna', 'Marty', 'Sammy']

print(names_in_list.index('Hanry')) # 0

print(names_in_list.count('Anna')) #  1

names_in_list.sort()
print(names_in_list) # ['Anna', 'Hanry', 'Marty', 'Sammy']

names_in_list.sort(reverse=True)
print(names_in_list) # ['Sammy', 'Marty', 'Hanry', 'Anna']

names_in_list.sort(key=len) # will sort it by the length of the elements
print(names_in_list) # ['Anna', 'Hanry', 'Marty', 'Sammy']

new_list_of_names = names_in_list.copy() # ['Anna', 'Hanry', 'Marty', 'Sammy']

new_list_of_names.clear() # []
```

# Methods in Tuple

In tuple, there are only two methods count() and index() there are the same as list methods

- index(): accept the argument as an element and returns the index of the element
- count(): accept the argument as an element and return the number of occurrences of the element in the list 

```python

names_in_tuple = ('Anna', 'Marty', 'Anna', 'Sammy')

print(names_in_tuple.index('Marty')) # 1

print(names_in_tuple.count('Anna')) #  2

```

# Methods in Set

- **add()**: Adding an element
- **copy()**:	Returns a copy
- **difference()**:	Returns a set containing the difference between two or more sets
- **difference_update()**: Removes the elements in the set that are also included in another set
- **discard()**: accept the argument as an element and remove it from the set
- **intersection()**: Returns a set, that is the intersection of two or more sets
- **intersection_update()**:	Removes the elements in this set that are not present in other
- **isdisjoint()**: Returns whether two sets have an intersection or not
- **issubset()**:	Returns whether another set contains this set or not
- **issuperset()**:	Returns whether this set contains another set or not
- **pop()**: by default pop the first element of the tuple or accept the argument as an index to pop the element in that index from the tuple
- **remove()**: accept the argument as an element and remove it from the list on the first occurrence of the element
- **symmetric_difference()**: Returns a set with the symmetric differences of two sets
- **symmetric_difference_update()**: inserts the symmetric differences from this set and another
- **union()**: Return a set containing the union of sets
- **update()**: Update the set with another set, or any other iterable
- **clear()**: Removes all the elements


```python

names_in_set = {'Anna', 'Marty', 'Sammy'}
names_in_set.add('Karma') # {'Anna', 'Marty', 'Sammy', 'Karma'}

new_set_of_names = names_in_set.copy()
print(new_set_of_names) # {'Anna', 'Marty', 'Sammy', 'Karma'}

second_names_in_set = {'Marty', 'Sammy'}
print(names_in_set.difference(second_names_in_set)) # {'Karma', 'Anna'}

names_in_set.difference_update(second_names_in_set)
print(names_in_set) # {'Anna', 'Karma'}

names_in_set.discard('Anna') # {'Karma'}

names_in_set.intersection(second_names_in_set)
print(names_in_set) # {'Karma'} 

names_in_set.intersection_update(second_names_in_set)
print(names_in_set) # set()

print(names_in_set.isdisjoint(second_names_in_set)) # True

print(names_in_set.issubset(second_names_in_set)) # True

print(names_in_set.issuperset(second_names_in_set)) # False

new_names_in_set = {'Anna', 'Marty', 'Sammy',  'Karma'}
print(new_names_in_set) #  {'Anna', 'Marty', 'Sammy', 'Karma'}
new_names_in_set.pop() # {'Marty', 'Sammy', 'Karma'}

new_names_in_set.remove('Marty') # { 'Sammy', 'Karma'} 

new_second_names_in_set = {'Hanry', 'Noa', 'Oliver', 'Sammy', 'Karma'}
print(new_names_in_set.symmetric_difference(new_second_names_in_set)) # {'Noa', 'Hanry', 'Oliver'}

new_names_in_set.symmetric_difference_update(new_second_names_in_set)
print(new_names_in_set) # {'Sammy', 'Oliver', 'Anna', 'Hanry', 'Noa'}

print(new_names_in_set.union(new_second_names_in_set) # {'Sammy', 'Anna', 'Karma', 'Oliver', 'Hanry', 'Noa'}

new_names_in_set.update(['Anna', 'Sam', 'Has'])
print(new_names_in_set) # {'Sam', 'Oliver', 'Noa', 'Karma', 'Anna', 'Has', 'Hanry'}

new_names_in_set.clear() # set()

```

# Methods in Dictionary

- **fromkeys()**: Returns a dictionary with the specified keys and value
- **get()**: Returns the value of the specified key
- **items()**: Returns a list containing a tuple for each key-value pair
- **keys()**: Returns a list containing the dictionary's keys
- **values()**: Returns a list of all the values in the dictionary
- **pop()**: Removes the element with the specified key
- **popitem()**: Removes the last added key-value pair
- **setdefault()**: Returns the value of the specified key. If the key does not exist: insert the key, with the specified value
- **update()**: Updates the dictionary with the specified key-value pairs
- **copy()**: Returns a copy of the dictionary
- **clear()**: Removes all the elements from the dictionary


```python

names = {'Anna', 'Sammy', 'Karma'}
salary = 1200
dict_names_with_salary = dict.fromkeys(names, salary)
print(dict_names_with_salary) # {'Karma': 1200, 'Sammy': 1200, 'Anna': 1200}

print(dict_names_with_salary.get('Anna')) # 1200

print(dict_names_with_salary.items()) # dict_items([('Anna', 1200), ('Sammy', 1200), ('Karma', 1200)])

print(dict_names_with_salary.keys()) # dict_keys(['Karma', 'Sammy', 'Anna'])

print(dict_names_with_salary.values()) # dict_values([1200, 1200, 1200, 2000, 1000, 1300, 1444])


dict_names_with_salary.pop('Anna')
print(dict_names_with_salary) # {'Karma': 1200, 'Sammy': 1200}

dict_names_with_salary['Maria'] = 2000
dict_names_with_salary['Henry'] = 3000
print(dict_names_with_salary) # {'Sammy': 1200, 'Karma': 1200, 'Anna': 1200, 'Maria': 2000, 'Henry': 3000}
dict_names_with_salary.popitem()
print(dict_names_with_salary) # {'Sammy': 1200, 'Karma': 1200, 'Anna': 1200, 'Maria': 2000}

dict_names_with_salary.setdefault('Oliver', 1000)
print(dict_names_with_salary) # {'Karma': 1200, 'Sammy': 1200, 'Anna': 1200, 'Maria': 2000, 'Oliver': 1000}

new_names = {'Noa': 1300, 'Lea': 1444}
dict_names_with_salary.update(new_names)
print(dict_names_with_salary) # {'Sammy': 1200, 'Anna': 1200, 'Karma': 1200, 'Maria': 2000, 'Oliver': 1000, 'Noa': 1300, 'Lea': 1444}

new_dict = dict_names_with_salary.copy()
print(new_dict) # {'Sammy': 1200, 'Anna': 1200, 'Karma': 1200, 'Maria': 2000, 'Oliver': 1000, 'Noa': 1300, 'Lea': 1444}

dict_names_with_salary.clear()
print(dict_names_with_salary) # {}

```

Methods in collections data type make it very easy to work with collections.

The most common interview questions are with a collection, for example: 

- Remove Item from List (and also Remove First and Last Item from List)
- Remove Duplicates from the List