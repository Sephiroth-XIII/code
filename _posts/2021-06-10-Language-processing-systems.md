---
title: "Language-processing Systems"
layout: post
---

There are a lot of programming lanugages that exist today for writing your
programs in, and different language-processing systems to run these programs, 
by making the machines on which they run understand these programs as step of 
instructions. Although compilers and interpreters have the exact same end 
goal - help us run our programs, they do take different paths for accomplishing 
this goal.

Compilers are translators. They take a program written by you in language `X`, 
& translate it into an equivalent program in language `Y`. When this target 
language `Y` is machine-lanugage, you are able to run the target program as an 
executable. On the way to creating the target program, compilers also perform a
very important task of reporting errors that you might have comitted in your 
source program. Unlike compilers, interpreters don't translate the program 
before executing them. They just execute the source program 
statement-by-statement. Interpreted programs trade better error-diagnostics for
faster execution speeds of compiled programs.

There also exist hybrid language-processors like Java's. Java programs are
compiled into an intermediate form called bytecodes, which can then be 
interpreted on same or a different machine over the network by a virtual 
machine (JVM). In some cases a just-in-time compiler can be used to translate
the intermediate bytecode form to machine-language before executing the 
program, in order to achieve faster execution speeds.


There are other programs required to create an executable target along with 
compiler:

- **Preprocessor**: Collects code that is divided into multiple modules and 
    files, and expands macros.
- **Compiler**: Compiler takes the preprocessed code and translates it into
    an equivalent program in assembly language. Compared to machine code,
    assembly is easy to generate & debug.
- **Assembler**: Assembler translates the assembly language program into
    relocatable machine code. This code is called relocatable code, cause it's
    execution address is not decided yet.
- **Linker**: The linker combines multiple relocatable object files with the
    required library files into code that can acutally run on the machine. It
    resolves the symbolic refrences in the relocatable codewith actual usable 
    addresses in memory.
- **Loader**: Loader loads all these executable object files into memory for
    execution.

We can see the intermediate outputs of the above programs in gcc easily. Write
a simple `Hello, World!` program in c, and instead of runing 
`gcc hello.c -o hello` which generates an executable target, run
`gcc --save-temps hello.c -o hello`

| file    | description                       |
|---------|-----------------------------------|
| hello.i | Preprocessor output               |
| hello.s | Compiler output (assembly code)   |
| hello.o | Assembler output                  |
| hello   | Linker output (executable target) |

This post covers the overview of language-processing systems, next we'll dive
further into `Structure of a Compiler`. 

*P.S. I am learning Compilers from the book "Compilers: Principles, 
Techniques, and Tools" AKA "The Dragon Book".*

