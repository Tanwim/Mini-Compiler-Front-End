# Mini Compiler Front-End

An educational **Mini Compiler Front-End** developed for the Compiler Construction course. The project demonstrates the major front-end phases of a compiler using **Flex, Bison, and C**.

The compiler accepts a limited, C-like subset of **C, C++, and Java-style syntax** and processes source programs through lexical analysis, syntax analysis, symbol-table handling, semantic analysis, and intermediate-code generation.

> **Note:** This is an academic compiler project, not a complete C, C++, or Java compiler. Only the language constructs implemented in the current grammar and source code are supported.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Compiler Architecture](#compiler-architecture)
- [Compiler Phases](#compiler-phases)
- [Supported Features](#supported-features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Installation and Setup](#installation-and-setup)
- [Building the Project](#building-the-project)
- [Running the Compiler](#running-the-compiler)
- [Testing](#testing)
- [Valid Test Cases](#valid-test-cases)
- [Invalid Test Cases](#invalid-test-cases)
- [Example Program](#example-program)
- [Three Address Code](#three-address-code)
- [Error Handling](#error-handling)
- [Limitations](#limitations)
- [Future Scope](#future-scope)
- [Authors](#authors)
- [License](#license)

---

## Project Overview

### Project Name

**Mini Compiler Front-End**

### Project Type

Academic Compiler Construction Project

### Implementation Language

**C**

### Main Tools

- Flex
- Bison
- GCC
- Make
- Git/GitHub

### Development Environment

**Visual Studio Code**

The project demonstrates how a compiler front-end transforms source code from a sequence of characters into tokens, checks its syntax according to grammar rules, performs semantic checks, maintains a symbol table, and produces an intermediate representation such as **Three Address Code (TAC)**.

The main components of the project are:

- Lexical Analysis
- Syntax Analysis
- Symbol Table
- Semantic Analysis
- Intermediate Code Generation
- Three Address Code
- Basic Code Optimization
- Error Detection and Reporting

---

## Objectives

The main objectives of this project are:

1. Develop a simplified compiler front-end using Flex and Bison.
2. Perform lexical analysis on source programs.
3. Generate and classify tokens.
4. Validate source code using grammar rules.
5. Maintain a symbol table for identifiers.
6. Detect basic semantic errors.
7. Generate Three Address Code.
8. Implement basic intermediate-code optimization.
9. Support a limited subset of C, C++, and Java-style programming constructs.
10. Provide meaningful syntax and semantic error messages.
11. Gain practical knowledge of compiler construction.

---

## Compiler Architecture

The overall processing pipeline is:

```text
                    Source Program
                          |
                          v
                +-------------------+
                | Lexical Analysis  |
                |      Flex         |
                +-------------------+
                          |
                        Tokens
                          |
                          v
                +-------------------+
                | Syntax Analysis   |
                |      Bison        |
                +-------------------+
                          |
                    Parsed Program
                          |
                          v
                +-------------------+
                |   Symbol Table    |
                +-------------------+
                          |
                          v
                +-------------------+
                | Semantic Analysis |
                +-------------------+
                          |
                          v
                +-------------------+
                | TAC Generation    |
                +-------------------+
                          |
                          v
                +-------------------+
                | Code Optimization |
                +-------------------+
                          |
                          v
                Intermediate Code
```

---

## Compiler Phases

### 1. Lexical Analysis

Flex reads the source program and converts characters into tokens.

For example:

```c
int age = 20;
```

can produce tokens such as:

```text
INT
ID
ASSIGN
INT_NUM
SEMICOLON
```

### 2. Syntax Analysis

Bison checks whether the token sequence follows the grammar of the compiler.

For example:

```c
int age;
age = 20;
```

is checked against the grammar rules.

A program such as:

```c
int age
age = 20;
```

contains a missing semicolon and should produce a syntax error.

### 3. Symbol Table

The symbol table stores information about declared identifiers.

Example:

| Name | Type |
|------|------|
| age | int |
| salary | float |
| grade | char |

The symbol table can be used to detect issues such as undeclared variables and duplicate declarations.

### 4. Semantic Analysis

Semantic analysis checks whether the program is logically valid.

Examples of semantic errors include:

- Undeclared variable
- Duplicate declaration
- Type mismatch
- Invalid assignment
- Invalid identifier usage
- Division by zero, where supported by the semantic-analysis implementation

### 5. Intermediate Code Generation

After successful analysis, the compiler can generate an intermediate representation.

This project uses **Three Address Code (TAC)**.

For example:

```c
a = b + c * d;
```

can become:

```text
t1 = c * d
t2 = b + t1
a = t2
```

### 6. Code Optimization

Basic optimization can reduce unnecessary operations.

Example:

```text
t1 = 5 * 2
```

can be optimized to:

```text
t1 = 10
```

Other basic techniques include algebraic simplification and removal of unnecessary operations.

---

## Supported Features

The supported features depend on the current Flex and Bison implementation.

### Data Types

- `int`
- `float`
- `char`
- `bool`
- Java-style `boolean` where implemented

### Statements

- Variable declaration
- Variable assignment
- Arithmetic expressions
- Relational expressions
- Logical expressions
- `if`
- `if-else`
- `while`
- `for`
- `return`
- Nested blocks
- Output statements where implemented

### Operators

#### Arithmetic

```text
+
-
*
/
%
```

#### Assignment

```text
=
```

#### Relational

```text
==
!=
<
>
<=
>=
```

#### Logical

```text
&&
||
!
```

#### Increment / Decrement

```text
++
--
```

The exact operators supported are determined by the current lexer and parser implementation.

---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| C | Compiler implementation |
| Flex | Lexical analysis |
| Bison | Syntax analysis |
| GCC | Compilation |
| Make | Build automation |
| Git | Version control |
| GitHub | Source-code management |
| Visual Studio Code | Development environment |

---

## Project Structure

The project is organized into source-code, testing, and documentation components.

A typical structure is:

```text
Mini-Compiler-Front-End/
│
├── src/
│   ├── lexer/
│   │   └── lexer.l
│   │
│   ├── parser/
│   │   └── parser.y
│   │
│   ├── symbol_table/
│   │   └── symbol_table.c
│   │
│   ├── semantic/
│   │   └── semantic.c
│   │
│   ├── tac/
│   │   └── tac.c
│   │
│   └── main.c
│
├── tests/
│   ├── valid/
│   │   ├── assignment.mc
│   │   ├── declaration.mc
│   │   ├── expression.mc
│   │   ├── for.mc
│   │   ├── if_else.mc
│   │   └── while.mc
│   │
│   └── invalid/
│       ├── divide_by_zero.mc
│       ├── missing_semicolon.mc
│       ├── redeclaration.mc
│       ├── syntax_error.mc
│       ├── type_mismatch.mc
│       └── undeclared_variable.mc
│
├── output/
│
├── Makefile
├── README.md
├── PROJECT_REPORT.md
└── .gitignore
```

> The exact files and folders may differ depending on the current implementation.

---

## Requirements

### Hardware

A standard modern computer is sufficient.

Recommended:

- Dual-core processor or better
- 4 GB RAM or more
- At least 1 GB of available storage

### Software

- Windows or Linux
- Visual Studio Code
- GCC
- Flex / WinFlex
- Bison
- GNU Make
- Git

---

## Installation and Setup

### 1. Install GCC

Make sure GCC is installed and available in the system `PATH`.

Check:

```bash
gcc --version
```

### 2. Install Flex

On Windows, the project may use `win_flex`.

Check:

```bash
win_flex --version
```

On Linux, use:

```bash
flex --version
```

### 3. Install Bison

Check:

```bash
bison --version
```

### 4. Install Make

Check:

```bash
make --version
```

### 5. Clone the Repository

```bash
git clone <repository-url>
```

Then enter the project directory:

```bash
cd Mini-Compiler-Front-End
```

---

## Building the Project

The project includes a `Makefile` to simplify the build process.

Build the compiler with:

```bash
make
```

The build process performs the following operations:

1. Runs Bison on `parser.y`.
2. Generates the parser source and header files.
3. Runs Flex on `lexer.l`.
4. Generates `lex.yy.c`.
5. Compiles the C source files.
6. Links the object files.
7. Produces the compiler executable.

### Clean the Build

```bash
make clean
```

### Rebuild

```bash
make rebuild
```

### Show Makefile Commands

```bash
make help
```

---

## Running the Compiler

After building the project, a source file can be passed to the compiler.

Example:

```bash
make run FILE=tests/valid/declaration.mc
```

A valid program should complete parsing successfully if all required phases accept the input.

For an invalid test:

```bash
make test-invalid FILE=tests/invalid/syntax_error.mc
```

For a valid test:

```bash
make test-valid FILE=tests/valid/declaration.mc
```

> The exact command may depend on how `main.c` handles the input filename in the current implementation.

---

# Testing

Testing is divided into **valid** and **invalid** source programs.

The tests cover:

- Variable declaration
- Variable assignment
- Arithmetic expressions
- Relational expressions
- `if`
- `if-else`
- `while`
- `for`
- Syntax errors
- Semantic errors
- Symbol-table checks
- TAC generation

---

## Valid Test Cases

The `tests/valid/` directory contains programs that should be accepted by the compiler.

### `declaration.mc`

```c
int age;
float salary;
char grade;
bool passed;
```

Expected:

```text
Valid
```

### `assignment.mc`

```c
int age;

age = 23;
```

Expected:

```text
Valid
```

### `expression.mc`

```c
int a;
int b;
int result;

a = 10;
b = 20;
result = a + b * 2;
```

Expected:

```text
Valid
```

### `if_else.mc`

```c
int age;

age = 20;

if (age > 18) {
    age = age + 1;
} else {
    age = age - 1;
}
```

Expected:

```text
Valid
```

### `while.mc`

```c
int i;

i = 0;

while (i < 5) {
    i = i + 1;
}
```

Expected:

```text
Valid
```

### `for.mc`

```c
int i;

for (i = 0; i < 5; i++) {
    i = i + 1;
}
```

Expected:

```text
Valid
```

> The `for` syntax must match the exact grammar implemented in `parser.y`.

---

## Invalid Test Cases

The `tests/invalid/` directory contains programs that intentionally contain errors.

### `missing_semicolon.mc`

```c
int age
age = 20;
```

Expected:

```text
Syntax Error
```

Reason:

The declaration is missing a semicolon.

---

### `syntax_error.mc`

```c
int age;

age = ;
```

Expected:

```text
Syntax Error
```

Reason:

There is no expression after the assignment operator.

---

### `redeclaration.mc`

```c
int age;
int age;
```

Expected:

```text
Semantic Error
```

Reason:

The variable `age` is declared more than once in the same scope.

---

### `undeclared_variable.mc`

```c
age = 20;
```

Expected:

```text
Semantic Error
```

Reason:

`age` has not been declared.

---

### `type_mismatch.mc`

```c
int age;

age = 20.5;
```

Expected:

```text
Semantic Error
```

Reason:

A floating-point value is assigned to an integer variable, assuming strict type checking is implemented.

---

### `divide_by_zero.mc`

```c
int a;
int b;
int result;

a = 10;
b = 0;

result = a / b;
```

Expected:

```text
Semantic Error
```

Reason:

Division by zero should be detected if this check is implemented in the semantic-analysis phase.

> Some of these errors are semantic rather than syntactic. Therefore, the parser may successfully parse the source before the semantic-analysis phase reports the error.

---

# Example Program

A simple complete example:

```c
int a;
int b;
int result;

a = 10;
b = 20;

result = a + b;

if (result > 20) {
    result = result + 1;
}
```

### Possible Tokens

```text
INT ID SEMICOLON
INT ID SEMICOLON
INT ID SEMICOLON

ID ASSIGN INT_NUM SEMICOLON
ID ASSIGN INT_NUM SEMICOLON

ID ASSIGN ID PLUS ID SEMICOLON

IF LPAREN ID GT INT_NUM RPAREN
LBRACE
ID ASSIGN ID PLUS INT_NUM SEMICOLON
RBRACE
```

### Symbol Table

| Name | Type |
|------|------|
| a | int |
| b | int |
| result | int |

### Possible TAC

```text
a = 10
b = 20
t1 = a + b
result = t1

if result > 20 goto L1
goto L2

L1:
t2 = result + 1
result = t2

L2:
```

---

# Three Address Code

Three Address Code is used as the intermediate representation.

For:

```c
a = b + c * d;
```

the compiler can generate:

```text
t1 = c * d
t2 = b + t1
a = t2
```

For a conditional:

```c
if (a < b) {
    c = a;
}
```

possible TAC is:

```text
if a < b goto L1
goto L2

L1:
c = a

L2:
```

For a loop:

```c
while (i < 5) {
    i = i + 1;
}
```

possible TAC is:

```text
L1:
if i < 5 goto L2
goto L3

L2:
i = i + 1
goto L1

L3:
```

The exact TAC depends on the implementation of the TAC-generation module.

---

# Error Handling

The compiler handles errors at different stages.

## Lexical Error

Occurs when an invalid character or token is encountered.

Example:

```text
@abc
```

Possible message:

```text
Lexical Error: Invalid character '@'
```

## Syntax Error

Occurs when the source code violates the grammar.

Example:

```c
int age
age = 20;
```

Possible message:

```text
Syntax Error
```

## Semantic Error

Occurs when the syntax is valid but the program violates semantic rules.

Example:

```c
int age;

salary = 50000;
```

Possible message:

```text
Semantic Error: Undeclared identifier 'salary'
```

---

# Limitations

This project is intentionally limited for educational purposes.

The current compiler does not aim to provide complete compatibility with C, C++, or Java.

The following advanced features are outside the current scope or may not be implemented:

- Function definitions
- Function calls
- Arrays
- Pointers
- Structures
- Unions
- File handling
- Dynamic memory allocation
- `switch`
- `do-while`
- Classes
- Objects
- Inheritance
- Exception handling
- Java generics
- Advanced C++ features
- Complete target-code generation

The compiler supports only the language constructs implemented in the current Flex and Bison grammar.

---

# Future Scope

The project can be extended with:

1. Function definitions and function calls.
2. Array support.
3. Pointer support.
4. Structures and classes.
5. Abstract Syntax Tree (AST) generation.
6. Improved semantic analysis.
7. Better scope management.
8. Advanced type checking.
9. More optimization techniques.
10. Improved error recovery.
11. Complete target-code generation.
12. Expanded C, C++, and Java language support.
13. Graphical compiler interface.
14. Automated test-case execution and reporting.

---

# Project Workflow

The overall workflow is:

```text
Source Code
     |
     v
   Flex
     |
     v
  Tokens
     |
     v
  Bison
     |
     v
Syntax Analysis
     |
     v
Symbol Table
     |
     v
Semantic Analysis
     |
     v
TAC Generation
     |
     v
Optimization
     |
     v
Intermediate Representation
```

---

# Project Summary

| Component | Implementation |
|-----------|----------------|
| Lexical Analysis | Flex |
| Syntax Analysis | Bison |
| Symbol Table | C |
| Semantic Analysis | C |
| Intermediate Representation | Three Address Code |
| Code Optimization | Basic |
| Supported Languages | C, C++, Java-style limited subset |
| Implementation Language | C |
| Build System | Make |
| Development Environment | Visual Studio Code |
| Version Control | Git/GitHub |

---

# Authors

**Mini Compiler Front-End Project**

Developed as an academic project for the study of **Compiler Construction**.

---

# License

This project is developed for **educational purposes**.
