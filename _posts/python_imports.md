# Imports

## What Is an Import?
**Imports** allow us to use code that lives somewhere else -- somewhere different than where we're currently working. 

### What Do You Mean by "Somewhere Else?"

### Modules
Python code lives in files that end in ".py"
In Python-speak, these Python files are called **"modules"**.
In a perfect world, we divide up our code into Python **modules** much in the same way as we divide up our writing into paragraphs. One paragraph expresses one idea, just as one **module** expresses one idea.

(Kitchen example! Fork.py, Knife.py, Spoon.py, KitchenDrawer.py )

### Packages
If Python code lives in modules, then where do modules live? 
Modules live in folders, or in Python-speak, **packages**.
Just as **modules** allow us to group together pieces of Python code, **packages** allow us to group together related **modules**. Continuing with our writing metaphor, **packages** are chapters that combine paragraphs together in order to express an even bigger idea.
And just like chapters can contain sub-chapters inside of them, packages can contain sub-packages! 

## Back to Imports
Now that we know where Python code lives, it's time to get back to our original question: how do we use Python code that lives somewhere else? How do we **import** that code from *where it lives* into *where we want to use it*?

## Imports 101: The Basics of Using Imports
What do you want to import?
	1. Absolute path from *where you currently are* to *what you want to import*
	2. Do you want to give it a nickname?

#### Importing a Module

#### Importing Something Inside of a Module

#### Absolute Imports

#### Relative Imports

## Imports 102: How Do Imports Work?

#### How Does Python Search for Objects to Import?

#### Running a Module Complicates Things

## Imports 201: How Do Imports *Really* Work?

#### Finders

#### Loaders

## Imports 202: How Do I Import *THAT*?

### Reasoning About Import Statements

### Importing from a Sibling

### Importing from a Child

### Importing from a Parent

### Importing Outside the Family Tree

## Imports 301: Hacking Python's Import System

### Creating Gitport, a GitHub-Based Importer

### Integrating Gitport with Python's Import API

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzE5NDU2MzksLTEyMTE1NzEyODcsMT
A0Njk2ODgxOSwxNTY0ODAyNjk0LC0xNTQwOTgwMDIxLC0xNDU3
MDI0Mzc1LC0xMDg3MTg2NzA4LDY4MDg2MDY2NywtMTY2MjY3ND
A3MSwxODExOTcyOTUwLDQ3MzYyMTE0M119
-->