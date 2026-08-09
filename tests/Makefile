# ============================================================
# Mini Compiler Front-End - Makefile
# ============================================================
#
# Project:
#   Mini Compiler Front-End
#
# Tools:
#   Flex / win_flex
#   Bison
#   GCC
#
# Expected project structure:
#
# Mini-Compiler-Front-End/
# ├── src/
# │   ├── main.c
# │   ├── lexer/
# │   │   └── lexer.l
# │   ├── parser/
# │   │   └── parser.y
# │   ├── symbol_table/
# │   │   └── symbol_table.c
# │   ├── semantic/
# │   │   └── semantic.c
# │   ├── tac/
# │   │   └── tac.c
# │   └── utils/
# │       └── *.c
# ├── tests/
# │   ├── valid/
# │   └── invalid/
# └── Makefile
#
# The Makefile is designed for GNU Make on Windows/Linux.
# On Windows, win_flex is preferred when it is available.
# ============================================================

CC      := gcc
BISON   := bison

# Use win_flex on Windows. If your command is named "flex",
# change this to:
# FLEX := flex
FLEX    := win_flex

CFLAGS  := -Wall -Wextra -I src -I src/parser -I src/lexer \
           -I src/symbol_table -I src/semantic -I src/tac -I src/utils

LDFLAGS :=

TARGET  := compiler

# ------------------------------------------------------------
# Source files
# ------------------------------------------------------------

MAIN_SRC := src/main.c

MODULE_SOURCES := \
	$(wildcard src/symbol_table/*.c) \
	$(wildcard src/semantic/*.c) \
	$(wildcard src/tac/*.c) \
	$(wildcard src/utils/*.c)

# Generated files
PARSER_C := src/parser/parser.tab.c
PARSER_H := src/parser/parser.tab.h
LEXER_C  := src/lexer/lex.yy.c

# Object files
MAIN_OBJ   := src/main.o
MODULE_OBJS := $(MODULE_SOURCES:.c=.o)
PARSER_OBJ := src/parser/parser.tab.o
LEXER_OBJ  := src/lexer/lex.yy.o

OBJECTS := $(MAIN_OBJ) $(MODULE_OBJS) $(PARSER_OBJ) $(LEXER_OBJ)

# ------------------------------------------------------------
# Default target
# ------------------------------------------------------------

.PHONY: all
all: $(TARGET)

# ------------------------------------------------------------
# Link the final compiler executable
# ------------------------------------------------------------

$(TARGET): $(OBJECTS)
	$(CC) $(OBJECTS) $(LDFLAGS) -o $@

	@echo.
	@echo ============================================
	@echo   Mini Compiler Front-End built successfully
	@echo   Executable: $(TARGET)
	@echo ============================================
	@echo.

# ------------------------------------------------------------
# Generate parser using Bison
# ------------------------------------------------------------

$(PARSER_C) $(PARSER_H): src/parser/parser.y
	$(BISON) -d -o $(PARSER_C) src/parser/parser.y

# ------------------------------------------------------------
# Generate lexer using Flex
# ------------------------------------------------------------

$(LEXER_C): src/lexer/lexer.l $(PARSER_H)
	$(FLEX) -o $(LEXER_C) src/lexer/lexer.l

# ------------------------------------------------------------
# Compile main.c
# ------------------------------------------------------------

$(MAIN_OBJ): $(MAIN_SRC) $(PARSER_H)
	$(CC) $(CFLAGS) -c $(MAIN_SRC) -o $@

# ------------------------------------------------------------
# Compile normal project source files
# ------------------------------------------------------------

src/%.o: src/%.c
	$(CC) $(CFLAGS) -c $< -o $@

# ------------------------------------------------------------
# Compile generated Bison parser
# ------------------------------------------------------------

$(PARSER_OBJ): $(PARSER_C) $(PARSER_H)
	$(CC) $(CFLAGS) -c $(PARSER_C) -o $@

# ------------------------------------------------------------
# Compile generated Flex lexer
# ------------------------------------------------------------

$(LEXER_OBJ): $(LEXER_C) $(PARSER_H)
	$(CC) $(CFLAGS) -c $(LEXER_C) -o $@

# ------------------------------------------------------------
# Run the compiler
#
# Usage:
#   make run FILE=tests/valid/declaration.mc
# ------------------------------------------------------------

.PHONY: run
run: $(TARGET)
	@if "$(FILE)"=="" ( \
		echo Usage: make run FILE=tests/valid/declaration.mc \
	) else ( \
		$(TARGET) "$(FILE)" \
	)

# ------------------------------------------------------------
# Run a valid test
#
# Usage:
#   make test-valid FILE=tests/valid/declaration.mc
# ------------------------------------------------------------

.PHONY: test-valid
test-valid: $(TARGET)
	@if "$(FILE)"=="" ( \
		echo Usage: make test-valid FILE=tests/valid/declaration.mc \
	) else ( \
		$(TARGET) "$(FILE)" \
	)

# ------------------------------------------------------------
# Run an invalid test
#
# Usage:
#   make test-invalid FILE=tests/invalid/syntax_error.mc
# ------------------------------------------------------------

.PHONY: test-invalid
test-invalid: $(TARGET)
	@if "$(FILE)"=="" ( \
		echo Usage: make test-invalid FILE=tests/invalid/syntax_error.mc \
	) else ( \
		$(TARGET) "$(FILE)" \
	)

# ------------------------------------------------------------
# Clean generated files, object files and executable
# ------------------------------------------------------------

.PHONY: clean
clean:
	-del /Q "$(TARGET).exe" "$(TARGET)" 2>NUL
	-del /Q "src\main.o" 2>NUL
	-del /Q "src\parser\parser.tab.o" 2>NUL
	-del /Q "src\parser\parser.tab.c" 2>NUL
	-del /Q "src\parser\parser.tab.h" 2>NUL
	-del /Q "src\lexer\lex.yy.o" 2>NUL
	-del /Q "src\lexer\lex.yy.c" 2>NUL
	-for /R "src" %%f in (*.o) do del /Q "%%f" 2>NUL
	@echo Clean complete.

# ------------------------------------------------------------
# Rebuild everything from scratch
# ------------------------------------------------------------

.PHONY: rebuild
rebuild: clean all

# ------------------------------------------------------------
# Show available commands
# ------------------------------------------------------------

.PHONY: help
help:
	@echo.
	@echo Mini Compiler Front-End - Make commands
	@echo.
	@echo   make
	@echo       Build the compiler
	@echo.
	@echo   make run FILE=tests/valid/declaration.mc
	@echo       Build and run a source file
	@echo.
	@echo   make test-valid FILE=tests/valid/declaration.mc
	@echo       Run a valid test case
	@echo.
	@echo   make test-invalid FILE=tests/invalid/syntax_error.mc
	@echo       Run an invalid test case
	@echo.
	@echo   make clean
	@echo       Remove generated files and executable
	@echo.
	@echo   make rebuild
	@echo       Clean and build again
	@echo.

# ============================================================
