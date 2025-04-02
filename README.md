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

Data Path Test:
<img width="1069" alt="Screenshot 2025-04-02 at 6 41 13 PM" src="https://github.com/user-attachments/assets/8baf5435-495d-4dff-9006-fe36a89e4510" />

