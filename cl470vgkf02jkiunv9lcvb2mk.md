## Organizing Files with Python

## Introduction
Python is a powerful programming language that can be used for a wide range of tasks. One of those tasks is organizing files. With just a few lines of code, you can create a script that will sort your files into folders based on their extension.

This can be a huge time-saver, and it can help you keep your computer organized with very little effort. This article will see how to do it.

## Writing dictionary

First will create a default dictionary extension.
The `key` will be the extension and the `value` will be for the folder name

```python
extensions = {
    "jpg": "images",
    "png": "images",
    "ico": "images",
    "gif": "images",
    "svg": "images",
    "sql": "sql",
    "exe": "programs",
    "msi": "programs",
    "pdf": "pdf",
    "xlsx": "excel",
    "csv": "excel",
    "rar": "archive",
    "zip": "archive",
    "gz": "archive",
    "tar": "archive",
    "docx": "word",
    "torrent": "torrent",
    "txt": "text",
    "ipynb": "python",
    "pptx": "powerpoint",
    "ppt": "powerpoint",
    "mp3": "audio",
    "wav": "audio",
    "mp4": "video",
    "m3u8": "video",
    "webm": "video",
    "ts": "video",
    "json": "json",
    "css": "web",
    "js": "web",
    "html": "web",
    "apk": "apk",
    "sqlite3": "sqlite3",

}


```

## Creating two functions

After that will use `pickle` to create, update or access a dictionary extension file.
Pickle stands for "portable, self-describing data", and is a Python file format that can store an object's structure. This means that when you need to find your stored data in the future, it doesn't need to be decoded - only converted back into objects and data.

We will create two functions: one that gets the data from the file and another that updates the information in the file.

```python
# Geting the data form the file or `returning None`
def get_dict_extensions_file_data():
    loaded_dict = None
    try:
        with open('saved_extensions.pkl', 'rb') as f:
            loaded_dict = pickle.load(f)
        return loaded_dict
    except FileNotFoundError:
        return loaded_dict


# updating data or creating a file if not exists
def update_dict_extensions_file_data(dict_extensions):
    try:
        with open('saved_extensions.pkl', 'wb') as f:
            pickle.dump(dict_extensions, f)
    except FileNotFoundError:
        raise FileNotFoundError

```

## Printing file data (extension => folder name) 

Then let's create a file, then will print data from the file to see what extension will be moved to what folder name.

```python
# first we call the `update_dict_extensions` to create a file with default data from dictionary `extensions`.
# checking if file exists, if not, passing dictionary extensions to create one
if get_dict_extensions_file_data() is not None:
    update_dict_extensions_file_data(get_dict_extensions_file_data())
else:
    update_dict_extensions_file_data(extensions)

# printing data from the file
print("All extensions with folder names\n")
for key, value in get_dict_extensions_file_data().items():
    print("Extension: " + key + " => Folder: " + value)


# Extension: jpg => Folder: images
# Extension: png => Folder: images
# Extension: ico => Folder: images
# Extension: gif => Folder: images
# Extension: svg => Folder: images
# Extension: sql => Folder: sql
# Extension: exe => Folder: programs
# Extension: msi => Folder: programs
# Extension: pdf => Folder: pdf
# ....
```

## Adding a custom extension to the file
Now let's make a user be enabled to add new extensions to the file.

```python
print(
    "If you don't see an extension that you want to organize add a custom one, or you can change the folder name of the extension that exists")

custom = input("Do you like to add custom extension or change folder name? y/n\n")


extensions = get_dict_extensions_file_data()

while True:
    if custom.lower() == 'y':
        extensions.update({input("Enter an extension without a dot\n"): input("Enter a name for the folder\n")})
        update_dict_extensions_file_data(extensions)
    if custom.lower() == 'n':
        break

    custom = input("Do you want to add more? y/n")


```
## Path to be organization.

Now create input for a path that will be organized.

```python

path = input("Ender full path, that you want to be organized\n")  # r"/home/sammy-code/Downloads"

```

## Organization function

Now we can create a function that organizes files in a specific path.
We will import `os`, `glob` and `shutil`. 

```python
def file_organization(path, file_extensions):
# checking if folder exists if not try again(using recrusion)
    if not os.path.exists(path):
        print("Folder not found")
        path = input("Ender full path, that you want to be organized\n")
        file_organization(path, file_extensions)
    else:
        for extension, folder_name in file_extensions.items():
            files = glob.glob(os.path.join(path, f"*.{extension}"))
            print(f"[*] {len(files)} files was found with {extension} extension")
            if not os.path.isdir(os.path.join(path, folder_name)) and files:
                # create the folder if it does not exist.
                print(f"[+] Folder with {folder_name} name was created")
                os.mkdir(os.path.join(path, folder_name))
            for file in files:
                # for each file in that extension, move it to the corresponding folder
                basename = os.path.basename(file)
                dst = os.path.join(path, folder_name, basename)

                print(f"[*] Moving {file} to {dst}")
                shutil.move(file, dst)

file_organization(path, get_dict_extensions_file_data())
```

# Running the program

And now let's try to run a file:

```
$ python file_organization.py


# Extension: jpg => Folder: images
# Extension: png => Folder: images
# Extension: ico => Folder: images
# Extension: gif => Folder: images
# Extension: svg => Folder: images
# Extension: sql => Folder: SQL
# ......

# If you don't see an extension that you want to organize add a custom one, or you can change the folder name of the extension that exists.
# Do you like to add a custom extension or change the folder name? y/n
# y
# Enter a folder name:
# python folder
# Enter an extension without a dot:
# py
# Do you want to add more? y/n
# n
# Ender full path, that you want to be organized
# /home/user/Downloads
# ........
# [*] 0 files was found with apk extension
# [*] 0 files was found with sqlite3 extension
# [*] 1 files was found with py extension
# [+] Folder with python name was created
# [*] Moving /home/sammy-code/Downloads/some_pyton.py to /home/sammy-code/Downloads/python/some_pyton.py


```

Full code: [GitHub](https://github.com/samer25/Organizing-Files-with-Python)