# Bank Account Management System

A secure, transactional command-line financial simulator written in **C**. This application implements multi-account balance processing, basic authorization screening, and persistent binary record streaming to handle account lifecycles safely without a relational database engine.

##  Core Features
* **Open Account (Creation):** Registers user details with real-time uniqueness validation constraints and auto-initializes the balance safely to `$0.00`.
* **Deposit & Withdraw:** Mutates transaction values on matching targets, checking boundaries like overdraft balances and pin access parameters.
* **Account-to-Account Transfers:** Synchronizes separate file positions simultaneously, processing safe deductions and deposits across transactional nodes.
* **Balance Inquiry:** Fast binary parsing and verification checks to provide real-time reporting on individual data fields.

##  Defensive Programming & Data Safety
* **Upgraded Memory Ranges:** Account trackers utilize large data constraints (`long double` or `long long`) to handle 10-digit account numbers securely without data wrapping or truncation.
* **PIN Authorization Barriers:** Security methods protect withdrawal, balance screening, and transfer pipelines by comparing entries against structural constants before permitting memory operations.
* **Overdraft Protection Guard:** The withdrawal sequence verifies bounds checking ($amount > balance$) before initiating offset writes, stopping balances from slipping into invalid negative values.
* **Dual-Target Stream Positioning:** The transaction algorithm uses file tracking mechanisms (`ftell` and `fseek`) to isolate explicit byte points (`SEEK_SET`). This updates internal structural contents directly without corrupting adjacent database slots.
* **Input Buffer Sanitation:** A custom utility function (`clearBuffer()`) flushes trailing newline tags and clears invalid text loops securely when invalid selection data types are parsed.

## Data Infrastructure & Prototyping
The architecture relies on an aligned user definition block mapped out in a clean storage layout:

```c
typedef struct {
    long long acc_no; // Holds 10-digit numeric assignments
    char name[50];    // Space for strings containing spaces
    int pin;          // Secret 4-digit verification access code
    float balance;    // Transaction record accounting float
} Account;
```
Operational methods organize actions cleanly via segregated stream access operations:
* `createAccount()`: Leverages binary append protocols (`ab`) to securely expand the record array.
* `deposit()` & `withdraw()`: Opens an updating binary pipeline (`rb+`) to alter data limits via relative offsets (`SEEK_CUR`).
* `transferMoney()`: Tracks and buffers two detached file locations smoothly, executing pinpoint read/write mutations.

##  Compilation & Running

1. **Compile the source code:**
   ```bash
   gcc -o bank_system main.c
   ```
2. **Execute the binary utility:**
   ```bash
   ./bank_system
   ```

## 🖥️ Layout Preview
```text
==============================
     CITY BANK SYSTEM     
==============================
1. Open Account
2. Deposit
3. Withdraw
4. Transfer
5. Balance Inquiry
6. Exit
Select Option: 3

Enter Account Number: 1000200030
Enter PIN: 1234
Enter Amount: 500.00
Insufficient funds!
```

##  Planned Upgrades & Future Roadmap
To further elevate this CLI banking utility into an enterprise-ready portfolio program, the following enhancements are scheduled:

- [ ] **Multi-Tier Password Encryption:** Upgrade flat 4-digit integer PIN fields by wrapping data passes in hashing algorithms (e.g., SHA-256) for optimal protection.
- [ ] **Dynamic Audit Logs:** Incorporate an explicit operational tracker that automatically appends chronological transaction data into a readable text history report (`ledger.txt`).
- [ ] **Transaction Rollback Routines:** Enhance the payment transfer system by implementing fallback checks that completely undo changes to the sender's account if the recipient's file update fails.
- [ ] **Automated Bank Code (Routing) Tracking:** Add account number structure checking routines to separate routing identifiers from baseline account tags via complex string validation modules.

##  License
Distributed under the MIT License.
