Student Management System

A robust, terminal-based CRUD (Create, Read, Update, Delete) application written in **C** to handle student data management. This system uses custom memory structures combined with persistent binary storage to provide data lifecycle tracking without a traditional database.

Core Features
* **Create (Add Records):** Stores student data with integrated real-time ID unique validation checks.
* **Read (Search & Display):** Instantly parses binary logs to locate a specific record or display all active logs in an aligned format.
* **Update (In-Place Modifications):** Locates records using targeted byte offset jumps and overrides active entries.
* **Delete (Garbage Cleaning):** Filters and rewrites non-deleted data logs to a temporary container before safely cleaning and restructuring the master log file.
* **View Sorted (Memory Buffering):** Calculates file allocation limits dynamically, copies raw data streams into a runtime buffer array, and runs a descending Bubble Sort algorithm by GPA.

 Defensive Programming & Data Safety:
 
Duplicate ID Prevention:The engine calls `idExists()` to cross-examine files before writing a fresh entry, preventing structural file anomalies and primary key collisions.
Byte Offset Integrity Guard: Uses dynamic stream modifications via `fseek(fp, -sizeof(Student), SEEK_CUR);` to ensure updating processes alter exactly the current structure segment without sliding data corruption down the file stream.
Dynamic Memory Allocations:During sorting processes, raw byte calculations (`ftell`) determine runtime sizes safely, mapping memory cleanly with `malloc()` and resolving leakage with proper `free()` callbacks.
Menu Control Sanitation: Intercepts wrong data types using an initial `scanf` state valuation, clearing memory buffers dynamically (`while(getchar() != '\n');`) to safely shut down potential terminal infinite loops.

 Data Infrastructure & Prototyping
The framework leverages a structured user definition tracking a unique layout format:
```c
typedef struct {
    int id;
    char name[50];
    float gpa;
} Student;

```
Data properties handle interactions consistently using decoupled process execution:
addStudent() & displayAll(): Manage append (ab) and read (rb) file locks safely.
updateStudent(): Opens a mixed binary pipeline (rb+) to read and execute targeted updates simultaneously.
deleteStudent(): Isolates structural streams, relying on file drops (remove) and system renaming blocks (rename).

Compilation & Running:
Compile the source code:
Bash
```c
gcc -o student_system main.c
```

Execute the binary:
Bash
```c
./student_system
```

Layout Preview:

Plaintext

--- STUDENT MANAGEMENT SYSTEM ---
1. Add Student (Validated)
2. Display All Records
3. Search by ID
4. Update Record
5. Delete Record
6. View Sorted (by GPA)
7. Exit
Selection: 1

Enter ID: 101
Error: ID 101 already exists!

 Planned Upgrades & Future Roadmap:
 
 To transition this CLI utility into an enterprise portfolio project, the following improvements are targeted:

[ ] Range Validation Filters: Introduce input range checks to reject illegal GPA scores (e.g., bounds beyond $0.00 - 4.00$) and truncate overly long name entries.

[ ] Advanced Sorting Architectures: Upgrade memory manipulation constraints from a standard Bubble Sort to high-speed sorting utilities like qsort() or Merge Sort structures.

[ ] Comprehensive Multi-Criteria Search: Extend simple target scans to handle complex name variations or dynamic GPA grouping ranges.

[ ] Data Export Interface: Incorporate formatting outputs to save runtime structures out of raw binary files (students.dat) and cleanly map them into comma-separated text sheets (students.csv).
 
 License Distributed under the MIT License.
