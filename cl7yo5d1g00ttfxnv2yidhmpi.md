## Python Decorators

## Introduction

Decorators are a feature of Python that lets you modify the behavior of functions without modifying their source code. This can be helpful with complex code, but it can also lead to some confusion if you're not careful. In this article, I'll explain how decorators work, and how they can be used in your own projects!


## Decorators

When you're working with Python, one of the most powerful things you can do is write decorators. Decorators add functionality to existing code, making it easier to reuse and extend.

There are many reasons to use decorators. They can help you:

- Reduce duplication of code
- Extend the functionality of existing code
- Write more expressive and readable code

A function can also generate another function:

```python
def hello_function():
     def say_hi():
         return "Hello"

     return say_hi


hello = hello_function()
print(hello())

```

## Closure

Python's closures are a powerful tool that allows a nested function to access the outer scope. This is a critical concept in decorators, which are a type of closure. Decorators are used to modify the behavior of a function, and they are especially useful for extending the functionality of third-party libraries. 

```python
def print_message(message):
     def message_sender():
         """Nested function"""
         print(message)

     message_sender()

print_message("Some message")
```

## Decorators definition

Python Decorators are very powerful and useful tools that allow us to modify the behavior of functions or classes. They are usually defined in the form of decorator functions which take a target object as an argument and return a modified version of this object. In Python, decorators can be applied to both functions and classes. When used properly, they can help reduce code repetition, make code more readable and make our programs more extensible.

## Creating decorators

In the example below we create a decorator function that converts a sentence to upper case

```python
def uppercase_decorator(function):
     def wrapper():
         result = function()
         uppercase_result = result.upper()
         return uppercase_result

      return wrapper

```

#### Using Decorators 

Our decorator function takes a function as an argument, so let us define a function and pass it to our decorator.
We learned earlier that we could assign a function to a variable.
We'll use that trick to call our decorator function.

```python
def say_hi():
     return 'hello there'

decorate = uppercase_decorator(say_hi)
print(decorate())
```

## Decorator an @

However, python provides a much easier way for us to apply decorators
We simply use the `@` symbol before the function we would like to decorate.

```python
@uppercase_decorator
def say_hi():
    return 'hello there'

print(say_hi())
```

## Accepting arguments 

Sometimes we might need to define a decorator that accepts arguments
We achieve this by passing the arguments to the wrapper function
The arguments will then be passed to the function that is being decorated at call time

```python
from time import time


def measure_time(func):
     def wrapper(*args, **kwargs):
         start = time()
         result = func(*args, **kwargs)
         end = time()
         print(end - start)
         return result

     return wrapper


@measure_time
def s():
     l = [1, 2, 3, 4, 5, 6, 7]
     return [x * 3 for x in l]

print(s())

```

## Passing arguments

In order to achieve this, we define a decorator maker that accepts arguments 
Then we define a wrapper function inside the decorator as we did earlier

```python
def repeat(n):
     def decorator(func):
         def wrapper(*args, **kwargs):
             for _ in range(n):
                 func(*args, **kwargs)

         return wrapper

     return decorator

@repeat(4)
def say_hi():
     print('hello')


say_hi()
```

## Class decorators

- classmethod - decorator function that converts a function to a class method

- abstractmethod - decorator function that converts an instance method to an abstract instance method

- abstractclassmethod - decorator function that converts a class method to an abstract class method

- @property - change your class methods/attributes so that the user of a class doesn't need to make any changes in their code

```python
class Person:
    def __init__(self):
        self.__name = ''

    @property
    def name(self):
        return self.__name

    @name.setter
    def name(self, value):
        self.__name = value


person = Person()

person.name = 'Sammy'

print(person.name)

```   

## Classes as decorators

We can also use classes as decorators
We usually do that when we need to maintain a state
to use a class as a decorator we need to implement the __call__ method
The __call__ method allows class instance to be called as functions

```python 
class Fibonacci:
    def __init__(self):
        self.cache = {}

    def __call__(self, n):
        if n not in self.cache:
            if n == 0:
                self.cache[0] = 0
            elif n == 1:
                self.cache[1] = 1
            else:
                self.cache[n] = self(n - 1) + self(n - 2)
        return self.cache[n]


fib = Fibonacci()

for i in range(5):
    print(fib(i))

print(fib.cache)


class FuncLogger:
    _logfile = 'out.log'

    def __init__(self, func):
        self.func = func

    def __call__(self, *args):
        log_string = self.func.__name__ + 'was called'
        with open(self._logfile, 'a') as opened_file:
            opened_file.write(log_string + '\n')
        return self.func(*args)


@FuncLogger
def say_hi(name):
    print(f'Hi {name}')


@FuncLogger
def say_buy(name):
    print(f'Bye {name}')


say_hi('Sammy')
say_buy('Sammy')
```