# Mini Compiler Front-End

## 1. Introduction

**Mini Compiler Front-End** is a simplified compiler developed for academic purposes using **Flex (Lex)** and **Bison (Yacc)**.

The compiler reads source programs written in a **limited subset of C, C++, and Java** and performs several important compiler front-end tasks.

The major phases and functionalities implemented in this project include:

* Lexical Analysis
* Syntax Analysis
* Symbol Table Generation
* Semantic Analysis
* Intermediate Code Generation (Three Address Code)
* Basic Code Optimization

The main purpose of this project is to demonstrate fundamental **Compiler Construction** concepts using Flex and Bison.

---

## 2. Supported Programming Languages

The compiler supports a limited subset of the following programming languages:

| Language | Support   |
| -------- | --------- |
| C        | Supported |
| C++      | Supported |
| Java     | Supported |

### C Example

```c
int age;

age = 20;

if (age >= 18)
{
    printf(age);
}
```

### C++ Example

```cpp
int age;

age = 20;

if (age >= 18)
{
    cout << age;
}
```

### Java Example

```java
int age;

age = 20;

if (age >= 18)
{
    System.out.println(age);
}
```

> **Note:** The compiler supports only a limited subset of C, C++, and Java syntax. It is not intended to be a complete compiler for these programming languages.

---

## 3. Project Objectives

The main objectives of this project are:

* To develop a Mini Compiler Front-End using Flex and Bison.
* To support a limited subset of C, C++, and Java.
* To perform lexical analysis and generate tokens.
* To perform syntax analysis using Context-Free Grammar (CFG).
* To maintain a symbol table for identifiers.
* To perform semantic analysis and detect semantic errors.
* To generate Intermediate Code using Three Address Code (TAC).
* To implement basic code optimization concepts.
* To improve understanding of compiler construction and front-end design.

---

## 4. Supported Data Types

The compiler supports the following primitive data types:

| Data Type | Description            |
| --------- | ---------------------- |
| `int`     | Integer numbers        |
| `float`   | Floating-point numbers |
| `char`    | Character values       |
| `bool`    | Boolean values         |

### Examples

#### C / C++

```c
int age;

float cgpa;

char grade;

bool status;
```

#### Java

```java
int age;

float cgpa;

char grade;

boolean status;
```

> **Note:** Java uses `boolean` for Boolean values, while C/C++ commonly use `bool`.

---

## 5. Keywords

The compiler recognizes keywords required for the supported language subset.

| Keyword              | Description                |
| -------------------- | -------------------------- |
| `int`                | Integer declaration        |
| `float`              | Floating-point declaration |
| `char`               | Character declaration      |
| `bool`               | Boolean declaration        |
| `boolean`            | Java Boolean type          |
| `if`                 | Conditional statement      |
| `else`               | Else block                 |
| `while`              | While loop                 |
| `for`                | For loop                   |
| `return`             | Return statement           |
| `printf`             | C/C++ output statement     |
| `cout`               | C++ output statement       |
| `System.out.println` | Java output statement      |

---

## 6. Operators

### 6.1 Arithmetic Operators

| Operator | Meaning        |
| -------- | -------------- |
| `+`      | Addition       |
| `-`      | Subtraction    |
| `*`      | Multiplication |
| `/`      | Division       |
| `%`      | Modulus        |

---

### 6.2 Assignment Operators

| Operator | Meaning             |
| -------- | ------------------- |
| `=`      | Assignment          |
| `+=`     | Add and assign      |
| `-=`     | Subtract and assign |
| `*=`     | Multiply and assign |
| `/=`     | Divide and assign   |
| `%=`     | Modulus and assign  |

---

### 6.3 Relational Operators

| Operator | Meaning               |
| -------- | --------------------- |
| `==`     | Equal                 |
| `!=`     | Not Equal             |
| `<`      | Less Than             |
| `>`      | Greater Than          |
| `<=`     | Less Than or Equal    |
| `>=`     | Greater Than or Equal |

---

### 6.4 Logical Operators

| Operator | Meaning     |   |            |
| -------- | ----------- | - | ---------- |
| `&&`     | Logical AND |   |            |
| `        |             | ` | Logical OR |
| `!`      | Logical NOT |   |            |

---

### 6.5 Increment and Decrement Operators

| Operator | Meaning   |
| -------- | --------- |
| `++`     | Increment |
| `--`     | Decrement |

Examples:

```c
i++;
i--;
```

---

## 7. Delimiters and Special Symbols

The compiler supports the following delimiters and symbols:

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

Other supported symbols may include:

```text
.
::
<<
```

depending on the programming language syntax being processed.

---

## 8. Comments

The compiler supports common single-line and multi-line comment styles.

### Single-Line Comment

```c
// This is a comment
```

### Multi-Line Comment

```c
/*
   This is
   a multi-line
   comment
*/
```

These comment styles are commonly used in C, C++, and Java.

---

## 9. Supported Statements

The compiler supports the following statement types:

* Variable Declaration
* Variable Assignment
* Arithmetic Expressions
* Relational Expressions
* Logical Expressions
* Compound Assignment
* Increment and Decrement
* `if` Statement
* `if-else` Statement
* `while` Loop
* `for` Loop
* Output Statements
* Nested Blocks
* `return` Statement

---

## 10. Variable Declaration

### C / C++

```c
int age;

float cgpa;

char grade;

bool status;
```

### Java

```java
int age;

float cgpa;

char grade;

boolean status;
```

---

## 11. Variable Assignment

Example:

```c
int age;

age = 20;
```

Arithmetic expressions are also supported:

```c
int a;
int b;
int result;

a = 10;
b = 20;

result = a + b;
```

---

## 12. Conditional Statements

### if Statement

```c
int age;

age = 20;

if (age >= 18)
{
    printf(age);
}
```

### if-else Statement

```c
int age;

age = 20;

if (age >= 18)
{
    printf(age);
}
else
{
    printf(age);
}
```

The same conditional structure can be represented using the supported syntax of C, C++, and Java.

---

## 13. While Loop

Example:

```c
int i;

i = 0;

while (i < 5)
{
    printf(i);
    i++;
}
```

---

## 14. For Loop

Example:

```c
int i;

for (i = 0; i < 5; i++)
{
    printf(i);
}
```

The compiler also supports nested loops within the supported grammar.

---

## 15. Output Statements

The compiler supports output statements from the supported language subset.

### C

```c
printf(age);
```

### C++

```cpp
cout << age;
```

### Java

```java
System.out.println(age);
```

> The exact supported syntax depends on the lexical and grammatical rules implemented in the current version of the compiler.

---

## 16. Nested Blocks

The compiler supports nested blocks and nested control structures.

Example:

```c
int i;

for (i = 0; i < 5; i++)
{
    if (i > 2)
    {
        printf(i);
    }
}
```

Nested loops and conditional statements can also be used within the supported grammar.

---

## 17. Symbol Table

The compiler maintains a **Symbol Table** to store information about identifiers used in the source program.

Typical information stored in the symbol table includes:

| Field | Description            |
| ----- | ---------------------- |
| Name  | Identifier name        |
| Type  | Data type              |
| Scope | Identifier scope       |
| Value | Current/assigned value |

Example:

```c
int age;
float cgpa;
```

Possible symbol table:

| Name | Type  | Scope  |
| ---- | ----- | ------ |
| age  | int   | Global |
| cgpa | float | Global |

---

## 18. Semantic Analysis

The compiler performs semantic checking on the source program.

Examples of semantic errors include:

* Undeclared variable
* Duplicate variable declaration
* Invalid assignment
* Type mismatch
* Invalid expression
* Incorrect use of identifiers

Example:

```c
int age;

salary = 50000;
```

If `salary` has not been declared, the compiler can report an undeclared identifier error.

---

## 19. Three Address Code (TAC)

The compiler generates **Three Address Code (TAC)** as an intermediate representation.

Example source code:

```c
a = b + c * d;
```

Possible TAC:

```text
t1 = c * d
t2 = b + t1
a = t2
```

For conditional statements, TAC may contain labels and conditional jumps.

Example:

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

---

## 20. Code Optimization

The compiler may apply basic optimization techniques to improve the generated intermediate code.

Examples include:

* Constant Folding
* Constant Propagation
* Simple Algebraic Simplification
* Removal of unnecessary temporary operations

Example:

```text
t1 = 5 * 2
```

can be optimized to:

```text
t1 = 10
```

---

## 21. Compiler Workflow

The Mini Compiler Front-End processes source code through the following stages:

```text
Source Code
     ↓
Lexical Analysis
     ↓
Syntax Analysis
     ↓
Symbol Table Generation
     ↓
Semantic Analysis
     ↓
Intermediate Code Generation
     ↓
Code Optimization
     ↓
Final Intermediate Representation
```

### Phase 1: Lexical Analysis

Flex scans the source code and converts the input into tokens.

Example:

```c
int age;
```

Tokens:

```text
INT
ID
SEMICOLON
```

### Phase 2: Syntax Analysis

Bison checks whether the sequence of tokens follows the grammar rules of the compiler.

### Phase 3: Symbol Table Generation

Identifiers and their associated information are stored in the symbol table.

### Phase 4: Semantic Analysis

The compiler checks semantic rules such as declaration, scope, and type compatibility.

### Phase 5: Intermediate Code Generation

The compiler generates Three Address Code (TAC).

### Phase 6: Code Optimization

Basic optimization techniques are applied to the generated intermediate code.

---

## 22. Technologies Used

| Technology         | Purpose                 |
| ------------------ | ----------------------- |
| Flex               | Lexical Analysis        |
| Bison              | Syntax Analysis         |
| C                  | Compiler implementation |
| GCC                | Compilation             |
| Git                | Version Control         |
| GitHub             | Project Repository      |
| Visual Studio Code | Development Environment |

---

## 23. Project Structure

A possible project structure is:

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
└── .gitignore
```

---

## 24. Compiler Limitations

The current version supports only a limited subset of C, C++, and Java.

The following advanced features are currently not supported:

* Functions
* Arrays
* Pointers
* Structures
* Unions
* File Handling
* Dynamic Memory Allocation
* `switch` Statement
* `do-while` Loop
* Classes
* Objects
* Inheritance
* Exception Handling
* Generics
* Advanced Java features

These features may be added in future versions.

---

## 25. Future Scope

The project can be extended with the following features:

* Function Definition
* Function Call
* Arrays
* Structures
* Pointer Support
* File Handling
* `switch` Statement
* `do-while` Loop
* Abstract Syntax Tree (AST)
* Advanced Code Optimization
* Type Checking
* Scope Management
* Better Error Recovery
* More C/C++/Java Language Features
* Target Code Generation

---

## 26. Educational Purpose

This project is developed primarily for **educational and academic purposes**.

It demonstrates the fundamental concepts of compiler construction, including:

* Lexical Analysis
* Parsing
* Context-Free Grammar
* Symbol Table
* Semantic Analysis
* Intermediate Code Generation
* Three Address Code
* Code Optimization

The project is not intended to replace a complete production-level C, C++, or Java compiler.

---

## 27. Conclusion

The **Mini Compiler Front-End** demonstrates how a compiler processes source code written in a limited subset of **C, C++, and Java**.

Using **Flex and Bison**, the project performs lexical and syntax analysis, maintains a symbol table, performs semantic checking, generates Three Address Code, and applies basic optimization techniques.

This project provides a practical understanding of the major concepts involved in **Compiler Construction** and can serve as a foundation for developing a more advanced compiler in the future.
