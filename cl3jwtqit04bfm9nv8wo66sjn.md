## Loops in Python Part 2

We will check loops in python with examples

# First let's see a for-loop

For loop is used to iterate over a sequence of iterable types like:

- tuple
- list
- other iterable types

Using an iterating variable that keeps track of the current item in the sequence. This allows a piece of code to be executed repeatedly for each member of the sequence.

For loop does not require an indexing variable to set beforehand.

##### Example:

```python

students_name = ['John', 'Anna', 'Sammy', 'Clark']

for name in students_name:
      print(name)

# John
# Anna
# Sammy
# Clark
 
```

#### range() function

With the range() function we can loop through a set of code a specified number of times.
The range() function returns a sequence of numbers, starting from 0 increments by 1, and ends at a specified number.

##### Example:

```python

for number in range(6):
      print(number)

# 0
# 1
# 2
# 3
# 4
# 5
```
Also, we can specify starting point in the range() function
by adding a number as the first parameter

##### Example:

```python

for number in range(2, 6):
      print(number)

# 2
# 3
# 4
# 5
```
The range() function increments the sequence by 1 but we can specify the increment value by adding a third parameter.

##### Example:

```python

for number in range(1, 6, 2):
      print(number)

# 1
# 3
# 5
```

#### items() method

We can use the items() method to access a key and a value of the dictionary

```python

words = {0: 'had', 1: 'hear', 3: 'home'}

for key, value in words.items():
      print(key, value)

# 0 had
# 1 hear
# 3 home
```

#### keys() and values() methods

Also there are keys() method and values() method
The keys() method returns the keys of the dictionary and the values() method returns the values

```python

words = {0: 'had', 1: 'hear', 3: 'home'}

for key in words.keys():
      print(key)

# 0
# 1
# 3

for value in words.values():
      print(value)

# had
# hear
# home
```
 

#### Else in for loop

Else in for loop executes the code after the for loop finished

##### Example:

```python

for number in range(3):
      print(number)
else:
     print('Done')

# 0
# 1
# 2
# Done
```
If the for loop is stopped by the 'break' statement code in the else statement will not be executed

#### Nested Loop

A nested loop is a loop inside another loop

##### Example:

```python

for i in range(3):
    print('first loop:', i)
    for j in range(2):
    	print('second loop:', j)

# first loop: 0
# second loop: 0
# second loop: 1
# first loop: 1
# second loop: 0
# second loop: 1
# first loop: 2
# second loop: 0
# second loop: 1
```

#### Break

The 'break' statement stops the loop before it has looped through all the items

##### Example:

```python
for name in students_name:
      if name == 'Sammy':
            print('found Sammy')
            break
```
#### Continue

The continue statement skips the current iteration of the loop and continues with the next value

##### Example:

```python
for name in students_name:
    if name == "Anna":
        print('skipped Anna')
        continue
    print(name)
```

# While loop

While loop we can execute a set of statements as long as a condition is true

##### Example:

```python

students_name = ['John', 'Anna', 'Sammy', 'Clark']

while students_name: # condition will be true until the list is empty
        students_name.pop()
        print(students_name)

# ['John', 'Anna', 'Sammy']
# ['John', 'Anna']
# ['John']
# []

```

#### Break and Continue

Also in the while loop, we can use a break and continue statements

```python

while students_name: # condition will be true until the list is empty
        if len(students_name) <= 1:
            break
        students_name.pop()
        print(students_name)

# ['John', 'Anna', 'Sammy']
# ['John', 'Anna']
# ['John']

```

#### Else 

Else in while loop executes the code after the condition is false

##### Example:

```python
while students_name: # condition will be true until the list is empty
        students_name.pop()
        print(students_name)
else:
        print('The list is empty')

# ['John', 'Anna', 'Sammy']
# ['John', 'Anna']
# ['John']
# []
# The list is empty

```
