# WLP4Compiler

## Introduction to WLP4

WLP4 is a subset of C++ and stands for “Waterloo, Language, Plus, Pointers, Plus, Procedures.” This language includes functions, integers, pointers, arrays, conditional statements, and while loops, and is taught within the "Foundations of Sequential Programs" course at the University of Waterloo.


For more information on WLP4, check out:
- [WLP4 Programming Language Tutorial](https://www.student.cs.uwaterloo.ca/~cs241/wlp4/WLP4tutorial.html)
- [WLP4 Programming Language Specification](https://www.student.cs.uwaterloo.ca/~cs241/wlp4/WLP4.html)

## WLP4 Compiler

This WLP4 Compiler implements scanning, parsing, context-sensitive analysis, and code generation to translate WLP4 code into MIPS assembly language. The project involves building a compiler that can convert WLP4 code into MIPS assembly. The source code for this project is not public, but feel free to email me at nnefsky@uwaterloo.ca for access.

### Compiler Processes:

#### 1) Scanning
First, the compiler tokenizes inputted WLP4 code. This process uses a Simplified Maximal Munch Algorithm, which consumes input until it encounters ambiguity, at which point it checks if the input is in an accepting state to produce a token. The scanning uses a Nondeterministic Finite Automaton (NFA), and the lexical syntax can be found <a href="https://student.cs.uwaterloo.ca/~cs241/wlp4/WLP4.html">here</a>.
<!-- A3 -->

#### 2) Parsing

Parsing is implemented using a Pushdown Automaton to check if the code conforms to a <a href="https://en.wikipedia.org/wiki/Context-free_grammar">Context Free Grammar (CFG)</a>. The CFG for WLP4 is available <a href="https://student.cs.uwaterloo.ca/~cs241/wlp4/WLP4.html">here</a>. The result is a derivation of the input string that defines a parse tree representing the program's structure. This compiler uses Bottom-Up Parsing, specifically with an <a href="https://en.wikipedia.org/wiki/Simple_LR_parser">SLR(1)</a> parser.
<!-- A5 -->

#### 3) Context-Sensitive Analysis
Then the compiler verifies whether the code meets WLP4's context-sensitive rules. This step involves analyzing the parse tree from the parsing stage to check rule compliance. Examples of these rules include:
- Ensuring no duplicate declarations within the same scope.
- Ensuring variables are declared before use.
<!-- A6 -->

#### 4) Code Generation
The final step is code generation, where WLP4 source code is translated into MIPS assembly language. Basic features supported include code generation for the main procedure, integer variables and constants, declarations, assignments, arithmetic, control flow, and printing. Additional support is also provided for pointers, procedures, and dynamic memory allocation.
<!-- A7/A8 -->
