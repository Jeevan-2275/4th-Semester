# Computer Organization & Architecture - Unit 2: Basic Computer Organization Deep Notes

> **Target:** 7-Mark Theoretical Questions & MCQs.
> **Focus:** Timing Diagrams, Instruction Cycle, Interrupts, Stack, Formats.
> **Source:** Merged content from Theory & Deep Notes.

---

## Q1: Explain the Instruction Cycle with a state transition diagram (Flowchart). (7 Marks)

**Answer:**
The **Instruction Cycle** is the process by which a computer retrieves a program instruction from memory, determines what actions the instruction describes, and then carries out those actions. It consists of three main phases:
1.  **Fetch:** Read instruction from memory into IR.
2.  **Decode:** Analyze the opcode and determine addressing mode.
3.  **Execute:** Perform the operation (and optional Interrupt).

**Phases & Timing Signals:**
*   **T0:** `AR ← PC` (Place next instruction address in AR).
*   **T1:** `IR ← M[AR], PC ← PC + 1` (Fetch instruction, Increment PC).
*   **T2:** Decode Opcode (IR 12-14), `AR ← IR(0-11)`, `I ← IR(15)`.
*   **T3:**
    *   If **Register/IO** (Opcode=111): Execute immediately.
    *   If **Memory Ref** (Opcode<111):
        *   **I=0 (Direct):** Effective Address is ready.
        *   **I=1 (Indirect):** `AR ← M[AR]` (Fetch effective address).
*   **T4:** Execution Phase starts.

> **Instruction Cycle Flowchart:**
>
> ```mermaid
> graph TD
>     Start([Start]) --> T0[Fetch: AR < - PC]
>     T0 --> T1[IR <- M[AR], PC++]
>     T1 --> T2[Decode Opcode]
>     
>     T2 --> CheckOp{Opcode = 111?}
>     
>     CheckOp -- Yes --> CheckIO{I Bit = 1?}
>     CheckIO -- Yes --> IO[Execute I/O Inst]
>     CheckIO -- No --> Reg[Execute Reg Inst]
>     
>     CheckOp -- No --> CheckInd{I Bit = 1?}
>     CheckInd -- Yes --> Ind[Indirect: AR <- M[AR]]
>     CheckInd -- No --> Exec[Direct: Execute Inst]
>     
>     Ind --> Exec
>     
>     IO --> End([Cycle Complete: SC<-0])
>     Reg --> End
>     Exec --> End
>     End --> Start
> ```

---

## Q2: Draw and Explain the Common Bus System. (7 Marks)

**Answer:**
A **Common Bus System** connects the registers and memory to allow efficient data transfer. It uses **Multiplexers (MUX)** to select which register puts data onto the bus.

| S2 | S1 | S0 | Selected Register |
| :---: | :---: | :---: | :--- |
| 0 | 0 | 0 | **None** |
| 0 | 0 | 1 | **AR** (Address Reg) |
| 0 | 1 | 0 | **PC** (Program Counter) |
| 0 | 1 | 1 | **DR** (Data Reg) |
| 1 | 0 | 0 | **AC** (Accumulator) |
| 1 | 0 | 1 | **IR** (Instruction Reg) |
| 1 | 1 | 1 | **Memory** (Read) |

**Operation:**
1.  **Source:** Control unit sends signals to Select Lines (S0-S2) to choose the *Source*.
2.  **Destination:** Control unit activates the **LOAD** signal of the *Destination* register to receive data.

---

## Q3: What is the Interrupt Cycle? How is it different from a Subroutine Call? (7 Marks)

**Answer:**
An **Interrupt** is a signal from an external device requesting the CPU's attention.

**The Interrupt Cycle (Hardware):**
If `IEN=1` (Interrupt Enable) and a Flag (FGI/FGO) is set:
1.  **Save Return Address:** `M[0] ← PC` (Current PC saved at memory location 0).
2.  **Jump to ISR:** `PC ← 1` (Start Service Routine from address 1).
3.  **Disable Interrupts:** `IEN ← 0` (Prevent nested interrupts).
4.  **Reset Flag:** Clear interrupt flag (R).

| Feature | Subroutine Call (BSA) | Interrupt Cycle |
| :--- | :--- | :--- |
| **Initiator** | Software (Instruction) | Hardware (External Device) |
| **Return Addr** | Saved at Effective Addr | Always saved at **Location 0** |
| **Service Addr** | Specified in Instruction | Always starts at **Location 1** |

---

## Q4: Explain Stack Organization (Register vs Memory Stack). (7 Marks)

**Answer:**
A **Stack** is a LIFO (Last-In First-Out) struture.

**1. Register Stack (CPU Internal):**
*   Organized as a collection of registers.
*   **PUSH:** `SP ← SP + 1`, `M[SP] ← DR`. (Increments SP).
*   **POP:** `DR ← M[SP]`, `SP ← SP - 1`. (Decrements SP).
*   **Status:** Checks for Overflow (Full) and Underflow (Empty).

**2. Memory Stack (RAM Area):**
*   Allocated in a portion of adjacent memory cells.
*   **PUSH:** `SP ← SP - 1`, `M[SP] ← DR`. (Decrements SP - Grows Down).
*   **POP:** `DR ← M[SP]`, `SP ← SP + 1`. (Increments SP).

**Key Difference:** Register stack is faster but limited in size. Memory stack is larger but slower.

---

## Q5: Compare Instruction Formats (3, 2, 1, 0 Address). (7 Marks)

Number of addresses in instruction determines the organization.

| Format | Instruction Example | Operation | Used In |
| :--- | :--- | :--- | :--- |
| **3-Address** | `ADD R1, A, B` | `R1 ← M[A] + M[B]` | General Register Org |
| **2-Address** | `ADD R1, B` | `R1 ← R1 + M[B]` | Commercial PCs |
| **1-Address** | `ADD B` | `AC ← AC + M[B]` | Accumulator Org |
| **0-Address** | `ADD` | `Pop A, B; Push(A+B)` | Stack Org |

---

## Q6: Explain Addressing Modes with examples. (7 Marks)

| Mode | Symbol | Effective Address (EA) | Example |
| :--- | :--- | :--- | :--- |
| **Immediate** | `#OP` | Operand in instruction | `MOV R1, #5` |
| **Direct** | `Addr` | EA = Address Field | `LDA 1000` |
| **Indirect** | `@Addr` | EA = M[Address Field] | `LDA @1000` |
| **Register** | `R` | EA = Register | `ADD R1` |
| **Relative** | `PC+` | EA = PC + Offset | `JMP +10` |
| **Indexed** | `X(R)` | EA = Base + Index Reg | `LD 100(R1)` |

---

## Q7: Hardwired vs Micro-programmed Control Unit. (7 Marks)

| Feature | Hardwired Control | Micro-programmed Control |
| :--- | :--- | :--- |
| **Design** | Fixed Logic Gates/Flip-Flops | Control Memory (ROM) + Microcode |
| **Speed** | **Faster** | **Slower** (Memory access) |
| **Flexibility** | Rigid (Rewiring needed) | **Flexible** (Update firmware) |
| **Architecture** | RISC | CISC |

---

## Q8: RISC vs CISC Architecture. (7 Marks)

| Feature | RISC (Reduced Instruction Set) | CISC (Complex Instruction Set) |
| :--- | :--- | :--- |
| **Instructions** | Simple, Single-cycle, Fixed length | Complex, Multi-cycle, Variable length |
| **Registers** | Large Register File | Few Registers |
| **Logic** | Hardwired Control | Micro-programmed Control |
| **Example** | ARM, MIPS (Mobile) | x86 (Desktop) |

---

## Unit 2 Important MCQs

1.  **Which register holds the address of the next instruction?**
    *   **PC (Program Counter)**
2.  **During Fetch (T0), the transfer is:**
    *   **AR ← PC**
3.  **Return address for Interrupt is stored at:**
    *   **Memory Location 0**
4.  **Addressing mode used for Arrays:**
    *   **Indexed Addressing**
5.  **0-Address instructions operate on:**
    *   **Stack (Top of Stack)**
