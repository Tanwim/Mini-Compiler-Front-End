# Mini Compiler — Full Grammar

## Notation
- Nonterminals: UPPER_CAMEL (e.g., Program, Statement)
- Terminals / tokens: UPPER_SNAKE or literal strings (e.g., IDENTIFIER, INTEGER, '+')
- EBNF operators:
  - A | B  — choice
  - A B    — sequence
  - A*     — zero or more
  - A+     — one or more
  - [A]    — optional A

## Token (lexical) summary (lexer responsibilities)
- Keywords: int, float, char, bool, if, else, while, for, printf, cout
- IDENTIFIER: /[A-Za-z_][A-Za-z0-9_]*/
- INTEGER: /[0-9]+/
- FLOAT_LITERAL: /[0-9]+\.[0-9]+/
- CHAR_LITERAL: /'(\\.|[^\\'])'/
- STRING_LITERAL: /"([^"\\]|\\.)*"/
- BOOL_LITERAL: /true|false/
- Operators and punctuation: '+', '-', '*', '/', '%', '==', '!=', '<=', '>=', '<', '>', '=', '++', '--', '<<', ',', ';', '(', ')', '{', '}', '<<'
- Whitespace and comments: skip (space, tab, newline, //..., /*...*/)

Longest-match rule: recognize multi-char tokens (==, <=, ++, etc.) before single-char ones.

---

## Grammar (BNF/EBNF) — ordered from start symbol to terminals

1. Program
   Program → StatementList

2. Statement list
   StatementList → Statement StatementList
   StatementList → ε
   (equivalently StatementList → Statement*)

3. Statement (top-level statement choices)
   Statement → Declaration
   Statement → AssignmentStatement
   Statement → SelectionStatement
   Statement → WhileStatement
   Statement → ForStatement
   Statement → PrintStatement
   Statement → Block
   Statement → EmptyStatement

4. Empty statement
   EmptyStatement → ';'

5. Declaration
   Declaration → Type IDENTIFIER [ '=' Expression ] ';'
   Type → 'int' | 'float' | 'char' | 'bool'

6. Assignment statement (including increment/decrement postfix)
   AssignmentStatement → IDENTIFIER '=' Expression ';'
   AssignmentStatement → IDENTIFIER '++' ';'   // postfix increment as statement
   AssignmentStatement → IDENTIFIER '--' ';'   // postfix decrement as statement

   (For expressions where ++/-- appear within expressions, treat them as postfix operators in Factor or as separate productions below.)

7. Expressions (arithmetic + parentheses + literals + identifiers)
   Expression → Expression '+' Term
   Expression → Expression '-' Term
   Expression → Term

   Term → Term '*' Factor
   Term → Term '/' Factor
   Term → Term '%' Factor
   Term → Factor

   Factor → IDENTIFIER
   Factor → INTEGER
   Factor → FLOAT_LITERAL
   Factor → CHAR_LITERAL
   Factor → BOOL_LITERAL
   Factor → STRING_LITERAL
   Factor → IDENTIFIER '++'      // postfix ++ as expression (optional)
   Factor → IDENTIFIER '--'      // postfix -- as expression (optional)
   Factor → '(' Expression ')'
   Factor → '+' Factor           // unary plus
   Factor → '-' Factor           // unary minus

8. Number categories (for completeness)
   Number → INTEGER | FLOAT_LITERAL

9. Condition (relational expressions)
   Condition → Expression RelationalOperator Expression
   RelationalOperator → '<' | '>' | '<=' | '>=' | '==' | '!='

10. Selection (if / if-else)
    SelectionStatement → 'if' '(' Condition ')' Block
    SelectionStatement → 'if' '(' Condition ')' Block 'else' Block

11. While loop
    WhileStatement → 'while' '(' Condition ')' Block

12. For loop (C-style)
    ForStatement → 'for' '(' ForInit? ';' Condition? ';' ForPost? ')' Block

    ForInit → DeclarationNoSemi | AssignmentNoSemi
    ForPost → AssignmentNoSemi | IDENTIFIER '++' | IDENTIFIER '--'

    // Use no-semi variants inside for parentheses:
    DeclarationNoSemi → Type IDENTIFIER [ '=' Expression ]
    AssignmentNoSemi → IDENTIFIER '=' Expression

13. Print / I/O statements
    // Simple printf form (arguments as expressions or string + expressions)
    PrintStatement → 'printf' '(' PrintArgs ')' ';'
    PrintArgs → (Expression | STRING_LITERAL) (',' (Expression | STRING_LITERAL))*

    // Simple cout form (C++-style chaining using '<<')
    PrintStatement → 'cout' CoutChain ';'
    CoutChain → '<<' CoutItem ( '<<' CoutItem )*
    CoutItem → Expression | STRING_LITERAL

    // Note: lexer must produce '<<' as token

14. Block
    Block → '{' StatementList '}'

15. Identifier decomposition (lexical — described for lexer)
    IDENTIFIER → Letter IdentifierTail
    IdentifierTail → (Letter | Digit | '_' )*
    Letter → a-z | A-Z | _
    Digit → 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

---

## Operator precedence & associativity (recommended ordering)
(from lowest precedence to highest; use Bison %left/%right)
- assignment: '='                      (right-assoc)
- relational: '<' '>' '<=' '>=' '==' '!='  (non-assoc)
- additive: '+' '-'                     (%left)
- multiplicative: '*' '/' '%'           (%left)
- unary: unary '+' unary '-'            (right-assoc; give token UMINUS)
- postfix: IDENTIFIER '++' / '--'       (highest; if treated)

Suggested Bison declarations (conceptual):
%right '='
%nonassoc LT GT LE GE EQ NE
%left '+' '-'
%left '*' '/' '%'
%right UMINUS

Map token names to actual %token entries (e.g., %token IDENTIFIER INTEGER FLOAT_LITERAL).

---

## Error-recovery suggestions
- Recover at semicolons and closing braces:
  - Add production: StatementList → StatementList error ';' { yyerrok; }
  - Add: StatementList → StatementList error '}' { yyerrok; /* maybe push back '}' */ }
- Report line & column at lexer level for helpful diagnostics.

---

## Implementation notes & mapping to Bison/Flex
- Lexer (Flex): implement token regexes, return token names and semantic values (yylval).
- Parser (Bison): implement productions, use %union for value types (int, double, char*, AST*).
- Build AST nodes in parser actions; keep type-checking for a later pass.
- Tests: create small files covering declarations, assignment, expression precedence, control flow, nested blocks, and print variants.

---

## Limitations (current)
- No logical operators (&&, ||, !). Add as additional precedence layer if needed.
- No function definitions or calls.
- No arrays, pointers, structs.
- Limited printf format-string parsing — currently treat string as literal, expressions separated by commas.
