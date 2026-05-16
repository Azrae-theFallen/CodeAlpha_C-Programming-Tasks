## Arithmetic Interface System

A robust, menu-driven command-line calculator written in C. This project was developed as part of the CodeAlpha C Programming Internship. It focuses on mastering core fundamentals like loops, conditional logic, and error-handling strategies.  

## Key Features:

Four-Function Arithmetic: Handles Addition, Subtraction, Multiplication, and Division. 

## Defensive Programming:

* Division Guard: Includes a "Critical Error" check to prevent division by zero, which would otherwise crash the program.

Input Sanitization: Uses buffer clearing logic (while (getchar() != '\n');) to handle cases where a user accidentally enters a letter instead of a number.

Interactive Flow Control: Features a custom "Flow Control Menu" that allows the user to either continue to a new calculation or exit the process entirely.

Precision Output: All results are formatted to two decimal places for professional readability.🛠️ Built WithLanguage: CStandard Libraries: stdio.h (Input/Output), ctype.h (Character manipulation for flow control).

## How to Use:

1.Compile the code:

Bash
```c
gcc -o calculator main.c
```
2.Run the program:

Bash
```c
./calculator
```
3.Operation:
```text
==================================
   SYSTEM: ARITHMETIC INTERFACE   
==================================
 1. [ADD]      Addition
 2. [SUB]      Subtraction
 3. [MUL]      Multiplication
 4. [DIV]      Division
 5. [EXIT]     Close Program
----------------------------------
Select Operation (1-5): 1

Enter first value: 4
Enter second value: 5

--- CALCULATION REPORT ---
Result: 4.00 + 5.00 = 9.00
----------------------------------
Choose: [C]ontinue to Menu or [E]xit Program? E

[SYSTEM] Process Terminated. Goodbye!
```
## Proposed Future Improvements:

1.To scale this utility into a more advanced tool, the following upgrades are planned:

2.Visual Hierarchy: Implementing ANSI color codes (e.g., Red for errors, Green for successful results) to improve the terminal UI.

3.Chain Calculations: Adding a "Running Total" or Accumulator mode so the result of one calculation can be used immediately in the next.

4.Complex Expressions: Moving from simple two-number inputs to full expression parsing (e.g., (10 + 5) * 2) using BODMAS/PEMDAS logic.

5.Scientific Module: Integrating math.h to support advanced operations like square roots, powers, and trigonometry.

6.History Logging: Automatically saving all session calculations to a history.txt file using C file handling.

## License
Distributed under the MIT License. 
