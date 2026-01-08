# PYTHON
This Repo helps to  gain a basic knowledge of python, which is required in devops.

## Module overview

1. Introduction to python.
2. Basic building blocks of programming.
   - work with strings, numbers, booleans
   - work with lists, sets, dictionaries.
   - variables and functions
   - accepting user input
   - input validations with conditionals(if/else)
   - error handling with try/ except
   - looping: for loop, while loop
3. Modules
   - write own modules
   - use built in python modules
4. Project- Countdown APP
   - work with datetime module
5. packages, PyPI & pip
6. Project: Automation with python
7. OOP - Classes and Objects
8. Project - API request to Gitlab
  
---

## What is Python?

Python is a programming language.  Compared to other programming languages, 
- Python has a very big advantages.
   - easy to learn
   - it has a very simple syntax
   - It's easy to setup
-Python is a Powerful Language.
  - It's called a Powerful Language based on it's eco system
  - many libraries
  - large Community
- Python is a flexible language
   - You're not Limited to Language Specifics.
## Why python used for?

Python is used for webdevelopment using libraries django and flask.
Python extremely became popular for DataScience, Machine Learning and Artificial Inrtelligence.
Python is also used for web scraping means collecting a data from Internet.
Python is also used for automation as it has many libraries to automate Devops Tasks.
- modules for CI/CD
- modules for aws cloud/ google cloud
- modules for monitoring
- Python scripts for automated backups/cleanups
- Automate general tasks with excel sheets

## Why you need python as a devops engineer?

- update jira tickets after jenkins build ran.
- trigger Jenkins Job on specific events.
- send notifications to team members on specific events.
- doing regular backups
- cleanup old docker images

Using Python, we can automate
- System Health Checks
- Managing cron
- CI/CD Related tasks
- Cleanup tasks
- Data Visualization
- Cusytom Ansible Modules
- Backup Tasks
- Monitoring Tasks
# Python Installation -l-183

## Python First Program

Create a main.py file 

```bash
print("200 is a great number")
o/p:
200 is a great number
```

## Pycharm is a IDE(Integrated Development Environment)
It contains
- Navigation
- Write code
- Execution context
We have a smart assistance with IDE like:
- on the fly error checking
- code completion
## Without IDE
```bash
create a test.py and enter a code in it then use
python3 test.py
```

## Strings & Numbers

#### Data Types
Different data types can do different things
- Text type data type are called  String (str) - we can use either "" quotes or '' quotes, there won't be any difference...!
- Number type data types:
   - Integer (int)
   - whole number, positive or negative, without decimals
   - Floating Point Number (Float) Number, positive or negative, containing 1 or more decimals.
   - eg. print (2), print(-20), print(29.99)

 ## Working with Numbers
 #### Arithmetic Operators
 - Arithmetic Operators are used with numeric values for mathematical operations.
 - Operators are used to perform operations
 - There are different types of operators

Calculate how many minutes in 20 days
```bash
print (20 * 24 * 60)
```

## String Concatenation
- Adding Strings together
  print ("20 days are 50 minutes")
  - Here, 50 isn't a string , but we have to call it as a string using the below methods.
  - Old Method - print ("20 days are" +str(50)+ "minutes")
  - New Method - print(f"20 days are {50} minutes")  -- it works only for newer versions.
Add Arithmetic Operation as a value inside a string
```bash
print(f"20 days are {20 * 24 * 60} minutes")
```

## Variables
- Variables are containers for storing values
- Use Descriptive Variable Names.
- Naming Convention of Variables
  - Naming convention  is  a convention (generally agreed scheme) for naming things.
  - Use lowercase with words seperated by underscores.


```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

print(f"20 days are {20 * calculation_to_units}{name_of_units}")
print(f"50 days are {50 * calculation_to_units}{name_of_units}")
print(f"60 days are {60 * calculation_to_units}{name_of_units}")
print(f"110 days are {110 * calculation_to_units}{name_of_units}")
```
## What are reserved keywords in python?
Reserved Words(also called keywords) are defined with predefined meaning and syntax in the language. These keywords have to be used to develop programming instructions. Reserved keywords can't be used as identifiers for other programming elements like name of variable, function etc.
- Following are the list of reserved keywords in python 3
  -and, as, assert, break, class, continue, def, del, elif, else, except, finally, false, for, from, global, if, import, in, is, lambda, nonlocal, None, not, or, pass, raise, return, True, try, with, while, yield.

## Functions
Functions are basically blocks of code.  
A function is defined using the def keyword.   
Block of code which only runs when it is called.
```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units():
    print(f"20 days are {20 * calculation_to_units}{name_of_units}")
    print("All Good!")

days_to_units()
```

## Function Parameters

# Parameters
- Information can be passed into functions as parameters
- Parameters are also called arguments

```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    print(f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}")
    print("All Good!")

days_to_units(20)
days_to_units(35)
days_to_units(110)

# Input multiple parameters in a single function

calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days, custommessage):
    print(f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}")
    print(custommessage)

days_to_units(20, "AWESOME!")
days_to_units(35, "Looks Good!")
days_to_units(110, "Great")

```

# Scope

A Variable is only available from inside the region it is created.
- Global Scope = variables available from within any scope
- Local scope = variables created inside the function , can only be used inside that function

```bash

calculation_to_units = 24 * 60 * 60      |
name_of_unit = "seconds"                 | --> Global Variables

def days_to_units(num_of_days, custommessage):                     # num_of_days, Custommessage are called local Variables
    print(f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}")       |
    print(custommessage)                                                                       | --> Function body

def scope_check()
my_var = "variable inside function"
print(my_var)
print(name_of_unit)                                 # my_var is a local Variable
```

## User Input
input()
- To ask user for an input
- Python stops executing when it comes to the input()
- It is a built in function by python language itself

Expression - is an instruction that combines values and operators and always evaluates down to a single value
e.g. 24 * 60 


```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    print(f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}")
    print("All Good!")

user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")   ##\n will moves the cursor to next line in cmd
print(user_input)
```

## Functions with Return Values

Return values 
- A Function can return data as a result
```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):                     # 1. Function is executed
    return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"
    print("All Good!")
#2. Return value is assigned to a variable
my_var = days_to_units(2)
print(my_var)                 ## Variable Value is print to standard output
```

## Back to user input example

# Casting - Means turning a one data type into another data type is called casting
int()
- It is a built-in python function
- Converts the specified value into an integer number
- the integer number is returned by the function

```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"
    

user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")   ##\n will moves the cursor to next line in cmd
user_integervalue = int(user_input)
calculated_value = days_to_units(user_integervalue)
print (calculated_value)
```

## Conditionals (if/else) & Boolean Data Type

Conditionals - Expressions that evaluate to either true or false.

##### **Python Comparision Operators**

Comparision operators are used to compare two values: 

| Operator | Name | Example|
|-----------|---------|---------|
| == | Equals | a == b |
| != | Not Equals | a != b |
| < | Less than | a < b |
| <= | Less than or equal to | a <= b |
| > | Greater than | a > b |
| >= | Greater than or equal to | a >= b |

##### **Python Arithmetic Operators**

Arithmetic Operators are used with numeric values to perform common mathematical Operations:

| Operator | Name | Example |
|------------|--------|-----|
| + | Addition | x+y |
| - | Subtraction | x-y |
| * | Multiplication | x*y |
| / | Division | x/y |
| % | Modulus | x%y |
| ** | Exponentation | x**y |
| // | Floor division | x//y |

```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    if num_of_days > 0:
       return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"
    else:
       return "You entered a negative value, so no conversion for you|"

user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")   ##\n will moves the cursor to next line in cmd
user_integervalue = int(user_input)
calculated_value = days_to_units(user_integervalue)
print (calculated_value)
```

 # Boolean Data Type
 - Boolean can only have 2 Values: True or False
 ```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    #print(num_of_days > 0)          # It prints either this condition is true or false
    condition_check = num_of_days > 0
    print(type(condition_check))              # Type is a key word which prints the class type
    if num_of_days > 0:
       return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"
    elif num_of_days == 0:
       return "you entered a 0, please enter a valid number"
    else:
       return "You entered a negative value, so no conversion for you|"

user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")   ##\n will moves the cursor to next line in cmd
calculated_value = days_to_units(int(user_input))                       ##  Return Value of inner function is the input value for the outer function.
print (calculated_value)

```

## More User Input Validation:
If user enters text instead of number, our program will be crashed to protect program from it.

 ```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    #print(num_of_days > 0)          # It prints either this condition is true or false
    condition_check = num_of_days > 0
    print(type(condition_check))              # Type is a key word which prints the class type
    if num_of_days > 0:
       return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"
    elif num_of_days == 0:
       return "you entered a 0, please enter a valid number"
    else:
       return "You entered a negative value, so no conversion for you|"

user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")
if user_input.isdigit():   
  calculated_value = days_to_units(int(user_input))                       
  print (calculated_value)
else:
    print ("your input is not a number. Don't ruin my program")
```

## Clean up our code

 ```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
    #print(num_of_days > 0)          # It prints either this condition is true or false
    condition_check = num_of_days > 0
    print(type(condition_check))              # Type is a key word which prints the class type
    if num_of_days > 0:
       return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"
    elif num_of_days == 0:
       return "you entered a 0, please enter a valid number"
    else:
       return "You entered a negative value, so no conversion for you|"

def validate_and_execute():
    if user_input.isdigit():   
       calculated_value = days_to_units(int(user_input))                       
       print (calculated_value)
    else:
        print ("your input is not a number. Don't ruin my program") 
user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")

```
## Nested - If else

```
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
     return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"


def validate_and_execute():
    if user_input.isdigit():
       user_inputnum = int(user_input)
       if user_inputnum > 0:   
          calculated_value = days_to_units(user_inputnum)                       
          print (calculated_value)
       elif user_inputnum == 0:
           print("you entered a 0, please enter a valid number")
    else:
        print ("your input is not a number. Don't ruin my program") 
user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")
validate_and_execute()

```

## Error Handling with try/except

Try/Except
- The try block: let's you "test" a block of code for errors
- The Except block: catches the error and lets you handle it
```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
     return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"


def validate_and_execute():
    try:
       user_inputnum = int(user_input)
       if user_inputnum > 0:   
          calculated_value = days_to_units(user_inputnum)                       
          print (calculated_value)
       elif user_inputnum == 0:
           print("you entered a 0, please enter a valid number")
       else:
           print("you entered a negative number, so no conversion happens for you!")
    except ValueError:
        print ("your input is not a number. Don't ruin my program") 
user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")
validate_and_execute()

```

## While loops

While loop is used to execute a set of statements as long as a condition is true

### Looping 
 - To execute logic multiple types
 - Python has 2 loop commands
### Conditions
 - evaluate to true or false
 - are used most commonly in "if statements" and "loops"
```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
     return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"


def validate_and_execute():
    try:
       user_inputnum = int(user_input)
       if user_inputnum > 0:   
          calculated_value = days_to_units(user_inputnum)                       
          print (calculated_value)
       elif user_inputnum == 0:
           print("you entered a 0, please enter a valid number")
       else:
           print("you entered a negative number, so no conversion happens for you!")
    except ValueError:
        print ("your input is not a number. Don't ruin my program")
while True:                                                                                   |
user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")      |  --> this continues looping until we manually stop it
validate_and_execute()

user_input = ""
while user_input != "exit":                           --> As long as the user inputs something different than "exit"
user_input = input("Hey user, enter a number of days and i will convert it to hours!\n")      |  --> this continues looping until we type exit
validate_and_execute()


```

# Lists & For Loop

Lists - To Store multiple items in a single variable.  
A list can contain different data types.  

For Loop - It is used for iterating over a sequence (like a list)  
So we can execute smth for each item in a list.

```bash
calculation_to_units = 24 * 60 * 60
name_of_unit = "seconds"

def days_to_units(num_of_days):
     return f"{num_of_days} days are {num_of_days * calculation_to_units}{name_of_units}"


def validate_and_execute():
    try:
       user_inputnum = int(num_of_days_element)
       if user_inputnum > 0:   
          calculated_value = days_to_units(user_inputnum)                       
          print (calculated_value)
       elif user_inputnum == 0:
           print("you entered a 0, please enter a valid number")
       else:
           print("you entered a negative number, so no conversion happens for you!")
    except ValueError:
        print ("your input is not a number. Don't ruin my program")

user_input = ""
while user_input != "exit":                           --> As long as the user inputs something different than "exit"
   user_input = input("Hey user, enter a number of days as a comma separated list and i will convert it to hours!\n")      |  --> this continues looping until we type exit
   print(type(user_input.split(",")))
   print (user_input.split(","))
   for num_of_days_element in user_input.split(","):
      validate_and_execute()
```
## Basic List Operations
- Create a list
- Access items of the list
- Add an item to the list
- Remove an item from the list
- Changes items in the list

```bash
lists.py

my_list = ["January", "Frebruary", "March"]
print(my_list[0])         --> access an items of the list
my_list.append("April")   -->Adds an item to the list
print(my_list)
my_list.remove("January")
print(my_list)
```
# Comments
U can comment the workflow expalanation using # in python file.
If you don't want a set of code in python file just keep # at the line beginning.

# Sets
```bash
user_input = ""
while user_input != "exit":                           --> As long as the user inputs something different than "exit"
   user_input = input("Hey user, enter a number of days as a comma separated list and i will convert it to hours!\n")      |  --> this continues looping until we type exit
   list_of_days = user_input.split(",")
   print(list_of_days)
   print(set(list_of_days))
   print(type(set(list_of_days)))
   
   for num_of_days_element in set(list_of_days):
      validate_and_execute()
```

## Basic Set Operations & Syntax
- Create a set
- Access items only via loop
- Add an item to the set
- Remove an item from the set
-  Unordered and Unchangeable
   - Items in a set do not have a defined order!
   - Items cannot be referred to by index!
   - Items cannot be changed, only added/removed!

```bash
sets.py

my_set = {"January", "February", "march"}
for element in my_set:
    print(element)
my_set.add("April")
print(my_set)
my_set.remove("January")
print(my_set)
```

## Built-in-Functions
#### Standalone Built-In-Functions

print() - Prints to the Standard output device
input() - Asks user  for input
set() - Returns a new set
int() - Converts Value into an integer number





