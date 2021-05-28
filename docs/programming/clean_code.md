# Clean Coding Principles in C#

## Resources
- "Code Complete 2" by *Steve McConnell*
- "Clean Code: A Handbook of Agile Software Craftsmanship" by *Robert C. Martin*
- "The Pragmatic Programmer: From Journeyman to Master" by *Andrew Hunt & David Thomas*

## Three Clean Code Principles

1. Select the right tool for the job
2. High signal to noise ratio, clean code optimizes for signal and strives to remove any noise that the reader can easily read the logic and understand the intent.
3. Self-documenting, write code in such a clear and expressive style that no documentation is needed at all.

## Maximizing Signal to Noise

### Signal

Signal = code that follows the "TED rule".
- Terse: code shouldn't be excessively wordy
- Expressive: clear what the code is trying to do
- Does one thing: the code should have a clear responsability

### Noise

Noise = code that reduce readability and hinder maintenance
- High cyclomatic complexity
- Huge classes
- Excessive indentation
- Long methods
- Zombie code
- Repetition
- Unnecessary comments
- No whitespace
- Overly verbose
- Poorly named structures

### The "rule of 7" effects:

Number of parameters per method
Number of methods in a class
Number of variables currently in scope

## DRY principle: Don't Repeat Yourself

### Databases

Database are normalized in an effort to assure each piece of data is defined in a single place. This assures that the database operates efficiently, consistently and eases maintenance.

### Duplication Issues

Copy paste is often a design problem
- Decreases signal to noise ratio
- Increases the number of lines of code
- Creates a maintenance problem

## Self-documenting code

1. Clear intent: clearly express the intent so that readers understand exactly what the programmer is trying to accomplish
2. Layers of abstraction: should be used so that the problem domain can be considered and walked through at different levels of detail
3. Format for readability: formatting in a friendly and consistent manner will optimize the reading experience
4. Favor code over comments, favoring code over comments when possible will assure that the code is as expressive as it can be without relying on comments to explain away unnecessary ambiguity

Self-documenting code idealy eliminate the need for out-of-band documentation (such as JavaDoc, wikis, ...)

## Naming classes

1. Specific names encourage small, cohesive classes
2. A well-design class should have a single responsibility, and its name should help reflect that
3. Class names are noun not verbs
4. Avoid Generic suffixes (*manager, *processor, Common, Utility)
5. Quality of the class name ?
   Ask the following question: *is an instance of [this] logical ?*

## Naming Methods

With a good method name, the reader doesn't need to read the method to know what it does.

## Rubber ducking

Verbalizing aids creativity, explain what a class does out loud
`Explain it to the rubber duck`

## Booleans

### Naming Booleans

Well-named boolean should sound like a true/false question:
```
isOpen, done, isActive, loggedIn
```
Not like a command:
```
start, open, status
```

### Naming: Strive for Symmetry

Use symmetrical names like:
```
on/off, fast/slow
```
unlike:
```
quick/slow, on/disable
```

### Boolean Comparison

Compare boolean implicitly, don't do:
```csharp
if (loggedIn == true) { ... }
```
do:
```csharp
if (loggedIn) { ... }
```

### Boolean Assignments

Assign boolean implicitly, do:
```csharp
bool goingToChipotleForLunch = cashInWallet > 6.00;
```

### Write positive boolean conditions

Be positive (don't be anti-negative), don't do:
```csharp
if (!isNotLoggedIn)
```

### Ternary expressions

Don't use chaining or nesting ternaries

### Be Strongly Typed

Be strongly typed, not "stringly typed"

Don't use strings:
```csharp
if (employeeType == "manager") { ... }
```

Use enums:
```csharp
if (employee.type == EmployeeType.Manager) { ... }
```

### Magic numbers, magic strings

Magic numbers/strings are to be avoided because they require careful review of the context and they expect the reader to fill gaps.


### Handling Complex Conditionals

- Use intermediate variables
- Encapsulate via function

### Prefer Polymorphism over Enums

- Favor polymorphism over Switch statement.
- Each class knows how to handle its unique behaviors.

## Clean methods and functions

### Function vs Method

Both methods and functions are pieces of code, called by name. Methods are associated with an object.

### When to create of function?
- Duplication
- Indentation
- Unclear intent
- Help maintain single responsability

### Arrow Code

Arrow code refers to excessive indentation levels. Arrow code is a sign that the code has a high cyclomatic complexity (a measure of the number of paths through code).

### Fail fast

1. Add guard clauses to throw an exception as soon as an unexpected situation that can't be handled occurs.
2. Guard clauses ensures a method inputs are valid before continuing processing.
3. Add default to switch statements and throw exceptions to fail fast

### Return early

> "Use a return when it enhances readability... In certain routines, once you know the answer... not returning immediately means that you have to write more code."
> *Code Complete, Steve McConnell*

### Parameters

A high number of parameters makes a function harder to understand. It's a sign the function is doing too much.
Strive for 0-2 parameters, this will make the code easier to read, understand and test.

### Signs a Method Is too Long

- Whitespace and comments
- Scrolling required
- Easy to name with a single define task
- Multiple conditionals
- Many layers of abstraction


## Handling Exceptions

Exception types:

### 1. Unrecoverable
- Null reference
- File not found
- Access denied

### 2. Recoverable
- Retry connection
- Try a different file
- Wait and try again

### 3. Ignorable
- Logging

The correct behavior for a broken application is to crash immediately.
`Fail fast. Fail loud`


## Clean classes

### When to Create a Class?

- New concept : abstract or real world
- Low cohesion : methods should relate
- Promote reuse : small and targeted
- Reduce complexity : solve once, hide away the complexity
- Clarify parameters : Identify a group of data

### Proximity Principle

- Make code read top to bottom when possible
- Keep related actions together

## The boy scout rule

> "Leave the code you're editing a little better than you found it"
> *Clean Code, Robert C. Martin*
