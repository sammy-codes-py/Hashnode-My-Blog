## File Handling with Python Part 7

## Introduction

As we all know, files play a critical role in our computing lives. We store documents on our personal computers, we save pictures of loved ones and cherished memories, and we keep important information accessible to us wherever we may be. Python offers a robust set of tools for file handling, allowing us to work with files in a variety of ways. In this blog post, we will explore some of the most important functions for file handling in Python.


## Python file object:

The `io` module provides a way to handle files and file-like objects in Python. This includes reading and writing to files, as well as working with streams. The io module implements many of the same interfaces as the standard library’s os module, making it easy to transfer files between different systems.

`io`  module is the default module for accessing a file
Don't need to import it

open() - returns a file object whose type depends on:
- The mode
- File operations such as reading and writing
- Files in a text mode(w, r, wt, rt, etc) return a TextIOWrapper


## Open() Function

The open() function in Python is one of the most fundamental functions in the language. It is used to open files and directories for reading and writing. 
The syntax is simple: 
`open(filename, mode)`, where filename is the name of the file or directory you want to open, and mode describes how you want to access the file. 
Some of the Files modes are:
`w, r, wt, rt, etc.`

If the file is not in the current directory the full path to the file can be provided.

```python
file_path = open('home/username/myfiles/text.txt', 'r')

```
If the file does not exist `FileNotFoundError` is thrown.
It can be caught in TRye finally block.

```python
try:
    file = open('invalid.txt', 'r')
except FileNotFoundError:
    print("File was not found!")
finally:
    print('Exit!')

# File was not found!
# Exit!
```

## File modes

The mode argument is optional and specifies the mode for manipulating the file.
The default value is `r` open for reading in the text mode.

`w`: open for writing, truncating the file first
`x`: create a new file and open it for writing
`a`: open for writing, appending to the end of the file if it exists
`t`: text mode(default)
`b`: binary mode
`+`: open a disk file for updating (reading and writing)


# Reading readline function

The `readline()` function is used to read one line of text from a file. It is a versatile function that can be used for a variety of purposes, such as reading input from a user, reading data from a file, or parsing text. 

```python
file = open('text.txt')
print(file.readline())
print(file.readline(1)) # print the second line of the text file

```

#### Looping over a file object

```python
file = open('text.txt', 'r')
for line in file:
    print(line, end=' ')
```

#### Creating and writing a file

The `write()` method writes a specified text to the file. Where the specified text will be inserted depends on the file mode and stream position.
Python file method `close()` closes the opened file. A closed file cannot be read or written any more. Is important to close the file after we finished specific work with the file.

```python
new_file = open('new.txt', 'w')
new_file.write("This is the write command")
new_file.close()
new_file = open('new.txt', 'r')
print(new_file.readline())

```

#### Append to a file

The `writelines()` method writes the items of a list to the file. Where the texts will be inserted depends on the file mode and stream position. `a` : 
The texts will be inserted at the current file stream position, default at the end of the file.

```python
new_file = open('new.txt', 'a')
line = ['\nwrite ', ' in ', ' file ']
new_file.writelines(line)
new_file.close()
new_file = open('new.txt', 'r')
print(new_file.readline())
```

## With Statement
File opened with the `with` statement will be closed automatically once it leaves the `with` block.

```python

with open('with_file.txt', 'w') as f: # naming the file as `f` to work with the file.
    f.write('This is with "with" statement')

```

#### Deleting a file
To delete a file you must import the os module

```
import os

os.remove('with_file.txt') # Can use full path

```
Keep in mind if the file does not exist an error will be raised

```
file_path = 'invalid.txt'
if os.path.exists(file_path):
    os.remove(file_path)
```

# Conclusion

Handling files in Python is easy. There are several modules and functions in Python that can be used to operate on files. As you see, this makes performing file operations quite simple and straightforward.