# llvm-obfuscator
LLVM-based code obfuscation pass implemented in C++ using LLVM/Clang and CMake.
🔐 LLVM-Based Intelligent Code Obfuscator

An advanced compiler-level code obfuscation framework designed to protect C/C++ programs against reverse engineering, static analysis, and unauthorized code inspection. The system operates at the LLVM Intermediate Representation (IR) level, transforming the structure and representation of programs while preserving their original functionality.

The project combines LLVM compiler technology, multiple code-obfuscation techniques, machine learning, and program-complexity analysis to create an intelligent and configurable software protection pipeline.

Unlike traditional obfuscators that apply the same transformations to every program, this framework analyzes the characteristics of the input program and uses a Machine Learning-based strategy selection mechanism to determine suitable obfuscation techniques.

🎯 Project Objective

The primary objective of this project is to develop a compiler-based software protection system capable of transforming readable and analyzable source programs into functionally equivalent but significantly harder-to-understand representations.

The framework aims to:

🛡️ Protect software against reverse engineering
🔍 Increase the difficulty of static code analysis
🧩 Transform program control flow and instruction patterns
🔐 Protect sensitive string information
🤖 Automatically select suitable obfuscation strategies using Machine Learning
📊 Measure the effectiveness and complexity of generated obfuscated code
⚙️ Maintain the original functionality of the protected program
✨ Project Highlights
🛡️ LLVM IR-Based Software Protection
🤖 Machine Learning-Driven Obfuscation Strategy Selection
🌲 Random Forest Classification Model
🔀 Control Flow Flattening
🔄 Instruction Substitution
🔐 XOR-Based String Encryption
📊 Automated Obfuscation Metrics Generation
📈 Complexity and Entropy Analysis
🧩 Modular and Extensible Architecture
🧪 Support for C/C++ Programs through LLVM/Clang
📚 Research-Oriented Implementation
🏗️ Architecture / Workflow
                 C / C++ Source Program
                          │
                          ▼
                    LLVM / Clang
                          │
                          ▼
                 LLVM Intermediate
                  Representation (.ll)
                          │
                          ▼
                    IR Parser
                          │
                          ▼
                Feature Extraction
                          │
             ┌────────────┴────────────┐
             │                         │
             ▼                         ▼
      Program Features          Complexity Analysis
             │                         │
             └────────────┬────────────┘
                          ▼
              Machine Learning Model
                 (Random Forest)
                          │
                          ▼
              Obfuscation Strategy
                    Selection
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
   Control Flow     Instruction      String
    Flattening      Substitution    Encryption
          │               │               │
          └───────────────┼───────────────┘
                          ▼
                 Obfuscated LLVM IR
                          │
                          ▼
                    LLVM / Clang
                          │
                          ▼
                Protected Executable
                          │
                          ▼
              Metrics & Evaluation
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
       Complexity Analysis      Entropy Analysis
🤖 Machine Learning Component

A major feature of the project is the integration of Machine Learning into the obfuscation pipeline.

The framework extracts characteristics from the input LLVM IR, such as:

Number of instructions
Number of basic blocks
Control-flow characteristics
Function complexity
Instruction distribution
String-related information
Program structure

These features are provided to a Random Forest classifier, which predicts an appropriate obfuscation strategy.

LLVM IR
   │
   ▼
Feature Extraction
   │
   ├── Instruction Count
   ├── Basic Block Count
   ├── Function Characteristics
   ├── Control Flow Features
   └── Program Complexity
            │
            ▼
      Random Forest
        Classifier
            │
            ▼
   Strategy Selection
            │
      ┌─────┼─────┐
      ▼     ▼     ▼
     CFF    IS    SE

This approach makes the system more adaptive compared with a fixed obfuscation pipeline.

🔀 Obfuscation Techniques
1. 🔀 Control Flow Flattening

Control Flow Flattening transforms the original control-flow structure of a program into a more complex dispatcher-based structure.

Instead of maintaining a straightforward execution path:

Block A → Block B → Block C → Block D

the obfuscated program can be transformed into:

             Dispatcher
              /  |  \
             /   |   \
           B1    B2    B3
             \   |   /
              \  |  /
             Dispatcher

This makes the original logical execution flow substantially harder to understand through static analysis.

2. 🔄 Instruction Substitution

Instruction substitution replaces selected instructions or instruction patterns with semantically equivalent alternatives.

For example:

Original:
x = a + b

may be represented using an alternative sequence of operations that produces the same result.

The objective is to make recognizable instruction patterns less obvious while maintaining program behavior.

3. 🔐 String Encryption

The framework provides XOR-based string encryption to protect sensitive string literals.

Instead of storing:

"Sensitive Information"

directly in the binary, the string can be transformed into an encoded representation and reconstructed during execution.

This helps make sensitive textual information less immediately visible during binary inspection.

📊 Obfuscation Metrics

The framework also provides an evaluation component for measuring the impact of obfuscation.

Important metrics include:

📈 Complexity

Measures how much the structural complexity of the program changes after obfuscation.

📊 Instruction Growth

Compares the number of instructions before and after applying obfuscation.

🧩 Basic Block Growth

Measures changes in the number of basic blocks and control-flow structures.

🔢 Entropy

Analyzes the distribution of information within the generated representation and can help evaluate changes caused by transformations such as string encryption.

⚡ Performance Impact

The framework can be used to compare the execution characteristics of the original and obfuscated programs.

🧪 Example Workflow

A typical execution flow is:

Input C/C++ Program
        │
        ▼
   LLVM / Clang
        │
        ▼
     LLVM IR
        │
        ▼
 Feature Extraction
        │
        ▼
 ML-Based Strategy Selection
        │
        ▼
   Obfuscation Passes
        │
        ├── Control Flow Flattening
        ├── Instruction Substitution
        └── String Encryption
        │
        ▼
 Obfuscated LLVM IR
        │
        ▼
   Compilation
        │
        ▼
 Protected Executable
        │
        ▼
 Metrics & Analysis
🛠️ Technology Stack
Component	Technology
Programming Language	C++, Python
Compiler Framework	LLVM
Compiler Frontend	Clang
Intermediate Representation	LLVM IR
Machine Learning	Scikit-learn
ML Algorithm	Random Forest
Data Processing	NumPy, Pandas
Build System	CMake
Analysis	LLVM IR Analysis
Version Control	Git / GitHub
📁 Project Structure
llvm-obfuscator/
│
├── ml/
│   ├── feature_extractor.py
│   └── model.py
│
├── obfuscation/
│   ├── control_flow.py
│   ├── instruction_sub.py
│   └── string_encrypt.py
│
├── parser/
│   └── ir_parser.py
│
├── report/
│   └── metrics.py
│
├── samples/
│   ├── arithmetic.ll
│   ├── bubble_sort.c
│   ├── bubble_sort.ll
│   ├── c_program.c
│   └── ...
│
├── main.py
├── python
└── README.md
🔬 Research Perspective

This project explores the intersection of compiler design, cybersecurity, program analysis, and machine learning.

By operating at the LLVM IR level, the framework provides a flexible environment for experimenting with different software protection techniques. The integration of machine learning introduces an adaptive component that can analyze program characteristics and assist in selecting appropriate transformations.

The project can serve as a foundation for further research into:

🧠 Intelligent code obfuscation
🔐 Software protection
🛡️ Anti-reverse-engineering techniques
🤖 ML-assisted compiler transformations
📊 Quantitative obfuscation evaluation
🔬 Automated obfuscation strategy selection
