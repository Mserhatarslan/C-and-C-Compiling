# C and C++ Compiling

In particular, the Linux process virtual memory map follows the mapping scheme shown in below. 

![image](https://github.com/Mserhatarslan/C-and-C-Compiling/assets/63358327/812521a2-2d04-491e-9f73-d2c07fbb9c09)

Regardless of the peculiarities of a given platform’s process memory division scheme, the following sections of the memory map must be always supported:

•	 Code section carrying the machine code instructions for the CPU to execute (.text section)

•	 Data sections carrying the data on which the CPU will operate. Typically, separate sections are kept for initialized data (.data section), for uninitialized data (.bss section), as well as for constant data (.rdata section)

•	 The heap on which the dynamic memory allocation is run

•	 The stack, which is used to provide independent space for functions

•	 The topmost part belonging to the kernel where (among the other things) the process-specific environment variables are stored

# Compiling 

Once you have written your source code, it is the time to immerse yourself in the process of code building, whose
mandatory first step is the compiling stage. Before going into the intricacies of compiling, a few simple introductory
terms will be presented first.

Introductory Definitions
Compiling in the broad sense can be defined as the process of transforming source code written in one programming
language into another programming language. The following set of introductory facts is important for your overall
understanding of the compilation process:

•	 The process of compiling is performed by the program called the compiler.

•	 The input for the compiler is a translation unit. A typical translation unit is a text file
containing the source code.

•	 A program is typically comprised of many translation units. Even though it is perfectly possible
and legal to keep all the project’s source code in a single file, there are good reasons (explained
in the previous section) of why it is typically not the case.

•	 The output of the compilation is a collection of binary object files, one for each of the input
translation units.


Related Definitions
The following variety of compiler use cases is typically encountered:

•	 Compilation in the strict meaning denotes the process of translating the code of a higher-level
language to the code of a lower-level language (typically, assembler or even machine code)
production files.

•	 If the compilation is performed on one platform (CPU/OS) to produce code to be run on some
other platform (CPU/OS), it is called cross-compilation. The usual practice is to use some of
the desktop OSes (Linux, Windows) to generate the code for embedded or mobile devices.

•	 Decompilation (disassembling) is the process of converting the source code of a lower-level
language to the higher-level language.

•	 Language translation is the process of transforming source code of one programming
language to another programming language of the same level and complexity.

•	 Language rewriting is the process of rewriting the language expressions into a form more
suitable for certain tasks (such as optimization).

•	 In order to become suitable for execution, the object files need to be processed through
another stage of program building called linking.

![image](https://github.com/Mserhatarslan/C-and-C-Compiling/assets/63358327/59dedb2d-dbc9-4f15-b446-b68e1b289bd8)


The Stages of Compiling
The compilation process is not monolithic in nature. In fact, it can be roughly divided into the several stages
(pre-processing, linguistic analysis, assembling, optimization, code emission), the details of which will be
discussed next.

# Preprocessing
The standard first step in processing the source files is running them through the special text processing program
called a preprocessor, which performs one or more of the following actions:

•	 Includes the files containing definitions (include/header files) into the source files, as
specified by the #include keyword.

•	 Converts the values specified by using #define statements into the constants.

•	 Converts the macro definitions into code at the variety of locations in which the macros
are invoked.

•	 Conditionally includes or excludes certain parts of the code, based on the position of #if,
#elif, and #endif directives.
The output of the preprocessor is the C/C++ code in its final shape, which will be passed to the next stage,
syntax analysis.

# Linguistic Analysis
During this stage, the compiler first converts the C/C++ code into a form more suitable for processing (eliminating
comments and unnecessary white spaces, extracting tokens from the text, etc.). Such an optimized and compacted
form of source code is lexically analyzed, with the intention of checking whether the program satisfies the syntax
rules of the programming language in which it was written. If deviations from the syntax rules are detected, errors or
warnings are reported. The errors are sufficient cause for the compilation to be terminated, whereas warnings may or
may not be sufficient, depending on the user’s settings.

More precise insight into this stage of the compilation process reveals three distinct stages:

•	 Lexical analysis, which breaks the source code into non-divisible tokens. The next stage,

•	 Parsing/syntax analysis concatenates the extracted tokens into the chains of tokens,
and verifies that their ordering makes sense from the standpoint of programming language
rules. Finally,

•	 Semantic analysis is run with the intent to discover whether the syntactically correct
statements actually make any sense. For example, a statement that adds two integers and
assigns the result to an object will pass syntax rules, but may not pass semantic check (unless
the object has overridden assignment operator).
During the linguistic analysis stage, the compiler probably more deserves to be called “complainer,” as it tends to
more complain about typos or other errors it encounters than to actually compile the code.


Optimization
Once the first assembler version corresponding to the original source code is created, the optimization effort starts, in
which usage of the registers is minimized. Additionally, the analysis may indicate that certain parts of the code do not
in fact need to be executed, and such parts of the code are eliminated.
