Resources:

Code Complete 2
Clean Code
The Pragmatic Programmer
Why Writing Clean Code Matters: Resources
0:27

delete

edit
Select the right tool for the job

High signal to noise ratio, clean code optimizes for signal and strives to remove any noise that the reader can easily read the logic and understand the intent.

Self-documenting, write code in such a clear and expressive style that no documentation is needed at all.

Clean Coding Principles: Three Clean Code Principles
0:22

delete

edit
Signal = code that follows the "TED rule".

Terse: code shouldn't be excessively wordy
Expressive: clear what the code is trying to do
Does one thing: the code should have a clear responsability
Clean Coding Principles: Maximizing Signal to Noise
0:34

delete

edit
Noise = code that reduce readability and hinder maintenance

High cyclomatic complexity
Huge classes
Excessive indentation
Long methods
Zombie code
Repetition
Unnecessary comments
No whitespace
Overly verbose
Poorly named structures
Clean Coding Principles: Maximizing Signal to Noise
1:10

delete

edit
The "rule of 7" effects:

Number of parameters per method
Number of methods in a class
Number of variables currently in scope
Clean Coding Principles: Maximizing Signal to Noise
1:50

delete

edit
DRY principle

-> Don't Repeat Yourself

Database are normalized in an effort to assure each piece of data is defined in a single place. This assures that the database operates efficiently, consistently and eases maintenance.

Clean Coding Principles: Don't Repeat Yourself
0:21

delete

edit
Duplication Issues

Copy paste is often a design problem

Decreases signal to noise ratio
Increases the number of lines of code
Creates a maintenance problem
Clean Coding Principles: Don't Repeat Yourself
1:00

delete

edit
Self-documenting code

Clear intent: clearly express the intent so that readers understand exactly what the programmer is trying to accomplish
Layers of abstraction: should be used so that the problem domain can be considered and walked through at different levels of detail
Format for readability: formatting in a friendly and consistent manner will optimize the reading experience
Favor code over comments, favoring code over comments when possible will assure that the code is as expressive as it can be without relying on comments to explain away unnecessary ambiguity
Clean Coding Principles: Self-documenting Code
0:47

delete

edit
Self-documenting code idealy eliminate the need for out-of-band documentation (such as JavaDoc, wikis, ...)

Clean Coding Principles: Self-documenting Code
1:32

delete

edit
Naming classes

Specific names encourage small, cohesive classes
A well-design class should have a single responsibility, and its name should help reflect that
class names are noun not verbs
avoid Generic suffixes (*manager, *processor, Common, Utility)
quality of the name: ask the following question :

is an instance of this logical ?
Naming: Naming Classes
1:18

delete

edit
Naming Methods

with a good method name, the reader doesn't need to read the method to know what it does
Naming: Naming Methods
1:17

delete

edit
Rubber ducking

Verbalizing aids creativity, explain what a class does out loud
Explain it to the rubber duck
Naming: Rubber Ducking
0:50

delete

edit
well-named boolean should sound like a true/false question

not a command like start, open, status
isOpen, done, isActive, loggedIn
Naming: Naming Booleans
0:14

delete

edit
Use symmetrical names like on/off, fast/slow unlike quick/slow, on/disable

Naming: Strive for Symmetry
0:35

delete

edit
Compare boolean implicitly, don't do

if (loggedIn == true)
Writing Conditionals That Convey Intent: Boolean Comparisons
0:28

delete

edit
Assign boolean implicitly, do:

bool goingToChipotleForLunch = cashInWallet > 6.00
Writing Conditionals That Convey Intent: Boolean Assignments
1:02

delete

edit
Be positive (don't be anti-negative), don't do:

if (!isNotLoggedIn)
Writing Conditionals That Convey Intent: Prefer Positive Conditionals
0:08

delete

edit
Don't use chaining or nesting ternaries

Writing Conditionals That Convey Intent: Ternaries Are Beautiful
2:08

delete

edit
Be strongly typed, not "stringly typed", don't

if (employeeType == "manager")
use enums and do
if (employee.type == EmployeeType.Manager)
Writing Conditionals That Convey Intent: Be Strongly Typed
0:14

delete

edit
Magic numbers are to be avoided because they require careful review of the context and they expect the reader to fill gaps

Writing Conditionals That Convey Intent: Avoid Magic Numbers
0:59

delete

edit
Complex conditionals,

Use intermediate variables
Encapsulate via function
Writing Conditionals That Convey Intent: Handling Complex Conditionals
0:33

delete

edit
Favor polymorphism over Switch statement.
Each class knows how to handle its unique behaviors.

Writing Conditionals That Convey Intent: Prefer Polymorphism over Enums
1:31

delete

edit
Function vs Method

Both methods and functions are pieces of code, called by name.
Methods are associated with an object
Writing Clean Methods: When to Create a Function
0:18

delete

edit
When to create of function

duplication
indentation
unclear intent
help maintain single responsability
Writing Clean Methods: When to Create a Function
1:04

delete

edit
Arrow code refers to excessive indentation levels.

Arrow code is a sign that the code has a high cyclomatic complexity (a measure of the number of paths through code)
Writing Clean Methods: Why Create a Method - Reason 2: Excessive Indentation
0:14

delete

edit
Fail fast

Add guard clauses to throw an exception as soon as an unexpected situation that can't be handled occurs
Guard clauses ensures a method inputs are valid before continuing processing.
add default to switch statements and throw exceptions to fail fast
Writing Clean Methods: Excessive Indentation - Solution 2: Fail Fast
1:00

delete

edit
"Use a return when it enhances readability... In certain routines, once you know the answer... not returning immediately means that you have to write more code."
Steve McConnell, Code Complete

Writing Clean Methods: Excessive Indentation - Solution 3: Return Early
1:39

delete

edit
A high number of parameters makes a function harder to understand. It's a sign the function is doing too much.
Strive for 0-2 parameters, this will make the code easier to read, understand and test.

Writing Clean Methods: How Many Parameters?
0:07

delete

edit
Sign a function is too long:

Whitespace and comments
Scrolling required
Easy to name with a single define task
Multiple conditionals
Many layers of abstraction
Writing Clean Methods: Signs a Method Is too Long
0:32

delete

edit
Exception types

Unrecoverable
Null reference
File not found
Access denied
Recoverable
Retry connection
Try a different file
Wait and try again
Ignorable
Logging
The correct behavior for a broken application is to crash immediately.

Fail fast. Fail loud
Writing Clean Methods: Handling Exceptions
0:26

delete

edit
When to create a class

New concept : abstract or real world
Low cohesion : methods should relate
Promote reuse : small and targeted
Reduce complexity : solve once, hide away the complexity
Clarify parameters : Identify a group of data
Writing Clean Classes: When to Create a Class
1:12

delete

edit
Proximity Principle

Make code read top to bottom when possible
Keep related actions together
Writing Clean Classes: The Proximity Principle
0:53

delete

edit
The boy scout rule:
Leave the code you're editing a little better than you found it
Robert C. Martin