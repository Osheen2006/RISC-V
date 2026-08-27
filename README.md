# RISC-V
Designed and implemented a **single-cycle RISC-V processor in Verilog**, integrating the ALU, control unit, register file, and memory modules. Synthesized and deployed the design on a **Xilinx Spartan-7 FPGA**, validating its functionality through hardware implementation.


RISC-V Processor Design and FPGA Implementation

Overview

This project implements a 32-bit single-cycle RISC-V processor in
Verilog HDL. The processor integrates the complete basic datapath
required for instruction execution, including the Program Counter
(PC), Instruction Memory, Control Unit, Register File, Immediate
Generator, ALU, ALU Control, Data Memory, and branch logic.

The design was synthesized and implemented on a Xilinx Spartan-7
FPGA, with functionality verified through simulation waveforms and
hardware implementation.

Features

32-bit single-cycle RISC-V processor

Verilog HDL implementation

Modular datapath and control-path design

Register file with two read ports and one write port

ALU supporting arithmetic and logical operations

Immediate value generation

Instruction memory and data memory

Load and store support

Conditional branch support

FPGA implementation on Xilinx Spartan-7

Functional verification using simulation waveforms

Processor Architecture

The processor follows the standard single-cycle architecture, where
every instruction completes within one clock cycle.

Main Modules

Module                              Function

PC                                Stores and updates the address of
the current instruction

Instruction Memory                Stores the program instructions

Control Unit                      Generates control signals based on
the instruction opcode

Register File                     Stores and provides source operands
and receives write-back data

Immediate Generator               Extracts and sign-extends
instruction immediate values

ALU Control                       Determines the ALU operation using
ALUOp, funct3, and function
bits

ALU                               Performs arithmetic and logical
operations

Data Memory                       Supports load and store operations

Datapath Flow

PC
 │
 ▼
Instruction Memory
 │
 ▼
Instruction Decode ───► Control Unit
 │
 ├──► Register File ───► ALU ───► Data Memory
 │         │                │            │
 │         ▼                │            ▼
 └──► Immediate Generator ──┘        Write Back
                                         │
                                         ▼
                                    Register File

Branch Decision ───► Next PC Selection ───► PC

Verification Program

The simulation uses a sequence of instructions to verify different
processor operations.

Instruction             Example Operation       Purpose

addi                  Load immediate values   Immediate and register
into registers          write-back verification

add                   Perform                 ALU operation
register-to-register    verification
addition

sw                    Store ALU result into   Memory write
data memory             verification

lw                    Load data from memory   Memory read and
into a register         write-back verification

beq                   Compare registers and   Branch control
update PC conditionally verification

The waveform sequence demonstrates the processor progressing through
these instructions while generating the corresponding control signals,
ALU results, register updates, memory accesses, and PC values.

Simulation Results

1. Instruction Fetch and Control Signal Verification

The following waveform shows the progression of instructions through the
processor along with signals such as:

PC and next_pc

Instruction and opcode

Immediate output

RegWrite

ALUSrc

MemRead

MemWrite

MemToReg

Branch

ALUOp



2. Register File and ALU Verification

This waveform verifies operand selection and ALU execution. It shows:

Source register selection: rs1 and rs2

Destination register: rd

Register read data

Immediate values

ALU control signals

ALU input operands

ALU result

Zero flag

The results confirm correct arithmetic execution and register write-back
behavior.



3. Data Memory Verification

The following waveform verifies memory operations during store and load
instructions. It includes:

MemRead and MemWrite control signals

Memory address

Write data

Read data

Data memory contents

The waveform demonstrates that data is correctly written to memory
during a store operation and subsequently retrieved during a load
operation.



FPGA Implementation

After functional verification through simulation, the processor design
was synthesized and implemented on a Xilinx Spartan-7 FPGA.

The FPGA implementation validates that the Verilog design can be mapped
from RTL to actual hardware, allowing the processor datapath and control
logic to operate on the target device.

Implementation Flow

Verilog RTL
    │
    ▼
Functional Simulation
    │
    ▼
Synthesis
    │
    ▼
Implementation
    │
    ▼
Bitstream Generation
    │
    ▼
Xilinx Spartan-7 FPGA

Project Structure

RISC-V-Processor/
│
├── src/
│   ├── single_cycle_cpu.v
│   ├── pc.v
│   ├── instruction_memory.v
│   ├── control_unit.v
│   ├── register_file.v
│   ├── immediate_generator.v
│   ├── alu_control.v
│   ├── alu.v
│   └── data_memory.v
│
├── simulation/
│   └── testbench.v
│
├── waveform1.png
├── waveform2.png
├── waveform3.png
│
└── README.md



Tools Used

Verilog HDL

Xilinx Vivado

Xilinx Spartan-7 FPGA

Vivado Simulator / behavioral simulation tools

Key Learning Outcomes

Designed a complete single-cycle processor datapath

Implemented instruction decoding and control logic

Developed and integrated ALU and ALU control logic

Implemented register file and memory interfaces

Verified load, store, arithmetic, and branch operations

Analyzed processor behavior using simulation waveforms

Synthesized and implemented the design on an FPGA

Future Improvements

Possible extensions include:

Multi-cycle or pipelined implementation

Hazard detection and forwarding

Additional RISC-V instructions

UART or GPIO-based input/output

Larger instruction and data memories

Hardware debugging using FPGA logic analysis tools

Author

Osheen Mahajan
RISC-V Processor Design and FPGA Implementation
