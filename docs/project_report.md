# Mini Compiler Front-End

## Project Report

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Introduction](#2-introduction)
3. [Problem Statement](#3-problem-statement)
4. [Project Objectives](#4-project-objectives)
5. [Scope of the Project](#5-scope-of-the-project)
6. [Supported Languages](#6-supported-languages)
7. [Compiler Architecture](#7-compiler-architecture)
8. [Compiler Phases](#8-compiler-phases)
9. [Lexical Analysis](#9-lexical-analysis)
10. [Syntax Analysis](#10-syntax-analysis)
11. [Symbol Table](#11-symbol-table)
12. [Semantic Analysis](#12-semantic-analysis)
13. [Intermediate Code Generation](#13-intermediate-code-generation)
14. [Three Address Code](#14-three-address-code)
15. [Code Optimization](#15-code-optimization)
16. [Error Handling](#16-error-handling)
17. [Supported Features](#17-supported-features)
18. [System Requirements](#18-system-requirements)
19. [Technologies Used](#19-technologies-used)
20. [Project Structure](#20-project-structure)
21. [Testing](#21-testing)
22. [Sample Input and Output](#22-sample-input-and-output)
23. [Limitations](#23-limitations)
24. [Future Scope](#24-future-scope)
25. [Conclusion](#25-conclusion)

---

# 1. Project Overview

**Project Name:** Mini Compiler Front-End

**Project Type:** Academic Compiler Construction Project

**Programming Languages Supported:** C, C++, Java (Limited Subset)

**Implementation Language:** C

**Main Tools:** Flex and Bison

**Development Environment:** Visual Studio Code

The Mini Compiler Front-End is an educational compiler project designed to demonstrate the fundamental concepts of compiler construction.

The compiler accepts source programs written in a limited subset of **C, C++, and Java** and processes them through several front-end phases.

The major functionalities include:

* Lexical Analysis
* Syntax Analysis
* Symbol Table Generation
* Semantic Analysis
* Intermediate Code Generation
* Three Address Code (TAC)
* Basic Code Optimization
* Error Detection and Reporting

The project demonstrates how source code is transformed from a sequence of characters into tokens, validated according to grammar rules, semantically checked, and converted into intermediate representation.

---

# 2. Introduction

A compiler is a system program that translates source code written in a high-level programming language into another form that can be executed or further processed by a computer.

Compiler construction is generally divided into several phases. The front-end of a compiler is responsible for analyzing the source program and generating an intermediate representation.

This project implements a simplified compiler front-end using **Flex and Bison**.

Flex is used to perform lexical analysis, while Bison is used to perform syntax analysis and parsing.

The project is designed to support common programming constructs from C, C++, and Java while keeping the implementation simple enough for academic learning.

---

# 3. Problem Statement

Understanding compiler construction theoretically can be difficult without implementing the individual compiler phases.

Students often learn concepts such as:

* Tokens
* Lexical Analysis
* Context-Free Grammar
* Parsing
* Symbol Tables
* Semantic Analysis
* Intermediate Code
* Three Address Code

independently.

The objective of this project is to combine these concepts into a single working system.

The proposed Mini Compiler Front-End provides a simplified environment where a source program can be analyzed step by step.

---

# 4. Project Objectives

The main objectives of the project are:

1. To develop a simplified compiler front-end using Flex and Bison.
2. To perform lexical analysis on source programs.
3. To generate tokens from source code.
4. To validate source code using grammar rules.
5. To maintain a symbol table.
6. To detect basic semantic errors.
7. To generate Three Address Code.
8. To implement basic intermediate-code optimization.
9. To support a limited subset of C, C++, and Java.
10. To provide meaningful syntax and semantic error messages.
11. To gain practical knowledge of compiler construction.

---

# 5. Scope of the Project

The project focuses mainly on the **front-end** of a compiler.

The supported scope includes:

* Source code processing
* Token generation
* Syntax checking
* Variable declaration
* Variable assignment
* Arithmetic expressions
* Relational expressions
* Logical expressions
* Conditional statements
* Loop statements
* Symbol table management
* Semantic checking
* Intermediate code generation
* Three Address Code
* Basic optimization

The project does not attempt to implement a complete C, C++, or Java compiler.

---

# 6. Supported Languages

The compiler supports a limited subset of:

### C

Example:

```c
int age;

age = 20;

if (age >= 18)
{
    printf(age);
}
```

### C++

Example:

```cpp
int age;

age = 20;

if (age >= 18)
{
    cout << age;
}
```

### Java

Example:

```java
int age;

age = 20;

if (age >= 18)
{
    System.out.println(age);
}
```

> The compiler supports only the language constructs implemented in the current Flex and Bison grammar. It is not a complete compiler for C, C++, or Java.

---

# 7. Compiler Architecture

The overall architecture of the Mini Compiler Front-End can be represented as follows:

```text
                 Source Program
                       |
                       v
              +------------------+
              | Lexical Analysis |
              |     (Flex)       |
              +------------------+
                       |
                     Tokens
                       |
                       v
              +------------------+
              | Syntax Analysis  |
              |     (Bison)      |
              +------------------+
                       |
                    Parse Tree
                       |
                       v
              +------------------+
              |  Symbol Table    |
              +------------------+
                       |
                       v
              +------------------+
              | Semantic Analysis|
              +------------------+
                       |
                       v
              +------------------+
              | TAC Generation   |
              +------------------+
                       |
                       v
              +------------------+
              | Code Optimization|
              +------------------+
                       |
                       v
              Intermediate Code
```

---

# 8. Compiler Phases

The compiler processes source code through the following major phases:

```text
Source Code
     |
     v
Lexical Analysis
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
Intermediate Code Generation
     |
     v
Code Optimization
     |
     v
Intermediate Representation
```

Each phase performs a specific task.

---

# 9. Lexical Analysis

Lexical analysis is the first phase of the compiler.

In this phase, the source code is converted into a sequence of tokens.

The lexical analyzer is implemented using **Flex**.

For example:

```c
int age = 20;
```

can be converted into tokens such as:

```text
INT
ID
ASSIGN
INT_NUM
SEMICOLON
```

## 9.1 Types of Tokens

The compiler recognizes different categories of tokens.

### Keywords

Examples:

```text
int
float
char
bool
if
else
while
for
return
```

### Identifiers

Examples:

```text
age
sum
count
result
```

### Numbers

Examples:

```text
10
25
3.14
```

### Operators

Examples:

```text
+
-
*
/
%
=
==
!=
<
>
<=
>=
&&
||
!
```

### Delimiters

Examples:

```text
;
,
(
)
{
}
[
]
```

---

# 10. Syntax Analysis

Syntax analysis is responsible for checking whether the sequence of tokens follows the grammar rules of the language.

The parser is implemented using **Bison**.

For example:

```c
int age;

age = 20;
```

is checked according to the grammar rules defined in the parser.

If the source program violates the grammar, the parser generates a syntax error.

Example:

```c
int age

age = 20;
```

The missing semicolon can be detected during syntax analysis.

---

# 11. Symbol Table

A symbol table is an important data structure used by the compiler.

It stores information about identifiers declared in the source program.

Typical information includes:

| Attribute | Description             |
| --------- | ----------------------- |
| Name      | Identifier name         |
| Type      | Data type               |
| Scope     | Scope of the identifier |
| Value     | Assigned/current value  |

Example source:

```c
int age;
float cgpa;
```

Possible symbol table:

| Name | Type  | Scope  |
| ---- | ----- | ------ |
| age  | int   | Global |
| cgpa | float | Global |

The symbol table can be used during semantic analysis to determine whether variables are declared and whether their usage is valid.

---

# 12. Semantic Analysis

Semantic analysis checks whether the source program is logically meaningful according to the language rules.

Examples of semantic errors include:

* Undeclared variable
* Duplicate declaration
* Invalid assignment
* Type mismatch
* Invalid identifier usage

Example:

```c
int age;

salary = 50000;
```

If `salary` has not been declared, the compiler can report:

```text
Semantic Error: Undeclared identifier 'salary'
```

Semantic analysis helps ensure that syntactically correct programs are also semantically valid.

---

# 13. Intermediate Code Generation

After syntax and semantic analysis, the compiler can generate an intermediate representation.

This project uses **Three Address Code (TAC)** as the intermediate representation.

Intermediate code provides a bridge between source code and lower-level code.

For example:

```c
a = b + c * d;
```

can be represented as:

```text
t1 = c * d
t2 = b + t1
a = t2
```

---

# 14. Three Address Code

Three Address Code is an intermediate representation where each instruction generally contains at most three addresses.

A temporary variable is often used to store intermediate results.

## Example

Source:

```c
a = b + c * d;
```

TAC:

```text
t1 = c * d
t2 = b + t1
a = t2
```

## Conditional TAC

Source:

```c
if (a < b)
{
    c = a;
}
```

Possible TAC:

```text
if a < b goto L1
goto L2

L1:
c = a

L2:
```

## Loop TAC

For a loop such as:

```c
while (i < 5)
{
    i++;
}
```

the intermediate representation can use labels and conditional jumps:

```text
L1:
if i < 5 goto L2
goto L3

L2:
i = i + 1
goto L1

L3:
```

The exact generated TAC depends on the implementation of the parser and TAC generation module.

---

# 15. Code Optimization

Code optimization attempts to improve the generated intermediate code.

The purpose of optimization is to reduce unnecessary operations and improve efficiency.

Basic optimization techniques may include:

### 15.1 Constant Folding

Before:

```text
t1 = 5 * 2
```

After:

```text
t1 = 10
```

### 15.2 Algebraic Simplification

Before:

```text
t1 = x + 0
```

After:

```text
t1 = x
```

### 15.3 Removing Unnecessary Operations

Unnecessary intermediate operations can be removed when they do not affect the final result.

> Optimization is limited to the techniques implemented in the current project version.

---

# 16. Error Handling

The compiler provides error detection during different phases.

## 16.1 Lexical Error

Occurs when an invalid character or token is encountered.

Example:

```text
@abc
```

Possible message:

```text
Lexical Error: Invalid character '@'
```

## 16.2 Syntax Error

Occurs when the source code does not follow the grammar.

Example:

```c
if (age >= 18
{
    printf(age);
}
```

Possible message:

```text
Syntax Error: Expected ')'
```

## 16.3 Semantic Error

Occurs when the program violates semantic rules.

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

# 17. Supported Features

The current compiler supports the following features, subject to the implemented grammar:

### Data Types

* `int`
* `float`
* `char`
* `bool`
* Java `boolean`

### Statements

* Variable declaration
* Variable assignment
* Arithmetic expressions
* Relational expressions
* Logical expressions
* `if`
* `if-else`
* `while`
* `for`
* `return`
* Nested blocks
* Output statements

### Operators

* Arithmetic operators
* Assignment operator
* Relational operators
* Logical operators
* Increment/decrement
* Compound assignment operators

### Compiler Features

* Lexical analysis
* Syntax analysis
* Symbol table
* Semantic analysis
* TAC generation
* Basic optimization
* Error reporting

---

# 18. System Requirements

## Hardware Requirements

The project can run on a standard computer.

Recommended:

* Processor: Dual Core or better
* RAM: 4 GB or more
* Storage: At least 1 GB free space

## Software Requirements

* Windows / Linux
* Visual Studio Code
* GCC
* Flex
* Bison
* Git
* GitHub

---

# 19. Technologies Used

| Technology         | Purpose                 |
| ------------------ | ----------------------- |
| C                  | Compiler implementation |
| Flex               | Lexical Analysis        |
| Bison              | Syntax Analysis         |
| GCC                | Compilation             |
| Git                | Version Control         |
| GitHub             | Source Code Management  |
| Visual Studio Code | Development Environment |

---

# 20. Project Structure

A recommended project structure is:

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
│   └── tac/
│       └── tac.c
│
├── tests/
│   ├── c/
│   ├── cpp/
│   └── java/
│
├── output/
│
├── README.md
├── PROJECT_REPORT.md
└── .gitignore
```

The actual project structure may vary depending on the implementation.

---

# 21. Testing

Testing is performed using different valid and invalid source programs.

The test cases cover:

* Variable declaration
* Variable assignment
* Arithmetic expressions
* Relational expressions
* Logical expressions
* `if`
* `if-else`
* `while`
* `for`
* Nested statements
* Output statements
* Syntax errors
* Semantic errors
* TAC generation

## 21.1 Valid Test Case

Input:

```c
int i;

i = 0;

while (i < 5)
{
    printf(i);
    i++;
}
```

Expected result:

```text
Parsing Successful
```

Possible TAC:

```text
L1:
if i < 5 goto L2
goto L3
L2:
print i
i = i + 1
goto L1
L3:
```

---

## 21.2 Invalid Syntax Test Case

Input:

```c
int i

i = 0;
```

Expected result:

```text
Syntax Error
```

because the declaration is missing a semicolon.

---

## 21.3 Semantic Error Test Case

Input:

```c
int age;

salary = 50000;
```

Expected result:

```text
Semantic Error: Undeclared identifier 'salary'
```

---

# 22. Sample Input and Output

## Sample Input

```c
int a;
int b;
int result;

a = 10;
b = 20;

result = a + b;

if (result > 20)
{
    printf(result);
}
```

## Expected Processing

### Tokens

```text
INT ID SEMICOLON
INT ID SEMICOLON
INT ID SEMICOLON

ID ASSIGN INT_NUM SEMICOLON
ID ASSIGN INT_NUM SEMICOLON

ID ASSIGN ID PLUS ID SEMICOLON

IF LPAREN ID GT INT_NUM RPAREN
LBRACE
PRINTF LPAREN ID RPAREN SEMICOLON
RBRACE
```

### Symbol Table

| Name   | Type |
| ------ | ---- |
| a      | int  |
| b      | int  |
| result | int  |

### Possible TAC

```text
a = 10
b = 20
t1 = a + b
result = t1

if result > 20 goto L1
goto L2

L1:
print result

L2:
```

---

# 23. Limitations

The current version is a simplified educational compiler.

The following advanced features are not currently supported or are outside the intended scope:

* Function definition
* Function calls
* Arrays
* Pointers
* Structures
* Unions
* File handling
* Dynamic memory allocation
* `switch`
* `do-while`
* Classes
* Objects
* Inheritance
* Exception handling
* Java generics
* Advanced C++ features
* Complete target-code generation

The compiler does not aim to provide complete compatibility with standard C, C++, or Java compilers.

---

# 24. Future Scope

The project can be extended in several ways.

Future improvements may include:

1. Function definitions and function calls.
2. Array support.
3. Pointer support.
4. Structure and class support.
5. Abstract Syntax Tree (AST) generation.
6. Improved semantic analysis.
7. Scope management.
8. Advanced type checking.
9. More optimization techniques.
10. Better error recovery.
11. Complete target code generation.
12. Expanded C, C++, and Java language support.
13. Graphical compiler interface.
14. Improved test-case automation.

---

# 25. Conclusion

The **Mini Compiler Front-End** is an educational compiler project that demonstrates the fundamental principles of compiler construction.

Using **Flex and Bison**, the project processes a limited subset of C, C++, and Java source code through lexical analysis and syntax analysis. It also demonstrates symbol table management, semantic analysis, intermediate code generation, Three Address Code, basic optimization, and error handling.

The project provides practical experience in understanding how a compiler analyzes source code and transforms it into an intermediate representation.

Although the current implementation supports only a limited subset of the three programming languages, it provides a strong foundation for further development toward a more complete compiler.

---

## Project Summary

| Component                   | Implementation                |
| --------------------------- | ----------------------------- |
| Lexical Analysis            | Flex                          |
| Syntax Analysis             | Bison                         |
| Symbol Table                | Implemented                   |
| Semantic Analysis           | Implemented                   |
| Intermediate Representation | Three Address Code            |
| Code Optimization           | Basic                         |
| Supported Languages         | C, C++, Java (Limited Subset) |
| Implementation Language     | C                             |
| Development Environment     | Visual Studio Code            |
| Version Control             | Git/GitHub                    |

---

## Authors

**Mini Compiler Front-End Project**

Developed as an academic project for the study of **Compiler Construction**.

---

## License

This project is developed for educational purposes.
**
