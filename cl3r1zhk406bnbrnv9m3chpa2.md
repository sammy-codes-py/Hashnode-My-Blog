## Iterators and Generators in Python. Part 6

# Introduction

Understanding loops is one of the fundamentals of programming. As a developer, you will use loops every day, so it's important to understand all of the ways that you can control them. In this tutorial, we will discuss: What are iterators?

What are generators?

How do you create your own iterators and generators?


# Iterators

An iterator is an object that can be iterated (looped) upon. Technically speaking, in Python, an iterator is an object which implements the iterator protocol, which consists of the methods __iter__() and __next__().

An object is called iterable if we can get an iterator from it
Such are list, tuple, string, etc.


The __iter__() method is used to return an iterator. For example, if you have a list, you can get an iterator from it by calling the `iter()` function on it:

### Example

```python
my_list = [4, 5, 6, 7, 8, 9]
my_iter = iter(my_list)  # get on iterator using iter()

```

In this case, `my_iter` is a list and our `iter()` call returned an object called “list_iterator". This is essentially an object which implements both __iter__ and __next__ methods. The next method returns the next element from this iterator until there are no more elements left in it:

```python
print(next(my_iter))
print(next(my_iter))
print(next(my_iter))
next(my_iter) # calling next element without printing it
print(next(my_iter))

# 4
# 5
# 6
# 8

```

## For loops and Iterators

The for loop can iterate automatically through the list.
The for loop can iterate over any iterable
A for loop is implemented as:

```python
iter_obj = iter(iterable)
While True:
    try:
        element = next(iter_obj)  # get the next item
        #  do something with elements 
    except StopIteration:
        #  if StopIteration is raised break
        #  for loop
        #  break

```

The for loop creates an iterator object (iter_obj) by calling iter() on the iterable.
Inside the loop, it calls next() to get the next element and executes the body of for loop with this value.
After all the items exhaust StopIteration is raised which is internally caught and the loop ends.


# Generators

Generators are functions that return an iterator to their caller.

They're not like normal functions, however - they're actually iterators themselves! A generator is an object that implements the __iter__ and __next__ methods of Python's iterator protocol. The function callable object then uses these methods to iterate over a series of values by calling other code inside the generator.

### Example

```python
def first_n(n):
    num = 0
    while num < n:
        yield num
        num += 1


sum_firs_n = sum(first_n(5))
print(sum_firs_n) # 10

```

## The yield statement

if the function contains at least one yield statement it becomes a generator function.
Both `yield` and `return`  will return a value from a function.
The difference between `yield` and `return` is that the `return` statement terminates a function entirely.
`Yield` however pauses the function saving all its states and later continues from there on successive calls.

## Generator Expression

Generators can be easily created using generator expressions.
Same as the `lambda` function creates an anonymous generator function.

Example: Generator Expression

```python

my_list = [1, 3, 6, 10]  # Initialize the list
# square each term using list comprehension
print([x ** 2 for x in my_list])

# the same thing can be done using a generator expression
# generator expressions are surrounded by parenthesis ()
print((x ** 2 for x in my_list))

```

One way I've found that makes me really happy about using generators is when dealing with data structures that have cycles (like lists). Usually, we would create an iterator by defining a class but with generators, we don't need classes at all!

With generators, instead of using the next() function all the time and having to call yield every once in a while, we can simply write something like:

```python
def reverse_str(my_str):
    length = len(my_str)
    for i in range(length - 1, -1, -1):
        yield my_str[i]


# For loop to reverse the string
for char in reverse_str("hello"):
    print(char)

# o
# l
# l
# e
# h
```

# Conclusion

Iterators and Generators are objects that can cycle through a series of values. Iterators have their own methods, with next() being the most common. Generators use the yield keyword to return values one at a time when called. They're simple to implement and use much less memory than iterators because they don't store all the values in memory at once.