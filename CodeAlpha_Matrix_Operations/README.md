Matrix Operations System

A modular, menu-driven terminal application written in C to handle basic linear algebra configurations. This utility is engineered with defensive validation checks and organized layout blocks using functions and multi-dimensional arrays.

Core Features:

Matrix Addition: Computes the sum of two matching matrices.

Matrix Multiplication: Multiplies two matrices after confirming valid mathematical dimension limits.

Matrix Transpose: Flips a matrix over its diagonal, switching its row and column indices.

Custom Comma-Separated Input: Prompts the user to input dimensions utilizing a clean rows,columns design layout (e.g., 3,2).

Defensive Programming & Robustness:

Input Buffer Cleaning: If a user inputs a character or invalid symbol during menu selection, the system clears the buffer (while (getchar() != '\n');) to safely prevent unexpected infinite loop failures.

Dimension Validation Guard: During multiplication, the program actively cross-checks the bounds ($c_1 == r_2$). If the columns of Matrix A do not match the rows of Matrix B, it throws a safe error message instead of executing illegal memory calculations.

Buffer Tracking: Implements explicit white-space handling (scanf(" %c", &repeat);) to isolate trailing newline characters from interfering with system loop control.

Modularity Breakdown:

The software utilizes clean prototyping separation to break down computing tasks into independent logic blocks:

inputMatrix(): Iterates through 2D space to record matrix entries cleanly.

displayMatrix(): Prints matrices with tabbed tracking (\t) for structured alignment layouts.

addMatrix(), multiplyMatrix(), transposeMatrix(): Dedicated execution blocks handling math formulas independently.

Compilation & Running:

1.Compile the file:

Bash
gcc -o matrix_ops main.c

2.Execute the binary:

Bash
./matrix_ops

Layout Preview:

===== MAIN MENU: MATRIX OPERATIONS =====
1. Matrix Addition
2. Matrix Multiplication
3. Matrix Transpose
4. Exit
Enter choice: 2

[SUB-MENU] Enter Matrix A rows,cols (e.g., 2,3): 2,2
Enter Matrix B rows,cols (e.g., 3,2): 3,2
Error: Matrix columns of A must match rows of B!

Done! Do you want to perform another operation? (y/n):

License
Distributed under the MIT License.
