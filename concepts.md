# Concepts
This is just a rough collection of all concepts that I have studied so far. The explanation is in my own words and will continuously change and evolve.

## Python Fundamentals
- venv - isolated storage shelf for package dependencies
- variables - memory addresses that point to places in memory that can be manipulated, python doesn't need you to declare datatype
- constants - memory addresses that point tot places in memory that cannot be manipulated (techincally they can, but naming of a var in all caps shows a constant which must not be touched)
- functions - blocks of lines that give a specific object as the return. Empty functions return None object
- return - keyword used to return objects of various datatypes at the end of the functions 
- type conversions - narrower values get converted to broader values when doing arithmetic, eg int gets promoted to float
- falsy values - empty string '', 0, None, all are falsy values (resolve to False) and can be used to in creating conditional statements. Or exploits it to execute more code flawlessly
- accumulator pattern - Start with empty result, build it incrementally based on conditions, return at end 
- Boolean Variables - Add boolean variables which test and hold result of conditions to make the code more readable
- Leap year logic - `return year % 4 == 0 and (year % 100 != 0 or year % 400 == 0)` This is an example of a single line mathematical condition, try to make as many of these as possible.
- `raise ValueError('msg')` - This raises an exception with a descriptive message for invalid input, preferred over None or -1. Check [grains](https://github.com/lunatic-man/python-exercism/blob/main/week2/grains/grains.py)
- Comprehensions - `[transform(item) for item in collection]` and `[item for item in collection if condition]` are two comprehensions that will return a list without actually needing to go through the entire for loop and writing multiple lines of code. It is also more readable.

## Control Flow
- boolean operators - operators used to compare and evalute values, output is True or False
- if/elif/else chains - be careful when making these chains, do not add redundant code, also check bounday precision
- boundary precision - check exactly how value at boundaries should be solved 

## Functions
- docstrings - official documentation that contains 3 parts, parameters (with datatypes), return value type and a brief of what the function does. Anything between """ """ is a docstring (multiple lines)
- function composition - this refers to using a function's output as another function's input, or calling a function inside another function
- DRY principle - Do not Repeat Yourself. This is very important as it removes redundant code and makes the program both small and easy to comprehend
- orphaned expressions - expressions that neither assign a value to a variable nor return it. These are dangerous as these are one of the hardest errors to catch in the debugging

## String Operations
- string immutability - strings in python are immutable and everytime you manipulate a string, you make a new string with a new memory address
- built-in string methods (title, endswith, strip, replace, join) - various built in methods that can be used to make string manipulation easier, so keep a track of these as time goes on
- membership testing (tuple vs string) - instead of testing using `card in "KQJ"`, use `card in ('K', 'Q', 'J')`. The former is an example of string, the latter is the example of member testing. 
- floor division and modulo - floor division returns the int value and modulo returns the remainder. added these because I unncessarily complicated a few solutions
- Strings are fundamentally different from other data types, because even after being declared as a variable, they behave as constants. When any function is called on a string, a new string is returned, without the original one changing.

## Git
- Git is basically a version control system for code. Best way I can put it, it keeps track of what changes you make to the code and why. 
- `git clone git@github.com:username/repo-name.git` - used to create a local copy of any repo hosted remotely
- `git status` - holy grail of everything, tells you where you are and what changes you have made, what are added to staging area and what you have committed
- `git branch` - shows you which branch you are currently working on. very useful when you want to manipulate branches
- `git add` - used to add any new changes to the staging area 
- `git commit -m "type: description"` - used to commit changes and to give a brief description to the commit
- `git push -u origin main` - sets an upstream as origin so that next time after a commit, you can simply use `git push` and all changes committed to main on local will automatically get pushed to the origin branch
- `git push origin --delete branch-name` - used to delete a branch at remote as remote is the shared source of collaboration
- `git log --oneline` - really helpful in analysing all the commits you have made in a short format

## Lists
- Even and Odd index - `list[0::2]` for getting the even index elements and `list[1::2]` for getting the odd index elements
- `sum()` and `len()` - built in aggregators that can be used
- `+` - list concatenation
- Value extraction and storing of values in variables when they need to be used multiple times 
- `sorted()` and `list.sort()` - `sorted()` returns a sorted copy of the list without modifying the original one. `list.sort()` modifies the original list and returns `None` as the object
