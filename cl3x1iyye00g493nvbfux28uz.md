## OOP (Object-oriented programming) in Python

## Introduction

Object-oriented programming (OOP) is a style of programming that focuses on using objects to design and build applications. Think of an object as a single data structure that contains data as well as functions; the functions of an object are called methods. You can represent real-world objects using OOP, such as dogs, cars, or humans. You can also use OOP to represent more abstract objects, like numbers or geometrical concepts.


## OOP stands for Object-Oriented-Programing

OOP stands for Object-Oriented Programming. Object-oriented programming is a way of thinking about software instead of procedural or functional (or any other type of) programming. OOP allows you to model the real world in your code, which makes it much easier to write programs that do what you want them to do. Let's break down exactly what this means:

- OOP stands for "Object-Oriented Programming".

- A program that uses OOP is called an [object-oriented program](https://en.wikipedia.org/wiki/Object-oriented_programming).

- An object is something that has properties and behaviors, which are also called attributes and methods respectively (you'll learn more about these later).

## Principles of OOP 

The basic principles of OOP involve Abstraction, Encapsulation, Inheritance, and Polymorphism. There are also objects and classes. Together, they stand as the working principle of any object-oriented programming language.

1. Abstraction: The ability to hide details from your code and make it easier to understand. You can do this by finding a commonality between the things that are different, and then writing code that operates on those commonalities.

2. Encapsulation: The ability to hide the details of how something works so that it can be accessed only through a well-defined interface (i.e., not having to look at or understand how something actually works).

3. Inheritance: The ability of an object to inherit its parent's attributes and behaviors. This allows for easier code reuse and reduces redundant coding efforts when building new functionality from existing functionality (which is what makes inheritance such an important feature in OOP).

4. Polymorphism: The ability for one class of objects to behave differently from another class of objects based on their type or context; this is typically done through overriding functions within each class' definition, which allows them to behave differently depending on which function gets called by Python's interpreter engine at runtime.


## The first thing we will see is what the classes are and then we will see how to build a class in Python. Afterward, we will see the principles of object-oriented programming.

### Class Definition

A class is a blueprint that software designers can use to illustrate how users will interact with software, typically in an architectural or engineering design.
Classes are a mechanism for gathering and processing data and functionality together. Each instance of a class can have attributes attached to it.
Class instances can also have methods for modifying their state
All classes create objects and all objects contain characteristics called attributes.

The `__init__` method takes at least one argument as input (conventionally called self). Unlike other methods, this method is not called on an object but on a class itself. This initiates the newly created empty object (self) and gives it all attributes defined in `__init__` with their corresponding values.

### Self Variables

The self parameter is a reference to the current instance of the class, 
used to access variables that belong to the class.
When defining an instance method the first parameter of the method should always be self.

#### Example

```python
class Person:
     def __init__(self, first, last, age=0):
         self.first_name = first
         self.last_name = last
         self.age = age
```

### Object Definition

While the class is the blueprint, an instance is the concrete object of the class type and it's the concrete object that's individualized according to the needs of each class

``` python
first_person = Person('Anna', 'Maria', 25)
print(first_person.first_name)
print(first_person.last_name)
print(first_person.age)

# Anna
# Maria
# 25
```

### Modifying attributes

You can change the values of the attributes of an object after initialization.
The change will be made only for that instance of the class

```python
first_person.age += 1
print(first_person.age)
# 26
```

### Class attributes

Instance attributes are specific to the object, while class attributes are the same for all instances.

```python
class SecondPerson:
     species = 'mammal'

     def __init__(self, name, age):
         self.name = name
         self.age = age

second_person = SecondPerson('Peter', 20)
print(second_person.species)

# mammal
```

### Instance methods:

Instance methods are defined inside a class and help you get the contents of an instance. They are often the best way to call methods on the instances of a class.
They can also be used to perform operations with the attributes of our objects.
Like the `__init__` method the first argument should always be `self`.

```python
class Animal:
     def __init__(self, name, age):
         self.name = name
         self.age = age

     def calc_human_age(self):
         return self.age * 7


 animal = Animal('Terra', 6)
 print(animal.calc_human_age())

# 42
```

We use different methods to process code into functional blocks. It is easier to debug and the process for each method is contained. A single method should implement a single function.


### Scope and Namespace(Local, Global, and Build-in Namespace)

A namespace is a standard interface for local, global, and build-in namespaces and mapping that object to object.
There is no relation between names in a different namespace. 

##### Namespace order:
Built-in Namespace
Module: Global Namespace
Function: Local Namespace

#### Scope

Scope
A region in a program where a namespace is directly accessible 
In most the cases there are at least three nested scopes:
- The innermost witch is searched first
- The scopes of any enclosing functions
- The next-to-last scope (module's global names)
- The outermost(built-in names)

Example:

```python
def scopes():
     def local_scope():
         text = 'Local text'

     def nonlocal_scope():
         nonlocal text
         text = 'nonlocal text'

     def global_scope():
         global text
         text = 'global text'
```

### Static and class methods

Static Methods

A static method is a method that cannot access instance or class level variables or access any non-static methods. It only knows what types of information it receives in the parameters that it receives.
It's easy to turn a method into a static method 
All we have to do is to add a line with decorator `@staticmethod` in front of the method header

```python
class Robot:
     __counter = 0

     def __init__(self):
         type(self).__counter += 1

     @staticmethod
     def robot_instance():
         return Robot.__counter

print(Robot.robot_instance())
r = Robot()
print(r.robot_instance())
r2 = Robot()
print(r2.robot_instance())
print(Robot.robot_instance())

# 0
# 1
# 2
# 2
```

Class method

A class method on the other hand is a method that gets passed the class it was called on (or instance).
This is usually used when you have a Factory class and you need it to be able to create objects from within the class.
A class method is a method that is bound to the class and not the object of the class.
They have the access to the state of the class as it takes a class parameter that points to the class and not the object instance.
It can modify a class state that would apply across all the instances of the class. For example, it can modify a class variable that will be applicable to all the instances.
All we have to do is to add a line with `@classmethod` in front of the method header.

```python
from datetime import date


class Persons:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def from_birth_year(cls, name, birth_year):
        return cls(name, date.today().year - birth_year)

    def display(self):
        return print(self.name + '\'s age is: ' + str(self.age))


person = Persons.from_birth_year('Anna', 1992)
person.display()

# Anna's age is: 30

```

## Now that we know what classes and how to create a class in Python, it's time to see how they can apply the four principles in Python.

### Encapsulation

Encapsulation Definition

Allows us to put restrictions and can prevent the accidental modification of data

How to control access?
- Using a single underscore
- Using double underscore
- Using getter and setter methods to access private variables

##### Single underscore

Using a single leading underscore is merely a convention 
A name prefixed with an underscore should be treated as a non-public method/variable
It does not make any variable or method private or protected 

```python
class SomeClass:
    def __init__(self, name, age=0):
        self.name = name
        self._age = age


some_class = SomeClass('Peter', 25)
print(some_class.name)
print(some_class._age)

Peter
25

```
##### Double underscore

To make a method or variable private you can do it by prefixing it with a double underscore.

```python
class SecondSomeClass:
    def __init__(self, name, age=0):
        self.name = name
        self.__age = age

    def info(self):
        print(self.name)
        print(self.__age)


ssc = SecondSomeClass('Petter', 30)
ssc.info()  # accessing data truth class method
print(ssc.name)  # accessing data directly from outside
print(ssc.__age)  # AttributeError: 'SecondSomeClass' object has no attribute '__age'
```
##### Getter and Setter methods

Accessing and changing private variables require the use of accessor `getter` methods and mutator `setter` methods, which should be used as they are part of the class.

```python
class Student:
    def __init__(self, name, age=0):
        self.name = name
        self.__age = age

    def info(self):
        print(self.name)
        print(self.__age)

    def get_age(self):
        print(self.__age)

    def set__age(self, age):
        self.__age = age


stu = Student('Sammy', 29)
stu.info()  # accessing data using class method
stu.set__age(26)
stu.get_age()

# Sammy
# 29
# 26

```
Defining a Pythonic getter and setter is by defining properties. 
By defining properties you can change the internal implementation of a class without affecting the program.

```python
class Dog:
    def __init__(self, age=0):
        self.__age = age

    @property
    def age(self):
        return self.__age

    @age.setter
    def age(self, age):
        if age > 12:
            self.__age = 12 * 7
        else:
            self.__age = age


dog = Dog(6)
print(dog.age)
dog.age = 42
print(dog.age)

# 6
# 84
```

Private Methods

A private method is a class method that should only be called from inside the class where it is defined 
To define a private method prefix the name with a double underscore 

```python
class Person:
    def __init__(self):
        self.first = 'Petter'
        self.last = 'Parker'

    def __full_name(self):
        return f'{self.first} {self.last}'

    def info(self):
        return self.__full_name()


person = Person()
print(person.info()) # Petter Parker
print(person.__full_name)  # AtributeError
print(person._Person__full_name()) # Petter Parker
```

### Inheritance

##### Definition and Benefits

In inheritance, the new class is to be derived from the existing class. By inheritance, the variables and methods of the existing class are accessible in the new class. All classes in python are derived from the object class. When we create a Python class, internally the object class becomes the superclass. The main advantage of inheritance is code accessibility.

Benefits of Inheritance
-Code re-usability 
-All features to a class without modifying it
-It is transitive in nature


```python 
class Person:
    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name

    def get_full_name(self):
        return f'{self.first_name} {self.last_name}'


class Student(Person):
    pass


student = Student('John', 'Smith')  # An object of class Student
print(student.get_full_name())

# John Smith
```

##### The super() Method 

Using the super() built-in object returns a temporary object of the superclass. This temporary object can then be called in order to call methods of the superclass.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def get_info(self):
        return f'{self.name} is {self.age} old'


class Students(Person):
    def __init__(self, name, age, student_id):
        super(Students, self).__init__(name, age)
        self.student_id = student_id

    def get_id(self):
        return self.student_id


person = Person('John', 29)  # creating an object of the superclass

print(person.get_info())

student = Students('Leo', 20, 10035)  # creating an object of the subclass
print(student.get_info())
print(student.get_id())


```

There are four types of Inheritance:

- Single Inheritance:
When a child class inherits only a single parent class.

- Multiple Inheritance:
When a child class becomes a parent class for another child class.

- Multi-level Inheritance:
When a child inherits from multiple parent's classes.

- Hierarchical Inheritance:
Involves multiple inheritances from the base or parent class.



##### Single Inheritance:

```python 
class Person:
    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name

    def get_full_name(self):
        return f'{self.first_name} {self.last_name}'


class Student(Person):
    pass


student = Student('John', 'Smith')  # An object of class Student
print(student.get_full_name())

# John Smith
```

##### Multiple Inheritance 

```python
class Father:
    def __init__(self):
        self.father_name = 'Tyler Evans'


class Mother:
    def __init__(self):
        self.mother_name = 'Bet Williams'


class Daughter(Father, Mother):
    def __init__(self):
        Father.__init__(self)  # calling constructors of both parents class
        Mother.__init__(self)

    def get_parent_info(self):
        return f'{self.father_name} and {self.mother_name}'


child = Daughter()
print(child.get_parent_info())

# Tyler Evans and Bet Williams
```

##### Multilevel inheritance

```python
class Base:
    def __init__(self, name):
        self.name = name

    def get_name(self):
        return self.name


class Child(Base):
    def __init__(self, name, age):
        super(Child, self).__init__(name)
        self.age = age

    def get_age(self):
        return self.age


class GrandChild(Child):
    def __init__(self, name, age, address):
        super(GrandChild, self).__init__(name, age)
        self.address = address

    def get_address(self):
        return self.address


grand_child = GrandChild('Grand', 19, '153')
print(grand_child.name, grand_child.age, grand_child.address)

# Grand 19 153
```
##### Hierarchical Inheritance (Mixins)

```python
class Vehicle:
    def __init__(self, position):
        self.position = position

    def travel(self, destination):
        pass


class RadioMixin:
    def play_song(self, station_frequency):
        return f'{station_frequency}'


class Car(Vehicle, RadioMixin):
    pass


class Clock(RadioMixin):
    pass


car = Car('Sofia')
clock = Clock()
print(car.play_song(95.6))
print(clock.play_song(103))

# 95.6
# 103

```


### Polymorphism and Magic Methods

##### Polymorphism

Polymorphism is based on the Greek word "Many Forms"

Polymorphism, a programming concept, implies that objects can be used in different ways based on their base class and interface.

```python
class Animal: 
  def type(self): 
    print("Various types of animals") 
       
  def age(self): 
    print("Age of the animal.") 
     
class Rabbit(Animal): 
  def age(self): 
    print("Age of rabbit.") 

animal = Animal()
rabbit = Rabbit()

animal.type()
animal.age()

rabbit.age()

# Various types of animals
# Age of the animal.
# Age of rabbit.
```

### Abstract Classes

Abstract methods are methods that are declared but contain no implementation.
Abstract classes are classes that contain one or more abstraction methods.
Abstract classes may not be instantiated and require subclasses to provide implementations for the abstract methods.
Python doesn't have true abstract classes and methods.

To create an abstract class with the abstract method we have to import it from the ABC module.

```python

from abc import ABC, abstractmethod


class Animal(ABC):
    def __init__(self, name):
        self.name = name

    @abstractmethod  # Decorator function that make method abstract
    def sound(self):
        raise NotImplementedError('Subclass must implement')


class Dog(Animal):  # Inherit abstract class
    def __init__(self, name):
        super(Dog, self).__init__(name)

    def sound(self):  # Implement the abstract class
        print("Bark!")


class Cat(Animal):
    def __init__(self, name):
        super(Cat, self).__init__(name)

    def sound(self):  # Implement the abstract class
        print("Meow!")

dog = Dog('Willy')
dog.sound()
cat = Cat('Merry')
cat.sound()

# Bark!
# Meow!

animal = Animal('Terra') # TypeError: Can't instantiate abstract class Animal with abstract methods sound
```

#### Magic Methods

Magic methods in Python are the special methods that start and end with the double underscores. 
They are also called dunder methods. Magic methods are not meant to be invoked directly by you, but the invocation happens internally from the class on a certain action. 
For example, when you add two numbers using the + operator, internally, the __add__() method will be called.

Use the dir() function to see the magic methods inherited by a class in the "int" class
```
>>> dir(int)
[__abc__, __add__, __and__, ....]
```
Example :
If we have a class Person and we want to compare them by their age using the > operator we can override the `__gt__` magic method.

```python
class Person:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def __gt__(self, other):
        return self.salary > other.salary


person = Person('Sammy', 1000)
person_two = Person('Max', 2000)
print(person > person_two)

# False

```


"""

## Dependency Inversion

The Dependency Inversion Principle (DIP) states that high-level modules should not depend on low-level modules; both should depend on abstractions.

## Dependency Injection

Software engineering technique for defining the dependencies among objects.

Why use dependency injection?
- Decreases coupling between a class and its dependency 
- Can be applied to legacy code as a refactoring because it doesn't require any change in code behavior.
- Allow a client to remove all knowledge of a concrete implementation that is needed to use.

###### Example:
```python

class Email:
    def send_email(self):
        pass


class Notification:
    def __init__(self):
        self._email = Email()  # notification depends on class Email

    def promotional_notification(self):
        self._email.send_email()

```
###### Example Constructor Injection

```python
class IMessageService: 
    def send_message(self):
        pass


class Email(IMessageService):
    def send_message(self):
        pass


class Notification:
    def __init__(self, service: IMessageService):
        self._service = service

    def promotional_notification(self):
        self._service.send_message()
```


## Conclusion

To summarize, OOP is a programming paradigm that uses objects and their interactions to design applications and computer programs. OOP provides a clear structure for programs. It helps programmers to do work more easily by creating reusable code. It also helps provide better control over data within the program. Object-oriented programming has four pillars: Abstraction, Encapsulation, Inheritance, Polymorphism