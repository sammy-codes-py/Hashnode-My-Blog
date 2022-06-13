## Build Solid Software (Testing)

## Introduction

The world of software testing can be a complicated and difficult one to navigate, especially for beginners. That's why it's crucial to have the right tools on hand when you're starting out because they'll help ease your onboarding process and make your test development much easier than it would be otherwise. In this blog post, we'll give you a rundown of some of the most important software testing tools available today and explain how they can take your career in this field to the next level.


## Testing

Testing is a process of verifying the quality of a software product and providing evidence that it can be trusted. Testing is not just about finding bugs, but also about improving the development process so that new features are integrated smoothly into the existing system. There are many different types of testing, including manual testing, integration testing, and performance testing. 

## Testing in Python and Types

Python has an extensive collection of built-in modules that make it easy to write complex programs quickly with few lines of code per task. However, this comes at the expense of less robustness than other programming languages such as C++ or Java, because these modules were designed for quick prototyping rather than full-fledged production applications(although they can be used in production if necessary). To ensure that your application works correctly once you, have finished building it with Python's default libraries/modules you must write various kinds of tests before releasing anything into production servers:

- Unit Test: These tests check if individual parts work correctly when combined together inside larger components like functions or classes;

- Integration Tests: This type involves calling different pieces together using actual data from external sources such as databases or network connections;

- Acceptance Tests: These verify whether some expected behavior matches what was originally specified by stakeholders (e..g.. clients) beforehand;

- System testing. Once all the pieces have been put together and tested separately, you can move on to system-level tests where you simulate real-world usage scenarios by using multiple components together in order to see how they behave under load conditions or against various kinds of data inputs.


## Triple-A Pattern

Arrange, act, and assert are a pattern for testing software (also known as AAA). You can use it to create a test case that verifies the correctness of your code.

- Arrange: Set up the data you need in order to test the functionality you want to test. For example, if you are testing an algorithm that calculates the average of a list of numbers, arrange some sample arrays with different numbers in them so they will make sense when run through your code.

- Act: Run your code and see if it gives you what you expect or not. If everything goes as planned and there are no errors or other problems during this step then we continue on; Otherwise, we stop here because something went wrong.

- Assert: Assert is a method useful in determining the pass or fail status of a test case. There are various types of assertions like Boolean, Null, Identical, etc.

## Manual Testing 

The best way to learn how to manually test software is by doing it. That said here are some tips:

- When you are testing manually you will want to watch out for two things: the application itself, and the environment in which it's running. One of the main advantages of manual testing is that it allows you more freedom than automated testing does; This means that you can look at your software from different angles and see how it behaves outside of its normal working environment (like with only one person using it instead of multiple users). The disadvantage here is that while you have more flexibility, less control over your environment means a greater chance that something will go wrong when you are typing to test out your idea or product.

- Even if there aren't any bugs with your program itself, there could still be problems associated with how users interact with those programs - for example, a user might click on an icon without realizing that clicking this icon launches another process entirely! These types of issues are harder for computers because they require human intelligence; however, they can be very easy for us as humans because we have experience using these kinds of interfaces ourselves.


## Away from Manual Testing

Away from manual testing (ATM) is a process of automating scripted testing by recording the actions performed by a human tester to test the application. It allows you to test your software continuously and ensure it works as expected.

There are several benefits to ATM:

- More time-efficient. You can run more tests in less time with automated tests than with manual ones.

- Less error-prone. Automated tests can be run repeatedly without human errors, so they are more reliable than manual tests.

- More efficient bug reporting and fixing cycles since bugs are identified faster and fixed quicker.


## Automated Testing

Automated testing is the process of using a computer program to test another software program. Automated testing is done by software tools like `pytest`, rather than by humans. It can be considered a type of white box testing.

An automated test is written as code and stored in source control like any other piece of code, with all the advantages (and disadvantages) it entails. In order for automated tests to be run consistently, they need to be integrated into the build procces.

#### Example:

We will create a simple test
For this test, we are going to use `pytest`.
Before we start, we have to install it.

```terminal
pip install pytest
```
Pytest expects our tests to be located in files whose names begin with `test_` or so that `pytest`.

 file name: `test_is_upper_case.py`

Also, the function has to start with `test_`.

```python
def make_srting_upper_case(string):
    return string.upper()

def test_is_upper_case():
    assert make_srting_upper_case('wow') == 'WOW'

```

To run the test, execute the `pytest` command:

```terminal
pytest

#  1 passed in 0.01s 
```

To learn more about `pytest` you can visit the official website: 
[Here](https://docs.pytest.org/)


## Unnitest Framework

Python's `unittest` module provides a standard framework for writing automated tests. It is built on top of `doctest`, which means that you can use `unittest` to test all kinds of things, including Python functions, classes, and modules.

The Python standard library and the documentation for Python itself are both extensively tested using `unittest`. The docs are available at [docs.python](https://docs.python.org/devguide/)


## Unit Testing

Unit testing is a form of testing that verifies the functionality of a small part of an application, such as a class or method. It involves writing a test case for each unit in order to determine if it has been implemented correctly, and then run that test case. If the test case is false, then it indicates one or more issues with the unit under test: either it doesn't meet its specifications, or perhaps there is some problem with how your code is interacting with other parts of your program.

#### Example

```python
import unittest


class SimpleTest(unittest.TestCase):
    def test_upper(self):
        result = 'wow'.upper()
        expected_result = 'WOW'
        self.assertEqual(result, expected_result)

if __name__ == '__main__':
    unittest.main()

# test_is_upper_case.py::SimpleTest::test_upper PASSED                  [100%]

# 1 passed in 0.00s
```
To run the rest:
```terminal
python -m unittest test_is_upper_case.py
```

#### The possible outcomes are:

- OK: all test passed
- Fail: one or many tests failed and an AssertionError exception is raised
- Error: the tests raised an exception other than AssertionError

#### Basic Unittest Terms:

- **unittest.TestCase** : create test cases by subclassing it
- **assertEqual() / assetNotEqual()** : tests the the two arguments are equal/unequal in value
- **assertTrue() / assertFalse()** : tests that the argument has a boolean value True/False
- **assertIn() / assertNotIn()** : tests that the first argument is in/ in not in the second
- **assertRaises()** : raises a specific exception
- **unittest.main()** : provides a command line interface to the test script
- **setUp()** : prepares the test fixture 
    The method is called immediately before the test method

#### Exampe for a class Person with methods get_full_name() and get_info():  


```python
class Person:
    def __init__(self, first, last, age):
        self.first_name = first
        self.last_name = last
        self.age = age

    def get_full_name(self):
        return f'{self.first_name} {self.last_name}'

    def get_full_info(self):
        return f'{self.first_name} {self.last_name} is {self.age} old!'

```

We can test both methods using the code below:

```python
import unittest


class PersonTest(unittest.TestCase):
    def setUp(self):
        self.person = Person('Anna', 'Maria', 25)

    def test_get_full_name(self):
        result = self.person.get_full_name()
        expected = 'Anna Maria'
        self.assertEqual(result, expected)

    def test_get_full_info(self):
        result = self.person.get_info()
        expected = 'Anna Maria is 25 old!'
        self.assertEqual(result, expected)

if __name__ == '__main__':
    unittest.main()

# test_is_upper_case.py::PersonTest::test_get_full_name PASSED             [ 50%]
# test_is_upper_case.py::PersonTest::test_get_info PASSED                  [100%]
# 2 passed in 0.00s
```

## Sapareting Unitest to module


Advantages to placing the test code in a separate module:

- Test module can be run standalone from the command line
- The test code can more easily be separated from snipped code
- Tested code can be refactored more easily 
- If the testing strategy changes there is no need to change the source code

Example Unittest Modules

Testing the class Person from the previous example:
Create the test in a separate module

* Project
   - __init__.py
   - person.py
* tests
   - __init__.py
   - test_person.py

```python
# in test_person.py

import unittest
from project.person import Person

class PersonTest(unittest.TestCase):
    def setUp(self):
        self.person = Person('Anna', 'Maria', 25)

    def test_get_full_name(self):
        result = self.person.get_full_name()
        expected = 'Anna Maria'
        self.assertEqual(result, expected)

    def test_get_full_info(self):
        result = self.person.get_info()
        expected = 'Anna Maria is 25 old!'
        self.assertEqual(result, expected)


if __name__ == '__main__':
    unittest.main()
```

## Mocking

Mocking objects are used to test the interactions between objects. We use them when we want to test a class but don’t want to create real instances of the class, or when we want to test a class that is expensive to create.

When you mock an object, you simulate its behavior and expectations with fake data. Let's say your application has a user sign-in feature and you want to write tests for it. You might mock out the database access layer so it doesn't actually query any data from your database--you'd just return dummy values instead. Then when your code calls this functionality, it'll work just like normal but won't hit the actual database; this allows you to write tests without worrying about whether there's data in there or not! If everything works as intended after mocking up all those dependencies then great! If not though…


## Naming Tests

Is important to name your test correctly for understanding what a specific test is doing.

Test names:
-Should use business domain terminology  
-Should be descriptive and readable

Incorrect:
test_increment_number(self): ...
test_test1(self): ...
test_transfer(self): ...

Correct:
test_deposit_x_euro_should_increase_balance_with_x_euro(self): ...
test_deposit_negative_euro_should_not_increase_balance(self): ...

## Seven Testing Principles

1: **Testing is context-dependent**:
- Testing is done differently in a different context

Example:
Safety-critical software is tested differently from an e-commerce site 

2: **Exhaustive testing is impossible**
- All combinations of inputs and preconditions are usually almost infinity number
- Testing everything is not feasible 
- Except for trivial cases
- Risk analysis and priorities should be used to focus testing efforts

3: **Early testing is always preferred**
- Testing activities shall be started as early as possible
- And shall be focused on defined objectives 
- The later a bug is found the more it costs!

4: **Defect clustering**
- Testing effort shall be focused proportionally 
- To the expected and later observed defect density of modules
- A small number of modules usually contains most of the defects discovered
- Responsible for most of the operational features 

5: **Pesticide paradox** 
- Same tests repeated over and over again tend to lose their effectiveness 
- Previously undetected defects remain undiscovered 
- New and modified test cases should be developed

6: **Testing shows the presence of defects**
- Testing can show that defects are present
- Cannot prove that there are no defects
- Appropriate testing reduces the probability of defects 

7: **Absence of errors fallacy**
- Finding and fixing defects itself does not help in these cases:
- The system built is unusable 
- Does not fulfill the user needs and expectations

## Conclusion

It’s important to remember that manual testing is not always the best option; it can be time-consuming and expensive. Automated testing is often better because it’s faster and cheaper. We recommend using unit tests because they’re easy to write, and they provide good coverage for your codebase.