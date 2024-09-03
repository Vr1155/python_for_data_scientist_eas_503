## EAS 503: Python for data scientists

https://mkzia.github.io/eas503-book/chapters/intro.html

### Course Content:
- quiz (9) - 25%
- programming assignments - 45%
- individual mini projects - 20%
- individual final project - 15%

- find quizzes in ublearns on saturdays.

- prof does not respond to emails. He prefers you reach out to TAs and graders on piazza

- **codio license $48**. you need to do this to complete programming assignments.

- Make sure you get a 100% in your assignments.

### Mini-Projects
- From Taking raw data to giving a deployment of a machine learning model.

### Project Requirements:

- data selection.
- data parsing: Instructor does not like students using specialized libraries for data parsing, use basic python (with pandas).
- Data normalization: it has to be approved by TA.
- Experiment Tracking: MLFlow and DAgsHub
- Deployment: deploy a docker container for inference/classification pipeline.

- Instructor made that wiki website using jupyter book.

- Instructor wants students to record their 12 minute presentation and submit on UB learn by 18th Dec.

### Late submission policy

- no assignment can be submitted more than 3 days after its original due date.

### Preparing for first class

- Install Anaconda, vscode, and python3.12

### Academic integrity:

- In this course, students rarely get less than A.
- It is possible for students to talk and discuss pseudocode but no sharing of code can take place.
- This class is not graded on a curve.
- Topic of final project will be decided by individual student. 
- Although it must be a classification model so students can present a classification report 
- with all the important classification meterics.
- mini-project topics are pre-decided by the instructor.

- Winter recess begins in 19th Dec 2024.

- This class will have a 10 minute break after 1 hour of lecture.


### Thats the end of course intro.


### Demo on codio:

- four sections: file explorer, text editor, terminal, question page.
- write code on editor and click check it! for running unit tests.
- you can read the unit tests on tests folder in file explorer.
- Takes some time to update scores from codio to ublearns.

### Getting started:
- Programming languages:
    - Natural langauges are fraught with ambiguity and imprecision
    - eg: "I saw a man on a hill with a telescope"
    - This sentence can have 5 different meanings.
- Computer Scientists have resolved this issue by devising notations for expressing computations precisely and without ambiguity.
- These special notations are called "programming langauges"
- Instructor wants students to write their code in a **PYTHONIC** way.


- Working with negative numbers:
    - python's integer division rounds towards negative infinity.
        - for eg: -16/5 = -3.2, but -16//5 = -4
        - similarly: -17/10 = -1.7, but -17//10 = -2, and -17%10 = 3
        - use the formula below to make sense of this!
    - n = q * base + r,
        - n = dividend
        - base = divisor
        - q = quotient from floor division
        - r = remainder from modulo

- anything that is valid syntax in python, does not mean its good programming.
    - for eg: 10. is actually 10.0

- float occupies a fixed amount of space while int takes up a variable amount of space.
- int values are stored as bignum data type behind the scenes.
- float values are approximations due to finite memory of computers
- if you dont need fractions, use int.

- you can also use libraries like **mpmath** for dealing with very large and very small numbers

- you can have extra underscores as separators for large numbers:
    - for eg: 10_000_000_000_000_000

=================================================================


# Lecture 2 - 29th aug 2024

- PEMDAS = "Please Excuse My Dear Aunt Sally"
- Parantheses
- Exponents
- Multiplication Division (left to right)
- Addition and Subtraction (left to right)

- operator precedence
    - in python:
        - Parentheses
        - Exponents
        - Unary plus, Unary minus
        - Multiplication, Division, Integer division, Modulus (Remainder)
        - Addition, Subtraction
        - eg:
            - 8/2 * (2+2) = 16.0
            - 8/(2*(2+2)) = 1.0
        - Always use extra set of parentheses to be accurate.

- Python keywords

   - Python keywords are reserved, meaning they cannot be used as variable names.
        - False      await      else       import     pass
        - None       break      except     in         raise
        - True       class      finally    is         return
        - and        continue   for        lambda     try
        - as         def        from       nonlocal   while
        - assert     del        global     not        with
        - async      elif       if         or         yield

    - only nonlocal and async are not covered in the course and docs.
    - you will not see int, float, and type in keywords, because they're functions.
    - it is not recommended to use int, float and type as variables as it overrides the functions.
    - eg:
        - type = "Seasonal"
        - print(type)   # Seasonal
        - type(3.14)    # TypeError: 'str' obj is not callable
        - del type
        - type(3.14)    # float
    - similarly you can use print as variable, but you will end up overriding the function, so you have to del the variable before using the function without any TypeErrors.

- conventions for variable names:
    - snake_case is pythonic! 
    - conventions are best practices that helps with code quality, maintainance, and onboarding in large orgs.


- Memory management in Python:
    - Everything in python is an object.
    - sticky note model of python. (look more into it!)
    - You can use Python Tutor to view how the sticky-notes change.

- errors in python
    - NameError
    - SyntaxError
    - ZeroDivisionError

- Formatting code
    - If a single statement becomes too large, you can make it span multiple lines by either surrounding the statement with parentheses or using the line-continuation character, which is a \.
    - eg:
        - 2 + \
        - 3

- exercises on finding SyntaxErrors.

- What is the purpose of "=" ?
    - left hand side should be a variable
    - right hand side should be a data type or rvalue.

## prof says he might put visual separator "_" in numbers as a quiz.

- Functions:
    - What are the advantages of using functions?
    - if nothing is returned from a function, python returns a None data type (also known as NoneType data type).
    - you can have any number of spaces as indentation, as long as you are consistent with it.

- built in functions in python:
    - abs
    - int
    - float
    - str
    - round
        - Warning! this function is somewhat unpredictable: 
        - Why do both 3.5 and 4.5 go to 4? Python uses IEEE 754 standard for rounding called the banker’s rounding. 
        - In this method when a number is between two numbers, **the number is rounded to the nearest value with an even least significant digit.**
        - Still, the behavior of round() can be surprising and unexpected.
        - Why some numbers are not rounded as expected?
        - Floats are only an approximation of the real number.
        - for eg: round(4.55) gives 4.5
            - this is because,
            - print(decimal.Decimal(4.55)) = 4.5499999
            - therefore, 4.55 still rounds to 4.5, despite the banker's rounding.
    - using ceil and floor from math module
    - decimal.Decimal to see the real value of float data type (Which is actually an approximation).
    - help
    - pow
    - min
    - max
    - id => to find memory address of a variable

- user defined functions

- quick quiz:
    - def ret_x(x):
    -   return x
    - y = 3
    - y += ret_x(2)

    - whats the value of y?
    - ans: 3
    - explaination: last line will throw an error, but value of y is still 3

    - def ret_x(x):
    -   return x
    - del print
    - type = 3
    - type += ret_x(2)
    - print(type)

    - ans: 5

=================================================================

# Lecture 3 - 3rd Sep 2024

- this class has 2 TAs.
- lecture notes for previous week are in week1 folder of the github repo.
- professor says he wont give a hard banker's rounding problem. for eg: 3.5 -> 4 <- 4.5

```python
def print_birthday():
    msg = """Happy birthday to you!!!
Happy birthday to you!!!


Happy birthday, dear John


Happy birthday to you!!!
Happy birthday to you!!!"""
    print(msg)

ret_val = print_birthday()
print(ret_val)  # this will print None
```

- notice how triple quotes will maintain the formatting and spaces.

- Namespace and Scope:
    - **Namespace**: 
        - an association between identifiers and the things they represent in a program. 
        - In Python, modules, classes, and objects act as namespaces.
    - **Scope**: 
        - The area of a program where a given variable maybe reference. 
        - For examples, variables defined in functions are said to have local scope.


```python
y = 1
def quadratic(a, b, c, X):
    """ax^2 + bx + c"""
    first = a * pow(x, 2) ## Changed
    second = b * x
    third = c
    return first + second + third
a =1
b = 2
c = 3
x = 10  # here x is a global variable and is still picked up by quadratic() function.
# This can be a source of errors
X = 2
quadratic(a, b, c, X)
```

```python
'NH ' + 3 # this will not work. You cannot add a string type and an int type.

'four score and ' + str(7) + 'years ago'
# this will work

x = 'He said, "they can\'t do this"'
 
print(x)    # recognizes escape chars

x           # does not recognize escape chars

# this is a quirk of jupyter notebook
```

- in TSV files, each data point is separated by a tab
    - for eg: x = 'col1\tcol2\tcol3'
- in CSV files, each data point is separated by comma.

- inorder to print /\/\:
    - print('/\\/\\')

- **Warning**: Input arguments to a function are not the same as the input function!

```python

number = input("Please enter a number: ")
type(number) # str

number = input("Please enter a number: ")
number = int(number) # 3
print(number * 4) # 12
```

## Instructor says he loves giving hard assignments on string formatting.
























