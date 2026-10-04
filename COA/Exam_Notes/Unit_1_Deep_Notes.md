# Computer Organization & Architecture - Unit 1: Introduction & Arithmetic Deep Notes

> **Target:** 7-Mark Theoretical Questions & MCQs.
> **Focus:** Diagrams, Key Definitions, Algorithms (Booth's), IEEE 754.

---

## Q1: Explain the Functional Units of a Computer System with a block diagram. (7 Marks)

**Answer:**
A computer consists of five main functional units that communicate to perform tasks.

**1. Input Unit:**
*   Accepts data and instructions from the outside world.
*   Converts human-readable data into machine-readable (binary) form.
*   **Examples:** Keyboard, Mouse, Scanner.

**2. Memory Unit:**
*   Stores data, instructions, and intermediate results.
*   **Primary Memory (RAM):** Volatile, fast, holds currently executing programs.
*   **Secondary Memory (HDD/SSD):** Non-volatile, large storage for long-term data.

**3. Arithmetic & Logic Unit (ALU):**
*   Performs arithmetic operations (Add, Sub, Mul, Div).
*   Performs logical operations (AND, OR, NOT, Compare).
*   Contains the **Accumulator (AC)** for storing results.

**4. Control Unit (CU):**
*   The "Brain" or "Nervous System" of the computer.
*   Fetches instructions from memory, decodes them, and generates timing signals.
*   Controls the flow of data between all other units.

**5. Output Unit:**
*   Sends processed results to the user.
*   Converts machine data into human-readable format.
*   **Examples:** Monitor, Printer.

> **Diagram:**
>
> ```mermaid
> graph TD
>     Input[Input Unit] -->|Data/Instr| Storage
>     
>     subgraph CPU [Central Processing Unit]
>     CU[Control Unit]
>     ALU[Arithmetic & Logic Unit]
>     end
>     
>     subgraph Storage [Storage Unit]
>     Mem[Memory]
>     end
>     
>     Storage -->|Instructions| CU
>     CU -.->|Control Signals| Input
>     CU -.->|Control Signals| ALU
>     CU -.->|Control Signals| Mem
>     CU -.->|Control Signals| Output
>     
>     Mem <-->|Data| ALU
>     
>     Storage -->|Info| Output[Output Unit]
> ```

---

## Q2: Explain IEEE 754 Standard for Floating Point Representation. (7 Marks)

**Answer:**
The IEEE 754 standard defines how floating-point numbers are represented in binary. It has two main formats: **Single Precision (32-bit)** and **Double Precision (64-bit)**.

### 1. Single Precision (32-bit) Format

| Sign (S) | Exponent (E) | Mantissa / Fraction (M) |
| :---: | :---: | :---: |
| 1 Bit | 8 Bits | 23 Bits |

*   **Sign Bit (S):** 0 for Positive (+), 1 for Negative (-).
*   **Exponent (E):** Uses **Bias-127**.
    *   Actual Exponent = E - 127.
    *   E ranges from 0 to 255.
*   **Mantissa (M):** Normalized fraction (1.xxxxx). The leading '1' is implicit (hidden).

**Formula:** $(-1)^S \times (1.M) \times 2^{(E-127)}$

---

### Example: Convert 12.5 to IEEE 754 Single Precision

**Step 1: Convert to Binary**
*   Integer 12 = `1100`
*   Fraction 0.5 = `0.1`
*   Result = `1100.1`

**Step 2: Normalize**
*   Shift decimal point to the left until one non-zero digit remains:
*   `1.1001` × $2^3$
*   Exponent = 3

**Step 3: Calculate Biased Exponent**
*   $E' = E + Bias = 3 + 127 = 130$
*   130 in binary = `10000010`

**Step 4: Determine Mantissa**
*   Drop integer part '1': `1001`
*   Add trailing zeros to make 23 bits: `10010000000000000000000`

**Step 5: Assemble**
*   Sign: 0 (+)
*   Exponent: `10000010`
*   Mantissa: `1001000...`

**Final IEEE 754:** `0 10000010 10010000000000000000000`

---

## Q3: Explain Booth's Multiplication Algorithm with Flowchart. (7 Marks)

**Answer:**
Booth's Algorithm is used for **signed multiplication** (positive and negative numbers) using 2's complement notation. It is more efficient than the standard add-shift method when there are strings of 0s or 1s.

### The Algorithm Mechanics:
*   **Registers:**
    *   **A:** Accumulator (Initially 0)
    *   **Q:** Multiplier
    *   **M:** Multiplicand
    *   **Q₋₁:** Extra bit (Initially 0)
    *   **Count:** Number of bits (n)

### Operation Logic (Check last 2 bits: Q₀ Q₋₁):

| Q₀ | Q₋₁ | Operation | Explanation |
| :---: | :---: | :--- | :--- |
| **0** | **0** | **Shift** | No arithmetic, just Arithmetic Shift Right (ASR). |
| **1** | **1** | **Shift** | No arithmetic, just ASR. |
| **0** | **1** | **Add & Shift** | **A ← A + M**, then ASR. (End of string of 1s) |
| **1** | **0** | **Sub & Shift** | **A ← A - M**, then ASR. (Start of string of 1s) |

> **Flowchart:**
>
> ```mermaid
> graph TD
>     Start([Start]) --> Init[A=0, Q-1=0, Count=n]
>     Init --> Check{Check Q0, Q-1}
>     
>     Check -- "10" --> Sub[A = A - M]
>     Check -- "01" --> Add[A = A + M]
>     Check -- "00 or 11" --> Shift[ASR A, Q, Q-1]
>     
>     Sub --> Shift
>     Add --> Shift
>     
>     Shift --> Dec[Count = Count - 1]
>     Dec --> Zero{Count = 0?}
>     
>     Zero -- No --> Check
>     Zero -- Yes --> End([End])
> ```

---

## Q4: Explain Restoring vs Non-Restoring Division. (7 Marks)

### 1. Restoring Division
*   **Principle:** Subtract Divisor (B) from partial remainder (A).
*   If result is **Negative** (Borrow), strictly **RESTORE** (add B back) and set Quotient bit = 0.
*   If result is **Positive**, set Quotient bit = 1.
*   **Steps:**
    1.  Shift Left (A, Q).
    2.  Subtract (A ← A - B).
    3.  Check sign of A.
    4.  If A < 0: Restore (A ← A + B), Q₀ = 0.
    5.  If A ≥ 0: No restore, Q₀ = 1.

### 2. Non-Restoring Division
*   **Principle:** Do not restore immediately if negative. Instead, Add B in the next step.
*   **Algorithm:**
    *   If sign of A is **Positive**:
        1.  Shift Left.
        2.  Subtract B.
    *   If sign of A is **Negative**:
        1.  Shift Left.
        2.  **ADD** B.
    *   **Final Correction:** If final remainder is negative, Add B to restore it.

**Comparison:**
*   Non-restoring is generally faster as it avoids the extra addition step inside the loop in negative cases.

---

## Q5: Explain Bus Types and Three-State Bus Buffers. (7 Marks)

**Answer:**
A **Bus** is a shared communication path.
1.  **Data Bus:** Bidirectional, carries data (16-bit or 32-bit).
2.  **Address Bus:** Unidirectional (CPU -> Memory), specifies location.
3.  **Control Bus:** Carries timing and control signals (Read/Write).

### Three-State (Tri-State) Buffer
A logic circuit used to control access to a common bus. It has three states:
1.  **Logic 0** (Low)
2.  **Logic 1** (High)
3.  **High Impedance (Hi-Z)**: Disconnected state (Open circuit).

> **Operation:**
> *   It has a **Control Input (C)**.
> *   If **C = 1**: Output = Input (Normal operation).
> *   If **C = 0**: Output = Hi-Z (Electrically disconnected).
>
> This allows multiple registers to be connected to the *same* wire without short-circuiting, as only one is enabled (C=1) at a time.

---

## Unit 1 Important MCQs

1.  **Which register holds the address of the next instruction?**
    *   a) IR
    *   b) **PC (Program Counter)**
    *   c) AC
    *   d) DR
    *   *Reason: PC specifically increments to point to the next instruction code.*

2.  **In IEEE 754 single precision, the exponent bias is:**
    *   a) 128
    *   b) **127**
    *   c) 255
    *   d) 1023
    *   *Reason: Bias = 2^(k-1) - 1. For 8 bits, 2^7 - 1 = 127.*

3.  **Booth's Algorithm is used for:**
    *   a) Unsigned multiplication
    *   b) **Signed multiplication**
    *   c) Floating point addition
    *   d) Division
    *   *Reason: It handles negative numbers in 2's complement efficiently.*

4.  **The High-Impedance state behaves like:**
    *   a) Logic 0
    *   b) Logic 1
    *   c) **Open Circuit**
    *   d) Short Circuit

5.  **Which unit decodes instructions?**
    *   a) ALU
    *   b) Memory
    *   c) **Control Unit**
    *   d) Input Unit
