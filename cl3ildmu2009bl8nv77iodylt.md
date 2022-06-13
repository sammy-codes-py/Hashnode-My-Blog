## Python Basic (Variables and Data Types) Part 1

Let's start with python basic. There will be a couple of parts.

Python is an interpreted language
An interpreter is system software that converts the python codes into machine language codes(binaries) so the CPU can read them and do the required processes.
An interpreter executes the statements of code one by one.

# First will start with variables:

Variables are a way to store information and are characterized by name, type, and value.

### Example:
```python
# name of the variable, assignment operator, the value of type integer
number = 23
```

## Next, let's see what is a data type in python:

A data type is a classification that specifies which type of value a variable has and what type of operations can be applied to it.

### In python the following data types are:

- Numeric types: int(Integers), float (Floating-point), and complex
- Strings: str
- List, Set, Tuple, Dictionary
- Boolean

Examples:
```python
type_int = int(25)

type_float = float(2.2)

type_complex = complex(1 + 2j)

type_string = str('Phyton')

type_list = list(['Python', 'Java', 'JavaScript'])

type_set = set({1, 2, 3, 4, 5, 6})

type_tuple = tuple((1, 2, 3, 4, 5, 6))

type_dictionary = dict({0: 'Python', 1: 'Java', 'JavaScript'})

type_boolean = True
```
## Now let's discuss more about the types

Strings:

String used to represent textual data
Each element in the String occupies a position in the string
The length of a string is the number of elements in it
The string literals in python are surrounded by single or double quotation marks
Strings are immutable unlike in languages like C

### Example:
```python
name = 'Johnny Depp'

print(name[1]) # o
print(len(name)) # 11

name[0] = 'L' # TypeError: 'str' object does not support item assignment
```

#### Boolean:

Boolean represents a logical entity and can have two values:
- True
- False

```python
boolean_true = True
boolean_false = False
```

#### List:

A list contains items separated by commons and enclosed within square brackets.
We can access a specific element in a list by there position

```python
names_in_list = ['Anna', 'Jhon', 'Sammy']

print(names_in_list[0]) # Anna
```

#### Tuple:

A tuple is a collection that is ordered and unchangeable
In python, tuples are written with round brackets.

```python
names_in_tuple  = ('Anna', 'Jhon', 'Sammy')
```

#### Set
A set is a collection that is unordered and un-indexed, and the value is unique

```python
number_in_set = {1, 2, 2, 3, 4, 4}

print(number_in_set) # {1, 2, 3, 4}
```

#### Dictionary

A dictionary is a collection that is unordered, changeable, and indexed
While other data types have only value as an element a dictionary has key and value
Value can be of any data type and can repeat
Keys must be of an immutable type and must be unique

```python
names_in_dictionary = {1: 'Anna', 2: 'Sammy', 3: 'Jhon'}

```
Key can be used either inside square brackets or within the get() method
The difference while using get() is that it returns "None" instead of a key error if the key is not found
Dictionary is mutable

```python
print(Get:)
print(names_in_dictionary.get(2)) # Sammy
```

We can add new items or change the value of existing items using an assignment operator
If the key is already present value gets updated else a new pair is added to the dictionary

```python
names_in_dictionary[4] = 'Maria'
print(names_in_ dictionary) # {1: 'Anna', 2: 'Sammy', 3: 'Jhon', 4: 'Maria'}
```

That is the basics of variables and data types later will learn more about them.


