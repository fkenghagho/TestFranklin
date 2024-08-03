# B Language Compiler

This project is about building a compiler for the B language, implemented in Python, which translates .b source code into x86_64 assembly code under Linux. However, note that though the actual execution of the generated .s code should be executed on x86_64 linux platforms, the genration of the .s can take place on any platform. The compiler consists of three main parts: the Front End, the Middle End, and the Back End. Before we actually jump into the code presentation, let present first the structure of the project folder as illustrated by the Figure 1 below.

## Project Structure

- **compiler.py**: module containg the main class of the compiler orchestrating the different compilation stages.
- **front_end.py**: module containing the FrontEnd class for lexical and syntactical analysis and abstract syntax tree construction.
- **middle_end.py**: module containing the MiddleEnd class for semantic analysis, optimization, and intermediate representation generation.
- **back_end.py**: module for generating the final .s assembly code.
- **utils.py**: Utility file containing helper classes and functions like file management and data structures.
- **b_grammar.gr**: File containing a Turing-complete grammar for the b language
- **requirements**: File containing the python dependency requirements
- **tests**: Folder containing the tests

<p align=center>
<img src="imgs/ProjectFolder.png"></img>
</p>

This project was developed in Python by Volgan and Sylvain.

## Front End

The Front End handles the initial phase of compilation:

- **Lexical Analysis**: Converts the source code into a stream of tokens.
- **Syntactical Analysis**: Checks that the tokens follow the defined grammar.
- **Abstract Syntax Tree**: Constructs a tree representation of the source code conforming to the grammar.
- **Symbol Table**: Generates a symbol table to track variables, functions, and other entities.

This project uses the Lark library for parsing in the Front End.

## Middle End

The Middle End performs semantic analysis and optimization:

- **Semantic Analysis**: Ensures semantic correctness of the program.
- **Optimizations**: Improves the code by eliminating dead code, propagating constants, etc.
- **Intermediate Representation**: Produces an optimized representation of the code.

## Back End

The Back End generates the final assembly code:

- **Code Generation**: Converts the intermediate representation into x86_64 assembly code.
- **Output**: Writes the assembly code to an .s file ready to be assembled and executed.

## Usage

To compile a .b source file, use the Compiler class:
```console
username@hostname:~$ ./path_to_project_foler/compiler.py
```

```python
from Compiler import Compiler

compiler = Compiler(grammar_file='b_grammar.gr')
input_source_file = "path/to/your/file.b"
compiler.run(input_source_file=input_source_file)


