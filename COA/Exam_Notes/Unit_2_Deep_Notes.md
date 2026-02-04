# Computer Organization & Architecture - Unit 2: Basic Computer Organization Deep Notes

> **Target:** 7-Mark Theoretical Questions & MCQs.
> **Focus:** Timing Diagrams, Instruction Cycle, Interrupts, Addressing Modes.

---

## Q1: Explain the Instruction Cycle with a state transition diagram (Flowchart). (7 Marks)

**Answer:**
The **Instruction Cycle** is the process by which a computer retrieves a program instruction from memory, determines what actions the instruction describes, and then carries out those actions. It consists of three main phases:
1.  **Fetch:** Read instruction from memory into IR.
2.  **Decode:** Analyze the opcode and determine addressing mode.
3.  **Execute:** Perform the operation (and optional Interrupt).

**Phases & Timing Signals:**
*   **T0:** AR ← PC (Place address of next instruction in AR).
*   **T1:** IR ← M[AR], PC ← PC + 1 (Fetch instruction, Increment PC).
*   **T2:** Decode Opcode (IR 12-14), AR ← IR(0-11), I ← IR(15).
*   **T3:**
    *   If **Register/IO** (Opcode=111): Execute immediately.
    *   If **Memory Ref** (Opcode<111):
        *   **I=0 (Direct):** Nothing (Effective Address is ready).
        *   **I=1 (Indirect):** AR ← M[AR] (Fetch effective address).
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
>     IO --> End([Cycle Complte: SC<-0])
>     Reg --> End
>     Exec --> End
>     End --> Start
> ```

---

## Q2: Draw and Explain the Common Bus System. (7 Marks)

**Answer:**
A **Common Bus System** connects the registers and memory to allow efficient data transfer. It uses **Multiplexers (MUX)** to select which register puts data onto the bus.

**Selection Logic (S2, S1, S0):**
The selection lines determine which register's data is placed on the bus.

| S2 | S1 | S0 | Selected Register | description |
| :---: | :---: | :---: | :---: | :--- |
| 0 | 0 | 0 | **None** | No Output |
| 0 | 0 | 1 | **AR** | Address Register |
| 0 | 1 | 0 | **PC** | Program Counter |
| 0 | 1 | 1 | **DR** | Data Register |
| 1 | 0 | 0 | **AC** | Accumulator |
| 1 | 0 | 1 | **IR** | Instruction Register |
| 1 | 1 | 0 | **TR** | Temp Register |
| 1 | 1 | 1 | **Memory** | Read from RAM |

**Operation:**
1.  **Source:** Control unit sends signals to Select Lines (S0-S2) to choose the *Source* register.
2.  **Destination:** Control unit activates the **LOAD** signal of the *Destination* register to receive data from the bus.

---

## Q3: What is the Interrupt Cycle? How is it different from a Subroutine Call? (7 Marks)

**Answer:**
An **Interrupt** is a signal from an external device requesting the CPU's attention.

**The Interrupt Cycle (Hardware):**
If `IEN=1` (Interrupt Enable) and a Flag (FGI/FGO) is set:
1.  **Save Return Address:** The current PC (return address) is stored at memory location **0**.
    *   `M[0] ← PC`
2.  **Jump to ISR:** Program Counter is set to address **1**.
    *   `PC ← 1`
3.  **Disable Interrupts:** `IEN ← 0` (to prevent nested interrupts initially).
4.  **Reset Flag:** The interrupt flag (R) is cleared.

**Difference: Interrupt vs Subroutine Call**

| Feature | Subroutine Call (BSA) | Interrupt Request |
| :--- | :--- | :--- |
| **Initiator** | Software (Program instruction) | Hardware (External device) |
| **When?** | At specific point in code | Asynchronous (Any time) |
| **Return Addr** | Saved at Effective Address | Always saved at **Location 0** |
| **Service Addr** | Specified in instruction | Always starts at **Location 1** |
| **Purpose** | Code reuse/Modularity | Handle I/O, Errors |

---

## Q4: Explain Addressing Modes with examples. (7 Marks)

**Answer:**
Addressing modes specify how the operand is chosen during program execution.

| Mode | Symbol | Effective Address (EA) Calculations | Example |
| :--- | :--- | :--- | :--- |
| **Immediate** | `#OP` | Operand is in instruction | `ADD #5` (Add 5 to AC) |
| **Direct** | `Addr` | EA = Address Field | `ADD 500` (Add M[500] to AC) |
| **Indirect** | `@Addr` | EA = M[Address Field] | `ADD @500` (Pointer at 500) |
| **Register** | `R` | EA = Register | `ADD R1` (Add R1 to AC) |
| **Relative** | `PC+` | EA = PC + Offset | `JMP +10` (Jump 10 forward) |
| **Indexed** | `X(R)` | EA = Base Addr + Index Reg | `LOAD 100(R1)` (Arrays) |

**Importance:**
*   **Immediate:** Fast constants.
*   **Indirect:** Pointers and passing parameters.
*   **Relative:** Relocatable code and branching (loops).
*   **Indexed:** Iterating through Arrays.

---

## Q2: Hardwired vs Micro-programmed Control Unit. (7 Marks)

| Feature | Hardwired Control | Micro-programmed Control |
| :--- | :--- | :--- |
| **Design** | Uses Gates, Flip-flops, Decoders | Uses Control Memory (ROM) |
| **Speed** | **Faster** (Combinational logic) | **Slower** (Memory access needed) |
| **Flexibility** | Rigid (Hard to modify) | **Flexible** (Just update ROM code) |
| **Complexity** | Complex wiring for large sets | Structured and organized |
| **Cost** | More expensive implementation | Cheaper for complex sets (CISC) |
| **Usage** | RISC Processors | CISC Processors |

---

## Unit 2 Important MCQs

1.  **Which register selects the memory address?**
    *   a) IR
    *   b) **AR (Address Register)**
    *   c) PC
    *   d) DR
    *   *Reason: AR connects directly to the address bus of the memory.*

2.  **During the Fetch cycle (T0), the operation is:**
    *   a) IR ← M[AR]
    *   b) **AR ← PC**
    *   c) PC ← PC + 1
    *   d) AR ← 0
    *   *Reason: First step is always moving the Program Counter to Address Register.*

3.  **The return address for an interrupt is stored at:**
    *   a) Stack
    *   b) **Memory Location 0**
    *   c) Memory Location 1
    *   d) Variable
    *   *Reason: In Basic Computer, hardware automatically saves PC to address 0.*

4.  **Which addressing mode is best for Arrays?**
    *   a) Direct
    *   b) Relative
    *   c) **Indexed Addressing**
    *   d) Register Indirect
    *   *Reason: Index register makes iterating through elements easy.*

5.  **One-Address instructions use which register implicitly?**
    *   a) PC
    *   b) **AC (Accumulator)**
    *   c) IR
    *   d) DR
    *   *Note: e.g., `ADD X` means `AC = AC + M[X]`.*
