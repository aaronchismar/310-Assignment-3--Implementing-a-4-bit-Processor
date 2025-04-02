# 310-Assignment-3--Implementing-a-4-bit-Processor
data-path-4-bit-processor:
<img width="1421" alt="Screenshot 2025-04-02 at 6 30 38 PM" src="https://github.com/user-attachments/assets/828f055c-d209-4541-a19c-2ab6b694b1cc" />
Design Choices
1. Program Counter (PC)
The PC holds the address of the next instruction to be fetched from Instruction Memory.

It updates on each clock cycle unless controlled by external logic for jumps or branches.

The PC output is fed to the instruction memory module to fetch the next instruction.

2. Instruction Memory and Instruction Registers
The Instruction Memory stores 16-bit instructions at addresses provided by the PC.

The instruction is passed to the Instruction Register's, which temporarily holds it before decoding.

The IRs are controlled by the IR-ctrl signal, allowing it to latch new instructions.

3. Register File
The Register File contains multiple 4-bit registers used to store intermediate values.

Two registers are read simultaneously (Read1 and Read2), based on decoded instruction operands.

The write control signal determines if the ALU result is stored in the destination register.

4. ALU
The ALU takes two register values as inputs and performs operations based on control signals.

The operation is selected using S1, S0.

The output is sent to ALU-out, and the overflow flag is generated if needed.

5. Data Outputs
Several outputs are included for debugging and testing, such as:

PC-Output

data-1-out and data-2-out 

ALU-out 

Control Signals
clk: passes instructions.

IR-ctrl: Enables IR to store new instructions.

Mem-ctrl & Mem-Input: Controls memory operations (read/write).

Register File Controls:

Read1, Read2 (register selection)

Write Enable (determines if ALU output is stored)

ALU Control:

S1, S0 (selects ALU operation)

Cin (carry-in bit for arithmetic operations)



Instruction Memory Module:
<img width="1432" alt="Screenshot 2025-04-02 at 6 43 13 PM" src="https://github.com/user-attachments/assets/1197c5aa-c5dd-45fb-8015-3f7019bdfecf" />
Design Choices
1. Program Counter (PC)
A 4-bit counter that increments every clock cycle, holding the next instruction address.

Controlled with pc-ctrl, which can modify the counter for jumps or conditional branching.

2. Instruction Memory
The instruction memory module stores instructions and outputs them to the Instruction Register (IR).

Controlled with instr-mem-ctrl and instr-mem-input, which regulate memory interactions.

3. Instruction Registers (IRs)
Multiple 4-bit Instruction Registers (IRs) are used to hold different instruction segments.

A decoder extracts control signals from the IR for execution.

4. Logic Gates for Control
The decoder logic processes the opcode and generates necessary control signals.

Two NOT gates, an AND gate, and a driver are used for instruction validation and execution logic.

Control Signals
clk: Controls the timing of instruction execution.

IR-ctrl: Enables the IR to latch the instruction.

pc-ctrl: Modifies the PC for normal execution or jumps.

instr-mem-ctrl & instr-mem-input: Manage instruction fetching.

Decoder Output Signals:

Enable different execution paths based on the opcode.

Determine register and ALU operations.


Instr Mem Module Test (values 1-8 loaded):
<img width="1424" alt="Screenshot 2025-04-02 at 6 50 57 PM" src="https://github.com/user-attachments/assets/8e002766-e19e-47e8-ad1f-150bf203bd32" />


Full Processor Test:
<img width="1069" alt="Screenshot 2025-04-02 at 6 41 13 PM" src="https://github.com/user-attachments/assets/8baf5435-495d-4dff-9006-fe36a89e4510" />

Testing for other files included in processor were completed in previous assignments.
